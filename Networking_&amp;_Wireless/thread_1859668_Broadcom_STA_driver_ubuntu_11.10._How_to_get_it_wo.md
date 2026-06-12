---
title: "Broadcom STA driver ubuntu 11.10. How to get it working!"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by Lisko on 2011-10-14
Hi, after installing broadcom sta driver in ubuntu 11.10 and Driver Center reported them Activated and in use, the system continued using the default kernel driver. To resolve this you have to blacklist the module brcmsmac in /etc/modprobe.d/blacklist-bcm43.conf. Hope Ubuntu team will fix it fast so no user-hand needed to properly activate the driver.

---

### Post by Kronalias on 2011-10-14
I've had this.

Disconnect from the net when you install Ubuntu 11.10
Don't install any extras or proprietary drivers when you install Ubuntu

If you've activated the Broadcom STA additional driver then remove it (System Settings => Additional Drivers = STA => remove)

Click on the Connection icon.
If it says it's turned off via hardware then you're on a Dell laptop or something similar so use the Fn-F2 (or whatever yours is) key and have another look

If it says the firmware isn't loaded then proceed

Connect to the net via ethernet

sudo apt-get update
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer

Click the Connection icon again and you should see Wireless Networks as per normal

Good luck!

---

### Post by Dragonbite on 2011-10-14
> **Kronalias said:**
> If you've activated the Broadcom STA additional driver then remove it (System Settings => Additional Drivers = STA => remove)

There are other drivers available (STA)?

My Broadcom isn't working (I started a thread here :[[COLOR="Blue"]_http://ubuntuforums.org/showthread.php?t=1859446_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1859446") ).  The Additional Drivers doesn't find anything and "firmware-b43-installer" gave me an error.

---

### Post by Kronalias on 2011-10-14
I've been installing the prerelease versions of 11.10 for the last few weeks, and I've had problems with the STA driver.

I've had occasional success by removing it, but the only guaranteed way for me to get it to work is with a fresh Ubuntu install and not even attempting to use the STA driver via the Additional Hardware Drivers route. The three sudo commands I posted earlier work for me.

---

### Post by imnvs on 2011-10-14
Doesn't work for the rest of us, though.  It's rather annoying having my laptop attached to the wall because the wireless card doesn't work.  Telling us it worked for you doesn't help rectify this, and only makes things worse for us after saying that those exact steps didn't work for us.

---

### Post by Kronalias on 2011-10-14
I wasn't trying to rub it in, I was just trying to clarify the exact steps I took.

---

### Post by Dragonbite on 2011-10-14
> **imnvs said:**
> Doesn't work for the rest of us, though.  It's rather annoying having my laptop attached to the wall because the wireless card doesn't work.  Telling us it worked for you doesn't help rectify this, and only makes things worse for us after saying that those exact steps didn't work for us.

That's why one of the first things I did was post the question on the forums and hope somebody comes across it with some advice!

So far the experience has been good, except for this!  Argh!

---

### Post by kra4ol4e on 2011-10-14
> **Lisko said:**
> Hi, after installing broadcom sta driver in ubuntu 11.10 and Driver Center reported them Activated and in use, the system continued using the default kernel driver. To resolve this you have to blacklist the module brcmsmac in /etc/modprobe.d/blacklist-bcm43.conf. Hope Ubuntu team will fix it fast so no user-hand needed to properly activate the driver.

I've blacklisted "brcmsmac" but after that it's not loading the STA module - the result is no wireless at all. Any ideas/suggestions?

---

### Post by Xenoty on 2011-10-14
On my Dell Dv6 6190 with b**13 card the wireless doesn't appear at all after the today's update, only the wired section.

---

### Post by kwaanens on 2011-10-14
This might be of use to some reading this thread: [http://ubuntuforums.org/showthread.php?t=1859749](http://ubuntuforums.org/showthread.php?t=1859749) 
I had trouble with my BCM4313, but now it works like a charm. Just adding this, because I know how irritating it is to read hundreds of threads to find the solution to what I'm strugglig with.

---

### Post by MDKfactorx4 on 2011-10-15
I used the steps outlined to get and install the fwcutter drivers. and I did notice that I had to restart the computer before Ubuntu 11.10 loaded the new drivers for my wireless card. The computer did not prompt me do do this after completing the install, its just a habit I have because Im so use to MS widows. After the restart my wireless card was working and I was able to connect to my network via the wireless card. Thank you for the info Ive noticed a couple here that don't realize that you were just trying to help.

---

### Post by Kronalias on 2011-10-15
Thanks for that - it made me feel better! I'm pleased it worked for you.

K

---

### Post by silvertwilight on 2011-10-15
As far as I can tell the b43 is different from STA.
I did the usual things to install the b43 driver including
blacklisting.  wireless still greyed out so  control alt t

sudo modprobe -r b43 ssb
sudo modprobe b43

this got the hidden wireless connection to work and I am on it 
now with firefox.  The problem is now I have to use this same
procedure everytime I start up ubuntu 11.10.  How does one 
transform this info into ubuntu 11.10 so that the hidden
wireless is no longer hidden and wireless is bright and not 
greyed out?   If I have to uninstall and reinstall the b43 driver,
what are the exact steps to do so?     Thanks for your help.
Perhaps the above can be modified for those that have STA driver.

---

### Post by wildmanne39 on 2011-10-15
Hi silvertwilight, this should fix that.
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thank you

---

### Post by silvertwilight on 2011-10-15
Thanks. WoW!  That did the trick!  Rebooted and wireless was there
and clicked firefox and it started right up with the wireless connection.  

In retrospect, since I had had this problem with previous installs
of UBUNTU,  I probably should have declined the choice that came
up with the install of 11.10   -  but who does that - we want
the full install, no matter what!   :-)   I hope that the others
find solutions to their wireless problems.

