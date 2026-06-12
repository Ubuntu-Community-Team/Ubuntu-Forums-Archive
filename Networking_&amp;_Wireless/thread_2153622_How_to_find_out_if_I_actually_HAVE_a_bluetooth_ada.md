---
title: "How to find out if I actually HAVE a bluetooth adapter"
date: 2013-06-11
forum: Networking &amp; Wireless
---

### Post by crayzmoron on 2013-06-11
Hi evry1!

I am running Ubuntu 13.04 i686 on my Fujitsu Lifebook A Series A530 and I LOVE it. I've been using Ubuntu since ubuntu 8 came out but just recently wanted to use Bluetooth coz I bought an awsome BT loudspeaker.

And here's the rub:
In the right upper corner I seemy BT icon and on right click I get the menu to torn on/off, bluetooth settings and search device. Now when I try to find the device (JAMBOX by JAWBONE) - which of course I put in pairing mode - the computer searches and searches and after a little more searching does not find any device.

First I thought that he JAMBOX could be the problem but it connects with absolutely no problem to my various cell phones.
So, I tried to find my LG P990, my LG 9, my iPod 4, my BT mouse that I use with my Mac but to no avail.

Obviously the problem lies within my PC or Ubuntu. 

I was wondering, maybe my PC doesn't have a BT adapter - or it is broken somehow - but how do I find out if my PC has the necessary hardware?
And if I have the hardware how do I find out if it works?

I tried TWEAK and some other programs to find the bleutooth adapter but, as usually, a terminal command would probably work better.

I would like to end this post with a BIG compliment to the developers of Ubuntu and would like to congratulate them on ther efforts!!

Although I loved GNOME I actually became quite fond of UNITY and its look.

I can't wait to have ubuntu on my phone :)

Anyhoo...

Helpless in Vienna
Cray

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by crayzmoron on 2013-06-11
Thank you ahallubuntu!
The code did not produce ANY result. Absolutely nothing happend. What should I have seen in the terminal window?
CHeers
Cray

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by sanderj on 2013-06-11
> **crayzmoron said:**
> Thank you ahallubuntu!
The code did not produce ANY result. Absolutely nothing happend. What should I have seen in the terminal window?
CHeers
Cray

See below three commands, plus output on my laptop with bluetooth:


```
ubuntu@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lsusb | grep -i bluetoo
Bus 002 Device 006: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
ubuntu@ubuntu:~$ lspci | grep -i bluetoo
ubuntu@ubuntu:~$
```

Bonus:

```
ubuntu@ubuntu:~$ dmesg | grep -i bluet
[   32.608484] Bluetooth: Core ver 2.16
[   32.608535] Bluetooth: HCI device and connection manager initialized
[   32.608543] Bluetooth: HCI socket layer initialized
[   32.608547] Bluetooth: L2CAP socket layer initialized
[   32.608556] Bluetooth: SCO socket layer initialized
[   32.872483] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.872494] Bluetooth: BNEP filters: protocol multicast
[   32.872514] Bluetooth: BNEP socket layer initialized
[   32.934590] Bluetooth: RFCOMM TTY layer initialized
[   32.934605] Bluetooth: RFCOMM socket layer initialized
[   32.934607] Bluetooth: RFCOMM ver 1.11
[ 1901.300162] init: bluetooth main process ended, respawning
ubuntu@ubuntu:~$ 
```

HTH

---

### Post by crayzmoron on 2013-06-12
Thank you for your efforts!

the strange thing is that I have Windows 7 (dual boot) as well and the same problem there: Shows BT but no connection ever. But is shows BT adapter as "working" in the hardware panel.

I never used it before and I try to avoid using Win7 all together (yeah yeah I know, I could use WINE but there are two programs that don't work on WINE and I need them for work - what a waste of HD space Windows is...) but I thought maybe it has to do with the settings in Windows that the BT adapter doesn't work when running on UBUNTU.

The weird thing is that the manufacturer seems to be under the impression that the machine should have a Bluetooth adapter...

Aw well...

Still confused in Vienna

Cray

---

### Post by sanderj on 2013-06-12
And ... did you run the four commands I gave you? If not, I'll leave this thread.

---

### Post by crayzmoron on 2013-06-12
Hi!
I ran all the suggested commands. This is the code that it produced:

cray@ubuntu:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

cray@ubuntu:~$ lsusb | grep -i bluetoo
cray@ubuntu:~$ lspci | grep -i bluetoo
cray@ubuntu:~$ dmesg | grep -i bluet
[   30.780714] Bluetooth: Core ver 2.16
[   30.780742] Bluetooth: HCI device and connection manager initialized
[   30.780751] Bluetooth: HCI socket layer initialized
[   30.780755] Bluetooth: L2CAP socket layer initialized
[   30.780761] Bluetooth: SCO socket layer initialized
[   31.025038] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.025043] Bluetooth: BNEP filters: protocol multicast
[   31.025053] Bluetooth: BNEP socket layer initialized
[   31.025589] Bluetooth: RFCOMM TTY layer initialized
[   31.025596] Bluetooth: RFCOMM socket layer initialized
[   31.025598] Bluetooth: RFCOMM ver 1.11

