---
title: "still getting Xruns"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by falkenberg_cph on 2006-06-15
Hi
This is really starting to irritate me. Im still getting Xruns when trying to run midi.

This is my setup:

Computer: modded asus a2d
CPU: amd athlon XP-M 2800
RAM: 2Gb kingston
Harddisk: 100Gb 7200 rpm

Lexicon Omega USB 1.0 sound interface
M-audio keystation 49e USB 2.0 midi-keyboard

Jack:
tried from 32-512 frames/period
tried 44100-48000
Buffer: 2

Im running it under Fluxbox.

Any suggestions how i can overcome this problem. My computer should be plenty fast to get the latency low. Atleast it works really well in XP.

Please help
Carsten

Any suggestion

---

### Post by zettberlin on 2006-06-15
Are these xruns doing something severe or are they just coming out of nowhere whithout causing any hearable effect?

a friend had a strange behaviour with an usb-Mididevice that could be solved by using 3 buffers instead of 2 - maybe worth trying...

---

### Post by falkenberg_cph on 2006-06-15
the xruns causes sound-clips. fx. the ZynAddFX completely stops playing for seconds, then starts again.

I will try the 3 buffers first thing in the morning.

Strange enough i dont get xruns when using just audio.

Carsten

---

### Post by bwanab on 2006-06-15
[QUOTE=falkenberg_cph]the xruns causes sound-clips. fx. the ZynAddFX completely stops playing for seconds, then starts again.

I will try the 3 buffers first thing in the morning.

Strange enough i dont get xruns when using just audio.

Carsten[/QUOTE]

Try frames/period = 512 and periods/buffer = 4. That's the best I've been able to do since the 2.6.15_18 kernel. I reported this on the ubuntu bug tracker, but no response. I keep the 2.6.15_18 kernel for "serious" audio work, but every kernel since then has sucked wind. In reality, we need a kernel with Ingo Molnar's preemption patch built in. Until we've got that it's just a compromise.

---

### Post by dolson on 2006-06-15
bwanab, can you do a diff -up on the two config files and see what the difference is?

---

### Post by falkenberg_cph on 2006-06-16
[QUOTE=bwanab]Try frames/period = 512 and periods/buffer = 4. That's the best I've been able to do since the 2.6.15_18 kernel. I reported this on the ubuntu bug tracker, but no response. I keep the 2.6.15_18 kernel for "serious" audio work, but every kernel since then has sucked wind. In reality, we need a kernel with Ingo Molnar's preemption patch built in. Until we've got that it's just a compromise.[/QUOTE]

512 and 4 buffers. It gives a latency about 46 msec. That is not good enough. Then im just gonna have to wait with ubuntu and use xp untill it works.

Tough
Carsten

---

### Post by dolson on 2006-06-17
Did you use a kernel with realtime/complete-preemption?

---

### Post by falkenberg_cph on 2006-06-17
No. Though i have followed your description, i have not been able to create one. (I only saw yesterday i needed the rt-patch for dapper - i dont know why, but i had gotten this idea that it was in the dapper package)

Why isnt it in the dapper package - If music on linux should become i serious alternative, it needs to be as easy as possible, so that all us ignorant xp users can get it going right away. Oh, now that im bitching, i also wanna say that you are doing a great job, both with the forum and the wiki.

Anyway - my problem started here: patch -sp1 < ../patch-2.6.16-rt26

Which i changed to : patch -sp1 < ../patch-2.6.17-rc6-rt5
It said no such patch.

---

### Post by bwanab on 2006-06-18
[QUOTE=dolson]bwanab, can you do a diff -up on the two config files and see what the difference is?[/QUOTE]
Dana, I'd be happy to if you could give me a clue where to find them. Just cause I've been doing this linux stuff for a whole heap a years doesn't mean I know anything :)

---

### Post by bwanab on 2006-06-18
[QUOTE=falkenberg_cph]512 and 4 buffers. It gives a latency about 46 msec. That is not good enough. Then im just gonna have to wait with ubuntu and use xp untill it works.

Tough
Carsten[/QUOTE]

Well, I agree, depending on your application. I've done a bunch of recording using exactly that and the results have been very good. That said, I'm looking forward to having a kernel that I can get the <5 ms that I've been getting under the agnula kernel.

---

### Post by dolson on 2006-06-19
Config files are stored in /boot/.

---

### Post by falkenberg_cph on 2006-06-20
can you explain my error, as i wrote in an earlier post.

---

### Post by dolson on 2006-06-21
Yes. You aren't following the tutorial on the wiki 100%, which has worked for me with no issues on two separate PCs, as well as for other people... From the sounds of it, your file you are trying to use as a patch does not exist.

---

### Post by bwanab on 2006-06-21
Dana,