---

### Post by wildmanne39 on 2011-10-15
Hi, I am glad it worked! Most people will get the wireless issues worked out but it will take some time.
Thank you

---

### Post by jayrulez on 2011-10-15
> **kra4ol4e said:**
> I've blacklisted "brcmsmac" but after that it's not loading the STA module - the result is no wireless at all. Any ideas/suggestions?

I suggest looking at the other blacklisted modules. Also, try to reinstall the additional drivers. 

Just blacklisting "brcmsmac" fixed the issue for me. Good luck

---

### Post by khalid.albouhi on 2011-10-15
> **kwaanens said:**
> This might be of use to some reading this thread: [http://ubuntuforums.org/showthread.php?t=1859749](http://ubuntuforums.org/showthread.php?t=1859749) 
I had trouble with my BCM4313, but now it works like a charm. Just adding this, because I know how irritating it is to read hundreds of threads to find the solution to what I'm strugglig with.

This worked for me Thanx :popcorn:

---

### Post by polyethlene on 2011-10-18
I had a firmware missing message under my wireless networks and could not activate the driver.

I used Kronalias advice

Connect to the net via ethernet

sudo apt-get update
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer

Then I had to go back through the System/Drivers and activate the Broadcom STA driver. Works now!  Thanks.

---

### Post by brunoscunha on 2011-12-15
I found this solution working @ [http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

« Fixing Problems with Gnome Indicator Applets
Ubuntu 11.10: Unity Desktop Poll »
Ubuntu 11.10 getting wireless BCM4311 working

October 15, 2011 by Neil Smith

I have an HP laptop model nx6325 with a Broadcom BCM4311 wireless card.  After installing Ubuntu 11.10, I find that my wireless doesn’t work.  The reason, Ubuntu detects the wireless but then loads the incorrect driver for this card.

I use the lspci command to display the details about my hardware. It will display all of your PCI connected hardware. I edited the output to show only the relevant information.  The important information here for  matching your hardware with mine is this indentifier [14e4:4312].

$ sudo lspci -v
 
30:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
        Subsystem: Hewlett-Packard Company Broadcom 802.11a/b/g WLAN
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c8000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb
 
$ sudo lspci -nn
30:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

The Solution

I am  going to install the correct driver for this wireless card. Then I will remove the “incorrect” driver (bcmwl) which Ubuntu installed by default.

$ sudo apt-get update
$ sudo apt-get install firmware-b43-installer
$ sudo apt-get remove bcmwl-kernel-source
$ sudo reboot

---

### Post by comperocean on 2011-12-25
> **Kronalias said:**
> I've had this.

Disconnect from the net when you install Ubuntu 11.10
Don't install any extras or proprietary drivers when you install Ubuntu

If you've activated the Broadcom STA additional driver then remove it (System Settings => Additional Drivers = STA => remove)

Click on the Connection icon.
If it says it's turned off via hardware then you're on a Dell laptop or something similar so use the Fn-F2 (or whatever yours is) key and have another look

If it says the firmware isn't loaded then proceed

Connect to the net via ethernet

sudo apt-get update
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer

Click the Connection icon again and you should see Wireless Networks as per normal

Good luck!

my computer: Dell inspiron, BCM 4312, at ubuntu 11.10 (oneiric ocelot) can not working;
apply all above, all is fine.
thanks so much.

---

### Post by Solthun on 2012-01-04
Thank you so much... I cant tell you how much time I wasted with this.....
I had everything intalled from a good couple of threads.... so all I really needed to do is remove that stuped thing from additional drivers and RESTART. Thanks again

---

### Post by ewolkowicz on 2012-02-06
> **silvertwilight said:**
> 

sudo modprobe -r b43 ssb
sudo modprobe b43



Just wanted to say thanks.  I have an old HP L2000 and in previous version of ubuntu had no trouble enabling the developers drivers that worked just fine.  This version could see the hardware but wouldn't load the correct drivers.  Now that I have the driver loading with the modules on boot I have no problem.  I had to blacklist the other drivers as was mentioned earlier.  So basically did [almost] everything, didn't work, found this post and it works!

I'm new~ish to ubuntu / debian, but definitely not new to linux.  I'm buried in RHEL / Fedora / CentOS every day - mostly servers with no broadcom hardware to deal with ;).

Thanks again silvertwilight, and everyone else who helped!

---

### Post by scedos on 2012-03-04
Thanks Kronalias,
For newbies, and those newly attempting to put Ubuntu on their Dell with a Broadcom wifi card, indeed, his solution works. Works on Lubuntu, too.  Hell, rub it in ;-)

---

### Post by Jonfirste on 2012-04-27
> **Kronalias said:**
> I've had this.

Disconnect from the net when you install Ubuntu 11.10
Don't install any extras or proprietary drivers when you install Ubuntu

If you've activated the Broadcom STA additional driver then remove it (System Settings => Additional Drivers = STA => remove)

Click on the Connection icon.
If it says it's turned off via hardware then you're on a Dell laptop or something similar so use the Fn-F2 (or whatever yours is) key and have another look

If it says the firmware isn't loaded then proceed

Connect to the net via ethernet

sudo apt-get update
sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer

Click the Connection icon again and you should see Wireless Networks as per normal

Good luck!This method works great. I have a Dell E1405. The Broadcom system quit working when I updated from Ubuntu 10.4 to Ubuntu 11.10. I spent hours trying to get the wifi to work. After finding your solution, it works great. Thanks a million. Jon

---

