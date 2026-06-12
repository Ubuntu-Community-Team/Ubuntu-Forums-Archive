---
title: "Laptop locks hard on login screen if no ethernet cable plugged in"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by scorbett on 2011-07-15
Acer 5250-BZ475 laptop, fresh install of Ubuntu 11.04. Boots up beautifully as long as an ethernet cable is plugged in. Otherwise, I get to the login screen and have just enough time to start typing in my password before the entire system hangs hard - no mouse, no keyboard, can't even get to a terminal, nothing. Have to hard power off the machine. 

It seems to be a problem with the wireless card trying to initialize, but there doesn't seem to be a bios option to disable wireless on this laptop, so I'm a bit at a loss as to how to fix this problem. By the way, wireless works fine if I boot up with a cable connected - I can see all the wireless access points in my area no problem. I just can't boot without a wired connection, which makes my laptop more or less useless when I'm away from home with it.

---

### Post by bennyroger on 2011-07-16
Hmmm try to disable automatic login via ethernet or disable it, then try unplugging and reboot.

---

### Post by Jamsers on 2011-07-16
Hey scorbett, I had the same problem as you recently. My solution was to enable network boot in the BIOS, then put the network on top of the hard drive in the boot sequence (meaning, make the BIOS try to boot from the network first before making it try to boot from the hard drive). I'm sorry if I can't be any clearer, I'm not that good with computers, and I'm not sure if my BIOS and your BIOS are the same. But I do hope this helps.

---

### Post by scorbett on 2011-07-18
bennyroger: googling for "automatic login via ethernet" brings me back to this very forum post as the first result, so I'm really not sure what you're talking about. Could you explain a little more what you were trying to say there?

Jamsers: thanks, but moving the network up or down in the boot order doesn't seem to have any effect. I've tried it before the hdd and after with the exact same results.

I've also tried removing all kernel modules related to wireless networking and then rebooting, but no luck. I'm really not sure what to do here, except maybe try an older version of ubuntu or maybe a different distro like arch or something to see if I have any better luck there.

---

### Post by bapoumba on 2011-07-18
Does it boot correctly from a live cd or usb ?
Which ethernet card does it have ?

Googling around only brings up this post and one at fedora's you obviously found out already..

Edit: and wireless card which seems to be causing trouble.

---

### Post by scorbett on 2011-07-19
Update: I installed Slackware 13.37 and I see it has the exact same problem: boots fine as long as an ethernet cable is plugged in, hangs horribly on boot if not. However, since Slackware outputs a heck of a lot more diagnostic information during boot, I'm finally able to see exactly where it's hanging:

```

  Polling for DHCP server on interface eth0:
  dhcpcd[1770]: version 5.2.11 starting
  dhcpcd[1770]: eth0: waiting for carrier
  dhcpcd[1770]: timed out
  dhcpcd[1770]: allowing 8 seconds for IPv4LL timeout
  dhcpcd[1770]: timed out

```Perhaps unsurprisingly, it's trying and failing to get an IP address (I don't have a wireless router at home, so of course this will not succeed). What I don't get is why it hangs completely and utterly after the second "timed out" message - no keyboard, no mouse, no nothing. I suspect that the only "fix" I will find for this problem is to take the network initialization out of the boot process altogether and only start the network manually after the system has come up.

Googling for "dhcpcd timed out" gets me a lot of results, but most are old (2007-2009) and none of them mention a system hang like what I'm seeing. I'll just leave this here for future google searchers who may have the same problem: acer laptop 5250 is maybe not the best choice for linux.

---

### Post by bapoumba on 2011-07-19
It is indeed very strange.

I've looked around with the errors you just reported but found nothing close to your symptoms.

I've moved your thread to the Networking area, may be people from here will have suggestions.

---

### Post by Jamsers on 2011-07-20
Huh, maybe you need to enable network booting. It doesn't work if you put it first in the boot sequence, but network booting is disabled.

Otherwise, there's this other solution by dino99. I haven't tried it cause I don't like mucking around the system, but it worked for many users. Hope it works for you too.

> **dino99 said:**
> googling a little around and found lot of users having troubles with wifi:

[https://encrypted.google.com/search?client=ubuntu&channel=fs&q=natty%2Baspire%2B522&ie=utf-8&oe=utf-8]("https://encrypted.google.com/search?client=ubuntu&channel=fs&q=natty%2Baspire%2B522&ie=utf-8&oe=utf-8")

and a possible solution:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034)

look post "3 to blacklist the module :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034/comments/3](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034/comments/3)

sudo gedit /etc/modprobe.d/blacklist.conf


but first you need to be able to boot:
- at bios end process, hold "shift" key down to get the grub menu
- choose "recovery" mode (second line choice)
- choose "network" to get a command line prompt
then run the command line above to blacklist the module, save and reboot  to see if it makes a difference, otherwise you should continue in  recovery mode and you should install the latest kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/current/")
in that order:
- install linux-headers...all.deb
- install linux-headers...i386.deb (as your install might be a 32 bits one, otherwise choose the amd64 one)
- then install the related linux-image package

---

### Post by bapoumba on 2011-07-21
[http://ubuntuforums.org/showthread.php?t=1805746](http://ubuntuforums.org/showthread.php?t=1805746)
[http://ubuntuforums.org/showthread.php?t=1805405](http://ubuntuforums.org/showthread.php?t=1805405)

May be you can find there some ideas to troubleshoot.

---

### Post by pedja_portugalac on 2012-02-18
> **Jamsers said:**
> Hey scorbett, I had the same problem as you recently. My solution was to enable network boot in the BIOS, then put the network on top of the hard drive in the boot sequence (meaning, make the BIOS try to boot from the network first before making it try to boot from the hard drive). I'm sorry if I can't be any clearer, I'm not that good with computers, and I'm not sure if my BIOS and your BIOS are the same. But I do hope this helps.

Thank you very much. It solves my wifes problem on Acer Aspire One 722 with Ubuntu 11.10. :D

---

