---
title: "Need Support For installng ZTE PCMCIA Wireless Card MC315+"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by Rishik4 on 2009-03-28
HI Guys,

I have recently upgraded from windows vista to ubuntu and im really happy about it.

i have been using a reliance internet connection and a ZTE MC315+ pcmcia type 2 datacard for mobile internet access.

Please support me to set it up for ubuntu. i am an absolute beginner and thus need to be guided step by step.

Thank You.
Regards,
Rishi.

---

### Post by pytheas22 on 2009-03-28
Please plug the device in, then post the output of these commands:
```

lshw -C Network
cat /proc/bus/usb/devices
```

With that information, I should be able to give you step-by-step instructions for making it work.

(This is based off a guide [here]("http://prithisd.blogspot.com/2007/12/reliance-zte-cdma-1x-mg880-working-with.html")--but I'm noting this more for my benefit than yours.)

---

### Post by Rishik4 on 2009-04-04
Hi Pytheas,

I am really thankful for Your Support :-).

For The Command :
lshw - C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:8c:07:14
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.7 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:37:d9:0d:91
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:54:62:77:81:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
rishi@rishi-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:8c:07:14
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.7 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:37:d9:0d:91
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:54:62:77:81:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

and for the command :
rishi@rishi-laptop:~$ cat /proc/bus/usb/devices
cat: /proc/bus/usb/devices: No such file or directory

(The ZTE MC 315+ Card Is A PCMCIA Type 2 Data Card just thought i should let u know if it helps.)

---

### Post by pytheas22 on 2009-04-04
Sorry, I thought it was a USB device for some reason and didn't ask for the appropriate output as a result.  Could you please post the output of this command right after plugging in the device:
```

dmesg | tail -30
```

I think [this page]("http://prithisd.blogspot.com/2007/07/reliance-zte-mc315-on-ubuntu-feisty-704.html") and [this page]("http://www.rimweb.in/forums/index.php?showtopic=9409") have instructions for making it work with a PCMCIA device.

---

### Post by Rishik4 on 2009-04-04
Hi this is what i got for command :
~$ dmesg | tail -30


