---
title: "TV tuner sound problems"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by scrook on 2006-09-27
Hi all,

I recently installed kubuntu-desktop and xubuntu-desktop on my dapper installation. I have an ATI tv wonder tuner card which has a cable which connects from the tuner to the line in on the sound card (built in sound on an Nforce2 motherboard).

Around the time I installed the alternative desktops, I noticed that I no longer had sound when I was running TVtime.

I've checked the mixer to ensure that the line in wasn't muted and was turned up and there were no problems that I could see.

I checked on my windows install and the sound is working there so I'm sure that this isn't a hardware problem.

Finally, I can get sound if I connect the TV tuner to the MIC input on the sound card.

I think it's most likely that it's a software conflict causing my line in not to work properly in Ubuntu. Does anybody have an idea on what may have happened and how I can go about fixing it?

---

### Post by pseudonym on 2006-09-28
You using ALSA for your sound setup? If so, I'd say it's something to do with your ALSA config. Best thing to do with nforce2 mobos is to junk ALSA and install the OSS driver from nvidia.com. It gives you something ALSA can't - hardware mixing (along with better sound quality, and use made of your Soundstorm APU if you have one).

The howto for doing this in Ubuntu is [here]("http://www.ubuntuforums.org/showthread.php?t=253725"). You should also read up on potential problems in the nvidia.com drivers section.

Once you install this, your sound issues should disappear, and your audio system will be much easier to configure.

---

### Post by scrook on 2006-09-28
Indeed I was using alsa for my sound setup, but I followed the instructions in the post you linked me to and now the tv tuner problem is fixed.

However:

Now I no longer have sound when I play a flash video in firefox. I installed flash via easyubuntu. My guess is that it is configured to use alsa. How do I set it to use the new sound config so I can hear sound in flash again.

---

### Post by pseudonym on 2006-09-28
That's weird - flash sound should be determined by how firefox is set up for sound, and if you only have OSS enabled now, it should output to /dev/dsp. I know it does on my system.

In the past I've had to hack the firefox executable (/usr/lib/firefox/firefox) to fix up some flash-related problems. I just had another look and there is a section related to sound - ```
## find /dev/dsp handler
##

if [ "${FIREFOX_DSP}" = "auto" ]; then
    FIREFOX_DSP=
    if pgrep -u `id -u` esd >/dev/null 2>&1; then 
        FIREFOX_DSP=esddsp 
    elif pgrep -u `id -u` arts >/dev/null 2>&1; then 
        FIREFOX_DSP=artsdsp 
    fi
elif [ "${FIREFOX_DSP}" = "none" ]; then
    FIREFOX_DSP=
fi
```. You could try specifying '/dev/dsp' here - ```
if [ "${FIREFOX_DSP}" = "auto" ]; then
    FIREFOX_DSP=/dev/dsp
