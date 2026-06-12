---
title: "LIRC ,Happauge PCI card, Totem plugin and amarok wierd problem"
date: 2008-08-17
forum: Multimedia Software
---

### Post by sturmer on 2008-08-17
Hi to you all after 10 days of trying all the possible guides and reading 100 of forums,guides etc. i found only one that makes some sense in my problem. First, i have Hauppauge TV/FM PCI card, and it has on board ir remote.This thing works out of the box the minute i install the Ubuntu 8.04, but only few keys the volume control (mute, vol+,vol-) and number buttons,the power button,and the OK button the rest of the keys are not responsive (cant see any input in txt file or when i run in shell irw).

Ok now for the things i want to work whit it

I want to use my remote with the Totem player, i know it has the lirc plugin,i try to use it but the totem gives me an error (Unable to activate plugin Infrared Remote Control.
Couldn't initialize lirc.)Then i used google,and search function on this forum to make it work i followed tons of guides but non of them worked...then i got this one...

[URL="http://umn.dl.sourceforge.net/sourceforge/lirc/lirc-0.8.0.tar.bz2"]
_**Lirc on Ubuntu Drapper**_[/URL]

Ok this is the code if i follow it form start to finish so if you can help...

(i know it is something gone bad in installation but dont know where to start to fix it)

```
root@Ensiferum:/#  apt-get install ncurses-dev lirc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting libncurses5-dev instead of ncurses-dev
libncurses5-dev is already the newest version.
lirc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Ensiferum:/#  wget http://umn.dl.sourceforge.net/sourceforge/lirc/lirc-0.8.0.tar.bz2
--16:34:45--  http://umn.dl.sourceforge.net/sourceforge/lirc/lirc-0.8.0.tar.bz2
           => `lirc-0.8.0.tar.bz2.3'
Resolving umn.dl.sourceforge.net... 128.101.240.209
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 514,359 (502K) [application/x-bzip2]

100%[===================================================================================================================>] 514,359      286.09K/s

16:34:48 (285.28 KB/s) - `lirc-0.8.0.tar.bz2.3' saved [514359/514359]

root@Ensiferum:/#  tar -xjvf lirc-0.8.1.tar.bz2 -C /usr/src
tar: lirc-0.8.1.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```



Ok now if i skip the part when i need to compile the driver modules agian i have errors
 TESTING LIRC
```

root@Ensiferum:/# modprobe lirc_i2c
root@Ensiferum:/# dmesg | grep lirc
[   58.084148] lirc_dev: IR Remote Control driver registered, major 61
[   58.084915] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[   58.585146] lirc_serial: auto-detected active low receiver
[   58.585151] lirc_dev: lirc_register_plugin: sample_rate: 0
root@Ensiferum:/# mode2
mode2: error opening /dev/lirc
mode2: No such file or directory
root@Ensiferum:/# irw
connect: Connection refused
root@Ensiferum:/#

```

but if i restart the lirc

```

root@Ensiferum:/# /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                                                                                                              [fail]
 * Loading LIRC modules                                                                                                                                 [ OK ]
 * Starting remote control daemon(s) : LIRC                                                                                                             [ OK ]
root@Ensiferum:/# irw
root@Ensiferum:/# 55841520   **------> i was pressing numbers on remote**
bash: 55841520: command not found **----> i pressed OK on remote**
root@Ensiferum:/# 0726  ** -----> again nubers**
bash: 0726: command not found** -----> again OK**
root@Ensiferum:/#
```



so does any one have an idea why this wont work in totem...??

---

### Post by sturmer on 2008-08-17
ok after more than 12 hours of searching i still don't have the answer it is FRUSTRATING to know that this BS is half working, and i need to get up every time to change the playing file,and pause the movie....and i have the 42 keys remote that is useless....

i found some thing but...don't know what i know from this...i would appreciate any help

(this is this card) but!!!

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_PCI")


but this is what i get when i lspci -v run

```

05:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: Hauppauge computer works Inc. Hauppauge WinTV 34xxx models
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at d3000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

05:06.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
        Subsystem: Hauppauge computer works Inc. Hauppauge WinTV 34xxx models
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at d4000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2

```


better 

lspci -v | grep Multi*

```
lspci -v | grep Multi*
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
05:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:06.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
```


But still the remote only works, on Desktop, to mute,and volume up and volume down...

---

### Post by SantoUbu21 on 2008-10-21
I too have similar issue.

The remote control plugin in Totem Movie Player stopped working for some reason in my HP Notebook in which I had installed Ubuntu few months ago. Also the notebook remote has no effect in controlling the volume in it. Previously I was able to increase and decrease the volume using the remote but now it has no effect.
Surprisingly the remote is able work when I select the speaker icon and use the up and down arrow keys but no effect if I use the volume adjustment buttons on it. 

If I try to enable "Infrared Remote Control" in Totem Movie Player it gives [COLOR="Black"]**[SIZE="5"]Plugin Error [/SIZE]**[/COLOR] [SIZE="3"][SIZE="4"]Unable to activate plugin Infrared Remote Control Couldn't initialize Iirc.[/SIZE][/SIZE]

The error message screen shot is at...
[COLOR="Blue"][http://picasaweb.google.co.in/AquaUbuntu21/UbuntuInfraredRemoteError#5259475621576275010]("http://picasaweb.google.co.in/AquaUbuntu21/UbuntuInfraredRemoteError#5259475621576275010")[/COLOR]

Any idea what might have caused this?

---

