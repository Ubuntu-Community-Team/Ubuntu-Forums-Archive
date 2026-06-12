---
title: "Zyxel Errors??"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by BKK on 2006-05-09
I am trying to instal amedyn driver for Zyxel 630-11
I have installed the required packages ( i think>)
I get this error when I make or sudo make...

jkbo@ubuntu:/usr/amedyn$ make
cd init && make clean
make[1]: Entering directory `/usr/amedyn/init'
rm -f amload amioctl amloaddbg amloaddbgt
make[1]: Leaving directory `/usr/amedyn/init'
cd module && make clean
make[1]: Entering directory `/usr/amedyn/module'
rm -f *.o .*.flags *.ko *.mod.* .*.o.cmd .*.ko.cmd
make[1]: Leaving directory `/usr/amedyn/module'
cd bridged && make clean
make[1]: Entering directory `/usr/amedyn/bridged'
rm -f br2684ctl
make[1]: Leaving directory `/usr/amedyn/bridged'
cd amcontrol && make clean
make[1]: Entering directory `/usr/amedyn/amcontrol'
rm -f amcontrol amcontroldbg amcontroldbgt
make[1]: Leaving directory `/usr/amedyn/amcontrol'
cd init && make && make install
make[1]: Entering directory `/usr/amedyn/init'
gcc -O2 -Wstrict-prototypes -fomit-frame-pointer -pipe -march=i686 -Wall -DLINUX -Wsign-compare -I../include -lusb  amload.c -o amload
amload.c: In function &#3650;€&#152;jump_to_address&#3650;€&#153;:
amload.c:400: warning: pointer targets in passing argument 3 of &#3650;€&#152;send_bulk&#3650;€&#153; differ in signedness
amload.c:405: warning: pointer targets in passing argument 3 of &#3650;€&#152;send_bulk&#3650;€&#153; differ in signedness
amload.c: In function &#3650;€&#152;send_cmds_sync&#3650;€&#153;:
amload.c:420: warning: pointer targets in passing argument 6 of &#3650;€&#152;transfer_ctrl_msg&#3650;€&#153; differ in signedness
amload.c:425: warning: pointer targets in passing argument 6 of &#3650;€&#152;transfer_ctrl_msg&#3650;€&#153; differ in signedness
amload.c:430: warning: pointer targets in passing argument 6 of &#3650;€&#152;transfer_ctrl_msg&#3650;€&#153; differ in signedness
amload.c:435: warning: pointer targets in passing argument 6 of &#3650;€&#152;transfer_ctrl_msg&#3650;€&#153; differ in signedness
amload.c:443: warning: pointer targets in passing argument 6 of &#3650;€&#152;transfer_ctrl_msg&#3650;€&#153; differ in signedness
amload.c: In function &#3650;€&#152;load_firmware&#3650;€&#153;:
amload.c:513: warning: pointer targets in assignment differ in signedness
amload.c:519: warning: pointer targets in passing argument 3 of &#3650;€&#152;send_block&#3650;€&#153; differ in signedness
amload.c:525: warning: pointer targets in passing argument 3 of &#3650;€&#152;send_bulk&#3650;€&#153; differ in signedness
amload.c:532: warning: pointer targets in passing argument 3 of &#3650;€&#152;read_bulk&#3650;€&#153; differ in signedness
amload.c:547: warning: pointer targets in passing argument 3 of &#3650;€&#152;send_block&#3650;€&#153; differ in signedness
amload.c:551: warning: pointer targets in passing argument 3 of &#3650;€&#152;send_bulk&#3650;€&#153; differ in signedness
amload.c:572: warning: pointer targets in passing argument 6 of &#3650;€&#152;transfer_ctrl_msg&#3650;€&#153; differ in signedness
amload.c:586: warning: pointer targets in passing argument 6 of &#3650;€&#152;transfer_ctrl_msg&#3650;€&#153; differ in signedness
amload.c:603: warning: pointer targets in passing argument 6 of &#3650;€&#152;transfer_ctrl_msg&#3650;€&#153; differ in signedness
amload.c:628: warning: pointer targets in passing argument 3 of &#3650;€&#152;usb_bulk_read&#3650;€&#153; differ in signedness
gcc -O2 -Wstrict-prototypes -fomit-frame-pointer -pipe -march=i686 -Wall -DLINUX -Wsign-compare -I../include -lusb  amioctl.c -o amioctl
make[1]: Leaving directory `/usr/amedyn/init'
make[1]: Entering directory `/usr/amedyn/init'
install -c -m 755 -p amload amioctl /usr/sbin
install: cannot remove `/usr/sbin/amload': Permission denied
install: cannot remove `/usr/sbin/amioctl': Permission denied
make[1]: *** [install_program] Error 1
make[1]: Leaving directory `/usr/amedyn/init'
make: *** [AME_INIT] Error 2

I dont know what to do!!

---

