---
title: "EVGA  6200 512 MB Video card not responding to ANY drivers....."
date: 2009-08-03
forum: Mythbuntu
---

### Post by sawbuck on 2009-08-03
I hope someone can steer me to a post or site that will cure my problems.  I've posted my installation on the sticky devoted to working/nonworking configurations.  My main issue is the inability of any driver solution suggested by numerous threads to solve the problem of being recognized.
 
Of course, the EVGA websiite maintains it does not support Linux but I assumed NVIDIA drivers would work but, alas, none of them do regardless how many I try, fresh install, stripping old non-working, using ANY of MYTHBUNTU update procedures, the "How to" thread for NVIDIA installation, ENVYNG, or anything, nothing I've tried works.
 
I am able to get MYTHBUNTU, 9.04 installed with open source VGA drivers, but LIVE TV or even Low Rez transcodings (720 by 480) are choppy.  Before a Fedora 8 system crash I was able for transcodes at that resolution to work.  When I rebuilt, upgrading an ATI 8500 Radeon 128 LE video card to the current EVGA card, I assumed 512 Mb video EVGA would make live TV (at least in std DTV) be watchable.  Ain't the case - it is choppy and always defaults back to VGA drivers before even booting.
 
Has anyone found a similar problem and, more importantly, a solution?  Would greatly appreciate hearing from you.

---

### Post by sawbuck on 2009-08-03
Still Trying,,,,

Tried a command i saw on a thread for "NVIDIA drivers" on the Absolute Beginner section of the forums.  the:

[INDENT]sudo apt-get install build-essential
[/INDENT]
command went off and got a bunch of stuff so I retried all the driver install techniques again but to no avail.

I still get the error message that seems to say it can't find the "PCI Device"   Does it make a difference that the card is AGP?  If so, where do I edit something to make it recognized?

---

### Post by klc5555 on 2009-08-04
> **sawbuck said:**
> Still Trying,,,,

Tried a command i saw on a thread for "NVIDIA drivers" on the Absolute Beginner section of the forums.  the:

[INDENT]sudo apt-get install build-essential
[/INDENT]
command went off and got a bunch of stuff so I retried all the driver install techniques again but to no avail.

I still get the error message that seems to say it can't find the "PCI Device"   Does it make a difference that the card is AGP?  If so, where do I edit something to make it recognized?

You won't get much of anywhere with the Open Source nv drivers, though they can be OK for SD/Analog playback on suitably hefty hardware. (I assume that even though the output is choppy, your open source driver _does_ actually function at a resolution above 640x480 and 16/256 colors; if not, then the problem is more serious). One way or another you'll need to get the proprietary NVidia driver loaded. The card is AGP, and some motherboard hardware bios setups require you specify "AGP" or "PCI". 

What PCI devices are on the machine? There is, for example, the well known NVidia driver conflict with the Hauppauge 1600 tuner's cx18 driver that is easy to fix.

A first step might be to gather and post the output of the lspci command to the list for everyone to see what's going on with the devices and driver loads.

---

### Post by sawbuck on 2009-08-04
> **klc5555 said:**
> You won't get much of anywhere with the Open Source nv drivers, though they can be OK for SD/Analog playback on suitably hefty hardware. (I assume that even though the output is choppy, your open source driver _does_ actually function at a resolution above 640x480 and 16/256 colors; if not, then the problem is more serious). One way or another you'll need to get the proprietary NVidia driver loaded. The card is AGP, and some motherboard hardware bios setups require you specify "AGP" or "PCI". 
 
What PCI devices are on the machine? There is, for example, the well known NVidia driver conflict with the Hauppauge 1600 tuner's cx18 driver that is easy to fix.
 
A first step might be to gather and post the output of the lspci command to the list for everyone to see what's going on with the devices and driver loads.
 
 
Ah, that (the fact I have the Hauppauge HVR 1600) sheds some light on it.  My original system - same 1600 card - had an ATI Radeon 8500 LE (AGP) that took some tweaking by my 'puter-whiz son before it was recognized by Fedora 8.
 
With Mythbuntu 9.04, TV does actually work but I selected a Samsun DVB for a TV input device in MYTH setup.  As far as resolutoin goes I thhing it does 1024x768 outside of TV - which I'm not sure what it is.
 
I'll see if my ASUS P4B533 has the ability to select AGP.  Also, I did the lspci but don't think I figured out how to get it into an editor or a post.  Any ideas?
 
Thanks for trying to help out this clueless noob.

---

### Post by klc5555 on 2009-08-05
> **sawbuck said:**
> Ah, that (the fact I have the Hauppauge HVR 1600) sheds some light on it.  My original system - same 1600 card - had an ATI Radeon 8500 LE (AGP) that took some tweaking by my 'puter-whiz son before it was recognized by Fedora 8.
 
With Mythbuntu 9.04, TV does actually work but I selected a Samsun DVB for a TV input device in MYTH setup.  As far as resolutoin goes I thhing it does 1024x768 outside of TV - which I'm not sure what it is.
 
I'll see if my ASUS P4B533 has the ability to select AGP.  Also, I did the lspci but don't think I figured out how to get it into an editor or a post.  Any ideas?
 
Thanks for trying to help out this clueless noob.

