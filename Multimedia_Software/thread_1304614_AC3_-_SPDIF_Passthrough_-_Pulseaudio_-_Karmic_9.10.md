---
title: "AC3 - SPDIF Passthrough - Pulseaudio - Karmic 9.10"
date: 2009-10-29
forum: Multimedia Software
---

### Post by Wyv on 2009-10-29
Hello,

This isn't a request for assistance, just a tip as I didn't see much else for SPDIF passthrough and Karmic.

When I upgraded to 9.10 from 9.04 my SPDIF passthrough was no longer working.

In 9.04 I would use Pulseaudio for everything but DD or DTS audio. All sound would still go over SPDIF. I had SMPlayer set up to directly access the SPDIF hardware device for AC3 or DTS.

In 9.10 this doesn't directly work; using the cool new hardware chooser to use your hardware setup in Preferences > Sounds Pulsaudio can now output to your SPDIF without you messing with conf files. However, it seems to keep the device (SPDIF) busy and so when an app tries to access it directly it won't work.

What I have to do is to open Preference > Sounds and choose something without IEC958 SPDIF in the hardware section. Then play my DD or DTS audio with the player set to use the ALSA device directly and SPDIF passthrough.

Then, after watching the movie I have to set it back so that Pulseaudio can use the SPDIF output again.

Tip: Opening and making changes in Preferences > Sound mutes audio often, making you think stuff is broken. You'll need to unmute it in the mixer in the system tray or use gnome alsa-mixer or summat.

It would be great if Pulseaudio could handle assigning a DD stream to a SPDIF device directly.

---

### Post by lloydsmart on 2009-10-31
Thank you! This explains why I couldn't get DD or DTS soundtracks to work, I tried disabling the hdmi sound in hardware selector as you suggested, and bingo! I'm getting bitstreamed DD/DTS over HDMI from XBMC. :)

My big problem now, is that I need some way to automate this. I have a mixture of media, some of which requires DD/DTS bitstreaming, and thus requires the HDMI to be disabled in the hardware selector, and some which comes in other sound formats such as MP3, FLAC, etc. which requires the HDMI to be on and working in the hardware selector.

Is there any way to get the HDMI in the hardware selector to automatically switch depending on what you're trying to play? I don't want to have to quit and relaunch XBMC every time I want to play DD/DTS!

Thanks.

---

