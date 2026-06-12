---
title: "Yet another person with sound problems(already used troubleshooting guide)"
date: 2008-12-20
forum: Multimedia Software
---

### Post by Fenix on 2008-12-20
Hello all,

I've recently done a fresh install of Ubuntu 8.10, but can't for the life of me figure out how to get my sound working. I've followed the Comprehensive Sound Problem Solutions Guide here on this forum, but it didn't help. Anyone have any tips? Thanks!

---

### Post by Open-SuSe-A-Me on 2008-12-20
hello, i am not sure what is on the official help page you looked at but...

how many sound cards do you have in your pc? if you have 2 or more you may have to use the "asoundconf set-default-card" command to set it properly.

other than that, what i do is in preferences>sound pick alsa for everything.

what soundcard do you have? if you are not sure, post the results of "lspci" from a terminal.

good luck

---

### Post by Fenix on 2008-12-20
Thanks for the reply!

The guide I followed was the one stickied here in this forum. I just have a single card a Creative Audigy Gamer.

Here are my lspci results:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
03:06.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 04)
03:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
03:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
03:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

---

### Post by StevenHarper on 2008-12-20
Yes I agree this thread has the same fix

[http://ubuntuforums.org/showthread.php?p=4205786#post4205786](http://ubuntuforums.org/showthread.php?p=4205786#post4205786)

run

```
asoundconf list
```

and take the name of the card you want and then

```
asoundconf set-default-card card
```

---

### Post by Open-SuSe-A-Me on 2008-12-20
i'm not sure if this will work, but try this....i'm sorry i am not as advanced as most of the people on the forums.

in a terminal do "asoundconf list" or it might be "asoundconf -list" and copy the result.

then in the terminal do "asoundconf set-default-card (whatever the result was)
so it would look like this: "asoundconf set-default-card creative034985" or whatever. then reboot.

if that doesnt work, go into the sound preferences, sometimes (like on my pc with a creative soundblaster) there will be multiple choices available for the sound device, like (hw,0 hw,1 hw,2) and just mess with it until it works.

also search the forums with the name of your soundcard, there may be a how-to written for it.

---

### Post by Open-SuSe-A-Me on 2008-12-20
woops didn't see that reply before mine

---

### Post by Fenix on 2008-12-20
I set it as default, but I am still without sound.

---

### Post by StevenHarper on 2008-12-20
Have you looked in the window when you RIGHT click on the sound icon n the tray and choose prefernces.

Try changing stuff in there.

---

### Post by Fenix on 2008-12-20
Change my device to something other than my Audigy?

---

### Post by StevenHarper on 2008-12-20
Possibly yes, it may just work.

On another approach : does you Motherboard also have a soundcard onboard - if so disabling it in the BIOS may help.

---

### Post by Fenix on 2008-12-20
Changing my preferences had no effect, and I do have onboard sound, but it's already disabled in my bios.

---

### Post by Fenix on 2008-12-20
I have fixed it! If anyone else is running on the Gnome Desktop and has an Audigy Gamer card, do this:

Right click on the sound icon in the top right on your tray
Open Volume Control
Go to Preferences
Scroll down to the bottom and check External Amplifier(Audigy Analog/digital Output Jack should already be checked by go ahead and check it if it isn't)
Close that window and then go to the switches tab
Now in that window uncheck both External Amplifier and Audigy Analog/digital Output Jack
Close that window

Now (hopefully) enjoy your sound!

---

### Post by joesenter on 2009-01-17
Thanks. That worked me as well!

---