Don't worry about the lspci. Since you have a 1600 and a Nividia card, the driver conflict is almost certainly the problem.

But it's very easy to fix. The problem is insufficient virtual memory allocation at boot for both drivers; the solution is to set the vmalloc=256m (or vmalloc=512m) parameter in Grub (menu.lst). 

Kernel parameters including vmalloc go on the kernel line in the menu.lst. After the root= statement and any other kernel parameters you may have operating. 

You can edit Grub any way you feel comfortable doing. There are numerous tutorials you can consult. One such is "Ubuntu - How to Edit Grub Boot Parameters" available here:
[http://grumpymole.blogspot.com/2007/...arameters.html](http://grumpymole.blogspot.com/2007/...arameters.html)

But before you actually edit anything, you will want to boot into the Grub command line and "trial" edit the vmalloc parameter into the boot command from there. That way, you can test the vmalloc=256m fix, but the edit won't be saved to disk, so if you really screw it up you'll still be able to boot next time. 

Then, once you're sure you have it right, you can permanently edit the menu.lst file.

---

### Post by sawbuck on 2009-08-05
> **klc5555 said:**
> Don't worry about the lspci. Since you have a 1600 and a Nividia card, the driver conflict is almost certainly the problem.
 
But it's very easy to fix. The problem is insufficient virtual memory allocation at boot for both drivers; the solution is to set the vmalloc=256m (or vmalloc=512m) parameter in Grub (menu.lst). 
 
Kernel parameters including vmalloc go on the kernel line in the menu.lst. After the root= statement and any other kernel parameters you may have operating. 
 
You can edit Grub any way you feel comfortable doing. There are numerous tutorials you can consult. One such is "Ubuntu - How to Edit Grub Boot Parameters" available here:
[http://grumpymole.blogspot.com/2007/...arameters.html](http://grumpymole.blogspot.com/2007/...arameters.html)
 
But before you actually edit anything, you will want to boot into the Grub command line and "trial" edit the vmalloc parameter into the boot command from there. That way, you can test the vmalloc=256m fix, but the edit won't be saved to disk, so if you really screw it up you'll still be able to boot next time. 
 
Then, once you're sure you have it right, you can permanently edit the menu.lst file.
 
Thanks to you, I think the problem is solved. I'm still in the temporary stage but I have a working NVIDIA panel, display up to 1440x900 - the whole thing, I guess. Live TV works great in standard DTV mode but is still stutters in HD. However, I rarely watch Live TV in Myth. In the old system I recorded any HD show and transcoded to mediaum quality which worked fine. I suspect I need a more powerful system if I wanted to watch HD Live.
 
So, thank you very much for the help in gettng past that problem. I was about to give up and go back to a Windows sollution which was not without its own set of problems - and cost. If I stumble on something that brings this Mythbuntu system to HD capability I'll post it here. For now I'll read the link you gave me to firm up the change vmalloc=256m. BTW, I went all the way up to 768m with no difference from 256m. Boot crashed when I went above that.

---

### Post by klc5555 on 2009-08-06
Glad it works.

For HD playback, try changing your playback profile to one of the more efficient ones: CPU-- or Slim, if it's not on one of these already. Reduce anything which may be consuming CPU cycles while you're doing playback.

I don't know the specs of your machine, but HD playback on a single machine depends mostly on CPU speed and how much processing can be offloaded onto the graphics card. The 6200 supports XvMC, a how-to for which is here: [http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC)

All the best.

---

### Post by sawbuck on 2009-08-06
klc5555,
 
Thanks again.  I'll be looking in to the latest tip when time gets freed.

---

### Post by sawbuck on 2009-08-10
klc5555,

Once again your tip was helpful.  I ran thru the processes described in the pointer to XvMCW  and have transcoded a couple of HD broadcasts.  They were perfect!!  Thanks so much for the help.  Again, as time permits I'll devote some of it to getting less "green" and experiment with my combo Backend/Frontend system and post progress/problems as I proceed.

The long term goal is to set up a backend with at least one frontend on the main TV.  Alternmatiele, I hope to have an additional backend in "my" relaxation area.  My wife and I don't always like the same fare.  BUT, the big decider is $$ followed by free time to do it.

---

### Post by klc5555 on 2009-08-11
> **sawbuck said:**
> klc5555,

Once again your tip was helpful.  I ran thru the processes described in the pointer to XvMCW  and have transcoded a couple of HD broadcasts.  They were perfect!!  Thanks so much for the help.  Again, as time permits I'll devote some of it to getting less "green" and experiment with my combo Backend/Frontend system and post progress/problems as I proceed.

The long term goal is to set up a backend with at least one frontend on the main TV.  Alternmatiele, I hope to have an additional backend in "my" relaxation area.  My wife and I don't always like the same fare.  BUT, the big decider is $$ followed by free time to do it.

Glad you're up and running.

The high-octane requirements for TV are (mostly) in playback on the frontend. So, looking down the road, a second backend/frontend combo like you contemplate may be the best solution. Or, if the two rooms are suitably networked (Fast Ethernet or Wireless N) you may want to add another tuner to your current backend/frontend combo, if feasible, (again, I don't know your hardware specs) and wire up just a remote frontend in your "entertainment area". There's a lot of scope for all kinds of setup variants as Myth systems expand.

All the best! :)

---

