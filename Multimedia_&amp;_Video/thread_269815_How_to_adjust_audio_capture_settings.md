---
title: "How to adjust audio capture settings?"
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by liquilife on 2006-10-02
When I select "Sound Recorder" under the Applications > Sound & Video menu I get the following error:
> Your audio capture settings are incorrect. Please correct them in the multimedia settings
However, I have no idea on exactly how to fix this nor how to even locate my multimedia settings.

I use an external USB soundcard through my JVC stereo which works great throughout everything else but I am guessing that my internal sound card needs to be functioning correctly to use the Sound Recorder? My internal sound card is a AC'97. I followed the instructions from the sticky "[Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449")" and added
```
options snd-intel8x0 ac97_quirk=3
```

My ultimate goal here is to record skype conversations (one step closer to leaving windows) but before I even attempt that I stumbled on this issue which I really want to resolve.

Here is the output of my playback devices:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [USB Audio DAC   ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 3: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Any ideas on how I can get my sound recorder working?

---

### Post by liquilife on 2006-10-03
Thought I would bump this. Any ideas on how to get my sound recorder working and fix my multimedia settings??

---

### Post by warjowuch on 2006-10-03
have you tried to double click on the loudspeaker-icon next to your clock? This has a set of sliders and checkboxes and other settings, maybe this can help...

This is the first first that comes to my mind. Good luck!

---

### Post by liquilife on 2006-10-03
I did check and it just allowed me to adjust the volumes which, unfortunately, did not solve my issue. Thanks for the tip though, never used that feature yet. :D

Any other ideas on how I can adjust my multimedia settings per the sound recorders error and its suggestion?

---

### Post by warjowuch on 2006-10-04
Well, if you go back to that same settings-panel: take a good look in the menu's. In file, you'll see an entry in which you can switch the device it uses.
THe sliders itself also have the possibility to mute or toggle capture (these are different!)

---

### Post by liquilife on 2006-10-04
Thanks again for the responce. your reply, while did not directly solve the problem, prompted me to go to System > Preferences > Sound and change my default sound device to my logitech headset. Once I did that then the sound recorder fired right up.

I'm still having issues running a skype conversation and the sound recorder at the same time. If the sound recorder is running I get the "Problem with sound device" in Skype. If I have skype running and try to run the sound recorder I get the "problem with your multimedia" error message from the sound recorder. Hmmmm

---

### Post by warjowuch on 2006-10-04
Glad I could be at help.

Oh, now I recognize your problem. It is true that skype is a bit arrogant/dominant in its use of the soundcard. When I run Skype, I can't play sound with streaming video from the internet at the same time. This is a bug in Skype as far as I know. I don't know a solution for this, this might be quite technical stuff, but I thought it's a Skype-problem. A friend of mine running gentoo (a really very skilled linux-user) has the same problem with skype, yet unsolved. For me, this says something :-)

edit: a new development is Jabbin, a jabber-based, open source VOIP client. Maybe, if we turn over our friends... :-)

---

### Post by liquilife on 2006-10-04
Haha, my friends would hate me if I tried converting them to yet another voip client :) First it was convincing everyone to get Google Talk, then MSN Live, then Skype. If I now tell them to go with a whole new voip client they'll abandon me for sure :D

I wonder how this guy got it to work:
[http://porpoisehead.net/hi/?q=node/23]("http://porpoisehead.net/hi/?q=node/23")

---

### Post by warjowuch on 2006-10-04
Wow, you converted your friends past so many clients for voip? :-) Whoops.

Well, this guy you talked about seems to know exactly what he was doing. He explains it very well. Now let's wait until skype-linux goes to version 1.3+!

Good luck until that very moment :-)

---

### Post by liquilife on 2006-10-04
Skype for linux is actually out for 1.3 beta. This is the version I assume he was referencing. Actually, 1.3 beta is much much better then the current stable release.

---

### Post by polywell on 2008-05-09
I was having the same problem [Your audio capture settings are incorrect. Please correct them in the multimedia settings] After installing multiple players, there are too many ways to adjust sound.
I found a double slider in 2 diferent setings tools under the [recording tab]. They say Capture at the top and at the bottom are 2 icons, the speaker and the mic. UNDER RECORDING U DONT WANT YOUR SPEAKER TO CAPTURE THE SOUND. Anyway I put a check/mute/deactivate over the speaker icon. That got me back in the sound arena.

---

### Post by wolterh on 2008-05-25
Hi. Yesterday i had your same problem, but I could fix (at least the recording issue) by selecting OSS as the sound recorder in Preferences > Sound , under the system menu.

Then, I could open the sound recorder and even record audio. When I'm in skype I can't call anybody because now it says problem with audio playback. I guess that know my ALSA is all screwed up. I'm trying to fix it right now.

---

