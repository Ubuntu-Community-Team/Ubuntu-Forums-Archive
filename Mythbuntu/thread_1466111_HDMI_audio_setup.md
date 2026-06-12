---
title: "HDMI audio setup"
date: 2010-04-30
forum: Mythbuntu
---

### Post by trevs.bronco on 2010-04-30
Hi all,

I did a fresh install of 10.04 and at the same time installed a new video card, geforce 210. I do not have audio at all, I have played with ALSA settings and the audio settings in mythtv and cannot get get anything working inside mythtv or out. is there a howto somewhere that can guide me? everthing I can fnd is a few versions out of date an of no help.

Thanks,

Trev

---

### Post by LowSky on 2010-04-30
take a look here. I had the same issue and this solved it

[http://www.mythtv.org/wiki/ATI_Radeon_HDMI#MythVideo_HDMI_Sound](http://www.mythtv.org/wiki/ATI_Radeon_HDMI#MythVideo_HDMI_Sound)

---

### Post by novellahub on 2010-04-30
Also see here:

[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

### Post by dmfrey on 2010-04-30
check the alsa website, there are some options you need to add to the module.  Also, these cards might have to wait for alsa 1.0.23, which isn't in the repo yet.  You can remove, download, and compile and then it should work.

---

### Post by novellahub on 2010-04-30
I will be instaling a GT 240 Card tonight along with Mythtbuntu 10.04. I will be upgrading alsa with these directions:

[http://monespaceperso.org/blog-en/2010/04/17/upgrade-alsa-1-0-23-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2010/04/17/upgrade-alsa-1-0-23-on-ubuntu-karmic-koala-9-10/)

---

### Post by trevs.bronco on 2010-05-01
Thanks for all the suggestions, bu unfortunately none have really paned out. When I was looking at the results from my ```
aplay -l
``` I noticed that I did not have an HDMI entry like I did on my other frontend, reading one of the links I realized I had not disabled the onboard sound in the BIOS after I did this I'm left with ```
shaw@Myth-Hybrid:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
``` So, does my card not support audio through hdmi? I thought it was part of the protocol. I can't find any documentation that states anything about sound capabilities of the card.

Trev

---

### Post by nickrout on 2010-05-01
with nvidia 2xx ersies cards you need to either have a recent version of alsa, or patch the version you do have. I am not sure of precise version info as it doesn't affect me, just reporting what i have read on the mailing list.

---

### Post by paoleary on 2010-05-01
I haven't updated the XBMC wiki yet (been busy), but on Mythbuntu 9.10 (and, I suspect, also on Lucid) it is sufficient to use the driver package from the [Ubuntu Audio Development Team PPA]("https://launchpad.net/%7Eubuntu-audio-dev/"), then follow the sound.conf configuration.  I believe with the latest drivers the enable_msi=0 option is not required (though it does not hurt, it just reiterates a default).

---

### Post by novellahub on 2010-05-01
> **paoleary said:**
> I haven't updated the XBMC wiki yet (been busy), but on Mythbuntu 9.10 (and, I suspect, also on Lucid) it is sufficient to use the driver package from the [Ubuntu Audio Development Team PPA]("https://launchpad.net/%7Eubuntu-audio-dev/"), then follow the sound.conf configuration.  I believe with the latest drivers the enable_msi=0 option is not required (though it does not hurt, it just reiterates a default).

I just added the PPA repository and it appears that only pulse audio is updated.  No updates to Alsa 1.0.23.

---

### Post by trevs.bronco on 2010-05-01
ok I tried following the upgrade that Novellahub linked too and ended up fubaring my system. this is how things went my first hurdle was that alsa-utils was not where listed, I found it in /sbin, insted of /etc and stopped it. everything went well until it was time to compile and install alsa-driver, when I went ```
sudo make
``` it started progressing as it should and then the crash came. I have been unable to recover from it, and for some strange reason whenever I try to boot the system, no mater how I do it, normal, recovery mode, live disk, I can not mount my second hard drive which has all my media on it. I don't know why it would have been affected by the crash, it didn't have any system files or anything and wasn't in use at the time. I think I might try a fresh install of 9.10 and upgrade the alsa and see if that works.

Trev

---

### Post by trevs.bronco on 2010-05-01
Well things have just gotten worse. I was just changing my BIOS so that I could boot from USB to install 9.10 from a flash drive I have it on and it crashed during the change. Now it shuts down after about 5 seconds no matter what I do. I think I'm gonna take a FUKITOL and go for fish and chips.

Trev

---

### Post by sigurnjak on 2010-05-01
For new ALSA you can use this repo :
[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

I am using it  it fixed my sound but i am not using HDMI or anything fancy . It just controls my volume better . 

Also i switched to kernel Linux 2.6.34-1-generic, so i think that helped a little .

---

### Post by novellahub on 2010-05-01
> **trevs.bronco said:**
> ok I tried following the upgrade that Novellahub linked too and ended up fubaring my system. this is how things went my first hurdle was that alsa-utils was not where listed, I found it in /sbin, insted of /etc and stopped it. everything went well until it was time to compile and install alsa-driver, when I went ```
sudo make
``` it started progressing as it should and then the crash came. I have been unable to recover from it, and for some strange reason whenever I try to boot the system, no mater how I do it, normal, recovery mode, live disk, I can not mount my second hard drive which has all my media on it. I don't know why it would have been affected by the crash, it didn't have any system files or anything and wasn't in use at the time. I think I might try a fresh install of 9.10 and upgrade the alsa and see if that works.

Trev

Sorry about that.  I was just about ready to try it out on my system.  I got as far as this and was a red flag for me:

```

novellahub@mythtvmaster:~$ sudo /etc/init.d/alsa-utils stop
[sudo] password for novellahub:
sudo: /etc/init.d/alsa-utils: command not found

```

I am about to try the directions here:

[http://cursisten.blogspot.com/2010/01/upgrade-to-alsa-1022-and-more-in-ubuntu.html](http://cursisten.blogspot.com/2010/01/upgrade-to-alsa-1022-and-more-in-ubuntu.html)

---

### Post by lidex on 2010-05-01
The easiest way, I'm thinking, to upgrade alsa is using the script provided by *soundcheck*. The link is in my sig. If it's not updated to 1.0.23 yet follow the direction in *Temüjin's* post here:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

---

### Post by trevs.bronco on 2010-05-01
Well if it isn't one thing it is another, came home from dinner found a disk with 9.10 on it threw it in the drive, looked at the monitor and nothing not even a power light...... screwed around with it a bit, came on for two seconds, just enough to let me know the video card works and that the 10.04 install can't mount my second HD. well that's enough for me for one day. Tomorrow I find another monitor and try again. Of course the warrenty on the monitor expired last month. I think tomorrow I will try the soundcheck script, I like simple!

Trev

---

### Post by novellahub on 2010-05-02
> **novellahub said:**
> Sorry about that.  I was just about ready to try it out on my system.  I got as far as this and was a red flag for me:

```

novellahub@mythtvmaster:~$ sudo /etc/init.d/alsa-utils stop
[sudo] password for novellahub:
sudo: /etc/init.d/alsa-utils: command not found

```

I am about to try the directions here:

[http://cursisten.blogspot.com/2010/01/upgrade-to-alsa-1022-and-more-in-ubuntu.html](http://cursisten.blogspot.com/2010/01/upgrade-to-alsa-1022-and-more-in-ubuntu.html)

The link above did not full upgrade Alsa to 1.0.23.  I ran the alsa upgrade script after that and now everything is up date. I did this change in the script first before running:

```
PACKAGE=1.0.23

setpack () {
DRIVER=alsa-driver-1.0.23
FIRMWARE=alsa-firmware-1.0.23
LIB=alsa-lib-1.0.23
PLUGINS=alsa-plugins-1.0.23
UTILS=alsa-utils-1.0.23
TOOLS=alsa-tools-1.0.23
OSS=alsa-oss-1.0.17
}

```

Now aplay -l shows all of my audio devices.  The last one on the list below is my on-board hdmi separate from my GT 240

```

novellahub@mythtvmaster:/etc$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia_1 [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia_1 [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia_1 [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia_1 [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I am able to get sound now!

Here is my asound.conf:

```

pcm.!default {
    type hw
    card 0
    device 7
}

```

---

### Post by paoleary on 2010-05-02
> **novellahub said:**
> I just added the PPA repository and it appears that only pulse audio is updated.  No updates to Alsa 1.0.23.

That's half right; the package you're looking for is linux-alsa-driver-modules-*, where * is your kernel version.  This is sufficient to get the HDMI support for the newer NVidia discretes but does not include  updated ALSA userspace tools (which aren't really necessary).

I don't think I even have PulseAudio installed.

---

### Post by JugeHuge on 2010-05-02
I have solved my HDMI audio problems with ATI in 08.04 and now 10.04 using these steps:

# Get card ID and device ID from running
aplay -l
# Mine was card 0 device 3

sudo nano /etc/asound.conf
# paste the contents the asoundrc file as describbed here. [http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly]("http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly")

# change card and device where needed. I only had to change device since my card id was the same (0)

#reboot the system.
shutdown -r now

After that just make sure that all applications have alsa:default or similar configured..

---

### Post by emillan on 2010-05-03
I fought with this a long time.  The solution ended up being stupid simple but completely unexpected.

It turns out my sound was muted.  The solution was to run alsamixer and un-mute, with the M key, the S/PDIF volume.  For some reason this un-muted my HDMI audio.  (I had been playing with alsamixer all along, but hadn't tried this before because (1) I'm not using S/PDIF, and (2) I didn't know about the M key.)

Hope this helps somebody.

Emilio

---

### Post by paoleary on 2010-05-04
> **emillan said:**
> ...The solution was to run alsamixer and un-mute, with the M key, the S/PDIF volume.  For some reason this un-muted my HDMI audio.  (I had been playing with alsamixer all along, but hadn't tried this before because (1) I'm not using S/PDIF, and (2) I didn't know about the M key.)

As far as ALSA is concerned, if it's a digital output, it's S/PDIF.  Glad you got it sorted.  (Unmuting S/PDIF is mentioned in the [XBMC Wiki page]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240") on NVidia HDMI audio, originally linked in post #2 of this thread.)

---

### Post by trevs.bronco on 2010-05-08
I still can't get my alsa updated. computer crashes during the compile every time. tried logging it , but the log file gets erased too. Any one have any ideas?

Trev

---

### Post by lidex on 2010-05-08
You need alsa 1.0.23, but also the nvidia 195 drivers. If your system is too unstable to update you should probably start from scratch. Do a minimal install, get everything updated and working, and then install myth?? What do you think?

---

### Post by hahu on 2011-02-27
Bump!
 Having problems with this myself. No sound at all from HDMI on Ubuntu 10.10. :( Is this a know problem? Anybody...

---

### Post by benlyboy on 2011-02-27
> Having problems with this myself. No sound at all from HDMI on Ubuntu 10.10. Is this a know problem? Anybody... 

HDMI sound has always been a problem with myth.
But I had less problems with a clean install of 10.10 and mythtv 0.24 than I had with earlier versions.

However HDMI does seem to be turned off by default, not really sure why.

---

### Post by nickrout on 2011-02-27
audio is completely rewritten in myth 0.24 and is much better. Also you need to have a version of alsa that supports your hdmi device. Usually it works fine. Scan for audio devices then choose the device that looks right.

---

