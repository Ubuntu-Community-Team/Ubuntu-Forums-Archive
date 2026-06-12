---
title: "[SOLVED] Wireless on a Dell Inspiron 6000"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by fredbird67 on 2008-12-13
I recently downloaded and installed Wubi with Xubuntu on my wife and I's Dell Inspiron 6000 laptop computer.  This thing has that infamous Broadcom BCM4311 wireless card that's giving me fits.  I tried the how-to article at [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526) but I'm still not getting much of anywhere at all.  Any ideas?

Thanx in advance,
Fred in St. Louis, MO USA

---

### Post by Ayuthia on 2008-12-13
The guide that you are using is missing some information for the Broadcom 4311 card.

You can try the following to see if it will work with you have done so far (in the Terminal):
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo iwlist scan
```

If this works then you need to post the results of the following so that we can make it permanent:
```
cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e ndiswrapper -e wl
cat /etc/modules|grep -e b43 -e ssb -e ndiswrapper -e wl
```

If it does not work, please post the results of the following:
```
lsb-release
uname -a
ndiswrapper -v
ndiswrapper -l
lshw -C network
```
We need some information about what version of Ubuntu you are using along with which version of ndiswrapper you are using and what you have loaded into ndiswrapper.

---

### Post by fredbird67 on 2008-12-13
Ooh...not good!

Right after the very first command, I got:
FATAL: Module ssb is in use.

What else am I supposed to do?

---

### Post by Ayuthia on 2008-12-13
> **fredbird67 said:**
> Ooh...not good!

Right after the very first command, I got:
FATAL: Module ssb is in use.

What else am I supposed to do?

Ok.  Let's try the following:
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo modprobe b44
sudo /etc/init.d/networking restart
sudo iwlist scan
```
If all this works and you are able to connect, please post the results of:
```
lshw -C network
cat /etc/modprobe.d/blacklist|grep -e b43 -e ssb -e bcm43xx -e wl -e 
ndiswrapper
cat /etc/modules|grep -e b43 -e ssb -e bcm43xx -e wl -e ndiswrapper
```
and we can give you the information on how to make it permanent.

EDIT: Just for your information, the ssb module in use means that there is anoter module that is using it.  Most likely you have a Broadcom wired card that is using the b44 module (which requires ssb).  If that is the case, you will also need a script to make your wired and wireless work.

---

### Post by fredbird67 on 2008-12-13
I just noticed -- you also asked for what Ubuntu version I'm running:  I'm running Xubuntu (the Xfce version -- I originally tried Ubuntu on this thing, but it kept choking and even freezing up with GNOME, so I scrapped that and redid it as a Xubuntu installation) Intrepid Ibex, and I've got NDISWrapper 1.5.3 on it (I think, and the reason I say I think is because of an error message I got below, as you'll see)

Anyways, getting back to the issue at hand...

OK, the "sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl" command must've executed OK, because it didn't say anything after that.

However, on the "sudo modprobe ndiswrapper" command, I got the following:
FATAL: Could not open '/lib/modules/2.6.27-9-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory

Thanks for all the help you've been giving so far, I appreciate it.

---

### Post by Ayuthia on 2008-12-13
For some reason the ndiswrapper.ko file is not there.  I think that the module is now found in linux-image.  You might need to reconfigure that package:
```
sudo dpkg-reconfigure linux-image-2.6.27-9-generic
```That should rebuild the kernel and the modules.

---

### Post by fredbird67 on 2008-12-13
and then I should be able to run those other commands, right?

---

### Post by Ayuthia on 2008-12-13
> **fredbird67 said:**
> and then I should be able to run those other commands, right?

Correct.

---

### Post by fredbird67 on 2008-12-13
Thanks a lot -- now I have no WIRED connection, either, and I even tried rebooting three times!  Thankfully this is a Wubi install, where I could scrap it and start all over again if I had to.  Hopefully there's a way out of this mess...

---

### Post by Ayuthia on 2008-12-13
> **fredbird67 said:**
> Thanks a lot -- now I have no WIRED connection, either, and I even tried rebooting three times!  Thankfully this is a Wubi install, where I could scrap it and start all over again if I had to.  Hopefully there's a way out of this mess...

Sorry about that!  I haven't seen that happen before.  Since it seems that you are using Intrepid (8.10), you might be able to use the wl driver.  Please try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
```
If no error messages occur, then your wired card hopefully has come back and maybe your wireless will work also.

EDIT: For the future, the next time you plan to rebuild Ubuntu,try using the wl driver first.  After you install Ubuntu, all you have to do is go to System->Administration->Hardware Drivers and activate the Broadcom STA driver.  That would be all you have to do.  We are going this route because you started with NDISwrapper first and it will take more steps to back everything out although the dpkg-reconfigure portion was unexpected.

---

### Post by fredbird67 on 2008-12-13
Nope, got an error on the very first command:
FATAL: Module ndiswrapper not found.

---

### Post by Ayuthia on 2008-12-13
Ok.  Let's skip the ndiswrapper portion for now and try:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart
```
For some reason, the ndiswrapper module is not loading/installed.

