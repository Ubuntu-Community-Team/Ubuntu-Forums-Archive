---
title: "HDMI/TV output sound not working when connected to my computer."
date: 2014-04-06
forum: Multimedia Software
---

### Post by SwingKid on 2014-04-06
Hi everybody. First post here. I use Ubuntu 12.04 LTS (with Cairo desktop layout) on my 2 year old HP Pavilion. My sound works great in my computer but when I want to switch to use it on my TV in order to watch some movies the sound doesn't follow. It works great with the picture, I can use it like a new form of monitor sort of, but the sound doesn't follow. :confused:  I've checked with the Sound Settings and the HDMI output is not muted. It is not muted either in ALSA but I have a hard time to understand which is which though. So, after looking at other questions (here and other sites) and trying their respective answers, I am still unable to get the hdmi audio out working. [COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]

Please I need help!

---

### Post by SwingKid on 2014-04-06
More info: In Sound Settings it says "RV710/730 HDMI Audio [Radeon HD 4000 series] Digital Stereo  [HDMI]

---

### Post by tristone2 on 2014-04-07
What's your display driver? Open source or proprietary?

It's said open source version of ATI driver disables HDMI audio by default. Check the first comment in the below article.

[http://voices.canonical.com/david.henningsson/2012/04/14/audio-over-hdmi-and-displayport-in-ubuntu-12-04/](http://voices.canonical.com/david.henningsson/2012/04/14/audio-over-hdmi-and-displayport-in-ubuntu-12-04/)

---

### Post by SeijiSensei on 2014-04-07
Audio works fine over HDMI using the proprietary ATI driver for my Radeon 6770M graphics card.  You can install it by using the "Additional Drivers" application in Ubuntu.

I've found **pavucontrol** to be the most effective application for selecting the correct sound source.

---

### Post by SwingKid on 2014-04-07
"[COLOR=#000000]What's your display driver? Open source or proprietary?"
I don't know. :/ How would I be able to find out? Is it an ATI driver that I have and how do I know that?[/COLOR]

---

### Post by SeijiSensei on 2014-04-07
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and type in this command:
```
lspci | grep VGA
```
You'll see entries like these:
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT]

```
This is a "hybrid" laptop with both Intel and ATI graphics.

If you have an ATI adapter, then run the [Additional Drivers]("http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers") application in Ubuntu.  It will check to see if the proprietary driver is available for your adapter and offer to download and install the driver if you choose.

---

### Post by trag on 2014-04-13
[COLOR=#4B4B4B][FONT=Arial]HDMI audio output is disabled by default. To enable it you need to pass theradeon.audio=1 option to the kernel at boot.[/FONT][/COLOR]
[COLOR=#4B4B4B][FONT=Arial]To do so:[/FONT][/COLOR]

[LIST=1]
[*]Edit /etc/default/grub and add radeon.audio=1 to the GRUB_CMDLINE_LINUX line, it should look like:GRUB_CMDLINE_LINUX="... radeon.audio=1 rhgb quiet"

[*]Update grub's config: $ sudo grub2-mkconfig -o /boot/grub2/grub.cfg

[*]Reboot.
[/LIST]
[COLOR=#4B4B4B][FONT=Arial]I hope this helps.[/FONT][/COLOR]

---