[10912.267997] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=98.227.127.103 DST=10.0.0.2 LEN=48 TOS=0x00 PREC=0x00 TTL=44 ID=11796 DF PROTO=TCP SPT=61279 DPT=45788 WINDOW=65535 RES=0x00 SYN URGP=0 
[10912.840281] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=60.241.171.51 DST=10.0.0.2 LEN=70 TOS=0x00 PREC=0x00 TTL=49 ID=20138 PROTO=UDP SPT=58106 DPT=45788 LEN=50 
[10913.147710] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=85.229.84.156 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=110 ID=2010 PROTO=UDP SPT=60599 DPT=45788 LEN=71 
[10913.223571] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=62.112.203.141 DST=10.0.0.2 LEN=93 TOS=0x00 PREC=0x00 TTL=108 ID=31669 PROTO=UDP SPT=62539 DPT=45788 LEN=73 
[10913.271757] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=98.227.127.103 DST=10.0.0.2 LEN=48 TOS=0x00 PREC=0x00 TTL=44 ID=10304 DF PROTO=TCP SPT=61279 DPT=45788 WINDOW=65535 RES=0x00 SYN URGP=0 
[10913.522228] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=68.230.57.112 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=107 ID=48066 PROTO=UDP SPT=59753 DPT=45788 LEN=71 
[10913.651333] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=24.215.184.187 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=48 ID=20030 PROTO=UDP SPT=1150 DPT=45788 LEN=71 
[10913.795688] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=66.206.245.112 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=33011 PROTO=UDP SPT=57007 DPT=45788 LEN=71 
[10913.882135] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=88.8.227.238 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=40604 PROTO=UDP SPT=28802 DPT=45788 LEN=71 
[10914.284652] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=98.227.127.103 DST=10.0.0.2 LEN=48 TOS=0x00 PREC=0x00 TTL=44 ID=29956 DF PROTO=TCP SPT=61279 DPT=45788 WINDOW=65535 RES=0x00 SYN URGP=0 
[10915.169805] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=82.34.204.144 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=110 ID=1518 PROTO=UDP SPT=39387 DPT=45788 LEN=71 
[10915.268306] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=216.121.150.151 DST=10.0.0.2 LEN=93 TOS=0x00 PREC=0x00 TTL=111 ID=20611 PROTO=UDP SPT=45714 DPT=45788 LEN=73 
[10915.393433] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=81.33.170.17 DST=10.0.0.2 LEN=93 TOS=0x00 PREC=0x00 TTL=112 ID=26992 PROTO=UDP SPT=62554 DPT=45788 LEN=73 
[10915.926880] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=87.15.167.201 DST=10.0.0.2 LEN=70 TOS=0x00 PREC=0x00 TTL=110 ID=59160 PROTO=UDP SPT=58397 DPT=45788 LEN=50 
[10916.012620] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=83.119.184.11 DST=10.0.0.2 LEN=93 TOS=0x00 PREC=0x00 TTL=48 ID=60933 PROTO=UDP SPT=54256 DPT=45788 LEN=73 
[10916.088721] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=87.15.167.201 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=110 ID=59193 PROTO=UDP SPT=58397 DPT=45788 LEN=71 
[10916.188102] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=81.57.62.107 DST=10.0.0.2 LEN=93 TOS=0x00 PREC=0x00 TTL=106 ID=18732 PROTO=UDP SPT=28104 DPT=45788 LEN=73 
[10916.295540] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=98.227.127.103 DST=10.0.0.2 LEN=48 TOS=0x00 PREC=0x00 TTL=44 ID=47107 DF PROTO=TCP SPT=61279 DPT=45788 WINDOW=65535 RES=0x00 SYN URGP=0 
[10918.900153] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=83.57.97.165 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=15265 PROTO=UDP SPT=34635 DPT=45788 LEN=71 
[10919.650102] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=77.225.255.6 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=111 ID=32511 PROTO=UDP SPT=10235 DPT=45788 LEN=71 
[10920.008939] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=74.57.64.132 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=45 ID=60330 PROTO=UDP SPT=37260 DPT=45788 LEN=71 
[10920.322864] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=98.227.127.103 DST=10.0.0.2 LEN=48 TOS=0x00 PREC=0x00 TTL=44 ID=23573 DF PROTO=TCP SPT=61279 DPT=45788 WINDOW=65535 RES=0x00 SYN URGP=0 
[10920.468567] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=212.67.69.242 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=6881 DPT=45788 LEN=71 
[10920.636374] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=96.52.129.82 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=105 ID=32446 PROTO=UDP SPT=51352 DPT=45788 LEN=71 
[10921.181859] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=91.15.68.62 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=28006 PROTO=UDP SPT=41970 DPT=45788 LEN=71 
[10921.471806] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=99.33.249.65 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=110 ID=11245 PROTO=UDP SPT=45668 DPT=45788 LEN=71 
[10921.703177] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=82.6.187.106 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=47 ID=607 PROTO=UDP SPT=21100 DPT=45788 LEN=71 
[10921.742569] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=89.12.164.52 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=25107 PROTO=UDP SPT=8500 DPT=45788 LEN=71 
[10921.891429] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=87.68.158.205 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=109 ID=64169 PROTO=UDP SPT=16587 DPT=45788 LEN=71 
[10924.166460] Inbound IN=wlan0 OUT= MAC=00:1f:3c:8c:07:14:00:1b:2f:fe:10:a2:08:00 SRC=90.157.252.222 DST=10.0.0.2 LEN=91 TOS=0x00 PREC=0x00 TTL=109 ID=62998 PROTO=UDP SPT=53992 DPT=45788 LEN=71 

Thanks Again - Rishi.

---

### Post by pytheas22 on 2009-04-05
ahhh, sorry, that wasn't the output I needed either.  It looks like something weird is going on and your dmesg is being spammed with information that's not relevant to us.  Please plug your device in, then post the output of this command:
```

dmesg
```

It will probably be pretty long, but please post it all.  Also, it might help if you did this after a fresh reboot, to reduce the amount of spam clogging up dmesg.

Sorry for asking you for all this information, but once I figure out the information I need (which is some stuff that identifies the exact parameters of your wireless card), it shouldn't be too hard to solve your problem.

---

