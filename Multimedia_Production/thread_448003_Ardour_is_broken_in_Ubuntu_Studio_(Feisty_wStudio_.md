---
title: "Ardour is broken in Ubuntu Studio (Feisty w/Studio REPO)"
date: 2007-05-18
forum: Multimedia Production
---

### Post by Spectre31337 on 2007-05-18
Last night after I added the Ubuntu Studio REPOs 

[COLOR="Blue"][I][SIZE="1"]sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update (as directed by the Ubuntu Studio website.)[/SIZE][/I][/COLOR]

It looked like everything was going to work. When I restarted I could no longer use my wireless card and the Ardour install was broken. :confused: Is it something I did? I tried everything to remedy this but nothing helped. Also this is a fresh install or Feisty and I do not have Ardour 1 installed (I don’t have a DVD-ROM or I would just get the ISO). 

Please let me know if there is anything I can do to get Ubuntu studio installed over clean install of Feisty


//Spec

---

### Post by MetalMusicAddict on 2007-05-18
Its not broken your missing something I bet.

I'm willing to bet you now have 2 kernels only one of which has the restricted modules for your wifi to work. Do this: **sudo apt-get install linux-lowlatency**

Next, uninstall **ardour-gtk** and install **ardour**. In bold are the exact package names you need to work with here.

---

### Post by Pocadotty on 2007-05-18
first, for good measure, you might want to do a complete removal of Ardour 2, which will be reinstalled with the ubuntustudio-audio package.

Since you already have the repos added, in Synaptic Package manager search for and add the fallowing packages.

ubuntustudio-desktop
ubuntustudio-audio
ubuntustudio-audioplugins 
ubuntustudio-graphics
ubuntustudio-video


this will update Fiesty to ubuntu-studio... If things arnt working, boot into the old kernel and add this package

linux-restricted-modules-lowlatency

which will likely fix any driver issues you may have.

did that answer your question?

---

### Post by Spectre31337 on 2007-05-18
Over lunch I tried to uninstall Ardour without any luck. You mentioned that I could boot in a different kernel. How do I do that?

Also what is the difference between the kernel that comes with Feisty and the low latency?

---

### Post by Pocadotty on 2007-05-20
when you boot your machine the grub boot-loader starts which selects which OS to boot.  For instance, windows would be an option if your doing a dual boot system.  When a new kernel is installed on your system it adds a new choice is grub, and changes the default if the new kernel is for the same OS.

So when you install ubuntustudio-desktop, and therefore the low lattency Kernel, when your system starts grub will automatically choose the new Kernel, unless you choose a different one with your arrow keys.  In this way you could boot up the system using whatever OS or Kernel you have installed on your machine.

The basic difference between the low latency kernel and the standard kernel is that the low latency one is optimized for better audio production performance.  Latency is the amount of time it takes for your system to respond to Audio requests.  Having a low latency is very important for audio recording and crucial if you want to do live effects of preform with your machine.

Standard linux kernels are not bad on latency, but the low latency kernels are golden.  If you are going to use your machine for audio work, you want the low latency kernel.

What did you do when you tried to uninstall Ardour? and why didn't it work?  did you use Synaptic?

---

### Post by zettberlin on 2007-05-20
> **Pocadotty said:**
> 
Standard linux kernels are not bad on latency, but the low latency kernels are golden.  

So if Ubuntus lowlatency-kernel ist "golden" what is an rt-kernel with Molnarpatches - paltinum? plutonium? ;-)

Due to the fact, that Ardour 2 still sees bugfix-updates frequently I recommend to download the recent sources from ardour.org and build it yourself - it is really not sooo complicated, you just need to install a couple of devel-packages and compilers with a few klicks in synaptic:

[http://ardour.org/building](http://ardour.org/building)

than you just have to issue scons in the folder in wich the sources are unpacked and you get a perfectly working Ardour 2 (Build works perfectly by the book on Ubuntu feisty).

good luck ;-)

---

### Post by ricrac on 2007-05-20
Just a datapoint: 
Multiboot
Installed Feisty 7.04 32bit converted to studio with meta-packages
and
Installed ubuntustudio-7.04-alternate-i386.iso
2.6.20-15-lowlatency kernel, default on ubuntustudio
Ardour/GTK 2.0 (built using 1762 and GCC version 4.1.2 (Ubuntu 4.1.2-0ubuntu4))

Removed ardour, installed ardour gtk2, works.

Self compiled version better, currently.  I have to, I need/want VST plugins.  

Note: I have not compiled ardour yet on Ubuntu or Ubuntu studio.  
I use 64Studio and Jacklab like this describes, Ardour2 article from LJ
[http://www.linuxjournal.com/node/1000224](http://www.linuxjournal.com/node/1000224)

---

### Post by Spectre31337 on 2007-05-21
I connected hardline to my router and installed

linux-restricted-modules-lowlatency

Worked like a charm thanks to all for your help

---