Here's the diff between 2.6.15_18 and 2.6.15_25. If I had to guess, I'd bet that the difference is the lines:

< CONFIG_HZ_1000=y
< CONFIG_HZ=1000
---
> CONFIG_HZ_250=y
> # CONFIG_HZ_1000 is not set
> CONFIG_HZ=250


:/boot$ diff config-2.6.15-18-686 config-2.6.15-25-686
3,4c3,4
< # Linux kernel version: 2.6.15-18-686
< # Thu Mar  9 15:23:09 2006
---
> # Linux kernel version: 2.6.15-25-686
> # Wed Jun 14 11:33:04 2006
139a140
> CONFIG_HPET_EMULATE_RTC=y
161c162
< CONFIG_EDD=m
---
> # CONFIG_EDD is not set
190,192c191,193
< # CONFIG_HZ_250 is not set
< CONFIG_HZ_1000=y
< CONFIG_HZ=1000
---
> CONFIG_HZ_250=y
> # CONFIG_HZ_1000 is not set
> CONFIG_HZ=250
836a838,841
> CONFIG_IEEE80211_1_1_13=m
> CONFIG_IEEE80211_1_1_13_CRYPT_WEP=m
> CONFIG_IEEE80211_1_1_13_CRYPT_CCMP=m
> CONFIG_IEEE80211_1_1_13_CRYPT_TKIP=m
1079a1085
> CONFIG_BLK_DEV_IDEACPI=y
1162a1169
> CONFIG_SCSI_SPI2_ATTRS=m
1167a1175,1180
> # SCSI Transport Layers
> #
> CONFIG_SAS_CLASS=m
> # CONFIG_SAS_DEBUG is not set
>
> #
1171d1183
< CONFIG_SCSI_ARCMSR=m
1179a1192,1193
> CONFIG_SCSI_AIC94XX=m
> # CONFIG_AIC94XX_DEBUG is not set
1197a1212
> CONFIG_SCSI_ARCMSR=m
1218a1234
> CONFIG_SCSI_SATA_ACPI=y
1527a1544
> CONFIG_R1000=m
1649a1667
> CONFIG_PRISM54_SOFTMAC=m
1654a1673,1675
> CONFIG_IPW3945=m
> # CONFIG_IPW3945_DEBUG is not set
> CONFIG_IPW3945_MONITOR=y
2010d2030
< CONFIG_INPUT_CPAD=m
2065c2085
< CONFIG_SERIAL_8250_NR_UARTS=4
---
> CONFIG_SERIAL_8250_NR_UARTS=48
2153,2155c2173
< CONFIG_RTC=m
< CONFIG_GEN_RTC=m
< CONFIG_GEN_RTC_X=y
---
> CONFIG_RTC=y
2829c2847
< # CONFIG_USB_SUSPEND is not set
---
> CONFIG_USB_SUSPEND=y
2836,2837c2854,2855
< # CONFIG_USB_EHCI_SPLIT_ISO is not set
< # CONFIG_USB_EHCI_ROOT_HUB_TT is not set
---
> CONFIG_USB_EHCI_SPLIT_ISO=y
> CONFIG_USB_EHCI_ROOT_HUB_TT=y
2875a2894
> CONFIG_USB_HIDINPUT_POWERBOOK=y
2897a2917,2918
> CONFIG_USB_SYNAPTICS=m
> CONFIG_USB_CPADDEV=y

---

### Post by dolson on 2006-06-23
You would be correct in your guess. I don't know why the default has changed, but that is a very good catch.

dana@polly:~$ grep CONFIG_HZ /boot/config-2.6.1*
/boot/config-2.6.15-23-386:# CONFIG_HZ_100 is not set
/boot/config-2.6.15-23-386:# CONFIG_HZ_250 is not set
/boot/config-2.6.15-23-386:CONFIG_HZ_1000=y
/boot/config-2.6.15-23-386:CONFIG_HZ=1000
/boot/config-2.6.15-25-386:# CONFIG_HZ_100 is not set
/boot/config-2.6.15-25-386:CONFIG_HZ_250=y
/boot/config-2.6.15-25-386:# CONFIG_HZ_1000 is not set
/boot/config-2.6.15-25-386:CONFIG_HZ=250
/boot/config-2.6.16-rt26:# CONFIG_HZ_100 is not set
/boot/config-2.6.16-rt26:# CONFIG_HZ_250 is not set
/boot/config-2.6.16-rt26:CONFIG_HZ_1000=y
/boot/config-2.6.16-rt26:CONFIG_HZ=1000

I don't know why the Ubuntu devs are messing around with this, but this is very annoying...

It is in the wiki for building the vanilla + -rt patch kernel:
*Set Processor type and features > Timer frequency to 1000 Hz.*

---

