---
title: "My Natty testing installation has gone nutty"
date: 2010-11-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-11-09
The last time I used natty (on my testing partition), everything was working. That was probably Sunday (two days ago).

This morning, when I booted to it, the first thing it did was scroll a bunch of text messages, the last few of which indicated it was recovering and checking the filesystem. That all completed successfully. Then, for some reason it came up with a text login. I logged in and ran "sudo service gdm start" and it successfully brought up the Gnome Shell desktop.

Next, I found out that it was disconnected from the ethernet. There were no network hardware problems, so I rebooted to Maverick, where there are no apparent problems and the ethernet connection is fine.

Is this related to the other thread about desktop breakage? I have not installed any updates or other changes since natty was working, Sunday.

Thanks,
Tim

---

### Post by dino99 on 2010-11-09
i've got it too but only once, no broken dependencies, might be a transitional problem

now everything is ok but i only use the main repo (no proposed, no ppa but x-swat)

---

### Post by ratcheer on 2010-11-09
> **dino99 said:**
> i've got it too but only once, no broken dependencies, might be a transitional problem

now everything is ok but i only use the main repo (no proposed, no ppa but x-swat)

Thanks. I guess I will just try again, later.

Tim

---

### Post by lonniehenry on 2010-11-09
I am getting this also.  It seems to be intermittant tho.  Sometimes it continues to a normal boot and sometimes it hangs.  Have puzzled over it but can't seem to find any reason for it. Nothing that I see in the logs.

---

### Post by ranch hand on 2010-11-09
> **lonniehenry said:**
> I am getting this also.  It seems to be intermittant tho.  Sometimes it continues to a normal boot and sometimes it hangs.  Have puzzled over it but can't seem to find any reason for it. Nothing that I see in the logs.
Plymouth as your boot manager has several bugs against it (pretty much ignored) having to do with the empty logs.  It is responsible for writing them.  It doesn't do it.  Therefore your boot is perfect.

---

### Post by ratcheer on 2010-11-10
The problems are not intermittent for me. It always recovers and checks the filesystem, finishes at a text login, does allow me to manually start the desktop, and is disconnected from the network.

If I boot to the next most recent kernel on the same testing partition (2.6.36-1), everything works, correctly. The kernel giving me all the trouble is 2.6.37-2.

Tim

---

### Post by autocrosser on 2010-11-10
Hmmm--I've been having problems with the -2 kernel also, on the -1 until things smooth out a bit. In my case GDM will start & then the system just hangs--this is not happening every time, but enough times to be a bit of a bother....when it will goto desktop there are no other problems........Interesting times have started

---

### Post by Benjamin_Lebsanft on 2010-11-10
Same here, always text login with .37-2

---

### Post by ratcheer on 2010-11-10
Does anyone think it would help to reinstall natty from today's CD image?

Tim

---

### Post by autocrosser on 2010-11-10
I would say to wait a bit--looks like things are in "flux'---My main install is now not loading gnome-panel or nautilus....so I'm on my backup 11.04 install that tests the Unity desktop....It's working just fine........

---

### Post by ronacc on 2010-11-10
After todays updates I can boot to a normal Gnome desktop with no problems but system>preferences>appearances freezes trying to enable effects ,The DT continues to function normally though .

---

### Post by ratcheer on 2010-11-11
Well, ok. I just tried to do a fresh install of natty from today's (Nov 11) iso image. It says it cannot detect my network hardware. I retried it twice, but I assume this is the same problem it is having with my network on my already installed 2.6.37-2 kernel.

There is obviously nothing wrong with my network hardware. It is working fine on 10.10 (I am using it now) and on natty with kernel 2.6.36-1 (and everything older).

I hope they haven't eliminated older hardware from being used. This PC is pretty old (6 years), but I didn't think it was *that* old.

Tim

---

### Post by ratcheer on 2010-11-11
Are manual bug reports a thing of the past? I have searched for a natty bug that I cannot install the current iso because the network hardware is not detected. Apport is useless for this kind of situation.

 I searched launchpad for the same or similar bug, but can only find two network bugs, neither of which is remotely similar.

Tim

---

### Post by cariboo on 2010-11-11
Have you tried filing a bug against ubiquity using:

```
ubuntu-bug ubiquity
```

---

### Post by ratcheer on 2010-11-12
No, but thank you for the tip.

Tim

---

### Post by ratcheer on 2010-11-13
There have been no new natty images for the past two nights. Are they approaching a new milestone?

PS - Just checked the release schedule and Alpha 1 is not until 2-Dec.

Tim

---

### Post by ratcheer on 2010-11-15
Still no love.

Since there is no revised alternate image for the past several days, this morning I tried to use the Live iso dated 11/15 (today). It doesn't work, either, but it doesn't tell me why. It sets up nouveau, then the keyboard, then the mouse. Then it just stops. No warning or error messages of any kind.