```. I'm just guessing this, but it seems like it could be worth a shot...

---

### Post by scrook on 2006-09-28
pseudonym,

I tried your most recent suggestion of messing around with firefox. It did not work however.

I wonder if it's possible alsa is still running in the background somewhere?

Also: I tried changing the firefoxrc file to
FIREFOX_DSP="auto" and FIREFOX_DSP="/dev/dsp" and FIREFOX_DSP="esd"

In all cases I see the following echoed out to the terminal after I save the file: /dev/dsp: Cannot allocate memory

I'm not quite sure what exactly is causing this but I thought it might help shed some light on the problem

---

### Post by pseudonym on 2006-09-29
hmmm, OK, return /usr/lib/firefox/firefox to its previous state. Now run -```
lsmod | grep snd
``` and post the output, if any. This is to check if ALSA modules are still running. 

Also, what flash package are you using, and from which repo? Or did you download it from adobe.com?

---

### Post by scrook on 2006-09-29
pseudonym,

I ran the commmand you specified in the terminal and it did not output anything. I assume that means that alsa isn't running.

As for flash, I installed it via EasyUbuntu. I'm not sure where it gets the package from. Would there be an easy way to check where the package came from in synaptic or through the terminal? If not I can ask around on the easyubuntu forum and find out from someone there.

Thanks for all the help man, it's really appreciated

---

### Post by pseudonym on 2006-09-29
scrook,

No, alsa doesn't appear to be running. That rules one thing out.

You can check your flash version in synaptic. Just search 'flash' and when you have it highlighted, click 'Properties' on the toolbar (I'm assuming that's what it's called - my system is set up in German). There is a 'Versions' tab which should tell you where the package came from. I'm guessing the Easy Ubuntu maintainers were conservative in their choice of flash package, though.

Also, I'm assuming you checked out several flash websites with audio, and you get sound in none of them?

---

### Post by scrook on 2006-09-29
I checked in synaptic and found the following:

The flash player itself doesn't show  up in synaptic but the "flashplugin-nonfree" package does. In the description for the package it says that it downloads flash from macromedia, installs it, and does the set up.

It would appear that we are looking at flash directly from macromedia.

Also, I did try to view several flash movies on different websites to make sure that it wasn't just a problem with one website. I tried back episodes of flash series that I follow and that I know the sound worked on before as well.

I hope that is the info you were looking for

Thanks again

---

### Post by scrook on 2006-09-29
Oh, I almost forgot:

The version number of the flahsplugin-nonfree installer is 

7.0.68~ubuntu2~dapper1(dapper-backports)

---

### Post by pseudonym on 2006-09-29
hmm, that's the standard flash plugin (it's from dapper-backports, but the one in the plain dapper repositories is out of date, so most people use the backports one). So it's not some bleeding edge flash which is causing your problem.

The only thing I can think of to do is to uninstall then reinstall the plugin. In synaptic, make sure to mark it for 'Complete Removal'. Or in a terminal just do 'sudo apt-get --purge remove flashplugin-nonfree'. Then reinstall.

Other than that, I'm not sure how to troubleshoot this. If reinstalling doesn't help, you might want to start a new thread about the issue.

---

### Post by scrook on 2006-09-29
pseudonym,

I have reinstalled flash as you recommended. Now there is sound but it has an extreme crackle and cuts in and out. Do you know of anything that could cause this?

---

### Post by pseudonym on 2006-09-29
Well, that's some sort of progress :) It's weird, though, because flash is set up to use OSS by default. The flash sound problems most people seem to have in linux are usually alsa-related, and the common fix is to install the alsa oss compatibility library aoss. But you're already running OSS with the nvidia driver :confused: 

Three things you could try -

1. Increase firefox's cache to 100mb : Edit>Preferences>Cache enter '100' and restart firefox.

2. Verify that the content you're looking at is not made with the latest version of flash (9). It's a big issue at the moment - stable linux support for flash 9 won't be available until early next year.

3. Uninstall flashplugin-nonfree and install the alternative flash plugin - libflash-mozplugin .

see how you go with these.

---

### Post by scrook on 2006-09-29
I tried increasing the cache and that was a no go. Also I tried uninstalling the nonfree flash player and installing the one you recommended. When I did this my speakers just made a bunch of 'popping noises' instead of the crackly sound that was there before.

I tried rolling back the changes you recommended I make to firefox. When I did this and changed  /etc/firefox/firefoxrc dsp settings the following is output to the terminal:

unsupported playback rate: 44100
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
unsupported playback rate: 44100
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.

Maybe this is the reason?

---

### Post by pseudonym on 2006-09-30
the nvidia oss driver upsamples everything to 48khz, AFAIK. That is what it's supposed to do, so I don't think it's part of your problem.

The only other thing I can suggest is to uninstall the ubuntu-packaged flash and download the version from adobe.com. Maybe that will work.

Other than that, I don't know what will.

In fact, I've just started having problems with my sound, too. any streaming kind of input (digital tv, internet radio in particular) becomes unstable and starts to break up. :(

It's happened with the last two custom kernels I've built. It's either something in those kernels, or maybe the oss driver isn't as good as I thought, at least on relatively recent kernels :confused: 

Has that happened to you?

---

### Post by scrook on 2006-09-30
I uninstalled the NVIDIA drivers this morning and I'm back to square one with my tv tuner sound, but everything else works like it's supposed to.

Last night, I listened to internet radio through rythymbox for a couple hours and it sounded fine with the NVIDIA driver installed. I'm running the standard kernel from ubuntu though so that could be why it was ok.

I think I'm going to try uninstalling xubuntu and see if that brings back the sound for the tv tuner as I really don't use xfce all that often and it seems that it was about that time that my tuner sound stopped working. I'm pretty sure it's not kubuntu b/c I always install that and this is the first time I've had this problem.

---

### Post by Jason_25 on 2006-09-30
The nvidia driver really is better.  Especially for things like tv playback/recording.  Alternatively, you could download flash videos with the firefox video downloader extension and play them back in vlc, minus the sound problems.

---

### Post by pseudonym on 2006-09-30
> **Jason_25 said:**
> The nvidia driver really is better.  Especially for things like tv playback/recording. Yeah, the problem I was having happens when I change the speaker setup in nvmixer. I posted about it in the [soundstorm howto]("http://www.ubuntuforums.org/showthread.php?t=253725&page=2&highlight=soundstorm"). If I leave it on 5.1, though, everything is fine.

---

