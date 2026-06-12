---
title: "DViCO FusionHDTV7 Dual Express"
date: 2008-08-15
forum: Mythbuntu
---

### Post by lucasmath on 2008-08-15
I am trying to set up my mythbuntu system with the FusionHDTV7 Dual Express.  I don't think that my system can see the card.

I am somewhat experienced with linux, but not mythtv.  I was wondering if someone could give me some step-by-step instructions on how to set up the tv tuner card.  Has anyone packaged the driver for mythbuntu so I can apt-get install or maybe dpkg -i?

Bonus Question:  How do I get the included fusion remote to work?

---

### Post by jzilbauer on 2008-08-16
I also have the same card, but am relatively new to ubuntu. If someone can help on the setup process, that will be great.

---

### Post by SadaraX on 2008-08-19
I do not have the card myself, but I found this after some googling.

[http://mythtv.org/pipermail/mythtv-users/2008-August/229796.html]("http://mythtv.org/pipermail/mythtv-users/2008-August/229796.html")

It looks like it should work for you, but it might take a little work.

---

### Post by jzilbauer on 2008-08-20
Ok, I'm pretty new to linux and I'm not sure how to run the extract.sh file. help please

---

### Post by SadaraX on 2008-08-21
> **jzilbauer said:**
> Ok, I'm pretty new to linux and I'm not sure how to run the extract.sh file. help please

I will try to keep this simple but informative.

The file extension '.sh' stands for "Shell Script." They are somewhat common in the Linux world. You need to run them using a terminal/console application. A terminal actually runs a command shell (which can run the shell script). You can open that app from the Applications menu in both Gnome or KDE.

The window will look something like this:

[IMG]http://www.math-linux.com/IMG/png/console.png[/IMG]

To run a .sh file, you can normally type into the window:
```

sh filename.sh

```

Another method is sometimes to run it with './filename.sh'. But that requires the file properties be set to executable. The 'sh filename.sh' always works. You see, "sh" is actually a program.

One more thing, the "sh" program needs to be given the exact location of the file. If the .sh file is on your desktop, you can type: 'sh /home/user/Desktop/filename.sh'. 

I hope that helps. If you have trouble, ask for help.

---

### Post by u!mp3 on 2008-08-29
[http://article.gmane.org/gmane.linux.drivers.dvb/43872]("http://article.gmane.org/gmane.linux.drivers.dvb/43872")

---

### Post by icon134 on 2008-09-23
So realizing that I didn't ask this question in the first place... thanks to the question and answers... I have managed to get the video adapter to work in mythbuntu but I haven't been able to get the computer to recognize the remote input.

I tried to base my installation of Lirc on the FusionHDTV5 RT remote but the system doesn't appear to see the input device.

when I do "cat /proc/bus/input/devices"

Nothing resembling the card appears to show up the only two entrys that I don't immediately recognize are these:

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=10000000000000 0

I'm assuming that the card just isn't fully supported yet but I figured I'd see if there were any ideas floating around.

Ultimately I'm getting the same irw error that is cropping up in this thread: [(irw problems)]("http://ubuntuforums.org/showthread.php?t=916078&highlight=irw+dvico") but the device doesn't appear to be showing up.

Any help would be appreciated...

---

### Post by u!mp3 on 2008-10-16
bump!

---

### Post by icon134 on 2008-10-20
I managed to get some basic functionality with the remote by running:

modprobe ir-kbd-i2c

but unfortunately I can only get limited functionality of the remote (only 6 keys seem to funcion and I can't seem to configure the remote)

I'm sure it is something I did when configuring the remote but I'm not sure how to make it work better.

Has anyone gotten this remote to work completely and if so how did you do it?

Scott

---

### Post by jzilbauer on 2008-11-11
ok so i finally got back around to trying to get this card to work with mythtv, and i have tried all the sugestions in this forum (thanks). But i have to say that i'm a total newbie at this stuff, i know very basic things in ubuntu. if someone could give me a walk through, that would be awesome. thanks in advance.

---

### Post by jzilbauer on 2008-12-01
Please Help

---

### Post by onehotcutey on 2008-12-14
> **icon134 said:**
> I managed to get some basic functionality with the remote by running:

modprobe ir-kbd-i2c

but unfortunately I can only get limited functionality of the remote (only 6 keys seem to funcion and I can't seem to configure the remote)

I'm sure it is something I did when configuring the remote but I'm not sure how to make it work better.

Has anyone gotten this remote to work completely and if so how did you do it?

Scott
icon,

Have you had anymore luck with the remote?  I have just built my HTPC using the Fusion 7 dual express (which is working wonderfully) but I haven't been able to get the IR receiver to be recogized.  

I'll try the modprobe ir-kbd-i2c when I get back to the system.  (I haven't hooked it up the TV officially yet, because the remote isn't working and my wife is alreay a nay sayers about this project)

I've read elsewhere that the remote is being seen as a mouse and/or keyboard, which is why so few buttons work.

Thanks for any help.

Daniel

---

### Post by onehotcutey on 2008-12-17
bump

---

### Post by daveisfera on 2009-03-16
> **icon134 said:**
> So realizing that I didn't ask this question in the first place... thanks to the question and answers... I have managed to get the video adapter to work in mythbuntu but I haven't been able to get the computer to recognize the remote input.

I tried to base my installation of Lirc on the FusionHDTV5 RT remote but the system doesn't appear to see the input device.

when I do "cat /proc/bus/input/devices"

Nothing resembling the card appears to show up the only two entrys that I don't immediately recognize are these:

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=10000000000000 0

I'm assuming that the card just isn't fully supported yet but I figured I'd see if there were any ideas floating around.

Ultimately I'm getting the same irw error that is cropping up in this thread: [(irw problems)]("http://ubuntuforums.org/showthread.php?t=916078&highlight=irw+dvico") but the device doesn't appear to be showing up.

Any help would be appreciated...

Could you please give some info on what you did to get this card working in Mythbuntu? I have the same care and I haven't had any luck getting it to work.

Thanks,
Dave

---

### Post by daveisfera on 2009-04-08
> **onehotcutey said:**
> icon,

Have you had anymore luck with the remote?  I have just built my HTPC using the Fusion 7 dual express (which is working wonderfully) but I haven't been able to get the IR receiver to be recogized.  

I'll try the modprobe ir-kbd-i2c when I get back to the system.  (I haven't hooked it up the TV officially yet, because the remote isn't working and my wife is alreay a nay sayers about this project)

I've read elsewhere that the remote is being seen as a mouse and/or keyboard, which is why so few buttons work.

I have this card and after running "sudo modprobe ir-kbd-i2c" I am able to get key presses from the remote to register in irw, so it's definitely a step in the right direction.

---

### Post by onehotcutey on 2009-06-11
Sorry I never made it back to this thread to update the status of the Card or the Remote.

I have both working very well (at least they were until I did dist upgrade, now I'm trudging through it all again).  Here are the steps I took to make the card and remote work.  Where I can I'll reference the tutorials I used.

1. The card:

This was actually very easy, follow the instructions here:
[http://linuxtv.org/wiki/index.php/Xceive_XC5000#How_to_Obtain_the_Firmware](http://linuxtv.org/wiki/index.php/Xceive_XC5000#How_to_Obtain_the_Firmware)

After a reboot you should see reference to the xc5000 firmware in your dmesg output and you should see two adapter appear in /dev/dvb.  Please note that for the DViCO FusionHDTV7 Dual Express only digital is currently supported.

2. The remote:

This takes a bit more effort but will eventually work.  Start by adding ir-kbd-i2c to /etc/modules, this will tell modprobe to load the module on boot.  Now you can either reboot or you can just run:

sudo modprobe ir-kbd-i2c

Next follow the directions for adding a remote in this Tutorial:
[http://ubuntuforums.org/showthread.php?t=616103](http://ubuntuforums.org/showthread.php?t=616103)

You will be adding version 2 of the remote and can ignore everything in the tutorial before "Remote Installation" (Though its a good read)

Under the "Create Symlink" section:

A. When you are searching through dmesg for the proper input number you should see something like this:
input: i2c IR (FusionHDTV) as /devices/virtual/input/input7

B.  If you are using Jaunty then you will need to create the file: 
/etc/udev/rules.d/60-symlinks.rules

I do most of my editing from the command line, but just use your favorite editor to do so.

Complete the installation and configuration of lirc and you should be ready to go.

From here you should examine the file lircrc, it has instructions for editing the keybindings in MythTV.

Hope this helps someone.

Daniel

---

### Post by particleMan86 on 2009-11-24
I am having some trouble as well. The remote functions at a basic level in mythtv, but only the arrow keys and one other button work.

When I restart lirc with verbose it says "Unable to load LIRC kernel modules." I tried "sudo modprobe ir-kbd-i2c" with no effect.

The only relevant output that I can tell is 

[    8.410106] CORE cx23885[0]: subsystem: 18ac:d618, board: DViCO FusionHDTV7 Dual Express [card=10,autodetected]

but nothing about input devices.

The remote was working before I upgraded (from Intrepid), and I was using the dev/input driver on event6 then.

Any ideas?

---