:(

I suspect it still does not detect my network card, but can't really tell.

Tim

---

### Post by VMC on 2010-11-15
> **ratcheer said:**
> Still no love.

Since there is no revised alternate image for the past several days, this morning I tried to use the Live iso dated 11/15 (today). It doesn't work, either, but it doesn't tell me why. It sets up nouveau, then the keyboard, then the mouse. Then it just stops. No warning or error messages of any kind.

:(

I suspect it still does not detect my network card, but can't really tell.

TimRead the contents of file ".xsession-errors". If you try the Try Ubuntu, then C+A+F1, and vi or cat out that file. I see reference to compiz errors.

---

### Post by ratcheer on 2010-11-15
> **VMC said:**
> Read the contents of file ".xsession-errors". If you try the Try Ubuntu, then C+A+F1, and vi or cat out that file. I see reference to compiz errors.

I'm not sure you understand. The Live CD never finishes coming up, it never gets to the point of "Try Ubuntu". There is a brief plymouth screen, then a text screen that gives messages about nouveau, keyboard, and mouse, then everything stops.

Thanks, though. I will try to find that file, somewhere.

Tim

---

### Post by VMC on 2010-11-15
> **ratcheer said:**
> I'm not sure you understand. The Live CD never finishes coming up, it never gets to the point of "Try Ubuntu". There is a brief plymouth screen, then a text screen that gives messages about nouveau, keyboard, and mouse, then everything stops.

Thanks, though. I will try to find that file, somewhere.

Tim

OK. I thought it stopped for you at the purple screen, with nothing else. That's how its been for the past two days for me. I then opened a VT and checked any errors that I could find, such s dmesg and the video logs.

---

### Post by ratcheer on 2010-11-16
There is a new version of the alternate image today. Also, I saw in yesterday's natty change logs a new version of hw-detect. So, I'm off to try the new alt, now.

Tim

---

### Post by ratcheer on 2010-11-16
> **ratcheer said:**
> There is a new version of the alternate image today. Also, I saw in yesterday's natty change logs a new version of hw-detect. So, I'm off to try the new alt, now.

Tim

Nope. It still fails to detect my network hardware. It is a simple Marvell Yukon dated ca 2004. :( It has always worked with my Ubuntu installations going back to Hardy and it worked with Natty through kernel 2.6.36-1.

Tim

---

### Post by cariboo on 2010-11-16
Can you manually load the module your network card needs?

---

### Post by ratcheer on 2010-11-16
> **cariboo907 said:**
> Can you manually load the module your network card needs?

That is beyond my current knowledge level. Can you teach me or point me to a tutorial?

Thanks,
Tim

---

### Post by cariboo on 2010-11-16
Check your working version to see what module is loaded by using the following command:

```
sudo lshw -C network
```

the output should look similar to thei:

```
sudo lshw -C network
[sudo] password for cariboo: 
Sorry, try again.
[sudo] password for cariboo: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:62:eb:b9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169 **driverversion=2.3LK-NAPI duplex=full ip=192.168.1.250 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:d800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdfe0000-fdfeffff(prefetchable) memory:feae0000-feafffff(prefetchable)
```

As you can see, my network card uses the r8169 driver. Just to be doubly sure, check the loaded modules. In my case I would use the following command:

```
lsmod | grep r8169
```

the output on my system looks like this:

```
lsmod | grep r8169
r8169                  39650  0 
mii                     5237  1 r8169
```

Now that we know what module the network card needs, go back to your Natty install, open a terminal and type:

```
sudo modprobe r8169
```

Of course you'll have to substitute your driver for the one in my example.. BTW module and driver are interchangeable.

---

### Post by ratcheer on 2010-11-16
Thanks very much.

I suppose you mean my working version of Natty. First, I will look at it in Maverick, then go to my working Natty. Then, I suppose, go to the non-working Natty and see if I can do the magic.

Thanks, again!

Tim

---

### Post by ratcheer on 2010-11-16
Ok, here is what I found and what happened.

Under Maverick and the working version of Natty, the module is skge.

When I boot to Natty 2.6.37-1, I see this on the screen of text messages:

```
skge_devinit .....
CR2: 0000000000000008
end trace ......
/sbin/modprobe -bv pci: ......
unexpected exit with status 0x0009
```When I try to do "sudo modprobe skge" in the non-working Natty, the command goes into never never land - no messages and it does not return. I checked the system monitor while it appeared to be running, but I could not find modprobe in the list of processes.

Tim

---

### Post by ratcheer on 2010-11-16
I Googled skge_devinit and found a reported kernel bug:

[http://us.generation-nt.com/bug-skge-not-working-module-2-6-37-rc1-help-201060201.html](http://us.generation-nt.com/bug-skge-not-working-module-2-6-37-rc1-help-201060201.html)

I'm not sure what to make of it, but it seems to be identical to my problem.

Tim

---

### Post by cariboo on 2010-11-16
> **ratcheer said:**
> Ok, here is what I found and what happened.

Under Maverick and the working version of Natty, the module is skge.

When I boot to Natty 2.6.37-1, I see this on the screen of text messages:

```
skge_devinit .....
CR2: 0000000000000008
end trace ......
/sbin/modprobe -bv pci: ......
unexpected exit with status 0x0009
```When I try to do "sudo modprobe skge" in the non-working Natty, the command goes into never never land - no messages and it does not return. I checked the system monitor while it appeared to be running, but I could not find modprobe in the list of processes.

Tim

If you don't get anything echoed backed that usually means the command was sucessful. You can check if the module was loaded by typing:

```
lsmod | grep skyge
```

---

### Post by ratcheer on 2010-11-16
Hmmm. Well, the network was still disabled. Also, the modprobe command never completed. I had to do Ctrl-c to get the command prompt back.

In view of the reported kernel error, I suppose I just need to keep waiting until it is fixed.

Tim

---

### Post by ratcheer on 2010-11-19
Finally! 2.6.37-5 kernel successfully detects my network hardware and I got a good, clean install of natty from the 19-Nov alternate ISO.

Tim

---

### Post by karmila on 2010-11-19
> **ratcheer said:**
> Finally! 2.6.37-5 kernel successfully detects my network hardware and I got a good, clean install of natty from the 19-Nov alternate ISO.

Tim

Glad to hear that.

OOT, My current natty installation now is in nice and (relatively) stable state. I think i'm going to backup this partition before next updates bring 'the magic' :D.

---

