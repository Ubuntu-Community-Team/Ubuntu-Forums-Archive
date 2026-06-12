---
title: "Compaq Deskpro"
date: 2006-02-09
forum: Multimedia &amp; Video
---

### Post by souteneur3190 on 2006-02-09
I was finnaly able to purswade my little brother into using ubuntu, I have a problem though..no sound.  I really have no idea what to do...pleas help

Compaq Deskpro

[http://666kb.com/i/10ts8o1b253pc.jpg](http://666kb.com/i/10ts8o1b253pc.jpg)

---

### Post by az on 2006-02-09
They are great machines!

[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

From the page:
"sudo modprobe snd-es18xx

That worked so, I added "snd-es18xx" to /etc/modules so that it would be loaded at boot time.

sudo gedit"

---

### Post by souteneur3190 on 2006-02-10
Thanks but it didnt work for me I have a feeling the sound card is slintley diffrent.

This is part of the tutorial:

"I used the information to get my older sound card working. For example, I opened my box and looked at the sound chip. It had ESS Audio Drive written on it (1899-45-68). I consulted the list and tried loading the ESS Audiodrive module by hand:

sudo modprobe **[COLOR="Red"]snd-es18x[/COLOR]**x"

is there a way i can find my sound card in devices so i can see what exactly to type in the red area

---

### Post by az on 2006-02-10
1.  Try snd-es1688
2.  I don't think it appears in the bios setting, but you can check.  It would be in the onboard devices menu.  It may not give you the name, just the port and irq, which is useless for now.
3.  Look on the compaq (now part of HP) website to see what the exact specs of the system are.  This is a common desktop computer, so you should still be able to find it.
4.  Open the case, look at the chip and google for the serial number.

---

### Post by az on 2006-02-10
I went here:
[http://search.hp.com/query.html?cc=us&lang=en&qt=deskpro+en&la=en](http://search.hp.com/query.html?cc=us&lang=en&qt=deskpro+en&la=en)

And picked the 6500 at random:

[http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?&lang=en&cc=us&contentType=SupportManual&docIndexId=120756&prodTypeId=12454&prodSeriesId=96266&lang=en&cc=us](http://h20000.www2.hp.com/bizsupport/TechSupport/DocumentIndex.jsp?&lang=en&cc=us&contentType=SupportManual&docIndexId=120756&prodTypeId=12454&prodSeriesId=96266&lang=en&cc=us)

and then read this:

[http://h20000.www2.hp.com/bc/docs/support/UCR/SupportManual/TPM_113c0498/TPM_113c0498.pdf](http://h20000.www2.hp.com/bc/docs/support/UCR/SupportManual/TPM_113c0498/TPM_113c0498.pdf)

Which says on page 35
2.4.8 AUDIO SUBSYSTEM
All models feature the Compaq Premier Sound system. The system board includes an embedded
16-bit full-duplex subsystem based on the ES1869 graphics controller. The audio output is
processed through a six-level equalizer designed to work with the chassis acoustics. A lowdistortion
5-watt amplifier drives a long-excursion speaker for optimum sound. The audio
subsystem is compatible with software written for industry-common sound hardware.


So the module should be snd-es18xx.  After you load that module, can you try restarting X (CTRL-ALT-Backspace) to let gnome redetect everything.  You should see a speaker in the top right corner and it may be muted, too.

If this is the case, I will ammend the wiki page since that is more straighforward than running alsamixer to test sound...

---

