---
title: "Toshiba satellite sound problem"
date: 2010-08-18
forum: Multimedia Software
---

### Post by FattyOwl on 2010-08-18
Sorry for the crosspost! This forum seems to fit my problem better than the hardware forum. My thread there can be deleted.

I've just installed ubuntu for the first time, and everything seems to be working great except for my sound. The sound card gets recognized and nothing is muted; but I still can't hear anything.

After searching this forum and others for a while I still haven't found a solution. The terminal told me to post the following link:

[http://www.alsa-project.org/db/?f=cc67a04a5bcb08f5395c1cd2019ca79b251ab860](http://www.alsa-project.org/db/?f=cc67a04a5bcb08f5395c1cd2019ca79b251ab860)

Currently I'm stuck, I've tried multiple options and even reinstalled ubuntu with no luck. I can't find my sound card in BIOS, but I did have sound in Windows Vista.

I'm a complete linux-noob, so any help would be appreciated!

Thanks

---

### Post by K-cid on 2010-08-18
Hi FattyOwl,

I just solved my soundproblem! These guides helped me a lot.

Basic "my sound does not work guide"
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

The underlying system is pulseaudio, if the above guide did not work, the solution might lie here.
[http://www.pulseaudio.org/wiki/Troubleshooting](http://www.pulseaudio.org/wiki/Troubleshooting)

Pulseaudio, you guesses it, depends on alsa. If pulseaudio does work as it supposed to...
[http://alsa.opensrc.org/TroubleShooting](http://alsa.opensrc.org/TroubleShooting)

Good luck finding a solution!

BTW, your link to alsadb does not work

---

### Post by FattyOwl on 2010-08-18
Thanks for the reply, fixed the link. I tried the pages you proposed but without success. Everything seems to be running fine, but I'm not hearing anything.

---

### Post by lidex on 2010-08-19
You have a newer sound codec that is best supported by the latest version of alsa.
Make sure you have build-essential installed. Using a Terminal="Applications->Accessories->Terminal":
```
sudo aptitude install build-essential
```
Now go on over to the alsa-upgrade link in my sig to update your alsa install.

---

### Post by FattyOwl on 2010-08-19
Thank you for your response. I installed the build-essential package and upgraded to the latest version of alsa using your script. This all went smoothly without any problems, and my sound card still gets recognized. I still can't hear any sound though, and nothing in alsamixer or the regular sound settings is muted. I've put them all on maximum db.

I think the problem might be in my alsa-base.conf file. I added that last line, but I am not sure that I did it correctly and chose the correct model.

My laptop is a Toshiba with 3 jacks in the front. One for headphones, one for a microphone and I have no idea what the third one does.

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel index=-2 model=toshiba
```

---

### Post by FattyOwl on 2010-08-19
I have tried 3stack and F1734 as models, with no success.

---

### Post by lidex on 2010-08-19
> options snd-hda-intel index=-2 model=toshiba
Yeah, that is a problem. The correct syntax is:
```
options snd-hda-intel model=toshiba
```
I've seen others making this same mistake, out of curiousity have you seen somewhere a recommendation to enter the model this way? I would suggest removing that line completely, then reboot. Next run this command:
```
ubuntu-bug audio
```

---

### Post by FattyOwl on 2010-08-19
Removed the line, rebooted and ran the debug. I get to the test tones, but they don´t come trough my speakers. After that I got the opportunity to send a report which I cancelled. Haven't heard anything trough my speakers yet.

---

### Post by lidex on 2010-08-19
>  Re: No audio Toshiba Satellite P100, ubuntu 10.04
I am embarrassed to say how the problem was resolved. This is my son's laptop and I was not familiar with it, but I just discovered that there is a recessed rotary volume control in front that was turned to off. The audio was working all the time, I just had the switch off. Sorry for any distraction this may have caused anyone trying to chase this down 
[http://ubuntuforums.org/showthread.php?t=1477998](http://ubuntuforums.org/showthread.php?t=1477998)

---

### Post by FattyOwl on 2010-08-19
My volume control wheel in the front of my laptop is on.

This is the information that I get about my audio device, if it is of any use:


00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff31
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by FattyOwl on 2010-08-19
I have found the following link as a possible solution:
[http://www.linuxquestions.org/questions/suse-novell-60/howto-fix-acpi-ich7-family-conexant-driver-on-toshiba-p100-105-series-531575/](http://www.linuxquestions.org/questions/suse-novell-60/howto-fix-acpi-ich7-family-conexant-driver-on-toshiba-p100-105-series-531575/)

However, it is with an older version of alsa and I'm not sure if those scripts would mess up my system.
And I have no idea how to upgrade my BIOS.

Should I follow the steps in that link?

---

### Post by lidex on 2010-08-19
OK. I think you should go ahead and submit the bug report.

---

### Post by FattyOwl on 2010-08-20
Do I get responses to my bug report on how to fix it after reporting it?

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621060](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621060)

---

### Post by FattyOwl on 2010-08-20
Might have done something stupid. I opened the grub window during boot, then opened the command prompt and entered ACPI=OFF. Right now, only my external USB keyboard and mouse work, everything else (like touchpad, keyboard) is disabled.

---

### Post by FattyOwl on 2010-08-20
Would a USB headset give me sound? Currently my sound card doesn't even get recognized anymore because of a guide that I followed. So when I connect a usb headset, will I need a soundcard?

---

### Post by lidex on 2010-08-20
> **FattyOwl said:**
> Do I get responses to my bug report on how to fix it after reporting it?

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621060](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621060)
These guys may be a little busy as we're trying to get bug reports submitted on most, if not all, audio issues so they can be fixed upstream rather than just applying work-arounds. Be patient. You are subscribed to that bug report and will receive feedback from the developers. If they can't fix it, no one can.

---

