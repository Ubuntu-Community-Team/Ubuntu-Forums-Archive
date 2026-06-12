---
title: "Jaunty and S/PDIF pass-through"
date: 2009-07-21
forum: Multimedia Software
---

### Post by MisterM on 2009-07-21
Hi,

First of all, let me say that I know there are already numerous threads about this topic, however I couldn't find a concrete answer in any of them.

I cannot get S/PDIF pass-through working in jaunty. It was working fine in intrepid, though. This is what I want to achieve:
[LIST=1]
[*]All sound should be played on the **analogue** 6-channel output **by default**.
[*]Movies with a **DTS/AC3** sound track should be **passed through** to the digital (coax) output, with **no decoding** taking place.
[/LIST]

I use smplayer for playing movies and after checking the *AC3/DTS pass-through S/PDIF* option, the sound is no longer heard on the analogue output (which is correct), however, nothing is heard on the coax either. My decoder displays the message *No digital data*.

I have all the *IEC958* options checked in alsa mixer (*IEC958*, *IEC958 Capture* and *IEC958 Default PCM*). I have also tried experimenting with a subset of them, and even tried rebooting after changing them. Nothing helps.

S/PDIF pass-through stopped working after upgrading to jaunty (from intrepid).

Here's some info about my hardware if it helps at all:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```
I've also uploaded some screenshots of my sound configuration.

I would much appreciate it if someone could please explain in simple terms, what I have to do to get S/PDIF pass-through working in jaunty, as it worked in intrepid.

If you need any more information about my system, please say so.

