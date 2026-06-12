---
title: "AC3 SPDIF Passthrough - I don't think it works for any setup"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by Pinnocchio on 2007-10-20
Having Googled extensively and posted messages (including to the ALSA mailing list) I have come to the conclusion that nobody has AC3 passthrough and normal sound working on their machines via SPDIF and under ALSA at the same time.

Can anyone tell me with certainty (please no I've heard this guys setup works - it has to work on your machine so we can then test your setup against other setups) that they have AC3 and Normal sound working via SPDIF under ALSA.

If anyone can I'll be pretty amazed (and probably have some follow up questions!!).

---

### Post by ariel on 2007-10-20
Hi, I just installed gutsy final and while I have the SPDIF output working, it sounds different from what I had with feisty; it sounds metallic. Also I notice that now I can control the spdif output volume from within ubuntu, something i couldn't do before. 

So I suspect that before, i had passthru, and now I don't have it, and I now have mediocre sound quality from spdif.

How can you ensure that spdif passthru is at least activated? I'm a bit lost with so many possible options in the alsa mixer.

thanks!

---

### Post by Pinnocchio on 2007-10-21
bump

Anyone?

---

### Post by iggee85 on 2007-11-09
I'm using SPDIF optical out on an onboard Realtek ALC883 and I have both SPDIF and speaker sound working under Gutsy. It took a lot of googling and scanning ubuntuforums though. I had to compile alsa from source in order to unmute SPDIF as well as normal sound. And I had to get SMPlayer to output AC3-Passthrough.

AC3-Passthrough won't work on any programs that use gstreamer. So that means watching DVDs using totem-gstreamer won't give you AC3-Passthrough. You'll have to use an alternative like totem-xine (Haven't tried it). There's some kind of design problem with gstreamer where it decodes AC3 into stereo before outputting to SPDIF.

---

### Post by ariel on 2007-11-29
> **iggee85 said:**
> I'm using SPDIF optical out on an onboard Realtek ALC883 and I have both SPDIF and speaker sound working under Gutsy. It took a lot of googling and scanning ubuntuforums though. I had to compile alsa from source in order to unmute SPDIF as well as normal sound. And I had to get SMPlayer to output AC3-Passthrough.

AC3-Passthrough won't work on any programs that use gstreamer. So that means watching DVDs using totem-gstreamer won't give you AC3-Passthrough. You'll have to use an alternative like totem-xine (Haven't tried it). There's some kind of design problem with gstreamer where it decodes AC3 into stereo before outputting to SPDIF.

Which version of ALSA did you compile?

---

### Post by flyingbrass on 2007-11-29
In Gutsy I just set up a Turtle Beach Riviera along with my new Logitech Z-5500 speakers.  I'm still having some issues getting 5.1 through analog, but an optical digital connection works great.

With this card all I needed to do was unmute the last IEC958 option (IEC958 Output)  in alsamixer.  The first (IEC958 5V) was already unmuted.  Press m to toggle mute.

Mplayer is passing AC3 through with this:

gmplayer -ac hwdts,hwac3,  movie.avi

Note the trailing comma.  That allows other codecs to be used if the ones specified aren't right (so non-Dolby stuff will play in stereo).  To avoid having to type that every time I put this in ~/.mplayer/config:

ac="hwdts,hwac3,"

Totem's AC3 passthrough option under its audio preferences isn't working.  Apparently an [almost 2 year old bug](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/28177) hasn't been fixed.

---

### Post by iggee85 on 2007-11-29
> **ariel said:**
> Which version of ALSA did you compile?

ALSA 1.0.15

---

### Post by Radon on 2007-11-29
Thanks for the info iggee85!  This might be what I'm looking for.

BTW, it doesn't matter whether it is digital or optical output right?

---

### Post by iggee85 on 2007-11-30
> **Radon said:**
> Thanks for the info iggee85!  This might be what I'm looking for.

BTW, it doesn't matter whether it is digital or optical output right?

It shouldn't matter, but mine is optical out only FYI.

---

