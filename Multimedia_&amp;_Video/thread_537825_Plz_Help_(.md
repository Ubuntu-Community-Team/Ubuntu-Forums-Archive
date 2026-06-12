---
title: "Plz Help :("
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by chroncile on 2007-08-29
I want to install the intellinuxgraphics drivers but I dont know how, I am a linux noob :(
plz i want to install it so i can play games faster on cedega, warcraft 3 is going at 10 fps, plz thanks.
my video card is intel 915G.
ty :)

---

### Post by tyggna1 on 2007-08-29
please post the output of:


```
lspci
```
and
```

glxinfo | grep direct
```


Then type in

```
gedit /etc/X11/xorg.conf
```

and post whatever is written under the section "device"

---

### Post by chroncile on 2007-08-29
Ok.

```
lspci
```

```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)
```


```
glxinfo | grep direct
```

```
direct rendering: Yes

```



```
gedit /etc/X11/xorg.conf
```

```
The program 'gedit' is currently not installed.  You can install it by typing:
sudo apt-get install gedit
bash: gedit: command not found

```

---

### Post by tyggna1 on 2007-08-29
looks like the drivers are installed.  Still need to see xorg.conf, though

type in:

```
sudo apt-get install gedit
```

and let that install, then try typing in 

```
gedit /etc/X11/xorg.conf
```

again

---

### Post by chroncile on 2007-08-29
Ty for helping me :)
```
gedit /etc/X11/xorg.conf
```

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

** (gedit:8325): WARNING **: Throbber animation not found

** (gedit:8325): WARNING **: Throbber fallback animation not found either
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found

```

---

### Post by chroncile on 2007-08-29
:((
It's still slow, what should I do, and the colours in warcraft 3 are off, they're too bright :(((((((

---

### Post by tyggna1 on 2007-08-29
I was just looking to see what was going on, and what the problem was.  x (the graphical interface) is having issues using your device. 

What version of Ubuntu are you using?

---

### Post by chroncile on 2007-08-29
I have kubuntu, but it's the same, right?
I installed this because I had problems with ubuntu, it was taking up all of my disk space.

---

### Post by tyggna1 on 2007-08-29
Also:  what's the name of a text editing program you use--it looks like gedit isn't working for you--so we'll have to use another.

once we know the name of that, then, also post your

/var/log/Xorg.0.log

file

---

### Post by tyggna1 on 2007-08-29
that would explain a lot.  Kubuntu is a different graphical environment than Ubuntu.  It uses a KDE environment.  

Almost all my experience has been with the GNOME environment.  They run differently.  I'd try flagging down a more experienced Kubuntu user.  Sorry, but I don't think I'll be able to help you--as I don't know how KDE runs.

A few forum tips--you're going to want to add what OSes you use to your profile, that will prevent these mixups all together.  Try to be more specific in your thread titles--something like: 3D programs running very slow, and then, still, post the details in the text.

Again, sorry, but keep posting--I'm sure some Kubuntu user knows what to do.

---

### Post by chroncile on 2007-08-29
NOOOOOO :((((((((
I need to run my games badly :(((((
i jjust like the way kubuntu looks :((((((((((((((((((((((((((((

---

### Post by tyggna1 on 2007-08-29
You could try reading [this]("http://forum.freespire.org/archive/index.php/t-8919.html") thread, and see if it's helpful--the people in it had a similar problem that you have--getting your graphics card to render 3D images.

Just keep looking--I'm sure the answer is out there.

Also, try another post, but mention that you're using Kubuntu.  Just don't give up.

---

### Post by chroncile on 2007-08-29
Well I'm trying that, I'm pretty sure it's not going to work :(
Hey, this is off topic, but do you know where I can get a vista aero theme for kubuntu?

---

### Post by chroncile on 2007-08-29
NOOOOOOOOOO
I did these steps
[http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen](http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen)
and now my kubuntu won't load, it has some error thingy, how do i edit the file to make it go back to normal :(((((((((((((( waaaaaaaa :(((((((

---

### Post by tyggna1 on 2007-08-29
all the lines that you added, make sure you put a # before them--that way your GUI won't read them.

All the lines that you put a # in front of, take them out.

Two ways to try it:

The easier way:

type alt-F2, and see if that will bring up a "run application" window.  If it does, type in gksudo nautilus, and find your xorg.conf file and change it back.

It that doesn't work,
then you'll need to press ctrl-all-F1 to bring up the command prompt.

Once there, navigate to /etc/X11/

and type in

sudo vim xorg.conf

That will open up a command-line editing utility.

Let me find instructions on how to use vim, and I'll post the link to them here.

---

### Post by tyggna1 on 2007-08-29
don't panic.  I've made the exact same mistake you did--it's not as big of a deal as you might think--it just seems that way because you don't have any graphic user interface to help you out.

Good news!  Ubuntu isn't based off a graphic user interface like windows--so everything is there and it's fine, you just can't access it using X (the linux GUI).
[here's your vim usage tutorial]("http://www.vi-improved.org/tutorial.php")

Vim stands for Vi-Improved.  Vi was an text editor that was entirely text-based--no graphics.  It's still there, on just about every linux machine for situations just like this.

In the future, before you edit any .conf file, type in

```
sudo cp /path/of/file/*.conf /path/of/file/*.conf.backup
```

to make a back up of your known-working file.

That way, if things mess up, you just have to press ctrl-alt-F1 and type:


```
sudo cp /path/of/file/*.conf.backup /path/of/file/*.conf
```

to set things to the way they were.

You're lucky- though, I had to reinstall Ubuntu completely because I didn't know how to use Vim back with this happened to me.  Of course, that might not be a bad idea. . .depends on your view point.  Vim is complicated, and difficult to learn.  You'll be glad you learned it, to be sure, but letting the computer just reset everything might seem easier to you.  Let me know how it goes.

---

### Post by chroncile on 2007-08-29
When do i press the alt-f2, kubuntu doesn't get to the login place, it just shows the logo and loads, then some random text appears but i cant read it cuz it goes away fast, then a black screen where i can write stuff but it doesnt' do anything.

---

