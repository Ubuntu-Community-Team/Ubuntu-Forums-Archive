---
title: "Speaker output on different port after recent update"
date: 2010-09-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MadNachos on 2010-09-29
After a recent update the speaker output on my soundcard has change ports from the one that has been in use for a few years. Any idea on how to control this? From time to time I'll boot this PC to Win or OSX and since they still use the default speaker output I have to swap the plug to a different port. A bit of a pita.

The sound card in question is a on-board Realteck ALC888 (Gigabyte EP45-DS3L board) with two speakers...no surround or anything fancy.

Any advice on how to troubleshoot this issue?

EDIT: I use the HDA_Analyzer from [www.alsa-project.org](www.alsa-project.org) and checked the settings. Looks like that jack had been set as a 'input' instead of an 'output'. I changed the setting and now it works as it should. Odd.

---

### Post by MadNachos on 2010-09-29
Here is the diff from the utility in case someone else finds it interesting:

```
Diff for codec 0/2 (0x10ec0888):
---  
+++  
@@ -158,17 +158,17 @@
   Connection: 2
      0x05 0x0b
 Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
 Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
 Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
 Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
 Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
   Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
-  Amp-In vals: [0x00 0x00]
+  Amp-In vals: [0x01 0x01]
   Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
   Amp-Out vals: [0x00 0x00]
   Pincap 0x0000003e: IN OUT HP Detect Trigger
   Pin Default 0x01014410: [Jack] Line Out at Ext Rear
     Conn = 1/8, Color = Green
     DefAssociation = 0x1, Sequence = 0x0
   Pin-ctls: 0x40: OUT
   Unsolicited: tag=0x00, enabled=0

```

---

