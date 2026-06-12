---
title: "ATI Radeon 7200 fails to display"
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by eapache on 2006-11-17
I recently salvaged a working ATI Radeon 7200 graphics card (PCI) from an old computer, and installed it in my own (I was using the default until then). My BIOS recognized it and displayed correctly, and GRUB also displayed fine. When I booted Edgy, the boot splash screen appeared, and the bar started to fill. Up until this point, everything worked fine. When about a third of the status bar had filled, it paused for an unusually long time. I assumed that it was downloading or caching a new driver for my card, and after a period of time, the bar continued to fill. After the bar was full, the splash disappeared, and the little blinking cursor appeared in the top left-hand corner. My screen then went blank, and nothing else displayed. I have auto-login enabled, and I heard the login music on my speakers, so the actual system was working, it just wasn't displaying. I turned it off and fiddled with IRQ and video settings in my BIOS to no avail. Booting in recovery mode works fine, and it appears to load the driver fine, but obviously it doesn't. Curiously enough, almost exactly the same thing happens in XP (same computer). The loading screen appears and finishes, the little blinking cursor appears in the top left, and the screen goes blank. I also hear the login music in XP, but nothing displays. Since on both operating systems, the screen goes blank when (I'm assuming this) they load the advanced drivers, it doesn't appear to be in BIOS. I switched the BIOS to use the onboard card, and it still works fine. Anyone have any suggestions? I'm running on a Dell Optiplex GX150 with BIOS version A09.

PS I can't boot from my Edgy cd right now to try that out because my CD drive died yesterday. Really bad timing. ](*,)

---

### Post by ardvark71 on 2006-11-17
Hi eapache...

Looks like your video card is bad or has some incompatibility with the motherboard. You might want to try another card that suits you and see what happens.

I have the same card (Radeon 7200) myself and it performs quite well with my copy of Breezy. The only problem I've had with it is that it won't work with a couple of OpenGL games in full screen mode....which I believe has more to do with the software than the card anyway.

Hope this helps...

:KS

---

### Post by eapache on 2006-11-18
My setup is a little strange. I'm not exactly sure what it is called, but instead of having any PCI slots directly on my motherboard, I have a slot that looks like a PCI slot only a little too big. It has a wierd card that plugs into it, and that card has two PCI slots built directly into it. So my PCI cards are parallel to my motherboard and both running through a single special card. This may be part of the problem, as they are not connected to the motherboard. If I had any other PCI slots directly on my motherboard I'd try plugging it in directly, but I don't. However, my BIOS does seem to recognize them both (the other PCI card I have gives me USB2) as seperate, functional PCI slots. Anyone else have any thoughts, because the card worked about a week ago in the old PC.

---

### Post by barney_1 on 2006-11-18
First of all, I would try commenting out (add a # at beginning of the line) the dri from your "Module" section in /etc/X11/xorg.conf:
```
#	Load	"dri"
```

If that doesn't fix it then you can rule out the video acceleration as the problem.  I have the agp version of this card so the next command might not work for you, but it certainly got me running.  Add this to your "Device" section of /etc/X11/xorg.conf:
```
	Option "AGPSize" "32"
```

---

### Post by eapache on 2006-11-18
The USB2 PCI card that I have in the other slot has also failed to function (it was working fine before). This could mean that my PCI splitter has broken, but then why would I still get basic video (GRUB, BIOS, etc.) running of the ATI card...

Barney, I would like verification that neither of those suggestions would possibly break my onboard card. I need this computer, and if I try one of your suggestions, and I can't switch back to my onboard, then I have no way to reverse the changes (my cd drive is broken).

---

### Post by barney_1 on 2006-11-18
Commenting out DRI just stops 3d acceleration from loading.  Neither of these will do any damage.  That being said, you're on your... if it brakes, that's your business.

If you think you have a faulty splitter, try a different motherboard.

---

### Post by eapache on 2006-11-19
I updated my bios (from A09 to A11), and that didn't solve anything.

I don't have another motherboard to test it on at the moment, so I'll play it safe and stick with my onboard for now. If I get my hands on another splitter or another motherboard, I'll try it.

Does anyone else have any suggestions in the meantime?

---

### Post by eapache on 2006-11-22
I asked here:

[http://forumz.tomshardware.com/hardware/modules.php?name=Forums&file=viewtopic&p=1359265](http://forumz.tomshardware.com/hardware/modules.php?name=Forums&file=viewtopic&p=1359265)

and still don't have a solution. I just thought I'd point to it so people know what I've already tried.

---

### Post by beara on 2007-03-01
From the Bios files you identified, I am assuming you have a dell. I too have had this issue. to resolve it, I booted with the monitor connected to the Radeon and chnged the bios to use the onboard graphics card. After reconnecting the monitor, and booting Unbuntu edgy sucessfully, i then used the information found here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

From reading through this document I came across the following command:

sudo dpkg-reconfigure xserver-xorg

Executing this allowed me to set the driver to that for an ATI card. Before running this command you will need the output from this command:

lspci -x

This will tell you what PCI slot your card is using. Currently the card works for me, but I am still working on adding video capture functionality to this install.

---

### Post by beara on 2007-03-01
Ow...forgot..

You will need to reboot after you make the changes so you can reset the bios to use the PCI card.

---

