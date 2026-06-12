---
title: "bcm43xx causing hard locks"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by unclben on 2006-06-10
I have tried to get my wireless (Dell TrueMobile 1400, using a Broadcom 43xx chip) working twice, following the steps in the [bcm43xx wiki]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx"). I tried the bcm43xx-fwcutter method and the experimental .deb from the cafuego repo. Both times, I got the same result:

1) After firmware installation, wireless support did not change. Dapper could 'see' the chip, but I couldn't scan for signals or connect.
2) When I would try to activate the interface, once via the terminal and once via the Network Manager, Ubuntu would freeze. Mouse and keyboard locked, and not even a ctrl-alt-delete had any effect. A hard shutdown was my only option.
3) After turning the computer back on, the boot would hang completely at a stage titled something like 'reading hardware devices'. Again, the system was totally unresponsive, and I have just reinstalled the OS after each event.

Obviously, I'm pretty sick of reinstalling Ubuntu. Does anybody have a clue as to what's happening? In all the bcm43xx threads, I've never seen anybody mention problems like this.

---

### Post by arottenmind on 2006-06-10
I just got mine working but i had the same problem as you, the lock ups and what not, i found that using bcm43xx-fwcutter and the firmware is what locked it up..

ndiswrapper is what made it work, at first it did not, but its cause i had the wrong .inf files, i to have bcm43xx... On my Dell Drivers Cd, there are 3 .exe files that all contain drivers for the wireless card iam using (not same as yours) Grab ndiswrapper, and ndisgtk from the synaptic package manager.. Once both are installed goto system > admin > windows wireless drivers 

I had to install bcmwl5a.inf and bcmwl5.inf..  Once both are added, make sure it says "Hardware Presnet: Yes" for both of them, if it says no, try the next set of .inf files from the cd.. 

I also had to setup a static ip, but that could be native to my router, and not yours..

But that did not make it work, what made it work in the end is these four commands

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

Once that is all done if it goes smooth, try a reboot..

There may be another way to get it to work but this way worked for me, we had the same error.. Iam not sure if you can disable bcm43xx-fcutter firmware (which is what iam sure caused the crashes, at least on mine anyways) I had to reinstall as i could not find a way to disable/remove the firmware

Hopefully this helps you some, if not gets it working.. Good Luck

---

### Post by unclben on 2006-06-10
Interesting... In a couple hours of searching the forum, you're only the second person I've seen that is getting the same kernel panic as me.

I have been avoiding NDISwrapper for a couple of reasons, but based on your experience it looks like it's my only option to get this POS working.

I think I've come to the decision that I'm going to buy a new mini-PCI card to support vendors who support Linux. In my case, that means Intel Pro/Wireless 2200. I hate to spend the $30, but I suppose it's a small price to pay in order to be able to surf the 'net from my couch. :if there was a 'geek' smiley, I'd use it here:

P.S. You mentioned not being able to disable the bcm43xx firmware... There is a package called bcm43xx-firmware that is installed as part of the base 'desktop' system in Dapper. I don't know what happens when you remove that package, but it's probably worth a try.

---

### Post by Fully216 on 2006-07-25
I had the same problem, running amd64 dapper with 2 GB of RAM.

To resolve this issue without a clean install, I booted into recovery mode.  From there you have a terminal window as root.

to remove the installed bcm43xx package, I simply

apt-get remove --purge bcm43xx-fwcutter
apt-get remove --purge nm-applet

Then I removed the firmware by 

cd /lib/firmware
rm bcm43*

Now when you reboot, there should be no problem.  ;)

---

### Post by quad3d@work on 2006-10-20
You are not the only one with hard-lock problem. I encountered same thing while using 64-bit... I revert back to 32-bit and everything runs fine.

---

### Post by yesudeep on 2008-01-03
I'm still facing the same problem on both am64 and i386 architectures.

Regards,
Yesudeep.

---

