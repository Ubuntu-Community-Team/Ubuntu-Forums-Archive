---
title: "100% don't understand ndiswrapper"
date: 2005-01-17
forum: Networking &amp; Wireless
---

### Post by MrTrumpets on 2005-01-17
I have searched this forum.  I was totally terrified to post here.

I have seen so many posts on "ndiswrapper" and how to make it work with wireless network cards.

Every single installation I see has instructions like this...

Install ndiswrapper..    (no clue)
install kernel-blah blah    (no clue)

find the path to your driver  (I have a vague idea)

tada!    ?

??????????????

I have no idea how to install ndiswrapper.. At first I downloaded it in "gz" format to /home/user (me)

I then extracted it..

from that point I was 100% lost.. how do I install?  I see an file called "install" but it does nothing.

I'm very very sorry for beating a dead horse, but I just don't get it!

EDIT.....  --------------

Ok.. I figured out that I can use Synaptic to get ndiswrapped

(I installed a network card on the Ubuntu PC and have my laptop (online wireless) in Windows XP sharing it's connection to directly connect to the Ubuntu PC for connectivity so I can update this PC).. sheesh!  lol

on the "How To - Set up Ndiswrapper"  step 3 says "Boot with the new kernel"

does that mean to simply reboot?

I got step 4 and 5.. maybe even 6 (but who know.. it still doesn't work)

---

### Post by hardcandy on 2005-01-18
If it supports your card, why not try [www.linuxant.com](www.linuxant.com) and use their driver loader for 30 days free trial. They have made fairly simple to install. After a month, you could try the ndiswrapper again.

---

### Post by Alexander Kirillov on 2005-01-20
[QUOTE=MrTrumpets]
on the "How To - Set up Ndiswrapper"  step 3 says "Boot with the new kernel"

does that mean to simply reboot?
[/QUOTE]

Yes. To be precise: if you did upgrade the kernel, then the boot loader offers you to boot using either new kernel (default) or the old one (in case the new one doesn't work). You'd want the new one, obviously. 

If you want more help, please post error messages you are getting when typing, e.g., ndiswrapper or iwconfig.

---

### Post by az on 2005-01-20
What howto did you read that says you need a new kernel to run ndiswrapper?

The problem you are experienceing is that ndiswrapper is a tool which does not yet have graphical user interface.  Ubuntu's next release may address this issue.

Here is the quick nitty gritty.

To make software, people have ideas.  These ideas get written in source code and compiled into executable bits of data.  The argument from the free software-open-source people is that this source code should be available to the users of the executable data.

The practical day-to-day is that you may obtain the source code and so long as it follows the rules, can be compled on any machine.  This is done by entering commands.

tar xvzf file # tar is a command to manipulate archives, xvzf is an argument to that command; Xtract, be Verbose, gZip compression, File named: file

cd directory  #change directory to the directory named directory.  Replace this name with that of the directory created by the extraction of the tarball.

./configure  #poke around and set variables as needed.
./make  #This makes the compiler go.
./make install  # This runs the installation script.

Debian packages are convieniently precompilled.  The installation script and package conflict are managed by your package manager (apt, or it's graphical interface - synaptic)

ndiswrapper itself has commands to run to make it go.  Any of these commands need to be run as the administrator of your system, or else you do not have permission to bugger around with your system files.

sudo ndiswrapper -i DEVICEDRIVER.INF  # this tells ndiswrapper whan proprietary windows driver files to use.
sudo modprobe ndiswrapper  #this loads the driver into the running kernel.
sudo ndiswrapper -l  #this tells ndiswrapper to tell you what you have running.

Next, you go into the network management utility and tell it to use the device now called wlan0.

If the version of ndiswrapper provided by Warty is too old to support your device (progress moves fast), you may need to compile a newer version of ndiswrapper.


Let me know if this helps.

---

### Post by MrTrumpets on 2005-01-21
Sorry I didn't reply sooner.. it helped a lot.. I posted a new topic related, but I AM online. :)

---

