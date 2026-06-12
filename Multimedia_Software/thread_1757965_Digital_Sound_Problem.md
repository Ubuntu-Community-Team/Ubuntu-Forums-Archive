---
title: "Digital Sound Problem"
date: 2011-05-14
forum: Multimedia Software
---

### Post by gramsyn on 2011-05-14
Hello everybody,

I use the on-board sound chip of a Gigabyte motherboard (Realtek)and I have connected it with optical cable to an amplifier, as I want to transmit digital sound (DTS, DD). At the sound settings, I have chosen the Internal Audio Digital Stereo Duplex Output IEC958.

Everything worked fine, until February, when an update changed the kernel and the PC stopped giving sound signal! When I returned to the previous kernel (at grub), again everything worked. So,it doesn't seem to be a connection or drivers problem.

I supposed that with 11.04 edition this problem would be solved. But it isn't. In fact I have serious problem now because the old kernel isn't listed in grub anymore.

I run the alsa-info-script. The output is found at the following link:

[http://www.alsa-project.org/db/?f=3545a51b63debd8f83a9182db4aaae31d761ed3c](http://www.alsa-project.org/db/?f=3545a51b63debd8f83a9182db4aaae31d761ed3c)

I would very much appreciate any help. Thanks in advance

---

### Post by fjf on 2011-05-14
I have a similar problem with my mobo and Natty.  Fortunately my sound card can use the usb out of my computer.  Anyway, if you know the problem is the kernel you can try to downgrade to any previous kernel downloading it from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

---

### Post by gramsyn on 2011-05-14
Thanks for the reply.

What do you mean by "Fortunately my sound card can use the usb out of my computer"?

What is everyone doing in order to have digital sound? Am I the only one at Ubuntu user who uses the digital output of the sound card???

I tried to install a previous kernel version, but it doesn't show up at Grub list

---

### Post by lidex on 2011-05-14
It sounds like you configured something on that working kernel and it needs to be reapplied to the new one. One thing that jumps out: 
```
hda_codec: ALC889: BIOS auto-probing.
```
Which generally means you need to set a model switch in alsa-base.conf

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot. 

Your model options:
```
ALC882/883/885/888/889
======================
  3stack-dig    3-jack with SPDIF I/O
  6stack-dig    6-jack digital with SPDIF I/O
  arima         Arima W820Di1
  targa         Targa T8, MSI-1049 T8
  asus-a7j      ASUS A7J
  asus-a7m      ASUS A7M
  macpro        MacPro support
  mb5           Macbook 5,1
  macmini3      Macmini 3,1
  mba21         Macbook Air 2,1
  mbp3          Macbook Pro rev3
  imac24        iMac 24'' with jack detection
  imac91        iMac 9,1
  w2jc          ASUS W2JC
  3stack-2ch-dig        3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig     6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire   Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion        Medion Laptops
  targa-dig     Targa/MSI
  targa-2ch-dig Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e   Lenovo 101E
  lenovo-nb0763 Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky    Lenovo Sky
  haier-w66     Haier W66
  3stack-hp     HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell   Dell machines with 6stack (Inspiron 530)
  mitac         Mitac 8252D
  clevo-m540r   Clevo M540R (6ch + digital)
  clevo-m720    Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a Intel IbexPeak with ALC889A
  intel-x58     Intel DX58 with ALC889
  asus-p5q      ASUS P5Q-EM boards
  mb31          MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto          auto-config reading BIOS (default)

```

---

### Post by fjf on 2011-05-15
I meant my soundcard (external) uses digital inputs either optical, coaxial or usb, and linux kernel recognize usb souncards much better than other digital connections.  The estrange thing is that some ubuntus recognize my digital out and other do not.  Natty does not.

> **gramsyn said:**
> Thanks for the reply.

What do you mean by "Fortunately my sound card can use the usb out of my computer"?

What is everyone doing in order to have digital sound? Am I the only one at Ubuntu user who uses the digital output of the sound card???

I tried to install a previous kernel version, but it doesn't show up at Grub list

---

### Post by fjf on 2011-05-15
> **gramsyn said:**
> I tried to install a previous kernel version, but it doesn't show up at Grub list

You need to repair grub.  You can try this one:  
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by gramsyn on 2011-05-15
@lidex:

at the bottom alsa-base.conf, I  have to paste just this line:

[HTML] options snd-hda-intel model=[/HTML]

or after = I should put something from the table you give (your model options)? I don't understand why you give me this table.

I have pasted the line just as written,reboor, but nothing happens

---

### Post by lidex on 2011-05-15
> **gramsyn said:**
> @lidex:

at the bottom alsa-base.conf, I  have to paste just this line:

[HTML] options snd-hda-intel model=[/HTML]

or after = I should put something from the table you give (your model options)? I don't understand why you give me this table.

I have pasted the line just as written,reboor, but nothing happens

Yes you need to put a model name from left column of that table directly after the = (no space). For example:
```
options snd-hda-intel model=3stack-dig
```
For each change you'll need to restart alsa or reboot.
```
sudo alsa force-reload
```

---

### Post by gramsyn on 2011-05-15
I have to provide my compliments and my thanks. It worked!!!

---

### Post by lidex on 2011-05-15
You're welcome. Enjoy.

---

