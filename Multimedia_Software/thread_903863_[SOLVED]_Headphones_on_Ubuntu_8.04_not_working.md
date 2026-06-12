---
title: "[SOLVED] Headphones on Ubuntu 8.04 not working"
date: 2008-08-28
forum: Multimedia Software
---

### Post by Benjaminp on 2008-08-28
The sound from my speakers work fine, but I have absolutely no sound coming from my headset... (although it does play the "welcome" sound when it's plugged in).
I've installed ALSA, changed the settings in Sound to the headphones, but nothing happens (My headphones connect to a USB port).

I reformatted my computer (where the headphones worked quite well, but I had no external speaker sound.)

Is there some way I can fix this? Any help would be much appreciated!

---

### Post by Crafty Kisses on 2008-08-28
Post results of > lspci

---

### Post by Benjaminp on 2008-08-28
Thanks for the quick reply!

Here's the results:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

---

### Post by Crafty Kisses on 2008-08-28
Have you checked all your volumes in volume control?

---

### Post by Benjaminp on 2008-08-28
Yep they're set to full volume.

---

### Post by Benjaminp on 2008-08-29
Bump

---

### Post by eggdeng on 2008-08-29
You might try
```
sudo apt-get install linux-backports-modules-generic
```
It seems to have worked for other people with the same card.

---

### Post by Benjaminp on 2008-08-29
I don't seem to be able to find the linux-backports-modules-generic package.. Is there a website i can download it from?

---

### Post by djRobbieF on 2008-08-29
If you can't find a backport, just a guess; make sure you have backports active in your Software Sources (System->Administration->Software Sources).

---

### Post by Benjaminp on 2008-08-29
Yep I checked the backports. (That's on the Updates tab, right? I also selected all the names in the 3rd party software list

---

### Post by djRobbieF on 2008-08-29
Then, if you're doing this through terminal, that's probably your issue; you're not specifying the version.

Instead, use synaptic package manager, do a search for "linux-backports-modules" (omit "Generic"), and you'll see the actual package is called linux-backports-modules-##VERSION##-generic

Alternatively, I think you could just do linux-backports-modules-hardy-generic to get the latest, whatever it is.

---

### Post by Benjaminp on 2008-08-29
I searched on synaptic for "linux-backports-modules" and I found a whole bunch of options..


*Edit* Oh ok I'll give that a try, thanks

---

### Post by Benjaminp on 2008-08-29
hmm didn't work.

---

### Post by eggdeng on 2008-08-29
Sorry, I should have pointed this out earlier. If you still haven't been able to install the backports-modules, run
```
gksudo gedit /etc/apt/sources.list
```
Do a search for the term 'backports'. Uncomment the lines (remove the # symbol from in front)
> # deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
Save the file and run 
```
sudo apt-get update
```
and you should now be able to run the original command.

---

### Post by Benjaminp on 2008-08-29
It couldn't find the package, although I'm installing some version backports-modules right now, in Synaptic.

---

### Post by Benjaminp on 2008-08-29
For some reason, my headphones seem to be working now when I change the settings in Sound from Autodetect to USB Media.
Each time I want to switch from headphones to external speakers, I have to change all the settings... Is there a way to fix "audtodetect"?

---

### Post by eggdeng on 2008-08-30
You can set the default device as follows
Code:
```
asoundconf list
```
to see how alsa identifies the available devices. Then run
```
asoundconf set-default-card xyz
```
where xyz is the name of the device you want to use, according to the output of the 1st command.
Reboot for changes to take effect.

---

### Post by Benjaminp on 2008-08-30
OK well this about wraps it up. Thanks for your helpful posts, they were much appreciated!

---

### Post by erikthedrink on 2009-09-08
On my system, I found the xyz under number 1, thus in Terminal, I typed

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then I closed and re-opened my browser (Mozilla Firefox) or restarted my system.
:)
Note, if you unplug my usb speakers, my laptop speakers will take over.  In order to re-establish contact with the usb speakers, I need to (plug them back in) restart the system.

---

