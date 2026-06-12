---
title: "No sound output from NI Audio 8 DJ"
date: 2011-04-26
forum: Multimedia Software
---

### Post by grantoos on 2011-04-26
I have a Native Instruments Audio 8 DJ USB soundcard, but I cannot get sound to come out of it.  In Windows, the setup is fine, I can hear everything, but in Ubuntu, no luck.

When I look at the Sound menu, I see the card and when I select the proper Input from the Audio8, I see the sound meter working, so obviously it's recognizing the sound coming from the Audio8.  But when I go to the Output tab, I select the proper Output but can't hear anything.  I've tried A,B,C,D and nothing.

Any help would be appreciated.  Thanks.

---

### Post by lidex on 2011-04-27
Not familiar with that hardware but I do enjoy a challenge. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by grantoos on 2011-04-28
Hey thanks for the response.

Here's what it gave me:
[http://www.alsa-project.org/db/?f=19c1492fd7a6ce8eaf6176691f41570fe8d4f3e3](http://www.alsa-project.org/db/?f=19c1492fd7a6ce8eaf6176691f41570fe8d4f3e3)

---

### Post by lidex on 2011-04-28
Something about your alsa install is not quite right. Try updating your system and re-installing alsa.
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo update-grub
```
**Reboot**
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by grantoos on 2011-04-28
Ok I ran all those commands, rebooted, etc. but still nothing.  

Actually now when I go to open the Sound settings, I get a dialog box that says "waiting for sound system to respond" and it just hangs like that.

Here's my ALSA info now: [http://www.alsa-project.org/db/?f=5c2b87bb25667efa4a74c6685e46ed816c651cf9](http://www.alsa-project.org/db/?f=5c2b87bb25667efa4a74c6685e46ed816c651cf9)

Thanks.

---

### Post by lidex on 2011-04-28
Still not right. What do you get for these:
```
sudo updatedb
```
```
locate libasound
```

The first command won't return anything.

---

### Post by grantoos on 2011-04-28
This is what I get for locate libasound:

```

/etc/ld.so.conf.d/libasound2.conf
/usr/lib/libasound.so.2
/usr/lib/libasound.so.2.0.0
/usr/lib/alsa-lib/libasound_module_conf_pulse.so
/usr/lib/alsa-lib/libasound_module_ctl_arcam_av.so
/usr/lib/alsa-lib/libasound_module_ctl_bluetooth.so
/usr/lib/alsa-lib/libasound_module_ctl_oss.so
/usr/lib/alsa-lib/libasound_module_ctl_pulse.so
/usr/lib/alsa-lib/libasound_module_pcm_bluetooth.so
/usr/lib/alsa-lib/libasound_module_pcm_jack.so
/usr/lib/alsa-lib/libasound_module_pcm_oss.so
/usr/lib/alsa-lib/libasound_module_pcm_pulse.so
/usr/lib/alsa-lib/libasound_module_pcm_speex.so
/usr/lib/alsa-lib/libasound_module_pcm_upmix.so
/usr/lib/alsa-lib/libasound_module_pcm_usb_stream.so
/usr/lib/alsa-lib/libasound_module_pcm_vdownmix.so
/usr/lib/alsa-lib/libasound_module_rate_samplerate.so
/usr/lib/alsa-lib/libasound_module_rate_samplerate_best.so
/usr/lib/alsa-lib/libasound_module_rate_samplerate_linear.so
/usr/lib/alsa-lib/libasound_module_rate_samplerate_medium.so
/usr/lib/alsa-lib/libasound_module_rate_samplerate_order.so
/usr/lib/alsa-lib/libasound_module_rate_speexrate.so
/usr/lib/alsa-lib/libasound_module_rate_speexrate_best.so
/usr/lib/alsa-lib/libasound_module_rate_speexrate_medium.so
/usr/share/doc/libasound2
/usr/share/doc/libasound2-plugins
/usr/share/doc/libasound2/NEWS.Debian.gz
/usr/share/doc/libasound2/changelog.Debian.gz
/usr/share/doc/libasound2/changelog.gz
/usr/share/doc/libasound2/copyright
/usr/share/doc/libasound2/examples
/usr/share/doc/libasound2/examples/asoundrc.txt.gz
/usr/share/doc/libasound2-plugins/README-arcam-av
/usr/share/doc/libasound2-plugins/README-jack
/usr/share/doc/libasound2-plugins/README-maemo.gz
/usr/share/doc/libasound2-plugins/README-pcm-oss
/usr/share/doc/libasound2-plugins/README-pulse
/usr/share/doc/libasound2-plugins/a52.txt
/usr/share/doc/libasound2-plugins/changelog.Debian.gz
/usr/share/doc/libasound2-plugins/changelog.gz
/usr/share/doc/libasound2-plugins/copyright
/usr/share/doc/libasound2-plugins/examples
/usr/share/doc/libasound2-plugins/lavcrate.txt
/usr/share/doc/libasound2-plugins/samplerate.txt
/usr/share/doc/libasound2-plugins/speexdsp.txt
/usr/share/doc/libasound2-plugins/speexrate.txt
/usr/share/doc/libasound2-plugins/upmix.txt
/usr/share/doc/libasound2-plugins/vdownmix.txt
/usr/share/doc/libasound2-plugins/examples/a52.conf_pulse
/usr/share/doc/libasound2-plugins/examples/asound.conf_jack
/usr/share/doc/libasound2-plugins/examples/asound.conf_oss
/var/cache/apt/archives/libasound2_1.0.23-1ubuntu2.1_i386.deb
/var/lib/dpkg/info/libasound2-plugins.list
/var/lib/dpkg/info/libasound2-plugins.md5sums
/var/lib/dpkg/info/libasound2.conffiles
/var/lib/dpkg/info/libasound2.list
/var/lib/dpkg/info/libasound2.md5sums
/var/lib/dpkg/info/libasound2.postinst
/var/lib/dpkg/info/libasound2.postrm
/var/lib/dpkg/info/libasound2.shlibs
```

---

### Post by lidex on 2011-04-28
Do you have a /usr/lib32 directory?

---

### Post by grantoos on 2011-04-28
Yes.  2 folders in there:

- nvidia-current
- vdpau

---

### Post by lidex on 2011-04-28
You may need to re-install your kernel. I would suggest going into your package manager and completely removing (purging) your current kernel image and header packages followed by a reboot, then re-install.

---

### Post by grantoos on 2011-04-28
Hmmm, well the thing is, I tried it on my other install, same version of Mint but on my laptop, and it's the same issue.  So that's telling me that it's either something to do with Mint because apparently the Audio 8 is supported in Linux and is supposed to just be recognized no problem.

I'm going to try it with an Ubuntu live CD and report back.

Thanks.

---

### Post by lidex on 2011-04-28
Mint may be using alsa differently so I could be approaching this wrongly. Let's try this. Add these lines to alsa-base.conf - if you have it:
```
alias snd-card-0 snd_usb_caiaq
alias sound-slot-0 snd_usb_caiaq
alias snd-card-1 snd_ca0106
alias sound-slot-1 snd_ca0106
```
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Save. Close. Reboot.

---

### Post by grantoos on 2011-04-29
Ok, did that, nothing.

Maybe it's me, maybe I'm misunderstanding how this soundcard works? 

I have it going into my PC but I also have the RCA outs going into an external mixer, then from the mixer to my speakers.  But still, like I said, with this connection it works in Windows, I don't know why the sound doesn't come through in Linux.

---

### Post by lidex on 2011-04-29
What is your aplay -l now?

---

### Post by grantoos on 2012-01-19
After not using the card for a while I've decided to use it now since it's a great card but once again it's not working for me in Xubuntu.

Before it was with Mint but with Xubuntu it's the same thing. I've tried changing the sound settings and all that but there's still no output.

Anyone have ideas as to why it's not working? I don't understand why, it's a USB soundcard, I'm stumped.

---

