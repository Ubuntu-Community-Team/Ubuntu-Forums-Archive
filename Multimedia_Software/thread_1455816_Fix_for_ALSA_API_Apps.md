---
title: "Fix for ALSA API Apps"
date: 2010-04-16
forum: Multimedia Software
---

### Post by Yellow Pasque on 2010-04-16
NOTE: On a fresh install of Lucid (and maybe some older Ubuntu), this should not be necessary. ALSA apps should show in the sound preferences dialog "out of the box" without any extra configuration (like in the screenshot).

A lot of people seem to be experiencing issues with ALSA apps (like Flash) on PulseAudio-enabled systems. Common issues include programs locking/"hogging" the ALSA sound device (prevents other apps from mixing and using the audio device) and also apps trying to use the ALSA software mixer (dmix).
Here is a method to route ALSA apps directly through pulse:
```
gksu gedit /etc/asound.conf
```
Copy/paste these lines into the resulting file:
```
pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }
```
Save. Quit. Reboot.
If it worked, you should now see ALSA apps in the volume control/preferences

---

### Post by davidmaxwaterman on 2010-05-16
> **Temüjin said:**
> A lot of people seem to be experiencing issues with ALSA apps (like Flash) on PulseAudio-enabled systems. Common issues include programs locking/"hogging" the ALSA sound device (prevents other apps from mixing and using the audio device) and also apps trying to use the ALSA software mixer (dmix).
Here is a method to route ALSA apps directly through pulse:
```
gksu gedit /etc/asound.conf
```
Copy/paste these lines into the resulting file:
```
pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }
```
Save. Quit. Reboot.