I am confused. Does it mean I HAVE an BT adapter or not?

Stumped in Vienna
Cray

---

### Post by crayzmoron on 2013-06-12
[INDENT] 					Hi!
I ran all the suggested commands. This is the code that it produced:

cray@ubuntu:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

cray@ubuntu:~$ lsusb | grep -i bluetoo
cray@ubuntu:~$ lspci | grep -i bluetoo
cray@ubuntu:~$ dmesg | grep -i bluet
[   30.780714] Bluetooth: Core ver 2.16
[   30.780742] Bluetooth: HCI device and connection manager initialized
[   30.780751] Bluetooth: HCI socket layer initialized
[   30.780755] Bluetooth: L2CAP socket layer initialized
[   30.780761] Bluetooth: SCO socket layer initialized
[   31.025038] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.025043] Bluetooth: BNEP filters: protocol multicast
[   31.025053] Bluetooth: BNEP socket layer initialized
[   31.025589] Bluetooth: RFCOMM TTY layer initialized
[   31.025596] Bluetooth: RFCOMM socket layer initialized
[   31.025598] Bluetooth: RFCOMM ver 1.11

I am confused. Does it mean I HAVE an BT adapter or not?

Stumped in Vienna
Cray 				[/INDENT]

---

### Post by crayzmoron on 2013-07-02
:confused:

So...
Since nobody was able to help me I decided to put in a new WiFi/Bluetooth card (Atheros AR9002WB-1NG) just to be sure I actually HAVE the Hardware for Bluetooth. But guess what? It still doesn't work.
I ran all the commands:

ubuntu@ubuntufujitsu:~$ lsusb | grep -i bluetoo
ubuntu@ubuntufujitsu:~$ lspci | grep -i bluetoo
ubuntu@ubuntufujitsu:~$ dmesg | grep -i bluet
[   24.336117] Bluetooth: Core ver 2.16
[   24.336161] Bluetooth: HCI device and connection manager initialized
[   24.336171] Bluetooth: HCI socket layer initialized
[   24.336174] Bluetooth: L2CAP socket layer initialized
[   24.336182] Bluetooth: SCO socket layer initialized
[   24.500528] Bluetooth: RFCOMM TTY layer initialized
[   24.500542] Bluetooth: RFCOMM socket layer initialized
[   24.500544] Bluetooth: RFCOMM ver 1.11
[   24.640332] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.640337] Bluetooth: BNEP filters: protocol multicast
[   24.640350] Bluetooth: BNEP socket layer initialized
soulmade@ubuntufujitsu:~$ lspci | grep -i bluetoo
soulmade@ubuntufujitsu:~$ lsusb | grep -i bluetoo
soulmade@ubuntufujitsu:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ubuntu@ubuntufujitsu:~$ 

As you can see some commands did not yield any results. Which is strange, no?

I also tried to find other devices (phone, loudspeaker) which didn't work either. I put it in "visible", searched for devices and other than the little turning circle cursor nothing happend.

I am totally at the end of my wits. Help PLEASE!

Still helpless in Vienna
Cray

---

### Post by zealibib slaughter on 2013-07-02
try hcitool dev
this should give you the mac addresses of all bluetooth devices connected to your system

also hciconfig will give you the status of your adapter

man hcitool may be of help and the command hcitool scan will scan for nearby bluetooth devices
this may (more than likely will) not solve your problem but you will get some terminal output that may point to errors.
also you may want to try blueman bluetooth applet instead of the default one

---

### Post by crayzmoron on 2013-07-02
Hi there!
Thanks for the reply and the pointers.
This is ther terminal output:

ubuntu@ubuntufujitsu:~$ hcitool dev
Devices:
    hci0    E8:39:DF:86:C0:4A
ubuntu@ubuntufujitsu:~$ hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: E8:39:DF:86:C0:4A  ACL MTU: 310:10  SCO MTU: 64:8
    UP RUNNING PSCAN ISCAN 
    RX bytes:1018 acl:0 sco:0 events:50 errors:0
    TX bytes:2143 acl:0 sco:0 commands:49 errors:0

ubuntu@ubuntufujitsu:~$ man hcitool
ubuntu@ubuntufujitsu:~$ hcitool scan
Scanning ...
ubuntu@ubuntufujitsu:~$ hcitool scan
Scanning ...
ubuntu@ubuntufujitsu:~$ hcitool scan
Scanning ...
ubuntu@ubuntufujitsu:~$ 

As you can see the scan did notyield any results although my phone an the loudspeaker was in pairing mode and recognized eachother but not my ubuntu laptop.

I am so frustrated about this and I do not know what the problem could be... Is it hardware or the frequency or a software glitch?????

Frustrated in Vienna
Cray

---

### Post by zealibib slaughter on 2013-07-02
ok well you have a bluetooth detected have you tried to put the laptop visible and pair through you phone instead of scanning with your computer?

also try service bluetooth stop
then service bluetooth start
to restart bluetooth

i dont understand why you are not getting anything on the scan though so also do lsusb and look for your bluetooth model it may be driver related
then do usb-devices and look for your bluetooth Manufacturer on the lines marked I: you should have something that says Driver=somethinghere

---

