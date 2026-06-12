---
title: "Problem with Pulseaudio and microphone"
date: 2010-05-15
forum: Multimedia Software
---

### Post by yadayada2 on 2010-05-15
Dear all

I guess, I am too stupid for pulseaudio. Since my upgrade to 10.04, I can't get the microphone to work. Neither with the sound recorder or with skype.

The computer I use is an Acer, which has several plug sockets on the rear and in the front. For convenience matters, I want to use those in the front. There is one socket for headphones and one for the microphone (which worked until the update).

Maybe this problem is related to the one from this thread [http://ubuntuforums.org/showthread.php?t=1473689&highlight=pulseaudio+mic]("http://ubuntuforums.org/showthread.php?t=1473689&highlight=pulseaudio+mic"), but the suggested solution does not work for me.

Please help me, if you can.

In case, it helps, here is the output of lspci:

```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```

By the way, skype only allows me to select pulseaudio local server. Just in case, that matters.

Furthermore, I will attach some screenshots of my pulseaudio settings.

Best regards and thanks in advance for any help!

---

### Post by VeeDubb on 2010-05-15
Easy.

I'd be willing to bet your microphone is a mono input microphone, not a stereo mic.  Let's face it, what computer has a stereo mic?

Yet, pulse thinks it's stereo.

Just uncheck the little lock icon to the right of the volume sliders for your mic, so you can adjust the left and right independently, and then turn the right channel all the way down to zero.


Oh, and as far as skype just seeing pulse and nothing else, that's normal, and it's really a good thing.  The idea is that you get pulse set up and configured, and treating each program the way you want it treated, and all your software can just be pointed at pulse.

---

### Post by yadayada2 on 2010-05-15
Thanks for your fast reply. Unfortunately, I have to say this didn't work either.

I attach two more screenshots. One of them shows the two rulers at different settings, the other one the recording tab, which states something of an ALSA plugin.

Is that helpful?

---

### Post by ajgreeny on 2010-05-15
I assume from the link you gave that you've tried alsamixer in terminal and set everything up as far as the levels and unmuting devices is concerned, but as you say there are sockets front and back for the microphone, have you tried changing mic1 for mic2 as well, either in the pulseaudio settings or in alsamixer?

---

### Post by yadayada2 on 2010-05-15
Yes, I have tried both settings. In pulseaudio I can switch from mic 1 to mic 2, while alsa lets me choose between mic and front mic.

---

### Post by yadayada2 on 2010-05-15
Maybe these further screenshots might help, too

Edit: In the meantime, I have also set Capture 1 two different levels for the left channel and the right one. Both input sources are now turned to front mic, but it doesn't change anything.

---

### Post by yadayada2 on 2010-05-15
Do you have any further ideas?

---

### Post by yadayada2 on 2010-05-15
Is it too early to "bump"? ;)

---

### Post by svenskmand on 2010-05-15
I have the same problem (except that I do not think I use pulseaudio, but only alsa. That is the default in Ubuntu 10.04 right?), and I also tried to turn everything up in alsamixer but with no luck :S here is the output of lspci:
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
08:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
09:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```
I would also very much like help :)

---

### Post by VeeDubb on 2010-05-15
> **svenskmand said:**
> I have the same problem (except that I do not think I use pulseaudio, but only alsa. That is the default in Ubuntu 10.04 right?)

Nope.  PulseAudio is the default in 10.04, and was the default in 9.10.  Not sure about 9.04, but either way, it's been the default for a while.  If you're having the same problem and you're sure you're using just also, you probably want to start a different thread.

---

### Post by svenskmand on 2010-05-15
> **VeeDubb said:**
> Nope.  PulseAudio is the default in 10.04, and was the default in 9.10.  Not sure about 9.04, but either way, it's been the default for a while.  If you're having the same problem and you're sure you're using just also, you probably want to start a different thread.
I just made a fresh install of Ubuntu 10.04 the other day, so as you say I must then also have PulseAudio. I was in doubt because I remember that I had to installed PulseAudio in Ubuntu 8.xx to avoid some annoying glitches in my audio when listening to music.

But I just got the mic working, unfortunately I do not know how, I was messing around with the "Sound Preferences" thing on the status line, and suddenly all my audio dissapeared :S, I restarted and it was still gone. Then I messed some more around with the "Sound Preferences" and suddenly I had audio again, and the mic was also working :)

To get the audio to disappear I selected another item (than the first one) from the list under the tab "Output" in the "Sound Preferences"

But it is working now :) :guitar:

---

### Post by yadayada2 on 2010-05-16
Congrats! At least one, who can use his mic ;)

Unfortunately, I still cannot use my microphone and any further help will be appreciated.

---

### Post by yadayada2 on 2010-05-16
bump

---

### Post by svenskmand on 2010-05-16
On a sidenote: how did you put your version of Ubuntu in you avatar? I cannot seem to find it :S

Also I found that if you turn the volume too much up on the recording page in the alsamixer then the mic does not record anything other than noise, even though you are speaking into it. So start by turning it half way up, do not know if it helps :S

---

### Post by yadayada2 on 2010-05-16
You can select your distro in your User CP -> Edit Your Details. Then you have to scroll down the whole page and there is a dropdown menu.

---

### Post by yadayada2 on 2010-05-16
@svenskmand: Unfortunately, changing the setting in alsamixer doesn't seem to do the trick.

---

### Post by yadayada2 on 2010-05-16
bump

---

### Post by yadayada2 on 2010-05-16
I just noticed something else. In alsamixer I have "Capture" and "Capture 1", as well as "Input Source" and "Input Source 1"

When I select front mic for "Capture", it does not seem to change anything. And when I reopen alsamixer it will be set back to mic, not front mic. 

I don't know if this has something to do with my recording problem. Furthermore, the Sound Recorder only offers the option to take "Capture", but I cannot select "Capture 1" or anything else. Capture is the only option I have. 

Might this be of any help?

---

### Post by lidex on 2010-05-16
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel probe_mask=1  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by yadayada2 on 2010-05-16
Thank you very much. Right now I am trying to get rid off pulseaudio and to see if this solves the problem. If not, I will reinstall pulseaudio and then follow your advice. 

Until later ...

---

### Post by yadayada2 on 2010-05-18
Getting rid of pulseaudio didn't change anything. So, I am back to pulseaudio.

Now a friend of mine, who has much more experience with Linux than I have, did take a look at the problem. As he tells me, the problem has nothing to do with pulseaudio. In his view it is a problem with the sound card driver. I have tried various related acer models for the **snd-hda-intel module**, but none of them worked.

As it seems, right now there is **no working driver model for the ALC1200 chip set on an Acer Aspire L5100**, which enables capturing audio over one of the microphone sockets :(

If anyone can come up with another solution, it would be great.

---

### Post by lidex on 2010-05-18
I would suggest you upgrade alsa to 1.0.23 via the alsa-upgrade link in my sig and then use the driver option from post #19.

---

### Post by yadayada2 on 2010-05-19
Thanks, I did that, but sadly it didn't work. Nonetheless, thanks for all your help.

---

