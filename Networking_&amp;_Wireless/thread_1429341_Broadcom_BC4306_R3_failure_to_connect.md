---
title: "Broadcom BC4306 R3 failure to connect"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by jippers_2008 on 2010-03-13
Hi All,

I'm getting to my wits end.  I am a newbie and I really want to use Ubuntu, really I do!  But i just can't get wireless going!!!

Here's what I have:

The machine I have installed Ubuntu Studio 9.10 on is a Compaq Presario M2000 with a Broadcom 4306 R3 wireless card in it.  

Here's what I have tried:

1.  Installing Ubuntu Studio with a wired connection.
2.  Downloading the driver (bc43) which comes natively with 9.10 and should support the card.
3.  Enabling the driver in Hardware Drivers.
4.  Using Synaptic package manager to get fwcutter and to install the firmware.
5.  Tried blacklisting the free driver and using ndiswrapper with the compaq windows driver.

All to no avail.

When running the machine on after doing points 2, 3 and 4, wire blue wireless light comes on, but there is no connectivity.  When I check the connection (i.e. to ping something) in Network Tools, I try to choose the option to "configure interface" for my wireless and I get a message saying "Cannot find the interface".

Now, two questions.

1.  How do I un-blacklist the drivers I blacklisted with the ndiswrapper install?
2.  Running a driver that is supposed to support the card, how do I get it to work???

I swear I've done heaps to resolve this and have come to nothing.  This may already be documented somewhere, and for the life of me I cannot find it.  And feedback would be appreciated!!

Thanx heaps

---

### Post by cchhrriiss121212 on 2010-03-14
Firstly do you have gnome network manager or wicd installed? US does not come with a network manager as it interferes with audio applications. Here is a similar thread:
[http://ubuntuforums.org/showthread.php?t=1421191](http://ubuntuforums.org/showthread.php?t=1421191)

---

### Post by jippers_2008 on 2010-03-16
Thank you for your feedback.  

I have read through the forums as you suggested through your links (thank you very muchly), installed the network manager as discussed, then i got the network icon in the top corner with the red cross on it.  I still couldn't get it to configure or connect to the network.  

So, following on from there, I ran:

sudo apt-get install bcmwl-kernel-source

and now my drivers in hardware Drivers are gone completely and the Network Manager reports there is no wireless at all.  I now don't know how to reverse this last command!!!

Feeling completely confused and disheartened now after another 2 hours working on this.  What do I do now?  Why is it so difficult????? *exasperated sigh* :confused:

---

### Post by cchhrriiss121212 on 2010-03-16
Wireless problems are very common with ubuntu, but most can be made functional eventually. The trouble with Studio is that wireless will interfere with audio applications, so if that is what you will be doing, I recommend a dual boot.  

If you don't want that I would try a live cd of regular desktop ubuntu and see how that goes. You could also check your bios settings for wireless enabled/disabled settings. Did you reboot after running that command?

---

### Post by jippers_2008 on 2010-03-17
ok - so maybe it's worth, then, running a standard install of Karmic (not the studio variant) and then adding the multimedia apps that I really want to add, such as Ardour, SoftSqueeze, MythTV et al separately through the Synaptic Package Manager, AFTER the base OS is running smoothly?

Hopefully a change in strategy will resolve the issues I'm facing...?

---

### Post by cchhrriiss121212 on 2010-03-17
Well just download a live cd of regular karmic and boot from it. If you can get wireless going in the live environment then I would use a fresh install of that or resize a partition and dual boot with a shared /home. You may have changed some setting which is causing trouble without realising.
This is what I do on my system so that I have one OS for basic things and another which is pure audio production.

---

### Post by jippers_2008 on 2010-03-18
I just find administering two operating systems on the one unit would be too time consuming.  Plus, my test machine isn't the speedyest machine on the planet, so it would require some more disk space and processing power before I did too much fancy stuff.

Anyway, I'll try the fresh install of Karmic Desktop and go from there.  

Thanx heaps

---

