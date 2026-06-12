---
title: "Network settings freeze when trying to set properties for &quot;Wireless connection&quot;."
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by Rotta on 2006-06-10
Hardware involved:

ECS NFORCE4.--A939 with AMD Athlon 64/3700
CNet Wireless-G PCI Wireless network board. (RT2500 chipset)

I have recently converted my laptop to Ubuntu 5.10, and beeing very happy with it, I have also upgraded it to 6.06.  :-D I would very much like this OS also on my new desktop computer (as described above), and happily inserted the CD in the player and switched power on.

Everything seems to go well, but I do not get netwok access through the wlan as I planned.  I see there are a lot of postings around on this issue but none with exactly the same sympthoms as I observe.  The RT2500 chipset is supposed to be supported by Ubuntu 6.06 right out of box.

Well: I have now installed the OS from scratch to make sure that I didn't do anything wrong in the process.  When the system is up and running, the first thing I do is to select System->Network settings.  The box says that eth0 is active (but I have not wired it to the router), and that the interface ra0 is not configured.  I select "Wireless connection" and press properties - and then the "wheel" starts spinning.  After that nothing happens [-(. I am not able to start any other applications and I have to reboot the system in "windows fashion" :-# to get up&running again.

Any clue, boys&girls?

-Rotta

---

### Post by mozetti on 2006-06-10
I had similar symptoms also.

My advice is to disable the eth0 connection first, in Network Settings, and then try to configure the ra0 interface. Also, if you're using an SMP kernel, then you need to get rid of it. When I checked a few weeks ago, one known issue was the RT2500 driver didn't play nice with SMP kernels.

---

### Post by sagarhshah on 2006-06-10
I had the problem of my OS freezing when I try to activate ra0 (ralink 2500 wireless networking card). And this was on a fresh install of dapper.

So what did I do? I installed breezy (wireless works fine in there) then did a dist upgrade to dapper and everything seems to be working fine even the wireless.

Dont understand why it worked like that.

The only problem is I will have to do it that way for each and every computer at home as all them have an RT2500 card (some pci some pcmcia some usb).

I think I'll leave breezy on my other computers for a while till wireless is sorted out.

---

### Post by Rotta on 2006-06-10
Both are good suggestions, but I'm afraid they do not work...[-( 

Disabling the eth0 before trying to set ra0 properties does not affect the problem at all.

The very reason for installing 6.06 in the first place was that it cured another problem: None of the 5.10 images I have tried has been able to install GRUB, and the installing process freezes at 0% progression at this point. So - if anyone got a solution to the "Grub install freeze probelm", I can give it another go - else I have to stick with the 6.06 and find a solution to the wlan problem in there.

By the way: I have installed the 6.06 Ubuntu Desktop AMD 64 image.

-Rotta

---

### Post by sagarhshah on 2006-06-12
I thought of something.

You could try setting up wireless using a live cd!!

Meaning basically boot into a live cd and then adjust the text file that holds the network settings. the location is /etc/network/ and the file name is interfaces

That might work.

---

### Post by Catweasle on 2006-07-03
Well, you are not alone.  I am also seeing the same problem of the computer locking up when I try to activate the CNET CWP-854 card using the RT2500 chipset.

I am using Breezy 5.10 and have tried disabling the ETH0, also tried upgrading to the latest driver from the CNET site.  Also tried recompiling a custom kernal. 

So far every thing I have found in the forums or WIKI has not helped.

lspci gives

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0d.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

so at some level, the computer knows the card is there.

Sorry I could not come up with a solution but I can confirm the same symptoms.  I am not ready to give up yet, but any suggestions welcome.

---

### Post by insyte2 on 2006-07-06
I have the same problem.  My laptop would also freeze when I try to change the settings of my wireless card after a fresh install of 6.06

0000:00:09.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

Currently trying out the solutions here in the forums, but so far none has also worked for me.

---

### Post by insyte2 on 2006-07-06
I have the same problem.  My laptop would also freeze when I try to change the settings of my wireless card after a fresh install of 6.06

0000:00:09.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

Currently trying out the solutions here in the forums, but so far none has also worked for me.

edit : sorry for the multiple posts, my connection was buggy, didnt realize that it was already posted. hope a moderator can fix this. Thanks.

---

