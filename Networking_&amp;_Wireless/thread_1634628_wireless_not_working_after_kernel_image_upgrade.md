---
title: "wireless not working after kernel image upgrade"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by vcrpex on 2010-11-30
hi,
I have been using ubuntu for the last two years, mostly resolved issues from going through the forum here. Recently I updated my kernel image to 2.6.35-23-generic #40, but my wireless stop working. I have to drop down to 2.6.35-22-generic #35 which I am currently using to surf and post to get some help here. My wireless card is Asus USB n10, I followed the instructions previously from [http://ubuntuforums.org/showthread.php?t=1572991&highlight=asus+usb+n10]("http://ubuntuforums.org/showthread.php?t=1572991&highlight=asus+usb+n10") and it worked. But when I do the same after the kernel update, it does not work anymore. I hope I can use the latest one update, else i just have to stick to 2.6.35.22-generic for now. my logs are as below:

terence@terence-M68MT-D3:~$ uname -a
Linux terence-M68MT-D3 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:14:33 UTC 2010 x86_64 GNU/Linux

terence@terence-M68MT-D3:~$ iwconfig wlan0
wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

terence@terence-M68MT-D3:~$ lsmod | grep "r8192"
r8192s_usb            317763  0 
eeprom_93cx6            1789  1 r8192s_usb

terence@terence-M68MT-D3:~$ sudo iwlist wlan0 scan
[sudo] password for terence: 
wlan0     Interface doesn't support scanning : Network is down

terence@terence-M68MT-D3:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:54:4d:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:177072 (177.0 KB)  TX bytes:177072 (177.0 KB)


any help will be truly appreciated. 
thanks in advance

---