---

### Post by fredbird67 on 2008-12-13
Ahh...I unplugged my network cable from my desktop computer (which is running Ubuntu 8.04, BTW -- the GNOME version, that is) after the third command and plugged it into the laptop and lo and behold I got the wired networking back before even having to enter that last command.  Should I go ahead and do that last command anyway?

---

### Post by Ayuthia on 2008-12-13
You don't really have to do the last command because it seems that the system found the modules quickly enough.  Are you able to see any wireless sites if you type:
```
sudo iwlist scan
```

---

### Post by fredbird67 on 2008-12-13
OK, I got a mess 'o stuff, but Ubuntu Forums won't let me post it because it says it contains too many images.  In looking at the error message details, it mentioned all the emoticons and such -- except I didn't use any in that post (probably from all those MAC addresses it spit out, I think)

However, I discovered that there's an attachment icon, so I've got the output of that command saved as a file attachment.  In fact, when I saw how much it spit out, I decided to save it to my flash drive and open it on the desktop that way instead of just typing in what it said, so I've got that to fall back on.  Therefore, the output is in the attachment.

I posted this about half an hour ago, and since there hasn't been a response yet, it's 11:00 PM here (U.S. central time) and so we're gonna hit the sack for now.  I might be on here tomorrow morning between 6 and 8 before going to church and will probably be back here sometime around 1:00 PM or so after church.

Thanx again for all the help you've given so far.

---

### Post by Ayuthia on 2008-12-14
> **fredbird67 said:**
> OK, I got a mess 'o stuff, but Ubuntu Forums won't let me post it because it says it contains too many images.  In looking at the error message details, it mentioned all the emoticons and such -- except I didn't use any in that post (probably from all those MAC addresses it spit out, I think)

However, I discovered that there's an attachment icon, so I've got the output of that command saved as a file attachment.  In fact, when I saw how much it spit out, I decided to save it to my flash drive and open it on the desktop that way instead of just typing in what it said, so I've got that to fall back on.  Therefore, the output is in the attachment.

I posted this about half an hour ago, and since there hasn't been a response yet, it's 11:00 PM here (U.S. central time) and so we're gonna hit the sack for now.  I might be on here tomorrow morning between 6 and 8 before going to church and will probably be back here sometime around 1:00 PM or so after church.

Thanx again for all the help you've given so far.

It looks like you might be able to connect.  You can try the following to see:
```
sudo iwconfig wlan0 essid linksys
sudo dhclient wlan0
```If it looks like it assigns you an ip address, then you should be connected.  The only thing that I would recommend is that you might want to change the name of your router and possibly the channel.  There is another access point with the same name and channel.  There is always the possibility that you might get on theirs or vice versa.

---

### Post by fredbird67 on 2008-12-14
OK, I don't appear to be getting an address.  I got the following:

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:34:5d:93
Sending on LPF/wlan0/00:14:a5:34:5d:93
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No CHEPOFFERS received.
No working leases in persistent database - sleeping.

BREAKING NEWS -- BREAKING NEWS -- BREAKING NEWS
I just logged out and logged back in and was able to click on "linksys" in time -- and it CONNECTED!!!!

However, if that wireless connection icon disappears before I can get to it, how do I get it to reappear again?  That's what happened the first time before I could get to it.

Anyways, Ayuthia, you are a GENIUS, and I mean that.  Thank you for all you've done.

PS -- I've also been wondering where one changes their network name in Xfce.  Wubi assigned it "ubuntu" but I'd like to change it to "laptop" instead, and I've been looking all over for that but can't find it.  Any idea?  Or is it something that has to be done via command line instead?

---

### Post by Ayuthia on 2008-12-14
You wil most likely need this so that it will work on rebooting next time:
```
echo -e '#ssb/wl workaround, added' `date` '\ninstall wl modprobe -r b43 b44 b43legacy ssb ndiswrapper; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl
```
All this will do is create a file in /etc/modprobe.d called wl.  It is a set of instructions to remove the b43, b44, ssb, and ndiswrapper modules.  Then it will load the wl module and finally load the b44 module.

As for the naming convention, if I recall correctly, it is assigned in /etc/hostname.  

Hope that helps!  Glad to see that the card is working!

EDIT:  I am not too sure about the network icon problem.  I do most of my things at the command line.  Sorry.

---

### Post by fredbird67 on 2008-12-14
Awesome!  Everything's working perfectly now.  You seem to know everything there is to know about all those commands and such.  Tell me something, how long have you been using Linux?  You must be a Linux network administrator or something...

Many, many thanks -- you ROCK! :guitar:

PS -- now my wife has asked me to get off of here so she can do something on here in that other operating system. LOL

---

### Post by Ayuthia on 2008-12-14
I have been using Linux since March 2007 or so.  However, I have used Unix since the early 90's so I have a decent background in the command line.  I am also a programmer so I like to tinker around with a lot of things in the system.  That is the nice part about Linux is that you can find a lot of things to dive into and learn.

I am glad that it is all working now. I hope that you have a lot of fun with Linux!

---

