---
title: "No Sound on an HP Pavillion dv6000 series laptop"
date: 2010-08-06
forum: Multimedia Software
---

### Post by RonB123123 on 2010-08-06
I recently had sound 'working' as in I had to reload the alsa drivers each time I booted up my computer. After a year of giving up how to fix it, I looked it up again and was told to update my alsa drivers. I updated my drivers to version 1.0.23 and my sound was working but was still acting weird. For example, my sound would play a song, in Adobe Flash, at its highest volume even if the volume wasn't at max. I was just happy that I didn't have to reload the drivers, but this was another problem.

Now, for some reason, sound just doesn't work. I've tried reloading the drivers several times and looked for a solution on these forums as well as on google. No luck. So I ask, is there anything I can do to get my sound to work?

---

### Post by RonB123123 on 2010-08-06
Bump

I tried to debug my sound problems and was wondering if there is an interfering motherboard chip? This is the information I receive when I run "lsmod | grep snd"

> 
snd_hwdep               7200  0 
snd_pcm_oss            37920  0 
snd_pcm                75296  1 snd_pcm_oss
snd_page_alloc          9156  1 snd_pcm
snd_mixer_oss          16028  1 snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  9 snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd


What can I do to solve this problem once and for all? I know sound can work on my laptop because it has worked before and I believe it's something to do with alsa. Would it be better to downgrade alsa so all I would have to do is reload the alsa drivers each startup to get sound to work? If so, whats the command to downgrade?

Thank you,
Ron

---

### Post by lidex on 2010-08-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by RonB123123 on 2010-08-08
Ok lidex, I ran the script and it outputted this link.

