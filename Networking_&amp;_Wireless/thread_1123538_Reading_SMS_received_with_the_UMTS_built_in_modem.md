---
title: "Reading SMS received with the UMTS built in modem"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by mpolito1969 on 2009-04-12
I connect to internet using a laptop with built in UMTS (HSDPA) modem.

With Ubuntu 8.10 everything is alright, I've got only one problem: I can't read SMS I receive to this SIM.

It's important because I get information from my ISP provider and to read them I have to boot in Windows Vista or removing the SIM from the laptop and inserting it in my phone.

Is there a way to read SMS from Linux?

ciao,
Max

---

### Post by demank on 2009-08-09
I have similar problem. I am using PCMCIA sierra 875 card as my modem. And using Linux mint 7 (ubuntu 9.04 variant) as OS. To internet connection is no problem with NetworkManager 0.7.x.x.
But i cannot send/receive sms., :((
anybody may help us?

---

### Post by arky on 2009-08-09
Try using AT commands to read the SMS. I don't have that device to give a try

---

### Post by mpolito1969 on 2009-08-09
> **arky said:**
> Try using AT commands to read the SMS. I don't have that device to give a try

Do you know about any tutorial explaining how to do that?

Ciao,
Max

---

### Post by arky on 2009-08-09
Don't know of any recent tutorials 

[http://linuxgazette.net/164/tomar.html](http://linuxgazette.net/164/tomar.html)

---

### Post by solitaire on 2009-08-09
Try the Repo's for "Vodafone Mobile Connect"
Vodafone created a linux version of their 3g software (it's not great and a bit of a pain to get working) but it should let you read SMS's

It's a bit overkill for just SMS@s but think it;s the only way at the moment...

but I'm currently looking at "smstools" in the repos see if that's any help...

---

### Post by Giovann on 2009-08-10
I have the same problem :( I've been trying for months to get pass is :( Im currently using a DELL D630 with an internal `Dell Computer Corp. Wireless 5520 Voda L Mobile Broadband (3G HSDPA) Minicard Status Port` Its really annoying have to take my sim out each time I want to check  my sms on the sim. Has anyone found a solution to this problem?

---

### Post by breaky9973 on 2009-12-22
1. Install gnome-phone-manager via Synaptics

2. Setup your phone connection. In my case I have to point it to    
   /dev/ttyUSB0

That's all...

---

### Post by mpolito1969 on 2009-12-23
> **breaky9973 said:**
> 1. Install gnome-phone-manager via Synaptics

2. Setup your phone connection. In my case I have to point it to    
   /dev/ttyUSB0

That's all...

Phone-manager is not good. There is nothing such an "Inbox" and "Outbox" directory so you can only see an incoming SMS, when you have read it it's gone.

Moreover, SMS received while the PC is turned off are never shown, I can only see SMS if they arrive while I'm at the PC.

I wrote a very small script using Perl and a command line tool named 'gnokii' ([http://www.gnokii.org/](http://www.gnokii.org/)). It's not so good but far better than Phone Manager.

Ciao,
Max

---

### Post by mikkellund42 on 2009-12-29
I have just got a Huawei E180 UMTS modem and have also been playing with Gnokii. You can install Gnokii with
```
sudo apt-get install gnokii
```
Gnokii needs to be set up for your modem/phone. In my case it was just the following lines
```

[global]
model = AT
port = /dev/ttyUSB1
connection = serial

```
which I saved as .gnokiirc in my home dir. A list of supported phones/modems and example config files can be found at [http://wiki.gnokii.org/index.php/Config]("http://wiki.gnokii.org/index.php/Config"). I can't remember the terminal commands for getting the messages, so I made a small script to get the them from the SIM card and store them in a file.
```

#!/bin/bash

# Check if phone is PIN locked
if gnokii --getsecuritycodestatus | grep PIN
  then gnokii --entersecuritycode PIN
fi

gnokii --showsmsfolderstatus
# Get messages and append them to getsms_file. Delete messages from SIM.
gnokii --getsms SM 0 end -a getsms_file -d

```

I have also made a small script for sending SMS messages
```

#!/bin/bash
usage (){
  echo "usage :: ./sendsms <phone number> <message>"
}

if [ -z $1 ] || [ -z $2 ]; then
 usage
exit 1
else

# Check if phone is PIN locked
if gnokii --getsecuritycodestatus | grep PIN; then
  gnokii --entersecuritycode PIN
fi
echo $2 | gnokii --sendsms $1 -r
fi

```

I couldn't find anything like this on the forum myself, so I hope this comes in handy for other UMTS users.

---

### Post by d.tamm on 2010-06-29
@mikkellund42: Thank you very much for your post. This works fine for me apart from showsmsfolderstatus which gives only an error.

lsusb:
...
Bus 008 Device 005: ID 1199:6812 Sierra Wireless, Inc. MC8775 Device
...

I had to use
port = /dev/ttyUSB2

Cheers

---

### Post by ieee488 on 2010-06-29
@mikkellund42 - Thank you!

worked for my T-mobile Webconnect UMG181 usb modem

had to use /dev/ttyUSB2 as well

---

### Post by georgelappies on 2011-02-09
If I have an internal modem how can I determine what /dev/file to use for the modem? Included is an ls of my /dev dir.

```

root@george-Studio-1558:/dev# ls -asl
total 4
0 drwxr-xr-x  20 root root        3920 2011-02-09 13:37 .
4 drwxr-xr-x  22 root root        4096 2011-02-09 13:16 ..
0 drwxr-xr-x   2 root root          60 2011-02-09 13:37 ati
0 crw-------   1 root root     10, 235 2011-02-09 13:37 autofs
0 drwxr-xr-x   2 root root         720 2011-02-09 15:37 block
0 drwxr-xr-x   2 root root         100 2011-02-09 15:37 bsg
0 crw-------   1 root root     10, 234 2011-02-09 13:37 btrfs-control
0 drwxr-xr-x   3 root root          60 2011-02-09 15:37 bus
0 crw-------   1 root root    180, 176 2011-02-09 13:37 cdc-wdm0
0 crw-------   1 root root    180, 177 2011-02-09 13:37 cdc-wdm1
0 lrwxrwxrwx   1 root root           3 2011-02-09 13:37 cdrom -> sr0
0 lrwxrwxrwx   1 root root           3 2011-02-09 13:37 cdrw -> sr0
0 drwxr-xr-x   2 root root        3420 2011-02-09 13:37 char
0 crw-------   1 root root      5,   1 2011-02-09 13:37 console
0 lrwxrwxrwx   1 root root          11 2011-02-09 13:37 core -> /proc/kcore
0 drwxr-xr-x   2 root root          60 2011-02-09 13:37 cpu
0 crw-------   1 root root     10,  58 2011-02-09 13:37 cpu_dma_latency
0 drwxr-xr-x   6 root root         120 2011-02-09 15:37 disk
0 lrwxrwxrwx   1 root root           3 2011-02-09 13:37 dvd -> sr0
0 lrwxrwxrwx   1 root root           3 2011-02-09 13:37 dvdrw -> sr0
0 crw-------   1 root root     10,  61 2011-02-09 13:37 ecryptfs
0 lrwxrwxrwx   1 root root          13 2011-02-09 13:37 fd -> /proc/self/fd
0 crw-rw-rw-   1 root root      1,   7 2011-02-09 13:37 full
0 crw-rw-rw-   1 root fuse     10, 229 2011-02-09 13:37 fuse
0 crw-------   1 root root    251,   0 2011-02-09 13:37 fw0
0 crw-------   1 root root    250,   0 2011-02-09 13:37 hidraw0
0 crw-------   1 root root    250,   1 2011-02-09 13:37 hidraw1
0 crw-------   1 root root     10, 228 2011-02-09 13:37 hpet
0 crw-------   1 root root     10, 183 2011-02-09 13:37 hwrng
0 drwxr-xr-x   2 root root          40 2011-02-09 15:37 .initramfs
0 -rw-r--r--   1 root root           0 2011-02-09 15:37 .initramfs-tools
0 drwxr-xr-x   4 root root         420 2011-02-09 13:37 input
0 crw-------   1 root root      1,  11 2011-02-09 13:37 kmsg
0 srw-rw-rw-   1 root root           0 2011-02-09 13:37 log
0 brw-rw----   1 root disk      7,   0 2011-02-09 13:37 loop0
0 brw-rw----   1 root disk      7,   1 2011-02-09 13:37 loop1
0 brw-rw----   1 root disk      7,   2 2011-02-09 13:37 loop2
0 brw-rw----   1 root disk      7,   3 2011-02-09 13:37 loop3
0 brw-rw----   1 root disk      7,   4 2011-02-09 13:37 loop4
0 brw-rw----   1 root disk      7,   5 2011-02-09 13:37 loop5
0 brw-rw----   1 root disk      7,   6 2011-02-09 13:37 loop6
0 brw-rw----   1 root disk      7,   7 2011-02-09 13:37 loop7
0 drwxr-xr-x   2 root root          60 2011-02-09 15:37 mapper
0 crw-------   1 root root     10, 227 2011-02-09 13:37 mcelog
0 crw-r-----   1 root kmem      1,   1 2011-02-09 13:37 mem
0 drwxr-xr-x   2 root root          60 2011-02-09 11:27 net
0 crw-------   1 root root     10,  57 2011-02-09 13:37 network_latency
0 crw-------   1 root root     10,  56 2011-02-09 13:37 network_throughput
0 crw-rw-rw-   1 root root      1,   3 2011-02-09 13:37 null
0 crw-------   1 root root      1,  12 2011-02-09 13:37 oldmem
0 drwxr-xr-x   2 root root          60 2011-02-09 15:37 pktcdvd
0 crw-r-----   1 root kmem      1,   4 2011-02-09 13:37 port
0 crw-------   1 root root    108,   0 2011-02-09 13:37 ppp
0 crw-------   1 root root     10,   1 2011-02-09 13:37 psaux
0 crw-rw-rw-   1 root tty       5,   2 2011-02-09 14:12 ptmx
0 drwxr-xr-x   2 root root           0 2010-09-24 14:27 pts
0 brw-rw----   1 root disk      1,   0 2011-02-09 13:37 ram0
0 brw-rw----   1 root disk      1,   1 2011-02-09 13:37 ram1
0 brw-rw----   1 root disk      1,  10 2011-02-09 13:37 ram10
0 brw-rw----   1 root disk      1,  11 2011-02-09 13:37 ram11
0 brw-rw----   1 root disk      1,  12 2011-02-09 13:37 ram12
0 brw-rw----   1 root disk      1,  13 2011-02-09 13:37 ram13
0 brw-rw----   1 root disk      1,  14 2011-02-09 13:37 ram14
0 brw-rw----   1 root disk      1,  15 2011-02-09 13:37 ram15
0 brw-rw----   1 root disk      1,   2 2011-02-09 13:37 ram2
0 brw-rw----   1 root disk      1,   3 2011-02-09 13:37 ram3
0 brw-rw----   1 root disk      1,   4 2011-02-09 13:37 ram4
0 brw-rw----   1 root disk      1,   5 2011-02-09 13:37 ram5
0 brw-rw----   1 root disk      1,   6 2011-02-09 13:37 ram6
0 brw-rw----   1 root disk      1,   7 2011-02-09 13:37 ram7
0 brw-rw----   1 root disk      1,   8 2011-02-09 13:37 ram8
0 brw-rw----   1 root disk      1,   9 2011-02-09 13:37 ram9
0 crw-rw-rw-   1 root root      1,   8 2011-02-09 13:37 random
0 crw-rw-r--+  1 root root     10,  62 2011-02-09 13:37 rfkill
0 lrwxrwxrwx   1 root root           4 2011-02-09 13:37 root -> sda5
0 lrwxrwxrwx   1 root root           4 2011-02-09 13:37 rtc -> rtc0
0 crw-------   1 root root    254,   0 2011-02-09 13:37 rtc0
0 lrwxrwxrwx   1 root root           3 2011-02-09 13:37 scd0 -> sr0
0 brw-rw----   1 root disk      8,   0 2011-02-09 13:37 sda
0 brw-rw----   1 root disk      8,   1 2011-02-09 13:37 sda1
0 brw-rw----   1 root disk      8,   2 2011-02-09 13:37 sda2
0 brw-rw----   1 root disk      8,   3 2011-02-09 14:00 sda3
0 brw-rw----   1 root disk      8,   4 2011-02-09 13:37 sda4
0 brw-rw----   1 root disk      8,   5 2011-02-09 13:37 sda5
0 brw-rw----   1 root disk      8,   6 2011-02-09 13:37 sda6
0 brw-rw----   1 root disk      8,  16 2011-02-09 13:37 sdb
0 brw-rw----   1 root disk      8,  17 2011-02-09 13:37 sdb1
0 drwxr-xr-x   4 root root          80 2011-02-09 13:37 serial
0 crw-rw----   1 root disk     21,   0 2011-02-09 13:37 sg0
0 crw-rw----   1 root cdrom    21,   1 2011-02-09 13:37 sg1
0 crw-rw----   1 root disk     21,   2 2011-02-09 13:37 sg2
0 drwxrwxrwt   2 root root         140 2011-02-09 14:09 shm
0 crw-------   1 root root     10, 231 2011-02-09 13:37 snapshot
0 drwxr-xr-x   3 root root         240 2011-02-09 13:37 snd
0 brw-rw----+  1 root cdrom    11,   0 2011-02-09 13:37 sr0
0 lrwxrwxrwx   1 root root          15 2011-02-09 13:37 stderr -> /proc/self/fd/2
0 lrwxrwxrwx   1 root root          15 2011-02-09 13:37 stdin -> /proc/self/fd/0
0 lrwxrwxrwx   1 root root          15 2011-02-09 13:37 stdout -> /proc/self/fd/1
0 crw-rw-rw-   1 root tty       5,   0 2011-02-09 14:12 tty
0 crw--w----   1 root root      4,   0 2011-02-09 13:37 tty0
0 crw-------   1 root root      4,   1 2011-02-09 13:37 tty1
0 crw--w----   1 root tty       4,  10 2011-02-09 13:37 tty10
0 crw--w----   1 root tty       4,  11 2011-02-09 13:37 tty11
0 crw--w----   1 root tty       4,  12 2011-02-09 13:37 tty12
0 crw--w----   1 root tty       4,  13 2011-02-09 13:37 tty13
0 crw--w----   1 root tty       4,  14 2011-02-09 13:37 tty14
0 crw--w----   1 root tty       4,  15 2011-02-09 13:37 tty15
0 crw--w----   1 root tty       4,  16 2011-02-09 13:37 tty16
0 crw--w----   1 root tty       4,  17 2011-02-09 13:37 tty17
0 crw--w----   1 root tty       4,  18 2011-02-09 13:37 tty18
0 crw--w----   1 root tty       4,  19 2011-02-09 13:37 tty19
0 crw-------   1 root root      4,   2 2011-02-09 13:37 tty2
0 crw--w----   1 root tty       4,  20 2011-02-09 13:37 tty20
0 crw--w----   1 root tty       4,  21 2011-02-09 13:37 tty21
0 crw--w----   1 root tty       4,  22 2011-02-09 13:37 tty22
0 crw--w----   1 root tty       4,  23 2011-02-09 13:37 tty23
0 crw--w----   1 root tty       4,  24 2011-02-09 13:37 tty24
0 crw--w----   1 root tty       4,  25 2011-02-09 13:37 tty25
0 crw--w----   1 root tty       4,  26 2011-02-09 13:37 tty26
0 crw--w----   1 root tty       4,  27 2011-02-09 13:37 tty27
0 crw--w----   1 root tty       4,  28 2011-02-09 13:37 tty28
0 crw--w----   1 root tty       4,  29 2011-02-09 13:37 tty29
0 crw-------   1 root root      4,   3 2011-02-09 13:37 tty3
0 crw--w----   1 root tty       4,  30 2011-02-09 13:37 tty30
0 crw--w----   1 root tty       4,  31 2011-02-09 13:37 tty31
0 crw--w----   1 root tty       4,  32 2011-02-09 13:37 tty32
0 crw--w----   1 root tty       4,  33 2011-02-09 13:37 tty33
0 crw--w----   1 root tty       4,  34 2011-02-09 13:37 tty34
0 crw--w----   1 root tty       4,  35 2011-02-09 13:37 tty35
0 crw--w----   1 root tty       4,  36 2011-02-09 13:37 tty36
0 crw--w----   1 root tty       4,  37 2011-02-09 13:37 tty37
0 crw--w----   1 root tty       4,  38 2011-02-09 13:37 tty38
0 crw--w----   1 root tty       4,  39 2011-02-09 13:37 tty39
0 crw-------   1 root root      4,   4 2011-02-09 13:37 tty4
0 crw--w----   1 root tty       4,  40 2011-02-09 13:37 tty40
0 crw--w----   1 root tty       4,  41 2011-02-09 13:37 tty41
0 crw--w----   1 root tty       4,  42 2011-02-09 13:37 tty42
0 crw--w----   1 root tty       4,  43 2011-02-09 13:37 tty43
0 crw--w----   1 root tty       4,  44 2011-02-09 13:37 tty44
0 crw--w----   1 root tty       4,  45 2011-02-09 13:37 tty45
0 crw--w----   1 root tty       4,  46 2011-02-09 13:37 tty46
0 crw--w----   1 root tty       4,  47 2011-02-09 13:37 tty47
0 crw--w----   1 root tty       4,  48 2011-02-09 13:37 tty48
0 crw--w----   1 root tty       4,  49 2011-02-09 13:37 tty49
0 crw-------   1 root root      4,   5 2011-02-09 13:37 tty5
0 crw--w----   1 root tty       4,  50 2011-02-09 13:37 tty50
0 crw--w----   1 root tty       4,  51 2011-02-09 13:37 tty51
0 crw--w----   1 root tty       4,  52 2011-02-09 13:37 tty52
0 crw--w----   1 root tty       4,  53 2011-02-09 13:37 tty53
0 crw--w----   1 root tty       4,  54 2011-02-09 13:37 tty54
0 crw--w----   1 root tty       4,  55 2011-02-09 13:37 tty55
0 crw--w----   1 root tty       4,  56 2011-02-09 13:37 tty56
0 crw--w----   1 root tty       4,  57 2011-02-09 13:37 tty57
0 crw--w----   1 root tty       4,  58 2011-02-09 13:37 tty58
0 crw--w----   1 root tty       4,  59 2011-02-09 13:37 tty59
0 crw-------   1 root root      4,   6 2011-02-09 13:37 tty6
0 crw--w----   1 root tty       4,  60 2011-02-09 13:37 tty60
0 crw--w----   1 root tty       4,  61 2011-02-09 13:37 tty61
0 crw--w----   1 root tty       4,  62 2011-02-09 13:37 tty62
0 crw--w----   1 root tty       4,  63 2011-02-09 13:37 tty63
0 crw--w----   1 root root      4,   7 2011-02-09 13:37 tty7
0 crw--w----   1 root tty       4,   8 2011-02-09 13:37 tty8
0 crw--w----   1 root tty       4,   9 2011-02-09 13:37 tty9
0 crw-rw----   1 root dialout 166,   0 2011-02-09 14:12 ttyACM0
0 crw-rw----   1 root dialout 166,   1 2011-02-09 13:37 ttyACM1
0 crw-rw----   1 root dialout 166,   2 2011-02-09 13:37 ttyACM2
0 crw-rw----   1 root dialout   4,  64 2011-02-09 13:37 ttyS0
0 crw-rw----   1 root dialout   4,  65 2011-02-09 13:37 ttyS1
0 crw-rw----   1 root dialout   4,  66 2011-02-09 13:37 ttyS2
0 crw-rw----   1 root dialout   4,  67 2011-02-09 13:37 ttyS3
0 drwxr-xr-x   8 root root         180 2011-02-09 13:37 .udev
0 crw-r-----   1 root root     10, 223 2011-02-09 13:37 uinput
0 crw-rw-rw-   1 root root      1,   9 2011-02-09 13:37 urandom
0 crw-------   1 root root    252,   0 2011-02-09 13:37 usbmon0
0 crw-------   1 root root    252,   1 2011-02-09 13:37 usbmon1
0 crw-------   1 root root    252,   2 2011-02-09 13:37 usbmon2
0 drwxr-xr-x   4 root root          80 2011-02-09 13:37 v4l
0 crw-rw----   1 root tty       7,   0 2011-02-09 13:37 vcs
0 crw-rw----   1 root tty       7,   1 2011-02-09 13:37 vcs1
0 crw-rw----   1 root tty       7,   2 2011-02-09 13:37 vcs2
0 crw-rw----   1 root tty       7,   3 2011-02-09 13:37 vcs3
0 crw-rw----   1 root tty       7,   4 2011-02-09 13:37 vcs4
0 crw-rw----   1 root tty       7,   5 2011-02-09 13:37 vcs5
0 crw-rw----   1 root tty       7,   6 2011-02-09 13:37 vcs6
0 crw-rw----   1 root tty       7,   7 2011-02-09 13:37 vcs7
0 crw-rw----   1 root tty       7, 128 2011-02-09 13:37 vcsa
0 crw-rw----   1 root tty       7, 129 2011-02-09 13:37 vcsa1
0 crw-rw----   1 root tty       7, 130 2011-02-09 13:37 vcsa2
0 crw-rw----   1 root tty       7, 131 2011-02-09 13:37 vcsa3
0 crw-rw----   1 root tty       7, 132 2011-02-09 13:37 vcsa4
0 crw-rw----   1 root tty       7, 133 2011-02-09 13:37 vcsa5
0 crw-rw----   1 root tty       7, 134 2011-02-09 13:37 vcsa6
0 crw-rw----   1 root tty       7, 135 2011-02-09 13:37 vcsa7
0 crw-------   1 root root     10,  63 2011-02-09 13:37 vga_arbiter
0 crw-rw----+  1 root video    81,   0 2011-02-09 13:37 video0
0 crw-rw-rw-   1 root root      1,   5 2011-02-09 13:37 zero
root@george-Studio-1558:/dev# 

```

---

