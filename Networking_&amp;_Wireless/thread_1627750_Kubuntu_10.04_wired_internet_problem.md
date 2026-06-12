---
title: "Kubuntu 10.04 wired internet problem"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by tpprynn on 2010-11-21
I set up a friend's computer to dual boot XP and Kubuntu 10.04. Though I don't have anything but mobile Broadband I set this up at my parents' place using wired internet. I did nex tto nothing, it just worked once I booted up.

now the friend has got it home the machine does not work in Kubuntu for wired internet. She found her software CD for XP and that is now working but Kubuntu remains offline.

I'm stumped as to how ot solve this, it was a hassle to get things over to my parents' place, my friend has no wireless or mobile broadband to replace Knetwork Manager with Wicd and i imagine a dependancies minefield exists as far as goes installing it from files on a pendrive.

Mobile Broadband remains 'greyed out' as an option when I try to use my dongle with my own Kubuntu setup so I needn't lend her that.

Any ideas? I suggested she have this dual boot setup seeing as XP is on the way out and will be a bit of a risk in the not too distant future.

Jargon-free answers please, especially as she's blonde. :-)  Thanks.

---

### Post by Hippytaff on 2010-11-21
Is there any way you can get the outputs of these commands in the terminal here (and before that have you checked that everything is enabled?)

```

lshw -C network

```
```

ifconfig

```
```

lspci | grep eth

```
:-)

---

### Post by tpprynn on 2010-11-22
Thanks. I've sent the friend instructions about this, but I think it might give her a heart attack. Hopefully you can look in later to see if I've had any luck with her, i'll post back.

Much appreciated.

---

### Post by tpprynn on 2010-11-22
Okay here's that output. The third command as you'll see yielded no output. Hopefully you can see round a couple of typos she made. She didn't have a heart attack, so that's good. Hopefully you can see what you need ot from here.

[COLOR=#000000][SIZE=3]gill@gill-pc:~$ lshw -C  network[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]WARNING: you should run this program as super-user.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]gill@gill-pc:~$ ifconfig  [/SIZE][/COLOR] 
 [COLOR=#000000][SIZE=3]eth0      Link encap:Ethernet  HWaddr e0:cb:4e:c3:f8:97  [/SIZE][/COLOR] 
 [COLOR=#000000]          [SIZE=3]UP BROADCAST MULTICAST  MTU:1500  Metric:1[/SIZE][/COLOR]
 [COLOR=#000000]          [SIZE=3]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/COLOR]
 [COLOR=#000000]          [SIZE=3]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/COLOR]
 [COLOR=#000000]          [SIZE=3]collisions:0 txqueuelen:1000 [/SIZE][/COLOR] 
 [COLOR=#000000]          [SIZE=3]RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/SIZE][/COLOR]
 [COLOR=#000000]          [SIZE=3]Interrupt:27 Base address:0xe000 [/SIZE][/COLOR] 
 

 [COLOR=#000000][SIZE=3]lo        Link encap:Local Loopback  [/SIZE][/COLOR] 
 [COLOR=#000000]          [SIZE=3]inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE][/COLOR]
 [COLOR=#000000]          [SIZE=3]inet6 addr: ::1/128 Scope:Host[/SIZE][/COLOR]
 [COLOR=#000000]          [SIZE=3]UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE][/COLOR]
 [COLOR=#000000]          [SIZE=3]RX packets:80 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/COLOR]
 [COLOR=#000000]          [SIZE=3]TX packets:80 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/COLOR]
 [COLOR=#000000]          [SIZE=3]collisions:0 txqueuelen:0 [/SIZE][/COLOR] 
 [COLOR=#000000]          [SIZE=3]RX bytes:4800 (4.8 KB)  TX bytes:4800 (4.8 KB)[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=3]gill@gill-pc:~$ lsspci | grep eth[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]No command 'lsspci' found, did you mean:[/SIZE][/COLOR]
 [COLOR=#000000] [SIZE=3]Command 'lspci' from package 'pciutils' (main)[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]lsspci: command not found[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]gill@gill-pc:~$ lspci | grep eth[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]gill@gill-pc:~$ lspci|grep eth[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]gill@gill-pc:~$ lspci | grep eth[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=3]gill@gill-pc:~$ [/SIZE][/COLOR] 
 
The router is a bit weird maybe. It's a BT Home Network 1200, which from my googling seemed fairly normal adsl router. I've asked her to try connecting by usb too as it has usb sockets.

Edit: It turns out she was connecting by usb anyway. Although this is a stab in the dark as far as my knowledge goes I've asked her to try an ethernet cable, hopefully this error was the weak link, but let me know what you think anyway.

thanks.

---

### Post by Hippytaff on 2010-11-22
Ethernet should work no problem - usb dongles sometimes need a bit of configuring depending on a number of things. They sometimes have driver issues, need modeswitching etc and sometimes they just work.
the outpuut of 
```
lsusb
```
will give us the chipset and manufacturer information, which will then give us a better idea of the problem. :-)

---

### Post by tpprynn on 2010-11-22
[COLOR=#000000][FONT=Sans Serif][SIZE=3]I'm guessing the BT usb item isn't among these things somehow - the computer isn't even seeing it? Thanks for any further input you can give.
[/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Sans Serif][SIZE=3]
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Sans Serif][SIZE=3]
[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Sans Serif][SIZE=3]gill@gill-pc:~$ lsusb[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif][SIZE=3]Bus 005 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif][SIZE=3]Bus 005 Device 002: ID 1630:0011  [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Sans Serif][SIZE=3]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif][SIZE=3]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif][SIZE=3]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif][SIZE=3]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif][SIZE=3]Bus 001 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif][SIZE=3]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans Serif][SIZE=3]gill@gill-pc:~$ [/SIZE][/FONT][/COLOR]

---

### Post by Hippytaff on 2010-11-22
Unless there was a usb pendrive plugged in at the time, it looks as though the usb wireless device is being recognised as a storage device...this is common, having to manually switch the mode. You need to look into usb_modeswitch 

[http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html)

---

