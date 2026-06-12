---
title: "Monitor refresh rate"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Rumpty on 2010-09-09
Meerkat beta. Running 1152 x 864 on my 17" CRT. Nvidia 256.53 driver. 

The only refresh rates available are Auto or 60Hz. In Lynx there are 60, 70, 75, 85 and Auto available, same computer, same monitor, Nvidia 256.35 driver.

---

### Post by x-shaney-x on 2010-09-09
Which is strange because on lucid, I only got Auto or 60Hz and it would only let me select from 2 resolutions.

Now I get several refresh rates and resolutions in maverick.

Maybe something to do with the nvidia driver?

---

### Post by Rumpty on 2010-09-09
Well, I went from the .35 driver in Lynx to the .53 driver in Meerkat. What are you running, x-shaney-x?

---

### Post by x-shaney-x on 2010-09-09
I'm not using nvidia here, it's intel which made me think your nvidia may be the issue.

---

### Post by realzippy on 2010-09-09
```
sudo nvidia-bug-report.sh

```
to get a clue.Post the produced bug-report here please (home folder)..

---

### Post by Rumpty on 2010-09-10
Here is the log file.

---

### Post by VinDSL on 2010-09-10
For what it's worth...

I'm running a Dell TFT panel, and the options are:

[LIST]
[*]Auto
[*]60Hz
[*]75Hz
[/LIST]

---

### Post by Rumpty on 2010-09-10
> **VinDSL said:**
> For what it's worth...

I'm running a Dell TFT panel, and the options are:

[LIST]
[*]Auto
[*]60Hz
[*]75Hz
[/LIST]

Ah, thanks. 

I looked the above log file, and noticed that the monitor horizontal and vertical rates in xorg.conf were restricting the options, so I changed the rates to the ones in the xorg.conf file in Lucid Lynx. Now I have refresh rates to 85Hz in Meerkat.

The rates in Lynx were derived from monitor EDID. Have to admit here that a couple of months ago I had modified the VGA cable on this monitor so that the computer could not access the monitor EDID, because W7 would not let me run the monitor at 1152 x 864, 75hz refresh. Strange that W7 restricted things more than Ubuntu? Both with Nvidia drivers.

So that is why Meerkat fell back to very restricted refresh, I guess.

---

### Post by MacUntu on 2010-09-10
If your monitor's EDID is valid, you shouldn't need to add the refresh rates to your xorg.conf, so it's possible that your monitor's EDID is bad. You can check that by installing the package read-edid.

```
sudo apt-get install read-edid
sudo get-edid
```

If you see something like this (like I do with my old CRT):
```
VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
EDID claims 153 more blocks left
```
then your EDID most likely is bad and you need to specify HorizSync and VertRefresh. You can find the right values in the monitor's manual.

---

### Post by realzippy on 2010-09-10
....the tool **get-edit** seems to produce wrong results;running it here
claiming:
**The EDID data should not be trusted as the VBE call failed**

VBE does not run when NVIDIA driver is installed.Can get the EDID with nvidia-settings or EDID-editor(Windows),and the file is correct for sure...:

00000000  00 FF FF FF FF FF FF 00 1E 6D 62 56 37 4B 09 00 .........mbV7K..
00000010  06 11 01 03 6A 2F 1E 78 EA D4 25 A4 55 49 9B 27 ....j/.x..%.UI.'
00000020  13 50 54 A7 6B 80 95 0F 95 00 81 80 81 40 71 4F .PT.k........@qO
00000030  01 01 01 01 01 01 7C 2E 90 A0 60 1A 1E 40 30 20 ......|...`..@0
00000040  36 00 DA 28 11 00 00 1A 21 39 90 30 62 1A 27 40 6..(....!9.0b.'@
00000050  68 B0 36 00 DA 28 11 00 00 1C 00 00 00 FD 00 38 h.6..(.........8
00000060  4B 1C 53 0F 00 0A 20 20 20 20 20 20 00 00 00 FC K.S...      ....
00000070  00 4C 32 32 35 57 00 0A 20 20 20 20 20 20 00 54 .L225W..      .T
00000080

---

