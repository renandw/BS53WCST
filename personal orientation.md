
esptool.py -p /dev/ttyUSB0 --baud 115200 write_flash -fs 8m -fm dout -ff 40m 0x0 rboot.bin 0x1000 blank_config.bin 0x2000 otaboot.bin



openssl sha384 -binary -out firmware/BS53WCST.bin.sig firmware/BS53WCST.bin

printf "%08x" `cat firmware/BS53WCST.bin | wc -c`| xxd -r -p >>firmware/BS53WCST.bin.sig




openssl sha384 -binary -out firmware/BS53WCST.bin.sig firmware/BS53WCST.bin
printf "%08x" `cat firmware/BS53WCST.bin | wc -c`| xxd -r -p >>firmware/BS53WCST.bin.sig

cp BS53WCST.bin /media/sf_Shared-Homekit-Files
cp BS53WCST.bin.sig /media/sf_Shared-Homekit-Files



esptool.py -p /dev/ttyUSB0 --baud 115200 write_flash -fs 8m -fm dout -ff 40m 0x0 rboot.bin 0x1000 blank_config.bin 0x2000 ledstrip.bin
