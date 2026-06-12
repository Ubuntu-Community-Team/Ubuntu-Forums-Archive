---
title: "Help with HDMI Audio ATI 3200 Outside of Myth"
date: 2010-12-03
forum: Mythbuntu
---

### Post by the_pod on 2010-12-03
Hi.  I could use some help.  I've spent a good chunk of time this week trying to find an answer to this question and I'm not having much luck.

As background, I'm running a MythBuntu 10.4 64 system and have an integrated ATI 3200.  The system has an onboard HDMI plug that I use to run video and sound to my TV via MythTV.  I have no problems with this.

However... I cannot get sound out of anything else.  No YouTube, no wav files on the internet, nothing.  It is very frustrating. I know that it is possible to do this because my install is relatively new, and when I had a 9.04 system on the exact same box 2 weeks ago I did not have this problem.

Can someone, anyone, please help?

Output of aplay is:
```


card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

edit /etc/asound.conf contains:
```

pcm.!default {
type hw
card 1
device 3
}
```

I'm going bananas here.  The only solution I've been able to find is re: the asound.conf mentioned above, but that only solved my MythTV sound issue.  I would like to have HuluDT and potentially Boxee integrated and I just don't see how this is possible w/o figuring out why my sound won't work.

Thanks for any help.

PS:  Alsa, PulseAudio, etc.. are maddeningly confusing.

---

### Post by the_pod on 2010-12-14
Any help?  Thanks.

---

### Post by JugeHuge on 2010-12-17
I have used this guide and haven't had problems since..

[No sound over HDMI with ga-ma78gm-s2h AMD 780G motherboard.]("http://www.gossamer-threads.com/lists/mythtv/users/333112#333112")

---

### Post by iitywygms on 2010-12-17
go here and read up.
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
I would not try the upgrade until you try the suggested fixes.
Specifically.
Before reporting "NO SOUND" problems - check if your alsamixer-channels are activated and unmuted (gnome-mixer/volume-control/preferences)!!
Very often there are headphone-jack, Toslink, SPDIF or microphone issues reported. Usually this has something to do with wrong alsamixer settings or more seldom with a wrong model-id assigned to your sound-driver in /etc/modprobe.d/alsa-base.conf .
If you're lacking certain controls in alsamixer or your driver is not even being loaded, you should check-out your model-id in attached HD-Audio-Models.txt.
I strongly recommend to try similar model-id's matching your codec to checkout if your faulty function gets working.
I'd guess 80% of the reported problems (group: other than alsamixer issues) over here are related to the model setting in alsa-base.

I searched for days and this finally fixed all sound issues for me.
I have no asound.conf or asoundrc and everything works as it should.

---

### Post by grandpaken on 2010-12-17
> **the_pod said:**
> Hi.  I could use some help.  I've spent a good chunk of time this week trying to find an answer to this question and I'm not having much luck.

Output of aplay is:
```


card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```edit /etc/asound.conf contains:
```

pcm.!default {
type hw
card 1
device 3
}
```I'm going bananas here.  The only solution I've been able to find is re: the asound.conf mentioned above, but that only solved my MythTV sound issue.  I would like to have HuluDT and potentially Boxee integrated and I just don't see how this is possible w/o figuring out why my sound won't work.

Thanks for any help.

PS:  Alsa, PulseAudio, etc.. are maddeningly confusing.

  One thing I notice is that your asound.conf appears to be wrong.  Your card should be 0 and not 1.

---

### Post by the_pod on 2010-12-17
> **grandpaken said:**
> One thing I notice is that your asound.conf appears to be wrong.  Your card should be 0 and not 1.

Thanks for the feedback, everyone.  To date (and with more testing & no fundamental changes) I can get sound thru HDMI via VLC with zero tweeks, just nothing thru a browser (again, flash, hulu, youtube, etc...).

Regarding the note above, doesn't this indicate my card is Card 1, Device 3?
```

card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Intuitively, I keep coming back to the idea that Flash is set to use the analog output by default instead of any master settings issued via the alsaconf file.  But I am unwieldy at best with linux.

TO JugeHuge - I've tried using that but either got nowhere or got stumped (not sure which).  There's a cleaner version of those instructions somewhere (the link inside the link to the Myth wiki is no longer valid), but the directions of "change card and device where needed" threw me for a loop b/c I don't understand the difference between PCM, digital, mixed digital, mixed analog, etc... and all the device settings inside.  I believe I'm trying to tell the system to route any analog sounds to the digital as well for a dual-output, but again - I'm just theorizing and obviously not enacting well.

