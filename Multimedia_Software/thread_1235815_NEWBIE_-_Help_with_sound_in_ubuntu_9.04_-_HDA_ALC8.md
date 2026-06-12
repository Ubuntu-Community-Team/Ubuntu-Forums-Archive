---
title: "NEWBIE - Help with sound in ubuntu 9.04 - HDA ALC883"
date: 2009-08-09
forum: Multimedia Software
---

### Post by cyb3rlion on 2009-08-09
Hello,

as the title implies, I am a newbie with linux and I am trying to do the complete switch from windows.
I have problems configuring correctly the sound in my LG S1 laptop. The sound worked fine in applications such as vlc, until I installed skype and realized that I had to play a little with the configuration to make the program work correctly.

I can't find the correct configuration to make skype work correctly.I have read a little of many articles, as I do not intend to spam, but I'm under the impression that no article describes my starting point and the situation in general. So I turned on the forum, hoping for someone to provide some help with my problem, or at least point out something that I missed during reading the posts...

My chipset is HDA Intel ALC883.

I have run:
aplay -l 

and given the result:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have some packages regarding ALSA installed using the synaptics manager.The following in particular:

alsa-base                                  alsaplayer-alsa
alsa-utils                                    alsa-source
libasound2                                 libasound2-plugins
linux-sound-base                      libsdl1.2debian-alsa
gstreamer0.10-alsa                  alsaplayer-common
gnome-alsamixer                      libpt2.6.1-plugins-alsa
libsd-alsa0                                 bluez-alsa
libalsaplayer0                            alsaplayer-gtk
alsaplayer-oss                          libalsaplayer-dev
alsamixergui

as well as the following general sound packages:

libao2
libmikmod2
pulseaudio

Giving the command lsmod gives the following results, regarding pcm and mixer oss.

snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss

In addition, I provide you with the options that I have at my Sound Preferences Window:

Sound Events > Sound Playback: 
Autodetect , HDA Intel Si3054 Modem (ALSA) , HDA Intel ALC883 Digital (ALSA) , HDA Intel ALC883 Analog (ALSA) , HDA Intel ALC883 Analog (OSS) , HDA Intel ALC883 Analog (OSS) , HDA Intel ALC883 Analog (OSS) - **YES, 3 TIMES, THAT IS CORRECT** , ALSA - Advanced Linux Sound Architecture , OSS - Open Sound System , PulseAudio Sound Server

Music and Movies > Sound playback:
The same

Audio Conferencing > Sound Playback:
The same

Audio Conferencing > Sound Capture:
HDA Intel Si3054 Modem (ALSA) ,  HDA Intel ALC883 Analog (ALSA) ,  HDA Intel ALC883 Analog (ALSA) , 
HDA Intel ALC883 Analog (OSS) ,  ALSA - Advanced Linux Sound Architecture , OSS - Open Sound System , PulseAudio Sound Server , TestSound , Silence

Default Mixer Tracks:
Capture: HDA Intel - ALC883 Analog (PulseAudio Mixer ) , Capture: Monitor of HDA Intel - ALC883 Analog (PulseAudio Mixer ) , HDA Intel ALSA Mixer , Playback: HDA Intel - ALC883 Analog (PulseAudio Mixer) , Realtek ALC883 (OSS Mixer)


Here follows the list of Sound Devices from skype's options window:
Sound In: 
Default Device (default) , hdmi , headset , pulse , HDA Intel (hw:Intel,0), HDA Intel (plughw:Intel,0) , HDA Intel (hw:Intel,1), HDA Intel (plughw:Intel,1) , HDA Intel (hw:Intel,2), HDA Intel (plughw:Intel,2) , HDA Intel (hw:Intel,6), HDA Intel (plughw:Intel,6).

Sound Out & Ringing are the same...

As you can understand I am deeply confused as I can't understand which settings are the right ones. I tried reading a bunch of relevant articles but the result was more confusion.

I tried to be as informative as I can...Can please someone with technical knoledge or someone who had this problem in the past point out the solution, or at least a link to some article that helps?

Thank you all in advance, and again sorry if this is answered before; If it is just give me a brief answer and/or point me to the correct article.

---

### Post by thefish123 on 2009-08-22
> **cyb3rlion said:**
> I have problems configuring correctly the sound in my LG S1 laptop. The sound worked fine in applications such as vlc, until I installed skype...I am VERY interested in what you say here right hat the beginning of your post.  I have the exact same computer and I have been running Ubuntu 8.10 and now 9.04 and have NEVER been able to get sound working.  It works for a few seconds upon initial startup (sometimes) particularly if the computer has been off for a while (I know that sounds ridiculous).

I have searched high and low and posted on forums and mailing lists alike.  No one appears able to help.  I and finally just rebooted into Windows.  Ubuntu is still on my other partition but I frequently think about formatting it and reclaiming the space for Windows.

I would love to get this working but I have started mentally writing if off as a pipe dream.

So, how did you get sound working?

Best regards,

The Fish

---

### Post by cyb3rlion on 2009-08-28
Hello, 
as far as the sound working in the start, it was already functionable after a fresh install! I have to be honest here, I can't really remember if it worked for the speakers that are embeded in the laptop, but certainly it worked when I was using the headphones which is the way I use more frequently...

I didn't have to do anything to get it working at that stage. There WAS something awkward though... While I had vlc in ubuntu playing some video files from the mounted windows partition, it suddenly froze everything and it wouldn't even Logout! I had to press the close button for 5 seconds to force it to close. After that, ubuntu wouldn't start, not even in safemode! I had to install it from scratch, and the funny thing is that it hasn't frosen since then. The sound still worked, only partially though! Now it only works for the the headphones. At some point I messed with some settings and i was able to make the speakers work, but then no sound would come out of the headphones ...The settings were something at the sound preferences.

That's all there is to it. The original problem described at the start remains unsolved since I didn't have the time to search for a solution. Any help would still be appreciated.

---

