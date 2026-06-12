---
title: "[SOLVED] Help with sound card! Too low, too lame!"
date: 2008-11-28
forum: Multimedia Software
---

### Post by arashiko28 on 2008-11-28
I recently bought a Lenovo Ideapad Y530 and it came with windows vista home premium. I made a dual boot and oh what a despair! It's not Linux's fault that the hardware is newer than the last Ubuntu's version, and that brought me a ton of error that I solved upgrading from 8.04 to 8.10. But there's still the sound issue. According to what I see in windows it has two sound devices, one for speakers and one for headphones.:confused:

But as the lspci that follows, Ubuntu only sees one.:confused:
The matter is that sound is pitiful, too low and doesn't matter how much I play with the equalizers, can't get a good sound. Everything is at 100% at the controllers, so that's not the problem.

> lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
06:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
06:03.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


According to windows there is a Realtek sound device for the microphone and headphone jacks and the one that Ubuntu sees.
Now, this one tat Ubuntu does recognize it's supposed to be a home theater with dolby 5.1 and I can't get the juice out of it.

Please help!!!

---

### Post by arashiko28 on 2008-11-28
Bump!

---

### Post by EasyRiderOnTheStorm on 2008-11-28
Dont't worry, that's actually just one soundcard. It just has two major elements: the Intel High Definition Audio controller sitting on your PCI bus, and a Realtek "codec" connected to the Intel chip: all your front and back connectors go to the Realtek codec.

As far as I can tell it should be a Realtek ALC888 codec, which still sees a lot of activity at Alsa (read: bugs are still found/fixed). Just to make sure, see what do you get when you type

> aplay -l

If it says "ALC888", that's it. There seems to be a bug about it, that sound just like yours, see [[here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217789")]. If that's it, you might just have to wait until it gets fixed.

Alternatively, (if ALC888 is right) you might attempt to use a different configuration model, by telling your Alsa driver to handle your codec with a some other config then it uses now. The way to do that should be to add a line like 

> options snd-hda-intel model=MODEL_NAME

to your /etc/modprobe.d/alsa-base file, where MODEL_NAME might be one of these:

> enum {
        ALC883_3ST_2ch_DIG,
        ALC883_3ST_6ch_DIG,
        ALC883_3ST_6ch,
        ALC883_6ST_DIG,
        ALC883_TARGA_DIG,
        ALC883_TARGA_2ch_DIG,
        ALC883_ACER,
        ALC883_ACER_ASPIRE,
        ALC888_ACER_ASPIRE_4930G,
        ALC883_MEDION,
        ALC883_MEDION_MD2,
        ALC883_LAPTOP_EAPD,
        ALC883_LENOVO_101E_2ch,
        ALC883_LENOVO_NB0763,
        ALC888_LENOVO_MS7195_DIG,
        ALC888_LENOVO_SKY,
        ALC883_HAIER_W66,
        ALC888_3ST_HP,
        ALC888_6ST_DELL,
        ALC883_MITAC,
        ALC883_CLEVO_M720,
        ALC883_FUJITSU_PI2515,
        ALC888_FUJITSU_XA3530,
        ALC883_3ST_6ch_INTEL,
        ALC888_ASUS_M90V,
        ALC888_ASUS_EEE1601,
        ALC1200_ASUS_P5Q,
        ALC883_AUTO,
        ALC883_MODEL_LAST,
};

then reboot and try wiggling the mixer again. Or you can try without editing the alsa-base file and without rebooting, just by removing and reinserting the snd_hda_intel module on-the-fly:

> 
sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel model=MODEL_NAME


...same as above. Good luck...

---

### Post by arashiko28 on 2008-11-29
:cry: what if my laptop model is not in the list you just gave me?
This is what I got from terminal:

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

But my laptop is a Lenovo Ideapad Y530 -40512WU
I will try it though...

---

### Post by EasyRiderOnTheStorm on 2008-11-29
OK, it seems we were right about the ALC888. 

> what if my laptop model is not in the list you just gave me?

Don't worry about that; very few computers are supported by their exact model name, and those are the quirky ones. Most other computers are supported by one of the "generic" modes for that codec, modes that fit many models. Such as the "ALC883_3ST_6ch", for instance, which is just to say "Computer with ALC883 codec, a 3-stack of jacks, in 6-channel mode". As I understand, the list includes various ALC883 and ALC888 codes together because the two codecs can be handled similarly...

---

### Post by EasyRiderOnTheStorm on 2008-11-29
Oh, I'm terribly sorry, I gave you the wrong label list. It's the right list, just the wrong labels. These are the right ones (please use the labels between the quotes, without the quotes):

```

        [ALC883_3ST_2ch_DIG]    = "3stack-dig",
        [ALC883_3ST_6ch_DIG]    = "3stack-6ch-dig",
        [ALC883_3ST_6ch]        = "3stack-6ch",
        [ALC883_6ST_DIG]        = "6stack-dig",
        [ALC883_TARGA_DIG]      = "targa-dig",
        [ALC883_TARGA_2ch_DIG]  = "targa-2ch-dig",
        [ALC883_ACER]           = "acer",
        [ALC883_ACER_ASPIRE]    = "acer-aspire",
        [ALC888_ACER_ASPIRE_4930G]      = "acer-aspire-4930g",
        [ALC883_MEDION]         = "medion",
        [ALC883_MEDION_MD2]     = "medion-md2",
        [ALC883_LAPTOP_EAPD]    = "laptop-eapd",
        [ALC883_LENOVO_101E_2ch] = "lenovo-101e",
        [ALC883_LENOVO_NB0763]  = "lenovo-nb0763",
        [ALC888_LENOVO_MS7195_DIG] = "lenovo-ms7195-dig",
        [ALC888_LENOVO_SKY] = "lenovo-sky",
        [ALC883_HAIER_W66]      = "haier-w66",
        [ALC888_3ST_HP]         = "3stack-hp",
        [ALC888_6ST_DELL]       = "6stack-dell",
        [ALC883_MITAC]          = "mitac",
        [ALC883_CLEVO_M720]     = "clevo-m720",
        [ALC883_FUJITSU_PI2515] = "fujitsu-pi2515",
        [ALC888_FUJITSU_XA3530] = "fujitsu-xa3530",
        [ALC883_3ST_6ch_INTEL]  = "3stack-6ch-intel",
        [ALC1200_ASUS_P5Q]      = "asus-p5q",
        [ALC883_AUTO]           = "auto",

```