To iitywygms - My settings in Alsa / Alsamixer are set correctly I believe - HDMI (iec95 switch or whatever it's called checked), and sound is produced via VLC when listening to music and/or watching a movie file...

~~~~~~~~~~~~~~~~~~

I do appreciate everyone's help.  I'll dig a little further into some of these suggestions this weekend.  But, also I'll need to avoid the wrath of the wife for breaking the TV (Thanksgiving weekend didn't go well), so it's hit or miss.

-Scott

---

### Post by iitywygms on 2010-12-17
Mine was solved with...

wrong model-id assigned to your sound-driver in /etc/modprobe.d/alsa-base.conf .

---

### Post by grandpaken on 2010-12-17
> **the_pod said:**
> Thanks for the feedback, everyone.  To date (and with more testing & no fundamental changes) I can get sound thru HDMI via VLC with zero tweeks, just nothing thru a browser (again, flash, hulu, youtube, etc...).

Regarding the note above, doesn't this indicate my card is Card 1, Device 3?
[code]
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-Scott
Your Aplay indicates the sound card is 0 - Your reference is for the video.
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]

---

### Post by the_pod on 2010-12-17
Update:  Tried the sound card as 0:1 (thanks grandpaken) and interestingly enough sound was still the same - worked thru VLC and MythTV (.23 fwiw).  This struck me as odd so I deleted everything from the asound.conf (and .asoundrc), rebooted and still status quo - sound via VLC and MythTV still.  

Is this odd?  I'm guessing asound.conf & .asoundrc don't do anything in my system.

Time to mess with alsa-base.conf.

---

### Post by the_pod on 2010-12-17
As additional follow-up, I went back to MythFrontend Setup to see how I had the sound rigged.  Audio output device is set as "ALSA:plughw:1,3", which I took to mean Card 1, Device 3 (thus my interpretation of the aplay).  Changing to any other options results in no sound, including 5.1, HDMI, ALSA:DEFAULT, etc...  

If that helps at all.  The one difference I see (but know nothing at all about) is this references "plughw" vs "hw", which is what was previously in my config files.  Off to the trial-and-error method.

---

### Post by newlinux on 2010-12-18
It definitely should be 1,3. You HDMI is you audio device as well in this case. You probably don't have anything connected to your sound card as I'm assuming you want to use HDMI for both video and sound.

Do you get sound when you do
```

speaker-test -c2 -twav -Dplughw:1,3

```?

HAve you tried putting
```

  pcm.!default {
     type plug
     slave.pcm "hdmi"
  }

``` in your .asoundrc?

Have you tried disabling your onboard audio in hte BIOS and just using HDMI (just as a test). It would switch to card 0.

---

### Post by JugeHuge on 2010-12-18
Ohh.. Link has changed.
[http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly]("http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly")

From that example ~/.asoundrc you need to replace all Card 0 definitions to Card 1

Uncomment some other setting if don't like dmix-analog
```
pcm.!default {
  type plug
## Uncomment the following to use (unmixed) "analog" by default
#  slave.pcm "analog-hw"
## Uncomment the following to use "mixed-analog" by default
  slave.pcm "dmix-analog"
## Uncomment the following to use (unmixed) "digital" by default
#  slave.pcm "digital-hw"
## Uncomment the following to use "mixed-digital" by default
#  slave.pcm "dmix-digital"
}
```

Then there is two places where you need to define your Device 3

Here
```
# Alias for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.analog-hw {
  type hw
  card 0
  # The default value for device is 0, so no need to specify
#  - Uncomment one of the below or create a new "device N" line as appropriate
#    for your sound card
#  device 1
#  device 4
}
```

and
```
# Alias for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.digital-hw {
  type hw
  card 0
  device 1
#  - Comment out "device 1" above and uncomment one of the below or create a
#    new "device N" line as appropriate for your sound card
#  device 2
#  device 4
}
```

Hope that helps.

---

### Post by the_pod on 2010-12-29
To all - thanks for the help, suggestions, and recommendations as I tried to fix this issue. I'm going to go ahead and mark it as "Solved".

The solution that worked was turning off the onboard sound in the system bios.  This does indeed make the HDMI the default sound and consequently sound in flash, etc.. is automatically routed that direction.

I somewhat fought this solution as I was certain there was a way to make these other programs utilize Card 1, Device 3 as the default sound... right?  Well, that was my thought. I grew weary of the battle however.

So - if anyone else out there has this card with the ATI 3200 onboard and associated HDMI, I've fought the good fight but the easiest answer is also the fastest and from what I can tell the only known way to get all sound pumped to the HDMI.

Thanks again everyone. Now I just wait for NewEgg to ship me my new HDMI receiver.  Merry Christmas to me.8-)

ETA - Didn't fully try JugeHuge's suggestion above as I was already moving forward with the easier option. For those willing to try his asoundrc suggestions may just work out.

---