[http://www.alsa-project.org/db/?f=8b499d23c7c4f2d1881ac7f2aa6c958265172df9](http://www.alsa-project.org/db/?f=8b499d23c7c4f2d1881ac7f2aa6c958265172df9)

It's not detecting my sound card?? I have no idea why because it always detected it before updating the alsa drivers.

---

### Post by simosx on 2010-08-08
> **RonB123123 said:**
> Ok lidex, I ran the script and it outputted this link.

[http://www.alsa-project.org/db/?f=8b499d23c7c4f2d1881ac7f2aa6c958265172df9](http://www.alsa-project.org/db/?f=8b499d23c7c4f2d1881ac7f2aa6c958265172df9)

It's not detecting my sound card?? I have no idea why because it always detected it before updating the alsa drivers.

Note the lines

[FONT="Courier New"]Driver version:     1.0.20
Library version:    1.0.23
Utilities version:  1.0.20
[/FONT]

You indeed updated to Alsa 1.0.23, however there has been a kernel update that you accepted, it got installed and it put back an old version of Alsa, 1.0.20. Do you have Ubuntu 9.10 or older originally?

You need to perform the installation of Alsa 1.0.23 again and get a fresh alsa-info.sh report.

To upgrade Alsa, use AlsaUpgrade.

---

### Post by RonB123123 on 2010-08-08
Just updated the alsa drivers and everything is at 1.0.23. Here's the new link:

[http://www.alsa-project.org/db/?f=f6f5870cd5b1647c32260abc56327b0bd4b59674](http://www.alsa-project.org/db/?f=f6f5870cd5b1647c32260abc56327b0bd4b59674)

Sound still doesn't work. What's weird is that I also lost mp3 support in rhythmbox, with GStreamer plugins still installed, and I cannot play the songs on The Hype Machine ([http://hypem.com](http://hypem.com)) anymore. Also, there is no volume control icon on the top right.

Every time I try to fix alsa, it seems more and more things break down...

> 
$ lsmod | grep snd
snd_intel8x0m          13960  0 
snd_via82xx_modem      11364  0 
snd_atiixp_modem       11972  0 
snd_ac97_codec        101472  3 snd_intel8x0m,snd_via82xx_modem,snd_atiixp_modem
ac97_bus                1596  1 snd_ac97_codec
snd_pcm                76928  4 snd_intel8x0m,snd_via82xx_modem,snd_atiixp_modem,snd_ac97_codec
snd_timer              21412  1 snd_pcm
snd                    62052  6 snd_intel8x0m,snd_via82xx_modem,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_timer
soundcore               7264  1 snd
snd_page_alloc          9124  4 snd_intel8x0m,snd_via82xx_modem,snd_atiixp_modem,snd_pcm


---

### Post by simosx on 2010-08-08
The alsa-info output has all the details of the kernel modules, so no need to type them again.

The alsa-info.sh output shows that you have indeed 1.0.23, but no alsa has been loaded.
I performed a search for your laptop model and I got this very recent thread from this forum,
[http://ohioloco.ubuntuforums.org/showthread.php?p=9664708](http://ohioloco.ubuntuforums.org/showthread.php?p=9664708)

which has the solution for you sound card.
Please try it out and tell us if it works. 
I'll try to help so that Alsa autodetects your sound card in future versions of the Linux kernel.

---

### Post by RonB123123 on 2010-08-11
thank you simosx. I'm stuck on step 3 of the link you shared with me. When I run alsamixer or gnome-alsamixer, I receive an error message.

```

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

and gnome-alsamixer just shows me a blank window. I tried upgrading alsa from stable releases and it brought me back to 1.0.20 lol...I'll configure/compile/install the latest one again but I'm sure it won't work. Somehow, I was able to get it to work last time with 1.0.20 but it detected my sound card then, it just needed to be reloaded on reboot each time. I remember looking everywhere for sound fixes then so one of the articles I must have read, must have enabled it. I went through a lot though.

How do I run alsamixer without receiving that error message?

---

### Post by simosx on 2010-08-11
Your Alsa driver went back to 1.0.20 if you installed any of the Linux kernel upgrades that where made available recently to Ubuntu 10.04.

So, this takes back your Alsa to 1.0.20 (old) and you kept the latest Alsa Lib to 1.0.23. This would be the source of the error message that you get. You would need to follow again the process of installing the latest Alsa and then verify with alsa-info that all is fine. Report the new alsa-info here again.

Good luck!

---

### Post by RonB123123 on 2010-08-11
Upgraded again, ran alsamixer and gnome-alsamixer, same story. That's why I just reinstalled from the repositories because no matter what I do, alsamixer in the terminal returns an error message?? Why, I have no idea.

Is there a way to replace ALSA with OSS? maybe I'd have better luck with a different sound driver.

---

### Post by simosx on 2010-08-11
> **RonB123123 said:**
> Upgraded again, ran alsamixer and gnome-alsamixer, same story. That's why I just reinstalled from the repositories because no matter what I do, alsamixer in the terminal returns an error message?? Why, I have no idea.

Is there a way to replace ALSA with OSS? maybe I'd have better luck with a different sound driver.

I think you are getting frustrated and you are getting further away from the solution. Installing OSS (OSS4) would probably complicate your system and most probably we would not be able to help to rectify it.

I requested above for you to install the full Alsa 1.0.23 using AlsaUpgrade, and after doing so to produce a fresh alsa-info.sh output. This would help verify that your system file are up to sync. You have not done this yet.

If the problem persists, an extra step is to push your Alsa driver to the snapshot version (that's the absolute latest version; Alsa 1.0.23 is from April 2010). Then, get an alsa-info.sh output and we can compare with the older alsa-infos.

If you feel doing these steps, I'll be able to help you take it further.

---

### Post by lidex on 2010-08-11
Alsa-backports would cause problems upgrading. What is this output:
```
dpkg -l | grep "alsa"
```

---

### Post by RonB123123 on 2010-08-14
Okay, I won't switch to OSS then if it will be worse than alsa.

This is my output after running your dpkg command, lidex.
> 
$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.20+dfsg-1ubuntu5                                 ALSA driver configuration files
ii  alsa-firmware-loaders                 1.0.20-1ubuntu1                                      ALSA software loaders for specific hardware
ii  alsa-oss                              1.0.17-1                                             ALSA wrapper for OSS applications
ii  alsa-source                           1.0.20+dfsg-1ubuntu5                                 ALSA driver sources
ii  alsa-tools                            1.0.20-1ubuntu1                                      Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                        1.0.20-1ubuntu1                                      GUI based ALSA utilities for specific hardware
ii  alsa-utils                            1.0.20-2ubuntu6                                      ALSA utilities
ii  alsamixergui                          0.9.0rc2-1-9                                         graphical soundcard mixer for ALSA soundcard driver
ii  alsaplayer-alsa                       0.99.80-3.1ubuntu2                                   PCM player designed for ALSA (ALSA output module)
ii  alsaplayer-common                     0.99.80-3.1ubuntu2                                   PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                        0.99.80-3.1ubuntu2                                   PCM player designed for ALSA (GTK version)
ii  alsaplayer-oss                        0.99.80-3.1ubuntu2                                   PCM player designed for ALSA (OSS output module)
ii  bluez-alsa                            4.51-0ubuntu2                                        Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                            ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.25-2ubuntu1.2                                   GStreamer plugin for ALSA
ii  libesd-alsa0                          0.2.41-5                                             Enlightened Sound Daemon (ALSA) - Shared libraries
ii  libsdl1.2debian-alsa                  1.2.13-4ubuntu4                                      Simple DirectMedia Layer (with X11 and ALSA options
ronak@ronak-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                             1.0.20+dfsg-1ubuntu5                                 ALSA driver configuration files
ii  alsa-firmware-loaders                 1.0.20-1ubuntu1                                      ALSA software loaders for specific hardware
ii  alsa-oss                              1.0.17-1                                             ALSA wrapper for OSS applications
ii  alsa-source                           1.0.20+dfsg-1ubuntu5                                 ALSA driver sources
ii  alsa-tools                            1.0.20-1ubuntu1                                      Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                        1.0.20-1ubuntu1                                      GUI based ALSA utilities for specific hardware
ii  alsa-utils                            1.0.20-2ubuntu6                                      ALSA utilities
ii  alsamixergui                          0.9.0rc2-1-9                                         graphical soundcard mixer for ALSA soundcard driver
ii  alsaplayer-alsa                       0.99.80-3.1ubuntu2                                   PCM player designed for ALSA (ALSA output module)
ii  alsaplayer-common                     0.99.80-3.1ubuntu2                                   PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                        0.99.80-3.1ubuntu2                                   PCM player designed for ALSA (GTK version)
ii  alsaplayer-oss                        0.99.80-3.1ubuntu2                                   PCM player designed for ALSA (OSS output module)
ii  bluez-alsa                            4.51-0ubuntu2                                        Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                            ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.25-2ubuntu1.2                                   GStreamer plugin for ALSA
ii  libesd-alsa0                          0.2.41-5                                             Enlightened Sound Daemon (ALSA) - Shared libraries
ii  libsdl1.2debian-alsa                  1.2.13-4ubuntu4                                      Simple DirectMedia Layer (with X11 and ALSA options


I'll upgrade my drivers again and post again.

---

### Post by lidex on 2010-08-14
No backports there.

---

### Post by RonB123123 on 2010-08-18
Problem is fixed, clean install of 10.04. Please be stable Lucid.

Thanks anyway. :)

---