Sorry again for the confusion. Gotta get more sleep. Or coffee...

---

### Post by arashiko28 on 2008-12-01
In the list there's only two ACL888, so I tried the first one with no success. I added this line to the alsa-base file:
> options snd-hda-lenovo-ms7195-dig=-2

I'll try the next one now.

.............

Second option: No good... :(

For the on-the-fly option, I get:> ERROR: Module snd_hda_intel is in use


---

### Post by EasyRiderOnTheStorm on 2008-12-02
> In the list there's only two ACL888, so I tried the first one with no success. I added this line to the alsa-base file:

[QUOTE]options snd-hda-lenovo-ms7195-dig=-2
I'll try the next one now.[/QUOTE]

Careful there, that's not quite right. What you need to have there is something like:

```
options snd-hda-intel model=lenovo-ms7195-dig
```

> For the on-the-fly option, I get:

[QUOTE]ERROR: Module snd_hda_intel is in use [/QUOTE]

Yes, I've seen that too; it's likely because your **desktop** is running and using the module (even if no sound is actually playing at the time). If you log in on a console only (no desktop) that would probably not happen; alternatively, what I do is **log out** from the desktop, and unload-reload the module in the 30 seconds it takes the system to auto-re-login (I'm on mythtv, and it does that). Works like a charm.

Oh, and it's not just the two models actually called '888' that you can try. In that list, any of the models might work with your soundcard, exactly because the 883 and the 888 codecs are handled in the same way by Alsa. That's why they are in the same list to begin with.

---

### Post by 1902 on 2008-12-22
Hi, i had the same issue with ALC888 and i used (auto) to fix it.

options snd-hda-intel model=auto

the weird thing is that i never had to use it before the last time i did a format for my laptop, that was the first time having sound problem, usually a little configuration for skype and that's it.
i did update the system after format before checking the sound.
there must be something with the update is conflicting with the sound.

good luck

:)

---

### Post by arashiko28 on 2009-01-04
Problem solved!!! I will make it short and easy taking in account that some users are not experienced in Linux.
For Ideapad Y530: open terminal and write
> sudo gedit /etc/modprobe.d/alsa-base

On the file, go to the end and add this line:
> options snd-hda-intel model=lenovo-ms7195-dig

If that option does not work for you, try the list given before in this same thread.

restart you computer and open the sound/volume manager. On the preferences list: Add the front mic, front mic boost, surround, center, LFE. Also add capture, headphone, IEC958, IEC958 default PCM and channel mode.

On switches, activate all.
On options, choose 6ch.

And you're ready to go.

If you want to record with the integrated mics, just raise up the bars of the mics, but be carefull, migth have a feedback, so lower or mute the other speakers volume before. Go to recording and raise both bars. Test it with sound recorder. It worked for me and the sound is loud and clear.

Good luck!

---

### Post by RetiredPCTech on 2009-04-25
i am new to linux and just installed mint on my new y530 and I just want to say thank you. I too found that after installing the sound was too low like in ubuntu. Your suggestions in this thread worked for me as well and now I have much better and louder sound. It still seems a little quiet, but maybe it's just me-it's been awhile since I have had a laptop. There still are some minor issues I have to work out (speakers not cutting out when headphones get plugged in, some of the function keys and the touch inductive keys don't work, the laptop dims on startup, the dim keys are reversed, and the standby/hibernate isn't working). I know some of these other issues have been posted here and at other sites, so I have some more reading to do, but again thank you for getting my sound better!  :D

---

### Post by arashiko28 on 2009-04-25
These problems were solved on Jaunty. But, for mint, go to preferences of battery and change your backlight to 0%.
For the sound, go to volume control, on preferences, choose, surround, central,front and LFE, when you plug in your head phones you'll have to manually mute surround, central and LFE, then you'll have just the headphones. It's temporal, but...

THe media buttons works, but only with movie player, mute button works, the assign doesn't, nor the dolby, the effects buttons, doesn't work either, but I'm looking for someone who can write scripts to change that soon enough :P

---

### Post by oedstero on 2009-04-25
In Jaunty, on my new Lenovo Y530, I found the model "options snd-hda-intel model=lenovo-sky" in alsa-base.conf to blow the others away as far as volume goes -- it actaully drives LFE and rear onboard speakers acceptably, all channels show up in alsamixer.

The kernel 2.6.28-12.43 from [http://kernel.ubuntu.com/~dtchen/test-kernels/]("http://kernel.ubuntu.com/%7Edtchen/test-kernels/") also eliminated the mp3 skipping I was experiencing.  

And yes, "tsched=0" is set on the "load-module module-hal-detect" line of .pulse/default.pa -- without it the audio was unbearable.

Hope this saves someone some time!

---