My file already contains that, but still no sound in flash :(

Any other ideas?

Max.

---

### Post by prosp4300 on 2010-05-24
Thank you very much, this should be delivered by default

After change every prefer device to pulse in kde system settings
and also gstreamer-properties, all apps working except flash that lock the device, and your solution get this issue done

---

### Post by Yellow Pasque on 2010-05-24
> this should be delivered by default

AFAICT, it is the default in fresh installs of Ubuntu 10.04 (at least it was in my Lucid virtualbox install).

---

### Post by Yellow Pasque on 2010-05-24
EDIT: Oops, double post

---

### Post by mpolito1969 on 2010-05-31
It didn't work for me. Audio keeps being OK everywhere except in Firefox.

Ciao,
Max

---

### Post by Vectorferret on 2010-06-09
Also not working for me. Flash still uses ALSA, as it does not appear in the applications using sound in the pulseaudio configuration, nor does it play sound when another application is doing so.

Edit: I have made it work. (I am teh happy!) I put the code into into ~/.asoundrc
```

pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }

```
It is still in /etc/asound.conf, but that didn't work before so I am assuming it needed to be in ~/.asoundrc

---

### Post by Bernie Gallagher on 2010-07-05
I'm having the same problem.  Ever since I installed a codec to play a MP3 that I downloaded from Amazon.com yesterday, I get no audio in Firefox when I play YouTube videos.

But I can't do this because I don't know how to type a "pulse."  What does that even mean?

EDIT:

Okay, I assumed that the { type pulse } is a comment for what those commands are doing, and created this file.  It works!  Yay!  I can listen to my MP3 and YouTube videos.  Thanks!  

But for the sake of us n00bs, you should make it clearer that {type pulse} doesn't mean you need to literally type a "pulse" into the file after each of those commands...

---

### Post by Bernie Gallagher on 2010-07-05
Wow!  Linux is so cool!  I don't need a gajillion different media players to play all my videos!  The one player that came with Ubuntu (after downloading the necessary codecs) plays my MP3s, my MOVs, my FLVs, and even plays my ancient AVIs that Windoze stopped being able to play after I upgraded from Win 95 to XP...

---

### Post by sleepee on 2010-07-14
I used this a few months ago when Flash would hijack my sound.
It worked perfectly for me.  Hope it helps other people too..

---

### Post by afrodeity on 2010-07-14
The above fix works for me, thank you.

But wondering how it relates to some other fixes:

eg: this one apparently is to [increase system wide sound]("http://linux.dipin.info/2009/08/increase-system-wide-sound-volume-in.html").

```

pcm.!default {
   type plug
   slave.pcm "softvol"
}

pcm.softvol {
   type softvol
   slave {
       pcm "dmix"
   }
   control {
       name "Pre-Amp"
       card 0
   }
   min_dB -5.0
   max_dB 20.0
   resolution 6
}

```

this one will make Twinkle sip phone work but prevent pulse from working on its own.

```

pcm.!default {
       type plug
       slave.pcm "asymed"
}

pcm.asymed {
       type asym
       playback.pcm "swmixer"
       capture.pcm "mixin"
}

pcm.dsp0 {
       type plug
       slave.pcm "asymed"
}

pcm.swmixer {
       type dmix
      ipc_key 1234
       slowptr yes
       slave {
               pcm "hw:0,0"
               period_time 0
               period_size 1024
               buffer_size 4096
               rate 48000
      }
}

ctl.dmixer {
       type hw
       card 0
}

pcm.mixin {
       type dsnoop
       ipc_key 5978293 # must be unique for all dmix plugins!!!!
      ipc_key_add_uid yes
       slave {
               pcm "hw:0,0"
               channels 2
               period_size 1024
               buffer_size 4096
               rate 48000
               periods 0
               period_time 0
       }
       bindings {
               0 0
               0 1
       }
}

```

Wish I could get a manual and/or a good tutorial on asound.conf hacks. Also some clarity from the developer of Twinkle on what exactly the above does, I am sure a more elegant solution could be found for the overall sound in Lucid.

---

### Post by hosts on 2010-08-30
> **Temüjin said:**
> NOTE: On a fresh install of Lucid (and maybe some older Ubuntu), this should not be necessary. ALSA apps should show in the sound preferences dialog "out of the box" without any extra configuration (like in the screenshot).

A lot of people seem to be experiencing issues with ALSA apps (like Flash) on PulseAudio-enabled systems. Common issues include programs locking/"hogging" the ALSA sound device (prevents other apps from mixing and using the audio device) and also apps trying to use the ALSA software mixer (dmix).
Here is a method to route ALSA apps directly through pulse:
```
gksu gedit /etc/asound.conf
```
Copy/paste these lines into the resulting file:
```
pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }
```
Save. Quit. Reboot.
If it worked, you should now see ALSA apps in the volume control/preferences

Thanks , this removed the hiss from my speakers!!!

---

### Post by mbaitoff on 2010-11-02
temporary solution for flash in chrome is probably described here: [http://code.google.com/p/chromium/issues/detail?id=27277](http://code.google.com/p/chromium/issues/detail?id=27277)

---

### Post by kb-linux-2 on 2010-11-04
One other thing that I noticed was that when I looked at the Sound Preferences - Applications page, There were no applications listed.  When I started a YouTube video, there were lines of text that very quickly flashed across the screen but it flashed so quickly that I could not read what the text said.

Thanks again.

kb-linux-2

---

### Post by francescofel on 2010-12-09
> **afrodeity said:**
> Wish I could get a manual and/or a good tutorial on asound.conf hacks
A good entry-point to asound.conf is [here]("http://alsa.opensrc.org/.asoundrc") in the ALSA wiki.

Thank you for this useful fix!

---

### Post by tigerlily09 on 2011-02-23
Thanks so much for the help. The ALSA fix worked for Lucid.

---

### Post by cabomix on 2011-09-24
> **Vectorferret said:**
> Also not working for me. Flash still uses ALSA, as it does not appear in the applications using sound in the pulseaudio configuration, nor does it play sound when another application is doing so.

Edit: I have made it work. (I am teh happy!) I put the code into into ~/.asoundrc
```

pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }

```
It is still in /etc/asound.conf, but that didn't work before so I am assuming it needed to be in ~/.asoundrc

What exactly did you do? I don't have an asoundrc file anywhere. I am using 11.04 beta2. same problem. Anybody have ideas how to deal with this on 11.04?

---

### Post by whosane21 on 2011-10-05
> **Temüjin said:**
> NOTE: On a fresh install of Lucid (and maybe some older Ubuntu), this should not be necessary. ALSA apps should show in the sound preferences dialog "out of the box" without any extra configuration (like in the screenshot).

A lot of people seem to be experiencing issues with ALSA apps (like Flash) on PulseAudio-enabled systems. Common issues include programs locking/"hogging" the ALSA sound device (prevents other apps from mixing and using the audio device) and also apps trying to use the ALSA software mixer (dmix).
Here is a method to route ALSA apps directly through pulse:
```
gksu gedit /etc/asound.conf
```
Copy/paste these lines into the resulting file:
```
pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }
```
Save. Quit. Reboot.
If it worked, you should now see ALSA apps in the volume control/preferences



Not sure how or why, but this did a trick on 11.04 using a USB Syba Sound card!  Sound was working natively, but wouldn't register through web-browsing (flash).

THANKS!

---

### Post by manueluribe on 2012-08-06
Newbie:

Same problem. Copied the code verbatim in 12.04 and rebooted. No sound in browsers.

**What is "~/.asoundrc"? A directory? A file? **

I ran a search and have surfed my directory structure up and down and can only find "asoundrc.txt.gz" which contains a file describing a file I apparently don't have...

---

### Post by manueluribe on 2012-08-06
> **manueluribe said:**
> Newbie:

Same problem. Copied the code verbatim in 12.04 and rebooted. No sound in browsers.

**What is "~/.asoundrc"? A directory? A file? **

I ran a search and have surfed my directory structure up and down and can only find "asoundrc.txt.gz" which contains a file describing a file I apparently don't have...
Solution that worked for me:

This started when I hooked in my TV via **HDMI** and sent the sound to the TV. I didn't use Sound Settings to send audio back to my Tosh. 


Soulution: I plugged the HDMI cable in again, used the Nvidia X-Server Settings to fire up Twin View to my TV again. Then sent the audio back to the TV using Sound Settings. Bingo! Sound on browsers!

Then I just sent the audio back to my laptop's speakers. It worked! I shut down, unplugged the HDMI, fired up, and end of problem : ) Switching outputs before I did this had absolutely no effect. Nor did using ALSAMixer or installing the audio development package. Only this worked. Can't believe it took me a week to try that : )

---