### Post by Wyv on 2009-11-01
None that I know of :(

If you're just using XBMC maybe it's worth looking at removing Pulseaudio.

nb: I actually quite like PA, but the inability to do anything useful with DD / DTS passthrough sucks. I wanna use the DACs in my receiver and also not have 95 cables connecting it :p

---

### Post by lloydsmart on 2009-11-01
Hmm... I guess I need to read up on what PulseAudio actually is, as XBMC isn't the only thing I use this computer for at the moment (although that was the intention when I built it, but I no longer have a laptop for other duties, so...)

What else does PA do? I need the sound to work generally in Ubuntu, such as system sounds, Youtube, VLC, etc. Plus it would be nice if it continued to work in games. All these functions currently work fine over the HDMI. Would they continue to do so if I removed PA?

If so, my next question would be: how does one go about removing PA, and could there be any other side effects?

Thanks!

---

### Post by Wyv on 2009-11-02
Pulseaudio is sound server; it takes all of the audio streams from applications, does mixing, volume control etc and then sends audio to particular sound devices.

You can remove it and just use ALSA and hardware mixing. There are guides around for removing PA and setting up an ALSA based system. ALSA is still used behind PA as it manages the sound hardware - you'd just be stripping PA off of the top of it.

I personally prefer to keep PA, but the SPDIF passthrough thing is really irritating - especially now as PA is hogging the output device.

---

### Post by lloydsmart on 2009-11-02
> **Wyv said:**
> especially now as PA is hogging the output device.

Right, this is exactly the issue causing problems, I think.

What we need is some way to have pulseaudio automatically step back and disable itself when we attempt to play an AC3 or DTS soundtrack. Does anyone have any idea how something like this could be achieved?

---

### Post by Wyv on 2009-11-02
I'm not aware of one - nothing obvious from searching for it.

The official RFE is here, not updated in 16 months: [http://www.pulseaudio.org/ticket/167]("http://www.pulseaudio.org/ticket/167")

With the increasing use of computers (and Linux) for home theatres this strikes me as core functionality.

---

### Post by lekzz on 2009-11-03
Passthrough is working for me, however playing normal (non-passthrough) audio seems to "mute" passthrough. Pressing mute and unmute makes passthrough work again.
This "mute" is also not showing in alsa-mixer, as everything is set like it should. But then again it's passthrough.

example after reboot:
open movie with passthrough - audio works
close movie
open movie with mp3 - audio works
close movie
open movie with passthrough - no audio
while movie open mute/unmute - audio works again

This happened during one of the last updates before 9.10 final, as i was running 9.10 from alpha6 and had no problems until just before the final.

---

### Post by lloydsmart on 2009-11-03
This is almost the same on my system. I'm running the 9.10 release, but I don't get passthrough by default after reboot, which I think is down to the fact that I'm using the Ubuntu system sounds, e.g. the noise that plays when you login, etc.

If I go to Preferences -> Sound, I can "turn off" sound ,which means that no normal stereo stuff plays, but passthrough works. Only problem with this is that I can't play anything with "non-passthrough" sound.

This is why I asked about some sort of automation. There must be something that can be set so that when a "passthrough" track is played, it turns off all other sound so that it works, then when a "normal" track is played, it uses PulseAudio again. I just don't know how to do it. :(

---

### Post by Wyv on 2009-11-03
I believe that's going to need something written / coded - which is beyond me :(

I'm not aware of anything that could detect the DD or DTS bitstream attempting to be passed through. I'm assuming if it were easy to do the Pulseaudio would have the ability to detect when it is given a DD / DTS stream and then pass that through unaltered to the output device.

---

### Post by sammydee on 2009-11-12
Try running your media player like this:

pasuspender $MEDIA_PLAYER_APP

This will suspend pulseaudio while the app is running and allow it full control of the sound card.

---

### Post by lloydsmart on 2009-11-12
Thanks for the tip , sammydee, but unfortunately this didn't work too well for me.

My media player app is XBMC (SVN version), and using this option just caused it to crash (freeze) when I select any video to play, bitstream or not.

Maybe I should compile a version of XBMC with pulseaudio support disabled? Or are there any other steps I should be taking to make ALSA available to the app?

Once again thanks for your help.

EDIT: Also, is there any chance we could get the "Solved" tag removed from this thread? We might get more responses that way. Thanks.

---

### Post by markbuntu on 2009-11-12
This has been discussed on the pulseaudio mailing list
> 

On Mon, 05.10.09 14:30, Dave Moore (davewantsmoore@gmail.com) wrote:
>
> > Hi Everyone.  I'm really sorry if this has been covered before, I've read
> > back through the past 6 months list history and found nothing.... and my
> OS
> > (ubuntu) and application support forums/lists are not being very helpful.
> >
> > I would like to pass digital audio completely unaltered ("bit-stream") to
> my
> > SPDIF output - Can this be done with pulseaudio?
>
> No. Not at this time. (See other mails in this thread for what is planned)
>
> If you need ac3 pass-thru then you need to bypass PA. Just make sure
> you are not using the SPDIF port for PA (use g-v-c or pavucontrol and
> make sure the sound card is notconfigured for any of the 'digital
> iec985' modes).
>
> Lennart

Message: 4
Date: Tue, 6 Oct 2009 11:56:14 -0700

You could use the device reservation utilities for this. When you have
encoded data for pass through you can PA to let go off the device. See
code in module-reserve
- P


So, there is some hint how to do it. Maybe someone could figure out this module-reserve and get back with a solution. I don't use AC-3 passthough so I cannot do it myself.

---

### Post by Wyv on 2009-11-14
> **sammydee said:**
> Try running your media player like this:

pasuspender $MEDIA_PLAYER_APP

This will suspend pulseaudio while the app is running and allow it full control of the sound card.

This works for me, thanks. Still a workaround but it is simpler than my GUI method.

---

### Post by tvcasualty on 2009-11-30
Can anyone help me out on giving pulse the boot and seting ALSA back up on 9.10?

This is a huge issue for me, and is the first time I've been let down in any way from a new Ubuntu release.  Frankly, I'm not sure how they let this slide through.  Happy to fix on my own, but last time I tried I had to reformat.  Next try will have me put 9.04 back on...

---

### Post by whittaker007 on 2009-12-05
I can't tell you exactly all the steps I have been through to get to where I am since this issue has caused me to try a lot of things that have not worked. However what I have done is install a few ALSA packages into Karmic, so I have both ALSA and Pulse at the same time. Using the Pulse volume controls I set Pulse to output to normal stereo out (so not using iec985). Even though Pulse is set to output to normal stereo, I still hear the standard system audio in stereo through the optical out.

From there I got AC3 passthrough working in both XBMC and VLC by assigning them each to use the iec985 output. This works pretty well but it's not perfect. Here are the issues I still have:

[LIST]
[*]System sound is muted and volume set to zero every time I restart. This is a real pain since I have to use the gui to set the volume which is a big usability problem for an HTPC and I'm a long way off getting this thing to work with a remote. Setting the volume, storing the preferences and restoring them as a startup item has not worked.
[*]Occasional audio dropouts: sometimes I lose stereo sound but can still get passthrough. Sometimes it's the other way around. Sometimes it's both. The only cure is a restart.
[*]I can only get VNC to give me a remote desktop style duplication of the currently logged in user - the same screen I see on my TV. Whenever I try to set it up to start a new user session on a virtual display I can't start gnome, get a login window or anything - just an empty black & white X window. OK this has nothing to do with sound but it's driving me nuts!
[/LIST]

---

### Post by adix87 on 2010-01-12
I had this problem. Here is what i did.
First, sorry for my bad english.

The problem was that i did not get surround sound from my Toslink optical cable. Only stereo. My soundcard is Xplosion 7.1 something..
Well first i didn't get sound at all but then i enabled IEC958 output from ALSA mixer that i installed from ubuntu software center.
Now i hear stereo sound.

Now for 5.1 passthrough.
Before you remove anything and mess up everything try this. Launch VLC, go to options -> Audio. Enable"Use S/PDIF when available" **AND** select Output device. "Default" is **NOT** okay here. You need to choose ALSA audio output. Default is something else i don't know. This will probably work for other players if they let you choose the output. But for example the normal "movie player" doesn't work with DTS or DD for me.
This is how i got it working.. other stuff i did was:
I removed the pulseaudio stuff from my system by launching "Ubuntu Software Center" and searched for pulseaudio and removed all packages i saw. 
This step might not be necessary.
And in GNOME ALSA Mixer i have enabled IEC958 5V, IEC958 Copyright and IEC958 Output.
And if you go to System -> Pref -> Sound -> Hardware tab . It is okay that it says "Digital output Stereo". VLC will still play in 5.1 DTS or DD because its passtrough, and youtube clips will play in stereo but also through optical cable.

If this didn't work, reeboot and try in VLC again. 


I hope i helped atleast someone.[]("http://en.wikipedia.org/wiki/Necessary")

---

### Post by whittaker007 on 2010-01-12
I managed to get it working without removing Pulse. Here is what I did:

[LIST=1]
[*]Install the Alsa libraries
[*]Open the Pulse default Sound Preferences
[*]Click the Hardware tab
[*]Choose Analog Stereo Duplex profile
[*]In every application that supports hardware configuration, set sound output to IEC985 or similar
[/LIST]

Of course your hardware may differ. The surprising thing for me is that if I select any other non-digital profile other than Analog Stereo Duplex it doesn't work. But I now have automatic 5.1 and stereo out working in VLC and XBMC. I haven't spent enough time with MythTV to get that working yet, and I only get stereo from the other media players, but VLC, XBMC and MythTV are the only ones I care about.

My system volume seems to be stable now and not muting on restart, however I also recently switched to Linux Mint (built on Karmic) so I don't know whether that made a difference in that case. I also fixed my VNC problem, though that's OT.

---

### Post by LucidParody on 2010-01-19
Whittaker, what are the alsa libraries?

---

### Post by whittaker007 on 2010-01-19
> **LucidParody said:**
> Whittaker, what are the alsa libraries?

Open a terminal window and type:

sudo apt-get install alsa

---

### Post by LucidParody on 2010-01-20
> **whittaker007 said:**
> I managed to get it working without removing Pulse. Here is what I did:

[LIST=1]
[*]Install the Alsa libraries
[*]Open the Pulse default Sound Preferences
[*]Click the Hardware tab
[*]Choose Analog Stereo Duplex profile
[*]In every application that supports hardware configuration, set sound output to IEC985 or similar
[/LIST]

Of course your hardware may differ. The surprising thing for me is that if I select any other non-digital profile other than Analog Stereo Duplex it doesn't work. But I now have automatic 5.1 and stereo out working in VLC and XBMC. I haven't spent enough time with MythTV to get that working yet, and I only get stereo from the other media players, but VLC, XBMC and MythTV are the only ones I care about.

My system volume seems to be stable now and not muting on restart, however I also recently switched to Linux Mint (built on Karmic) so I don't know whether that made a difference in that case. I also fixed my VNC problem, though that's OT.

Thanks -- this worked perfectly.  After three different installs of Ubuntu/XBMC, and over 20+ hours, who would have guessed the solution would be so simple?  :)

---

### Post by excessuk on 2010-01-23
I've been trying to sort this out for weeks now. Tried installing alsa, removing pulse, re-adding it, touching every audio config file under the sun without any luck, and yet this simple solution worked straight away. 
I CAN'T THANK YOU GUYS ENOUGH!! :D:D:D:D:D:D:D:D

---

### Post by 8301 on 2010-03-12
HAHA

It worked!!!!

Who could believed that

---

### Post by whittaker007 on 2010-03-13
I'm glad my solution worked for you guys!

Unfortunately some recent update has broken it again for me, along with a few other things. Now I can get 5.1 out of VLC but I'm stuck with stereo on XBMC. No combination of output hardware selections in system and XBMC seem to work - including manually typing in the audio hardware to output to in XBMC (hw:0,1).

I's been over 4 months since I set the machine up and despite spending nearly half of every weekend fiddling with it I still don't have a stable user-friendly way to play back audio and video. I really want this to work but for the amount of time I've spent it probably would have been worth buying Windows 7 media center... I can't stand Windows, but it does work most of the time now.

---

### Post by whittaker007 on 2010-03-13
Sod's law - after having this problem for weeks, the moment I feel it necessary to complain about it in a forum post, it fixes itself through another update. Oh well...!

---

### Post by krul on 2010-03-21
> **lekzz said:**
> Passthrough is working for me, however playing normal (non-passthrough) audio seems to "mute" passthrough. Pressing mute and unmute makes passthrough work again.
This "mute" is also not showing in alsa-mixer, as everything is set like it should. But then again it's passthrough.

example after reboot:
open movie with passthrough - audio works
close movie
open movie with mp3 - audio works
close movie
open movie with passthrough - no audio
while movie open mute/unmute - audio works again

This happened during one of the last updates before 9.10 final, as i was running 9.10 from alpha6 and had no problems until just before the final.

I am experience this behaviour too! Very annoying, pulseaudio is in 9.10 still very buggy :(

---

### Post by kebirek on 2010-04-03
> **whittaker007 said:**
> I managed to get it working without removing Pulse. Here is what I did:

[LIST=1]
[*]Install the Alsa libraries
[*]Open the Pulse default Sound Preferences
[*]Click the Hardware tab
[*]Choose Analog Stereo Duplex profile
[*]In every application that supports hardware configuration, set sound output to IEC985 or similar
[/LIST]


This worked! Thank you!!

---

### Post by NiksaVel on 2010-08-28
Hey guys, just thought to share my experience on my recent HTPC install with LinuxMint 9 - Lucid based, 64 bit version.

I did exactly as described here...  although I didn't need to install alsa-tools  it seemed to already be installed (maybe a dependancy of some of my software?)...

Set PA to audio stereo duplex (left it alone as default) and unmuted and turned volume on on everything in alsamixer.

This got me both stereo and passthrough in VLC (set to use spdif and alsa output). Desktop sounds work.

Next installed XBMC - audio default, passthrough iec958 - works.
Latest Boxee install - audio default, passthrough custom: iec958
- everything started working when I turned off menu sounds (which is strange because they work normal in XBMC).

Now the problems...  sometimes when switching rapidly between passthrough and stereo encoded videos, stereo seems to get muted. 
The workaround is to drop to another terminal (i.e. ctrl+alt+f7) and than back (ctrl+alt+f8) and for some reason- voila the sound is restored instantly (the coursor gets stuck on screen and it also disappears with a alt+tab twice).

1.
the dropouts seem to be related to rapid switching (i.e. sub 10 sec), but I'm not sure yet.

2.
found a possible workaround on XBMC wiki, but it doesn't really work for me - I get stable stereo, but no passthrough at all... comments anyone?
[http://wiki.xbmc.org/index.php?title=XBMC_for_Linux_specific_FAQ#S.2FPDIF_out_for_both_analog_and_digital_audio]("http://wiki.xbmc.org/index.php?title=XBMC_for_Linux_specific_FAQ#S.2FPDIF_out_for_both_analog_and_digital_audio")

3.
can anyone help me get audio to work stable?

---

### Post by Meneer Jansen on 2010-10-10
> **NiksaVel said:**
> 
can anyone help me get audio to work stable?


Forget the 1,000 workarounds on the 'net. The only thing that worked for me is to give PulseAudio the boot (can somebody hack their site, server and office to let them disappear from the Galaxy, please?). See this Ubuntuforum thread (should be sticky): [http://art.ubuntuforums.org/showthread.php?t=1313253](http://art.ubuntuforums.org/showthread.php?t=1313253)

Summary:
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer
```
Reboot.

**Notes:**
-run gstreamer-properties in terminal to set defaults to alsa (the old system/preferences/sound in jaunty)
-remove gstreamer0.10-pulseaudio to get sound in totem
-gnome-alsamixer is for changing the volume, not an applet but better that nothing

---

### Post by lipemat on 2011-02-23
> **adix87 said:**
> I had this problem. Here is what i did.
First, sorry for my bad english.

The problem was that i did not get surround sound from my Toslink optical cable. Only stereo. My soundcard is Xplosion 7.1 something..
Well first i didn't get sound at all but then i enabled IEC958 output from ALSA mixer that i installed from ubuntu software center.
Now i hear stereo sound.

Now for 5.1 passthrough.
Before you remove anything and mess up everything try this. Launch VLC, go to options -> Audio. Enable"Use S/PDIF when available" **AND** select Output device. "Default" is **NOT** okay here. You need to choose ALSA audio output. Default is something else i don't know. This will probably work for other players if they let you choose the output. But for example the normal "movie player" doesn't work with DTS or DD for me.
This is how i got it working.. other stuff i did was:
I removed the pulseaudio stuff from my system by launching "Ubuntu Software Center" and searched for pulseaudio and removed all packages i saw. 
This step might not be necessary.
And in GNOME ALSA Mixer i have enabled IEC958 5V, IEC958 Copyright and IEC958 Output.
And if you go to System -> Pref -> Sound -> Hardware tab . It is okay that it says "Digital output Stereo". VLC will still play in 5.1 DTS or DD because its passtrough, and youtube clips will play in stereo but also through optical cable.

If this didn't work, reeboot and try in VLC again. 


I hope i helped atleast someone.

Thank You so Much. This solved my spdif problem that I have all but given up on. The key was setting the output device. I will be quoting this solution on my forum as well. [http://lipeimagination.info/forum](http://lipeimagination.info/forum)

---

