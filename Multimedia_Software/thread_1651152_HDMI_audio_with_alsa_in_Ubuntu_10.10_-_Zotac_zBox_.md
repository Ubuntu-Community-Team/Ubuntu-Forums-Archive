---
title: "HDMI audio with alsa in Ubuntu 10.10 - Zotac zBox HD-ID11"
date: 2010-12-22
forum: Multimedia Software
---

### Post by funben on 2010-12-22
Hi,

Here is my situation, I have a Zotac zBox HD-ID11
 - I had Ubuntu 10.04 and got audio trough HDMI after applying this : [AlsaUpgrade]("http://ubuntuforums.org/showthread.php?p=6589810")
 - I migrated to Ubuntu 10.10
During the process I was asked "do you want to replace this alsa* file" I said Yes

After the migration I had alsa 1.0.23 and the aplay -l showed the proper sounds cards.

using "aplay -Dplughw:X,Y -fcd /mySound.wav"  
When X, Y was 0,0 I had sound though analog
When X was 1 and Y was  3, 7, 8, 9 had no sound though hdmi.

So I tried many of the help topic over the internet, but I messed up my system since, I now have no sound card recognized

Here are the alsa-info.sh result before and after the home fixing
[http://www.alsa-project.org/db/?f=ef4c81ff7833767d361c978060f957a002d5960c](http://www.alsa-project.org/db/?f=ef4c81ff7833767d361c978060f957a002d5960c)
[http://www.alsa-project.org/db/?f=81fd1c6a524ab7c1313c5b937f68a0715090ce2f](http://www.alsa-project.org/db/?f=81fd1c6a524ab7c1313c5b937f68a0715090ce2f)

My question is how to get back to original status ?
I tried to reinstall the alsa* package using ubuntu package manager

---

### Post by tjones00 on 2010-12-22
The alsa-info.sh is stating that 1.0.23 is installed but no modules are being loaded.

Double check by typing.

```
sudo cat /proc/asound/version
```

Does 

```
sudo aplay -l
```

list anything? It could just be a user permissions issue with the reinstall.

---

### Post by baberone on 2010-12-24
Hi

I've got exactly the same problem (no sound on Maverick 10.10 and on Zotac HD 11)

Also Info: 
  
 [http://www.alsa-project.org/db/?f=748776a12c949a2fbcf9c2c41134c9227b3cf3b1](http://www.alsa-project.org/db/?f=748776a12c949a2fbcf9c2c41134c9227b3cf3b1)

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
```

```
ben@zotac:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/ben not ours.
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

In alsamixer, on the second sound card (HDA NVidia) I've unmuted S/PDIF...

I must say that the Nvidia video drivers is not enabled because this breaks everything (no desktop interface - x doesn't seems to run correctly with the latest nvidia drivers. Currently the 'nouveau' drivers are used)

---

### Post by tjones00 on 2010-12-24
Are you using a probemask barberone? 

The ZBox HD-ID11 uses an ion2 (gt218 310m) nvidia card. With alsa 1.0.23 aplay -l should list 4 devices.

Although this is for 10.04 you can use this as a base reference for troubleshooting.

[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

Post #8 and #21 are the solutions for ion2 hdmi audio in 10.04. Post #8 should still work in regards to 10.10 for troubleshooting hdmi audio.

---

### Post by baberone on 2010-12-27
Thanks for the feedback tjones00.

I managed to get it working, but with a 2.6.37-rc7 kernel.

Check this post, where I tried to explain how I've done it:

[http://ubuntuforums.org/showthread.php?t=1620914](http://ubuntuforums.org/showthread.php?t=1620914)

---

### Post by tjones00 on 2010-12-27
Hmmm that's interesting. I haven't tried 10.10 on my ion2 system yet. 

So why did you have to use the 2.6.37-rc7 kernel? It was specifically for oss support? Sounds to me that snd-hda-intel might be on the fritz again.

From the looks of that thread you guys abandoned alsa to get it working. Hey as long as it works good stuff!

If you revisit this thread could you leave a bit more info about how you setup the ion2 with oss in 10.10? All the post kernel compile stuff and  I'll link to your 10.10/oss info on my 10.04 ion2 thread. Or hell just leave the 10.10 oss setup info on the 10.04 ion2 thread lol.

---

### Post by baberone on 2010-12-27
I used the latest kernel for a couple of reasons. The main reason was that I thoughed that my Haupppauge WinTV-HVR-900 HD TV tuner would be recognised (which is not the case by the way..). So I tried with a 2.6.35 kernel (found on some forum that Ubuntu 10.04 did not support it, but 10.10 should), but then Alsa and NVidia did not worked correctly.

So I decided to go for the latest kernel, the 2.6.37... I compiled the kernel (enabling all OSS kernel parameters - see other post) and was very happy to hear a sound when logging in :) 

NVidia drivers compiled without any problem. I also tried a precompiled kernel (2.6.36), but then NVidia was complaining about gcc 4.4 instead of 4.2...

It's not very clear for we what did the trick, but now I'm back to the starting point (like on 10.04) which is audio on HDMI and NVidia drivers working.

If you want some more specific info about the config, let me know I'll try to come back here once in a while.

---

### Post by tjones00 on 2010-12-27
Just so I'm clear on things.

Compile a kernel with oss support.

Install oss.

And boom everything worked without any tweaking?

---

### Post by baberone on 2010-12-28
Yes this is basicly it. Although I didn't install any extra OSS stuff (alsamixer v1.0.23 was already installed with the [Alsa Upgrade script]("http://ubuntuforums.org/showthread.php?p=6589810") to fix the 'no controls or not recognized problem' for HDA NVidia)

In alsamixer, I did of course unmute the  S/PDIF on the HDA NVidia sound card (all others are also unmuted, except the mic)

The kernel changes in .config file:

```
CONFIG_SOUND=y
CONFIG_SOUND_OSS_CORE=y
CONFIG_SOUND_OSS_CORE_PRECLAIM=y
CONFIG_SND=y
CONFIG_SND_TIMER=y
CONFIG_SND_PCM=y
CONFIG_SND_HWDEP=m
CONFIG_SND_RAWMIDI=m
CONFIG_SND_JACK=y
CONFIG_SND_SEQUENCER=m
CONFIG_SND_SEQ_DUMMY=m
CONFIG_SND_OSSEMUL=y
CONFIG_SND_MIXER_OSS=y
CONFIG_SND_PCM_OSS=y
CONFIG_SND_PCM_OSS_PLUGINS=y
```

But don't ask me exactly what they do !! I've read somewhere that OSS is being replaced by pulseaudio, but the replacement is not yet fully working (I also removed pulseaudio). And that from 10.10 on, OSS is not anymore built in the kernel. It might also work by modprobeing the needed modules, but I haven't tried that.

---

### Post by applejuicekiss on 2011-01-24
my experiences with this...
HDMI audio works!  mostly.  i have some things to work out still.

zbox hd-id11
ubuntu 10.10 64bit. 
pretty much stock install with normal updates from Partners, Independent, and Medibuntu.

now, i don't really remember when the last kernel image update was, or if anything alsa related was ever updated, but again, i haven't added any extra PPAs other than those listed above, and i don't know if this worked before updates.

what i did:
in terminal:~$ alsamixer -c1
now in alsamixer, viewing HDA NVidia, Nvidia 0b HDMI/DP [playback]
unmuted S/PDIF 1

now i havn't tried xbmc on this box, but in smplayer i then had to change the output driver to alsa (n.n-HDA NVidia)
running smplayer -> options -> Preferences -> Audio tab -> Output driver.
for output driver i selected "alsa(1.7-HDA NVidia)".

so now in smplayer i can hear audio out of my tv via hdmi.  it is still not perfect however.  only smplayer uses hdmi audio right now, and banshee and many other apps don't have a gui control for output driver, so they are using the intel analog out. furthermore, smplayer no longer uses the intel analog output.

changing the output device to HDMI in Sound Preferences results in no sound (except smplayer which still uses only hdmi)

so, i am happy enough that i can watch movies through the tv and enjoy stereo sound via hdmi through the tv built in speakers.  i would like to be able to send all audio through both devices simultaneously, and that seems like it should be possible since i get some audio through hdmi...

... i did not test the s/pdif out as i don't have a cable, and i did not test anything other than hdmi stereo, as i only have this stereo tv to test with. (so no 5.1 or 7.1)

hope this helps someone and i would appreciate any suggestions to get everything working together/at same time.

*edit:  i originally said that any alsa output driver worked equally in smplayer.  After rebooting, it did not.  i changed it to 1.7 instead of 1.9 and now it is fine.

---

### Post by applejuicekiss on 2011-02-04
SOLVED (for me)

Zotac zBox HD-ID11
Ubuntu 10.10, 64bit fully updated 
(with Partners, Independent and Medibuntu repositories enabled, not that i think it made any difference)

the following instructions are taken from this blog:
[http://ossnotebook.blogspot.com/search?updated-min=2010-01-01T00%3A00%3A00-08%3A00&updated-max=2011-01-01T00%3A00%3A00-08%3A00&max-results=14](http://ossnotebook.blogspot.com/search?updated-min=2010-01-01T00%3A00%3A00-08%3A00&updated-max=2011-01-01T00%3A00%3A00-08%3A00&max-results=14)

Quoted (with minor modification):
on alsamixer press F6 to select the nvidia card, enable all s/PDIF devices

    # list the devices
    aplay -l
    # my sound gets enabled when I play on device speaker-test -D plughw:1,7 -r 44100, after that the sounds starts to work. It's important to use the -r 44100 since the drivers are not setting up the correct frequency.
    speaker-test -D plughw:1,3 -r 44100
    speaker-test -D plughw:1,7 -r 44100
    speaker-test -D plughw:1,8 -r 44100
    speaker-test -D plughw:1,9 -r 44100



In case you want to make a permanent change for the hdmi sound as the deafult card you can update /usr/share/alsa/alsa.conf and change these lines:

defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0

to this:

defaults.ctl.card NVidia
defaults.pcm.card Nvidia
defaults.pcm.device 7

ENDQUOTE 
(note that in the original blog they used device 9.  i found that i had to use device 7 and i have changed the instructions to reflect that.  presumably this will be the case for other HD-ID11 users.)

this is all i had to do.  i now have sound through HDMI to my tv system-wide

good luck

---

### Post by Java Glitch on 2011-02-07
Your instructions worked like a champ!  Thanks.

---

### Post by shubes on 2011-04-04
+1. Thanks.

---

### Post by schodt on 2011-06-10
Yes this works but it disables the internal Intel card. Do you still see both audio devices in your sound preferences?

---

### Post by applejuicekiss on 2011-06-12
yes schodt, if i remember correctly that is the case.  it would be good to have a way make full use of both audio devices, but for my application, running all sound through the tv is sufficient.  let us know if you find a solution.

---

