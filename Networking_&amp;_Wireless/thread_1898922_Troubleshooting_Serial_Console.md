---
title: "Troubleshooting Serial Console"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by toiq on 2011-12-22
Hi all,
 
 This is my first post here.
 
 I have been using Ubuntu since 6.06 and until now have been able to solve all my problems just googling, but I have been stuck with this for weeks.
 
 I am trying to set up a serial console to further investigate why my home server is randomly hanging.
 
The server is not physically accessible so I planned to run a serial connection through rj45. This didn't work. I thought it might be the cable or the DB9-rj45 adapters so I brang the server to the living room and bought a null modem cable. This also didnt work. I have electrically checked the cable and it is OK. It is a null model cable with hardware negotiation, like this: [http://en.wikipedia.org/wiki/File:D9_Null_Modem_Wiring.png](http://en.wikipedia.org/wiki/File:D9_Null_Modem_Wiring.png)

So it must be either the serial ports are wrong or a configuration issue.

I'm following [https://help.ubuntu.com/community/SerialConsoleHowto#fndef-283362bf341d9e44937bd88d7d77896f17b0f175-0](https://help.ubuntu.com/community/SerialConsoleHowto#fndef-283362bf341d9e44937bd88d7d77896f17b0f175-0)
 
Computers are as follows:
 
Server:  
 -Motherboard: Intel D945GSEJT
 -Processor: integrated Atom N270
 -OS: Ubuntu Server 10.04.3 LTS
 -Kernel: 2.6.32-34-generic-pae
 
 Client:
 -Motherboard: AsRock H61M/U3S3
 -Processor: Intel G620T
 -OS: Ubuntu Server 8.0.4.4 LTS
 -Kernel: 2.6.24-29-generic
 
Both have integrated serial ports which I am trying to use. Both seem to work:
 
Server:
 
```
sudo stty -a -F /dev/ttyS0  
 
speed 9600 baud; rows 0; columns 0; line = 0;  
 intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>; eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;  
 werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;  
 -parenb -parodd cs8 hupcl -cstopb cread clocal -crtscts  
 -ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr -icrnl -ixon -ixoff -iuclc -ixany -imaxbel -iutf8  
 -opost -olcuc -ocrnl -onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0  
 -isig -icanon -iexten -echo -echoe -echok -echonl -noflsh -xcase -tostop -echoprt -echoctl -echoke
```Client:
 
```
stty -a -F /dev/ttyS0  
 
speed 9600 baud; rows 0; columns 0; line = 0;  
 intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>; eol2 = <undef>; swtch = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R;  
 werase = ^W; lnext = ^V; flush = ^O; min = 1; time = 0;  
 -parenb -parodd cs8 hupcl -cstopb cread clocal -crtscts  
 -ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff -iuclc -ixany -imaxbel -iutf8 
 opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0  
 isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt echoctl echoke
```This is what I am doing:
 
On the server:
 
 Check serial ports are enabled
 
```
dmesg |grep tty  
[    0.000000] console [tty0] enabled  
 [    2.134827] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A  
 [    2.135072] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A  
 [    2.136073] 00:03: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A  
 [    2.136559] 00:04: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
```Create  /etc/init/ttyS0.conf:  
```
# ttyS0 - getty  
 #  
 # This service maintains a getty on ttyS0 from the point the system is  
 # started until it is shut down again.  
 
 start on stopped rc or RUNLEVEL=[2345]  
 stop on runlevel [!2345]  
  
 respawn  
 exec /sbin/getty -L 9600 ttyS0 vt102
```Status of ttyS0 before starting getty
```
ls -l /dev/ttyS0  
 crw-rw---- 1 root dialout 4, 64 2011-12-22 14:21 /dev/ttyS0
```Start getty
```
sudo start ttyS0  
 ttyS0 start/running, process 1135
```Status of ttyS0 after starting getty, now owned by root
```
/etc/init$ ls -l /dev/ttyS0  
 crw------- 1 root root 4, 64 2011-12-22 14:42 /dev/ttyS0
```Check if getty is running on ttyS0
```
ps -A|grep tty  
   
740 tty4     00:00:00 getty  
   744 tty5     00:00:00 getty  
   748 tty2     00:00:00 getty  
   749 tty3     00:00:00 getty  
   753 tty6     00:00:00 getty  
   966 tty1     00:00:00 getty  
   967 ttyS0    00:00:00 getty
```So I assume the computer should be listening for connections at ttyS0, which is owned by root
 
 On the client:
 
 Check permissions on /dev/ttyS0
 
```
ls -l /dev/ttyS0  
 crw-rw---- 1 root dialout 4, 64 2011-12-22 12:57 /dev/ttyS0
``````
id -Gn |grep dialout  
 user adm lp dialout cdrom floppy audio dip video plugdev fuse mythtv admin lpadmin  
```So I do sudo minicom -s and set up serial device to ttyS0 and baudrate to 9600
 
 I never get connected to the host.
 
My minicom.log file looks like this:
 
 ```
cat minicom.log  
 20111222 14:52:57 Hangup (0:00:34)  
 20111222 14:53:13 Quit without reset while online.  
 20111222 14:55:06 Hangup (0:01:30)  
 20111222 15:17:29 Hangup (0:00:18)  
 20111222 15:17:59 Hangup (0:00:04)
```Have tried with and without hardware control, and with different baudrates. Also tried changing IRQs in BIOS. Since the server has 2 serial ports, I even tried to connect from ttyS1 to ttyS0.
 
 Is there anything than can be done to isolate the problem? How can I check if the server is really listening?

Any help will be much appreciated.

---

### Post by toiq on 2012-01-26
Hi all,

After trying everything I could think of, I found the cause. The bracket that connect to the headers in the motherboard were wrong.

---