EDIT:
I forgot to mention that selecting *HDA Intel ALC1200 Digital (ALSA)* in Sound Preferences and clicking test, produces no sound on either the analogue nor the digital output, while selecting *HDA Intel ALC1200 Analog (ALSA)* throws the following error:
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
[SIZE="4"]**SOLUTION:**[/SIZE]
You have to add the following line to /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=6stack-dig probe_mask=1
```
This works with my ALC1200 sound card. If you have a different card, the above line might differ for you.

---

### Post by MisterM on 2009-07-22
Does no one know how to fix this? :(

---

### Post by MisterM on 2009-07-25
I found another related strange behaviour. After a while, DTS/AC3 tracks stop working on analogue output as well. I have not been able to figure out when or why this happens, but a reboot fixes it every time.

I think there must be something wrong with my ALSA configuration. Any ideas what?

---

### Post by CianDeimos on 2009-08-08
I've been having the same problem.  after 2 days I seem to have finally got it working.
  After agreeing that it seems to be an issue in the alsa configuration, I reinstalled alsa.  First, I went to synaptic package manager and typed alsa in the search with all packages selected on the left.  I then marked all the alsa packages for reinstallation. Finally, I verified my alsamixer settings and was able to get ac3 passthrough on the latest vlc player 1.0.1

Hope this helps.

---

### Post by MisterM on 2009-08-08
Hi, CianDeimos,

Thanks for your suggestions.

I did as you suggested and reinstalled the following packages:
```
alsa-base (1.0.18.dfsg-1ubuntu8)
alsa-utils (1.0.18-1ubuntu11)
bluez-alsa (4.32-0ubuntu4.1)
gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2)
gstreamer0.10-alsa (0.10.22-5)
libesd-alsa0 (0.2.40-0ubuntu3)
libpt-1.10.10-plugins-alsa (1.10.10-2ubuntu3)
libpt2.6.1-plugins-alsa (2.6.1-0ubuntu4)
libsdl1.2debian-alsa (1.2.13-4ubuntu3)
python-alsaaudio (0.2-1ubuntu2)
```

However, the situation is still the same. I even tried rebooting afterwards. I believe alsa isn't working at all, neither analogue nor digital. **Any other ideas?**

You mentioned you verified your alsamixer settings. **What exactly did you check and/or change?**

---

### Post by CianDeimos on 2009-08-09
In alsaixer I verified that IEC958 is not muted and I lowered the slider all the way to the bottom.  These were suggestions I found somewhere on my search for a solution.  I'm fairly new to linux so I've been fumbling around trying to get things working.  

after re-reading my last post.  I believe I completely removed alsa packages  and then I went back and Installed them again rather than just clicking reinstall.  I've found that completely removing packages has a better chance of removing the old configuration files so new ones can be generated.

---

### Post by MisterM on 2009-08-09
> **CianDeimos said:**
> In alsaixer I verified that IEC958 is not muted and I lowered the slider all the way to the bottom.  These were suggestions I found somewhere on my search for a solution.

I don't have a slider for IEC958, I only have those checkboxes that can be seen in the screenshots in my first post. This is probably due to having a different soundcard than you.

> **CianDeimos said:**
> after re-reading my last post.  I believe I completely removed alsa packages  and then I went back and Installed them again rather than just clicking reinstall.  I've found that completely removing packages has a better chance of removing the old configuration files so new ones can be generated.

I tried completely removing (purging) and then installing again the following packages:
```
alsa-base (1.0.18.dfsg-1ubuntu8)
alsa-utils (1.0.18-1ubuntu11)
gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2)
```
Again, the situation has not changed. :(

**Could you please check which packages you removed?** You can do this by opening Synaptic and clicking File > History.

Thanks for trying to help, CianDeimos.

---

### Post by efgevh on 2009-08-09
I also have the HDA Intel ALC1200 Digital - got the exact same problem.

---

### Post by efgevh on 2009-08-09
Seems this was reported on April on the launchpad 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/365411]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/365411")

, and the ticket has now the status "new" and "undecided".

---

### Post by MisterM on 2009-08-09
> **efgevh said:**
> Seems this was reported on April on the launchpad 

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/365411]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/365411")

, and the ticket has now the status "new" and "undecided".

According to that bug report, support for ALC1200 was added in the next version, which is apparently still not in the Ubuntu repositories. What's strange is that it worked fine on intrepid, however the current version in the intrepid repository is 1.0.17, which is even older.

Is there an ALSA ubuntu (or debian) repository, where we can get the latest stable version? Or could this play havoc with dependencies?

So, does this mean, there's nothing wrong with my configuration and that my card is actually not supported in the jaunty version of ALSA? I find that quite hard to believe.

On another note, is it possible to get S/PDIF pass-through with pulse, so I wouldn't have to bother with ALSA at all? Everything else seems to work fine with pulse.

---

### Post by efgevh on 2009-08-09
> **MisterM said:**
> According to that bug report, support for ALC1200 was added in the next version, which is apparently still not in the Ubuntu repositories. What's strange is that it worked fine on intrepid, however the current version in the intrepid repository is 1.0.17, which is even older.

Is there an ALSA ubuntu (or debian) repository, where we can get the latest stable version? Or could this play havoc with dependencies?



there is a "sound solution guide" that mentions getting pulse 0.915 that has a newer alsa, however there's a limit to how much configuration you can do in my opinion before you make your system unstable. Here's the thread anyways :

[http://ubuntuforums.org/showthread.php?t=843012&highlight=sound]("http://ubuntuforums.org/showthread.php?t=843012&highlight=sound")

> 

So, does this mean, there's nothing wrong with my configuration and that my card is actually not supported in the jaunty version of ALSA? I find that quite hard to believe.


Well, it would not be the first time with linux.


> 
On another note, is it possible to get S/PDIF pass-through with pulse, so I wouldn't have to bother with ALSA at all? Everything else seems to work fine with pulse.

I think since pulse relies on alsa drivers that will not work either.

---

### Post by MisterM on 2009-08-09
> **efgevh said:**
> Well, it would not be the first time with linux.

Heh, of course. It's just strange, since it was working fine in intrepid.

> **efgevh said:**
> I think since pulse relies on alsa drivers that will not work either.

If this is the case, than there *must* be something wrong with my configuration, because pulse is working fine. In sound preferences, if I select pulse and click Test, I get a tone. If I do the same with ALSA, I get this message:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

Could it be that pulse is locking ALSA for its own use, and therefore no other application can use it directly? I'm probably stabbing in the dark here, since I still don't quite understand how all this sound stuff (pulse, alsa, oss,...) works and interconnects in ubuntu. :-k

---

### Post by efgevh on 2009-08-09
you mean in sound prefs you select pulseaudio for e.g. music playback ang get sound on spdif? My problem is that doesn't work, not with pulse, not with alsa, there's just no sound.

The analog, hda intel alc1200 analog (alsa), is working with alsa, not with pulse in which case i get a similar error msg to the one you provided.

---

### Post by MisterM on 2009-08-09
> **efgevh said:**
> you mean in sound prefs you select pulseaudio for e.g. music playback ang get sound on spdif? My problem is that doesn't work, not with pulse, not with alsa, there's just no sound.
No, I've never got any sound out on s/pdif (since upgrading to jaunty). It's just that on pulse it works on analogue at least and on alsa even that doesn't work (I get the error above).

> **efgevh said:**
> The analog, hda intel alc1200 analog (alsa), is working with alsa, not with pulse in which case i get a similar error msg to the one you provided.
Heh, this is just the reverse as in my case then. :rolleyes:
I just hate having these sound problems in ubuntu, cause there's a ton of posts and guides on the subject, but nothing that quite fits my case. Or if there is, I can't seem to find it. :-?

---

### Post by CianDeimos on 2009-08-09
> **MisterM said:**
> I don't have a slider for IEC958, I only have those checkboxes that can be seen in the screenshots in my first post. This is probably due to having a different soundcard than you.



I tried completely removing (purging) and then installing again the following packages:
```
alsa-base (1.0.18.dfsg-1ubuntu8)
alsa-utils (1.0.18-1ubuntu11)
gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2)
```Again, the situation has not changed. :(

**Could you please check which packages you removed?** You can do this by opening Synaptic and clicking File > History.

Thanks for trying to help, CianDeimos.

I purged and installed the same packages you listed.  Sorry I couldn't be of more help

---

### Post by CianDeimos on 2009-08-09
Just had a thought.  if you haven't already.  Install those packages while your surround reciever is hooked up and turned on.  Just thought it may not set up correctly if it doesn't detect anything on the spdif port.  And when I originally installed ubuntu my reciever was off.  When I reinstalled the packages it was on.

---

### Post by MisterM on 2009-08-10
> **CianDeimos said:**
> Just had a thought.  if you haven't already.  Install those packages while your surround reciever is hooked up and turned on.  Just thought it may not set up correctly if it doesn't detect anything on the spdif port.  And when I originally installed ubuntu my reciever was off.  When I reinstalled the packages it was on.

My surround "receiver" is actually a Logitech Z-5500 speaker set and it was turn on at all times.

---

### Post by efgevh on 2009-08-10
same here, had my dac connected during install. somewhat comforting to know that i get sound on spdif in karmic. also, the soundcard interface seems much better organized there too.

---

### Post by Maheriano on 2009-08-10
I got AC3 working in 9.04 in less than 2 minutes, it's plug and play. Are you sure your receiver isn't set to digital only? Mine has the option for analogue/digital/auto. I can post my settings for you if you want, when I get home.

---

### Post by MisterM on 2009-08-10
> **Maheriano said:**
> I got AC3 working in 9.04 in less than 2 minutes, it's plug and play. Are you sure your receiver isn't set to digital only? Mine has the option for analogue/digital/auto. I can post my settings for you if you want, when I get home.

The problem is not getting AC3 working. It's working fine on analogue output. The problem is getting S/PDIF pass-through working, so that raw digital signal is sent to the receiver.

---

### Post by Maheriano on 2009-08-10
> **MisterM said:**
> The problem is not getting AC3 working. It's working fine on analogue output. The problem is getting S/PDIF pass-through working, so that raw digital signal is sent to the receiver.

That's what I have done, it's easy. I'll take a look at my settings when I get home, I've set it up twice now in under 2 minutes each time.

Are you sure you volume is on zero? You won't get any digital sound until you bring your slider volume to zero, anything else will result in no sound.

---

### Post by MisterM on 2009-08-10
> **Maheriano said:**
> That's what I have done, it's easy. I'll take a look at my settings when I get home, I've set it up twice now in under 2 minutes each time.

Looking forward to your solution then. :)

> **Maheriano said:**
> Are you sure you volume is on zero? You won't get any digital sound until you bring your slider volume to zero, anything else will result in no sound.

Which volume do you mean? In intrepid, I never had any volume at zero and digital output worked fine.

---

### Post by Maheriano on 2009-08-10
They modified Pulse Audio immensely, I can't remember if it was in 8.1 or 9.04 but it changed a lot. Try bringing your volume to zero and see if it works, that was the trick on mine after searching for a week.

---

### Post by MisterM on 2009-08-10
> **Maheriano said:**
> They modified Pulse Audio immensely, I can't remember if it was in 8.1 or 9.04 but it changed a lot. Try bringing your volume to zero and see if it works, that was the trick on mine after searching for a week.

Which volume?

---

### Post by Maheriano on 2009-08-10
master

---

### Post by MisterM on 2009-08-10
Nope, doesn't help. :(

Tried muting as well.

---

### Post by Maheriano on 2009-08-10
Here we go, hope you appreciate this. Here are the settings I use that give me digital 5.1 AC3 and DTS from my Ubuntu machine. Keep in mind that you need a digital source like a DVD or AC3 encoded file. Songs won't play in Dolby Digital.

System - Preferences - Sound

[IMG]http://www.danmaher.com/images/pulse screenshots/1.png[/IMG]

Volume Control (sorry, doesn't need to be muted, was fixed in Pulse Audio in 9.04)

[IMG]http://www.danmaher.com/images/pulse screenshots/2.png[/IMG]

Pulse Audio Volume Control
If you right click on the stream, it'll show you which device the sound is being output to. When I installed it I had to move the stream from my Envy24 sound card (not supported) to my onboard nVidia chipset on my motherboard. So make sure this is set right for you too.

[IMG]http://www.danmaher.com/images/pulse screenshots/3.png[/IMG]

VLC settings

[IMG]http://www.danmaher.com/images/pulse screenshots/4.png[/IMG]

VLC settings

[IMG]http://www.danmaher.com/images/pulse screenshots/5.png[/IMG]

---

### Post by Bartender on 2009-08-11
Thanks for taking the time to make the screenshots.  I have an Acer 5920 laptop with a combination headphone/spdif jack.  Trying to get the spdif feed working.  Your screenshots helped!

---

### Post by MisterM on 2009-08-11
> **Maheriano said:**
> Here we go, hope you appreciate this. Here are the settings I use that give me digital 5.1 AC3 and DTS from my Ubuntu machine. Keep in mind that you need a digital source like a DVD or AC3 encoded file. Songs won't play in Dolby Digital.

Thanks for the screenshots, Maheriano. I have the exact same settings as you, but it doesn't work. One thing I noticed is that when I select S/PDIF pass-through in the movie player (VLC or smplayer), the stream doesn't show up in Pulse Audio Volume Control. However, if I disable S/PDIF, it does. I'm guessing this is normal, since the sound isn't being decoded with S/PDIF enabled.

Another thing is that under Output Devices in Pulse Audio Volume Control, there's only one device (*HDA Intel - ALC1200 Analog*). There is no digital counterpart. I don't know if this is important though, since the output selected in movie player is alsa and not pulse.

---

### Post by Maheriano on 2009-08-11
> **MisterM said:**
> Thanks for the screenshots, Maheriano. I have the exact same settings as you, but it doesn't work. One thing I noticed is that when I select S/PDIF pass-through in the movie player (VLC or smplayer), the stream doesn't show up in Pulse Audio Volume Control. However, if I disable S/PDIF, it does. I'm guessing this is normal, since the sound isn't being decoded with S/PDIF enabled.Correct.

> **MisterM said:**
> Another thing is that under Output Devices in Pulse Audio Volume Control, there's only one device (*HDA Intel - ALC1200 Analog*). There is no digital counterpart. I don't know if this is important though, since the output selected in movie player is alsa and not pulse. Negatory, your volume manager and Pulse Audio should show all audio devices installed on your machine. If it's not picking up your SPDIF out then there's something wrong. It should be listed there with the rest.

- Is it digital coaxial or fiber optical? (yellow RCA or toslink)
- onboard or sound card?
- chipset?
- enabled/disabled in BIOS?
- what kind of receiver do you have?

---

### Post by Frysboxen on 2009-08-11
This configuration works for me (let the pictures speak for them selves):

Setup:
NForce4 CK804 chipset, using spdif through coax
Logitech Z5500

Alsa-configuration:

[img]http://www.implode.se/ubuntu/alsa1.png[/img]

[img]http://www.implode.se/ubuntu/alsa2.png[/img]

[img]http://www.implode.se/ubuntu/alsa3.png[/img]

Pulseaudio configuration:
No configurations made in the volume control.
Enabled 6 channels with this guide:
[http://webupd8.blogspot.com/2009/06/enable-surround-sound-in-ubuntu-linux.html](http://webupd8.blogspot.com/2009/06/enable-surround-sound-in-ubuntu-linux.html)

except for those configurations, exactly the same configurations was made as the previous poster.

I hope it helps some people out there! :)

---

### Post by MisterM on 2009-08-11
> **Maheriano said:**
> Is it digital coaxial or fiber optical? (yellow RCA or toslink)
Coax

> **Maheriano said:**
> onboard or sound card?
Onboard ALC1200

> **Maheriano said:**
> chipset?
Intel ICH10

> **Maheriano said:**
> enabled/disabled in BIOS?
Enabled, obviously. :) (analogue works)

> **Maheriano said:**
> what kind of receiver do you have?
Logitech Z-5500

---

### Post by Maheriano on 2009-08-11
The problem is you're missing the drivers because PulseAudio is not picking up that you even have a digital output.

From [here]("http://bbs.archlinux.org/viewtopic.php?id=69658") it looks like it's not yet supported in the kernel and the only way to get it working is to either download the latest Alsa update and compile it from scratch or patch your kernel like in that link.

But your problem is definitely coming from the fact that your digital output is not even listed in your audio outputs.

---

### Post by MisterM on 2009-08-11
Maheriano, you're a god! :D

At the link you provided, I found the following solution:

**You have to add the following line to /etc/modprobe.d/alsa-base.conf**
```
options snd-hda-intel model=6stack-dig probe_mask=1
```

After adding the line and rebooting, S/PDIF started working! =D> \\:D/

Thank you very much for taking the time to search for a solution!

---

### Post by Maheriano on 2009-08-11
> **MisterM said:**
> Maheriano, you're a god! :D

At the link you provided, I found the following solution:

**You have to add the following line to /etc/modprobe.d/alsa-base.conf**
```
options snd-hda-intel model=6stack-dig probe_mask=1
```

After adding the line and rebooting, S/PDIF started working! =D> \\:D/

Thank you very much for taking the time to search for a solution!

Glad the Linux community could give the ability for a Canadian boy to help a Slovenian! :) I was there 3 years ago too, have fun with your new sound system!

---