### Post by Rishik4 on 2009-04-05
hi Pytheas, thx again, u can ask all the info you need i really need this one working. Please Find Attached The Text Document.

Thanks
Rishi

---

### Post by pytheas22 on 2009-04-05
Thanks for that.  I finally have the information I need.  According to the tutorials I linked to earlier, this is what you should do to connect:

1. install the necessary utilities, if you haven't already, by typing:
```

sudo apt-get install wvdial setserial
```

2. open your wvdial.conf file by typing:
```

sudo gedit /etc/wvdial.conf
```

Erase everything that's in the file currently, and replace it with this:
```

[Dialer Defaults]
Modem = /dev/ttyS3
Baud = 57600
SetVolume = 0
Dial-AT-OK ATDT Command =
Init1 = ATZ
FlowControl = Hardware (CRTSCTS)
Phone = #777
Username =
Password =
New PPPD = yes
Carrier Check = no
Stupid Mode = 1
```

Be sure to fill in your username and password as appropriate.  Then save and close the file.

3. run these two commands to connect (please post all output):
```

setserial /dev/ttyS3 baud_base 460800
wvdial
```

Hopefully this will work, but one of the tutorials mentions having to experiment with different baud rates to get the right one, so don't be too upset if you don't connect on the first try.  We can keep at it till we get the right settings (and once we figure them out, we can hopefully also find a way to set this up so you don't have to connect from the command line each time).

---

### Post by Rishik4 on 2009-04-05
Hi,
I Ran the First Set And Edited And Saved The Document. But When I Ran The Second Set Of Commands Output is:

rishi@rishi-laptop:~$ setserial /dev/ttyS3 baud_base 460800
/dev/ttyS3: No such device
rishi@rishi-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyS3: No such device
--> Cannot open /dev/ttyS3: No such device
--> Cannot open /dev/ttyS3: No such device

Thx
Rishi

---

### Post by pytheas22 on 2009-04-06
The problem may have been that you needed to run those commands as root.  Please run:
```

sudo setserial /dev/ttyS3 baud_base 460800
sudo wvdial
```

and post the output.

---

### Post by Rishik4 on 2009-04-06
Hi Pytheas,
The output is :

root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS3 baud_base 460800
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyS3: Input/output error
--> Cannot open /dev/ttyS3: Input/output error
--> Cannot open /dev/ttyS3: Input/output error

Thanks
Rishi

---

### Post by pytheas22 on 2009-04-06
I'm wondering if maybe the modem got changed from /dev/ttyS3 to something else.  Please open your /etc/wvdial.conf file again by typing:
```

sudo gedit /etc/wvdial.conf
```

Look for the line that says 'Modem = /dev/ttyS3' and change it to 'Modem = /dev/ttyS0'.  Then run:
```

sudo setserial /dev/**ttyS0** baud_base 460800
sudo wvdial
```

If this doesn't work, please repeat the steps above, replacing 'ttyS0' with 'ttyS1' and 'ttyS2' (there is no ttyS4 or higher).  Is the output the same in every case?

---

### Post by Rishik4 on 2009-04-06
Hi Pytheas,
There is an error output: 

root@rishi-laptop:/home/rishi# sudo etc/wvdial.conf
sudo: etc/wvdial.conf: command not found

Please Help.
Thanks
Rishi

---

### Post by pytheas22 on 2009-04-07
> There is an error output

Ahh, sorry, I made a mistake in the command I told you to type (I fixed it in the original post).  You should type:
```

sudo gedit /etc/wvdial.conf
```

I forgot the 'gedit' part before.  Please try again with the updated command and let me know how it goes.  Sorry for the mistake.

---

### Post by Rishik4 on 2009-04-07
Hi Pytheas,

rishi@rishi-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

I think you may crack it the next time!
Thanks
Rishi.

---

### Post by pytheas22 on 2009-04-07
Alright, I think we're to the point where we need to experiment with different baud rates until we hit the right one (the tutorials mention having to do this).  Please run the following commands and post the output--hopefully one of them will hit the right rate:
```

sudo setserial /dev/ttyS0 baud_base 115200
sudo wvdial
sudo setserial /dev/ttyS0 baud_base 230400
sudo wvdial
sudo setserial /dev/ttyS0 baud_base 460800
sudo wvdial
sudo setserial /dev/ttyS0 baud_base 921600
sudo wvdial
```

Please give each of these a try and post the output for each one.  Also, note that in the commands above, you're using 'ttyS0'.  If you get a 'device not found' message like you did earlier, change 'ttyS0' to the appropriate value ('ttyS1', 'ttyS2', etc...).

---

### Post by Rishik4 on 2009-04-07
Hi I Got All Replys As Modem Not Responding :

rishi@rishi-laptop:~$ sudo su
[sudo] password for rishi: 
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 baud_base 115200
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 baud_base 230400
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 baud_base 460800
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 baud_base 921600
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Does This Help!
Thanks!
Rishi

---

### Post by pytheas22 on 2009-04-07
Please give these a try and post the output:

```
sudo setserial /dev/ttyS0 baud_base 57600
sudo wvdial
sudo setserial /dev/ttyS0 baud_base 230400
sudo setserial /dev/ttyS0 uart 8250
sudo wvdial
sudo setserial /dev/ttyS0 uart 16450
sudo wvdial
sudo setserial /dev/ttyS0 uart 16550
sudo wvdial
sudo setserial /dev/ttyS0 uart 16550A
sudo wvdial
sudo setserial /dev/ttyS0 uart 16650V2
sudo wvdial
sudo setserial /dev/ttyS0 uart 16750
sudo wvdial
sudo setserial /dev/ttyS0 uart 16850
sudo wvdial
sudo setserial /dev/ttyS0 uart 16950
sudo wvdial
sudo setserial /dev/ttyS0 uart 16954
sudo wvdial
```

Hopefully one of those will get it.

---

### Post by Rishik4 on 2009-04-07
Hi Pytheas,
No Luck

root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 baud_base 57600
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 baud_base 230400
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 uart 8250
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 uart 16450
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 uart 16550
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 uart 16550A
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 uart 16550V2
Illegal UART type: 16550V2
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 uart 16750
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 uart 16850
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 uart 16950
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@rishi-laptop:/home/rishi# sudo setserial /dev/ttyS0 uart 16954
root@rishi-laptop:/home/rishi# sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Thanks
Rishi

---

### Post by Rishik4 on 2009-04-07
Hi Pytheas,
I Also Tried With baud_base 460800... same result. :-(

rishi@rishi-laptop:~$ sudo setserial /dev/ttyS0 baud_base 460800
rishi@rishi-laptop:~$ sudo setserial /dev/ttyS0 uart 8250
rishi@rishi-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
rishi@rishi-laptop:~$ sudo setserial /dev/ttyS0 uart 16450
rishi@rishi-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
rishi@rishi-laptop:~$ sudo setserial /dev/ttyS0 uart 16550
rishi@rishi-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
rishi@rishi-laptop:~$ sudo setserial /dev/ttyS0 uart 16550A
rishi@rishi-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
rishi@rishi-laptop:~$ sudo setserial /dev/ttyS0 uart 16550V2
Illegal UART type: 16550V2
rishi@rishi-laptop:~$ sudo setserial /dev/ttyS0 uart 16750
rishi@rishi-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
rishi@rishi-laptop:~$ sudo setserial /dev/ttyS0 uart 16950
rishi@rishi-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
rishi@rishi-laptop:~$ sudo setserial /dev/ttyS0 uart 16954
rishi@rishi-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Thanks
Rishi

---

### Post by Rishik4 on 2009-04-07
I also did the same for 
baud_base 57600
baud_base 115200
baud_base 921600

same result!

Buddy Pl Help!

Thanks
Rishi.

---

### Post by pytheas22 on 2009-04-07
Rishi: sorry it's still not working.  I've noticed that there's an 'autoconfig' option for the 'setserial' command in Ubuntu.  None of the tutorials mention this (maybe it didn't exist when they were written), but at this point it's worth a try.  So please run:
```

sudo setserial /dev/ttyS3 autoconfig
sudo wvdial
```

Any luck?

---

### Post by GeorgeVita on 2009-04-08
Hi **pytheas22** and **Rishik4**,

I am attending this post as it is interesting and so HARD to make it work!
Trying to help I would like to note that reading links from post #4 of this thread:

from 1st link:

> 
1. Now my dmesg says (after inserting a card in pcmcia slot);

[ 2713.564000] pccard: PCMCIA card inserted into slot 0
[ 2713.564000] pcmcia: registering new device pcmcia0.0
[ 2713.612000] ttyS3: detected caps 00000700 should be 00000100
[ 2713.612000] 0.0: ttyS3 at I/O 0x2e8 (irq = 3) is a 16C950/954


and from the 2nd link:

> 
...
The trick is simple - you have to play with the UART and the baud_base.

Just run setserial on your machine and it will give the following output for UART and baud_base

* uart set UART type (none, 8250, 16450, 16550, 16550A,
16650, 16650V2, 16750, 16850, 16950, 16954)
* baud_base set base baud rate (CLOCK_FREQ / 16)
...


Determining the port will minimize the painful tests.

Hope you will succeed it!
George

---

### Post by Rishik4 on 2009-04-08
Hi Pytheas

rishi@rishi-laptop:~$ sudo setserial /dev/ttyS3 autoconfig
rishi@rishi-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyS0: Input/output error
--> Cannot open /dev/ttyS0: Input/output error
--> Cannot open /dev/ttyS0: Input/output error
rishi@rishi-laptop:~$ sudo setserial /dev/ttyS0 autoconfig
rishi@rishi-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyS0: Input/output error
--> Cannot open /dev/ttyS0: Input/output error
--> Cannot open /dev/ttyS0: Input/output error

This is what i had. btw we did not set up any clock frequency

Thanks

Rishi

---

### Post by GeorgeVita on 2009-04-08
Hi **pytheas22** and **Rishik4**,

trying to self educate in subject "modems with Ubuntu" and as this is a real "hard" case, I borrowed an old DACOM/PSION pcmcia card inserted in my Toshiba Satellite L30-113 running Ubuntu 8.10, noticed the following lines in the **dmesg** output:

[ 6107.384575] cs: memory probe 0xc0100000-0xc01fffff: excluding 0xc0100000-0xc011ffff
[ 6107.395938] pcmcia: registering new device pcmcia0.0
[ 6107.604351] 0.0: **ttyS2** at I/O 0x3e8 (irq = 3) is a **16550A**

Then I tryied **minicom -s** (downloaded via Synaptic Package Manager for debugging purposes) and I did a "Serial Port Setup" to use **/dev/ttyS2** (as stated in dmesg output). The default baud rate was 115200 N81 and Hardware Flow Control=Yes.

The result is that I can handle the modem (AT, ATZ, AT&V tested).

Hope this will help.

Regards
George

---

### Post by pytheas22 on 2009-04-08
Rishi: please give this a try.  I think it should cover every possible permutation of baud_rate and uart (sorry it's so long).  If this doesn't work, we may have to go back to Google...

(Be sure to replace '/dev/ttyS3' with the appropriate string for your device, and make sure that the right device is also specified on the 'Modem=/dev/XXX' line of /etc/wvdial.conf.)

```
sudo setserial /dev/ttyS3 uart 8250
setserial /dev/ttyS3 baud_base 115200
sudo wvdial
setserial /dev/ttyS3 baud_base 230400
sudo wvdial
setserial /dev/ttyS3 baud_base 460800
sudo wvdial
setserial /dev/ttyS3 baud_base 921600
sudo wvdial

sudo setserial /dev/ttyS3 uart 16540
setserial /dev/ttyS3 baud_base 115200
sudo wvdial
setserial /dev/ttyS3 baud_base 230400
sudo wvdial
setserial /dev/ttyS3 baud_base 460800
sudo wvdial
setserial /dev/ttyS3 baud_base 921600
sudo wvdial

sudo setserial /dev/ttyS3 uart 16550
setserial /dev/ttyS3 baud_base 115200
sudo wvdial
setserial /dev/ttyS3 baud_base 230400
sudo wvdial
setserial /dev/ttyS3 baud_base 460800
sudo wvdial
setserial /dev/ttyS3 baud_base 921600
sudo wvdial

sudo setserial /dev/ttyS3 uart 16550A
setserial /dev/ttyS3 baud_base 115200
sudo wvdial
setserial /dev/ttyS3 baud_base 230400
sudo wvdial
setserial /dev/ttyS3 baud_base 460800
sudo wvdial
setserial /dev/ttyS3 baud_base 921600
sudo wvdial

sudo setserial /dev/ttyS3 uart 16550V2
setserial /dev/ttyS3 baud_base 115200
sudo wvdial
setserial /dev/ttyS3 baud_base 230400
sudo wvdial
setserial /dev/ttyS3 baud_base 460800
sudo wvdial
setserial /dev/ttyS3 baud_base 921600
sudo wvdial


sudo setserial /dev/ttyS3 uart 16750
setserial /dev/ttyS3 baud_base 115200
sudo wvdial
setserial /dev/ttyS3 baud_base 230400
sudo wvdial
setserial /dev/ttyS3 baud_base 460800
sudo wvdial
setserial /dev/ttyS3 baud_base 921600
sudo wvdial

sudo setserial /dev/ttyS3 uart 16850
setserial /dev/ttyS3 baud_base 115200
sudo wvdial
setserial /dev/ttyS3 baud_base 230400
sudo wvdial
setserial /dev/ttyS3 baud_base 460800
sudo wvdial
setserial /dev/ttyS3 baud_base 921600
sudo wvdial

sudo setserial /dev/ttyS3 uart 16950
setserial /dev/ttyS3 baud_base 115200
sudo wvdial
setserial /dev/ttyS3 baud_base 230400
sudo wvdial
setserial /dev/ttyS3 baud_base 460800
sudo wvdial
setserial /dev/ttyS3 baud_base 921600
sudo wvdial

sudo setserial /dev/ttyS3 uart 16954
setserial /dev/ttyS3 baud_base 115200
sudo wvdial
setserial /dev/ttyS3 baud_base 230400
sudo wvdial
setserial /dev/ttyS3 baud_base 460800
sudo wvdial
setserial /dev/ttyS3 baud_base 921600
sudo wvdial
```

George: thanks for your suggestion.  I'm learning this as I go as well.  I'm a little confused as to what exactly you did with minicom.  Did you find a way to make it tell you which values you should use for baud_rate and uart?  If so, could you please explain exactly how you found them?

Also, just for note, there's another guide [here]("http://www.freelists.org/post/saint/HOW-TO-Reliance-Data-Card-ZTE-MC315") (basically it says the same thing as the others, but it seems to be written more clearly).

---

### Post by GeorgeVita on 2009-04-09
> **pytheas22 said:**
> ...
George: thanks for your suggestion.  I'm learning this as I go as well.  I'm a little confused as to what exactly you did with minicom.  Did you find a way to make it tell you which values you should use for baud_rate and uart?  If so, could you please explain exactly how you found them?
...


The only note I have is that as you suggest in post#6 the **dmesg** command will show the **/dev/ttySx** and the **UART** detected. Assumed this function works well in 8.10, **Rishik4** has to try only the baudrates.

In my test I found that **dmesg** shows other port and uart (in my case) that worked with **minicom**. In the past I have faced many problems when system (wvdial, minicom or network manager) "hold" a port causing it unusable unless you restart!

I used **minicom** as it is a very old program and it possibly handles better the baudrate & uart (automatically). Finally and unfortunately I borrowed a Huawei E620 PCMCIA card that detected directly by the system assigning some /dev/ttyUSBx ports so I could not simulate the problem locally.

Hope I am not out of this subject!
Regards,
George

---

### Post by Rishik4 on 2009-04-15
Hi Guys,
Thanks For All Your Help! :-). U were really amazing.

I Tried All Of That... But The Same result modem not responding... i then thought something was wrong with my hardware... so i installed windows xp on my laptop... it works fine... outlook also works better with my blackberry mobile than ubuntu... I hate to do this... my network costs will increase by 10X but i will have to stick to windows xp and outlook in the foreseeable future! :-(
    It was a privilege being a ubuntu user.
Thanks Once Again
Regards
Rishi

---

### Post by GeorgeVita on 2009-04-16
sorry, wrong post

---

### Post by pytheas22 on 2009-04-16
Rishi: I'm very disappointed it didn't work out, but I hope you'll give Ubuntu another try in the future.  Best of luck.

---