### Post by kioftes on 2007-12-02
[http://gentoo-wiki.com/HOWTO_Dolby_Digital_Out_(AC3,_SPDIF](http://gentoo-wiki.com/HOWTO_Dolby_Digital_Out_(AC3,_SPDIF))

Worked fine for me! I am using spdif on a laptop with one of these mini optcal/stereo integrated outputs. When optical cable in, i have digital output, when audio cable in, i have normal, nondigital, output.I cant test both outputs together however...

---

### Post by PaulRSte on 2007-12-03
Hi, I have an ASUS M2NPV-VM motherboard in my HTPC running 64 bit Ubuntu, recently upgraded to Gutsy.  I just found a place that sells the S/PDIF output module for this which I have now installed and connected to my receiver via coax.

As a Linux newbie I was not impressed with the amount of work that seemed to be required to get this working.  I looked at mythtv first of all and this was already saying that sound output was via ALSA and when I checked the AC3 and DTS pass through option was set to "default" and had "IEC958" as an alternative.  

I reasoned that if this is already saying that it is using ALSA then it must be installed so I checked in aptitude and there it was at 1.0.14.  Whilst there, I got aptitude to install the gui option for this and once installed, all it took to get it working was to un-mute the IEC958.  The sound quality is great, much clearer than the analogue output.  I've not been able to check either AC3 or DTS yet as everything but everything complains about the codecs.

I hope it's good news to someone that maybe you don't have to compile ALSA to get s/pdif working.  Just need to find out which codecs are required. 
:)

---

### Post by miceagol on 2008-01-13
> **flyingbrass said:**
> 
Totem's AC3 passthrough option under its audio preferences isn't working.  Apparently an [almost 2 year old bug](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/28177) hasn't been fixed.

AC3 Passthrough is possible with Totem, but you must use totem-xine. Close Totem, and edit the configuration file manually:
```

gedit ./gnome2/Totem/xine_config

```
Remove the comment # from the following line
```

# device used for 5.1-channel output
# string, default: iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2
audio.device.alsa_passthrough_device:iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2

```
and replace "iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2" with your digital device name. The alias for my digital device is "plug:spdif". Remove # also from the line
```

# speaker arrangement
# { Mono 1.0  Stereo 2.0  Headphones 2.0  Stereo 2.1  Surround 3.0  Surround 4.0  Surround 4.1  Surround 5.0  Surround 5.1  Surround 6.0  Surround 6.1  Surround 7.1  Pass Through }, default: 1
audio.output.speaker_arrangement:Pass Through

```
and replace whatever is behind the colon with "Pass Through".

Passthrough should now work. If not, you might have entered the wrong device name.

EDIT: When it comes to VLC and Passthrough, I'm clueless. Enabling S/PDIF in the config file gives no sound output.

---

### Post by fno on 2008-01-13
There's a bug fixed in VLC 0.8.6d that enables S/PDIF passthrough. 
"* Linux: Fixed S/PDIF passthrough with ALSA"
[http://forum.videolan.org/viewtopic.php?f=13&t=42599](http://forum.videolan.org/viewtopic.php?f=13&t=42599)

---

### Post by miceagol on 2008-01-14
> **fno said:**
> There's a bug fixed in VLC 0.8.6d that enables S/PDIF passthrough. 
"* Linux: Fixed S/PDIF passthrough with ALSA"
[http://forum.videolan.org/viewtopic.php?f=13&t=42599](http://forum.videolan.org/viewtopic.php?f=13&t=42599)

Ah, good to hear. I'll test it later on. :)

---

### Post by yct on 2008-02-09
I'm using Feisty 64-bit, and:

1. current VLC package has S/PDIF broken

2. latest VLC sources from SVN fail to build on 64-bit

3. VLC 0.8.6d (rebuilt from Hoary source package) has S/PDIF fixed, but the sound mutes for 1 second once a while (every 1 to 5 min)

4. Finally got SPDIF working 100% by using Xfmedia player (universe repository), setting it's output to pass-through.

5. Seems to me that VLC is not the best anymore.

---

