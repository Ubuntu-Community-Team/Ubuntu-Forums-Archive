---
title: "Realtek ALC268 Ext. Mic missing after upgrade to 10.04"
date: 2010-05-10
forum: Multimedia Software
---

### Post by sspence65 on 2010-05-10
After my upgrade, I lost the ability to select the ext. mic on my Acer Aspire 5515 with tha Realtek ALC268. The option does not exist, only the internal mic, which works fine, but very inconvenient.

---

### Post by ParsonT on 2010-05-18
Same problem, with the same sound chip, in a Starling Netbook.

---

### Post by lidex on 2010-05-20
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by ParsonT on 2010-05-20
In my case, it's a system76 Starling Netbook

Here's the output you asked for:

Linux system76-netbook 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).

Codec: Realtek ALC268


Sorry, I'm not sure about posting text output using code tags.
Here's what is in the browser navigation toolbar;

[http://ubuntuforums.org/showthread.php?t=1478933&highlight=alc268+external](http://ubuntuforums.org/showthread.php?t=1478933&highlight=alc268+external)

---

### Post by lidex on 2010-05-20
Sorry, the toolbar in the post editor.
What is this output:
```
lspci | grep HDA

```

Might as well get this one too:
```
sudo lshw -C multimedia
```

---

### Post by ParsonT on 2010-05-20
The lspci command returns nothing.

Here's the output from the lshw command:

  *-multimedia
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:27 memory:94340000-94343fff

---

### Post by lidex on 2010-05-20
Try this and see what happens:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo pulseaudio --kill
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by Yellow Pasque on 2010-05-20
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Copy/paste the following line to the end of the file and substitute one of the keywords from the list below. Save, quit, and reboot. (or sudo alsa reload). You might have to try a few options, but hopefully, one of the acer options will work.
```
options snd-hda-intel model=*KEYWORD*
```

```
ALC267/268
==========
  quanta-il1	Quanta IL1 mini-notebook
  3stack	3-stack model
  toshiba	Toshiba A205
  acer		Acer laptops
  acer-dmic	Acer laptops with digital-mic
  acer-aspire	Acer Aspire One
  dell		Dell OEM laptops (Vostro 1200)
  zepto		Zepto laptops
  test		for testing/debugging purpose, almost all controls can
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)
```

---

### Post by ParsonT on 2010-05-20
sudo pulseaudio --kill   produces this:

E: core-util.c: Home directory /home/myusername/ not ours.
E: main.c: Failed to kill daemon: Permission denied


Do I need to change some permissions?

---

### Post by ParsonT on 2010-05-20
Changing the keyword in 
options snd-hda-intel model=*KEYWORD from acer-aspire to acer *seems to have done the trick.Many thanks to both of you for your help.

---

