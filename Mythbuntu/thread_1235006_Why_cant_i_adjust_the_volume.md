---
title: "Why cant i adjust the volume?"
date: 2009-08-08
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-08-08
For some reason I am not able to change the volume of any music that plays on my myth setup.  I am using audio over hdmi and am wondering if this is the reason? 

I can see the volume slider going up and down and have tried setting myth to adjust both pcm and master volumes with no change.  

Anyone had any success adjusting hdmi audio volumes?  

Can anyone point me in the direction of a solution?

---

### Post by geekyhawkes on 2009-08-11
Anyone any ideas on what might be going here, or how i could solve it?

---

### Post by geekyhawkes on 2009-08-15
This is still an on going issue for me, has anyone had success in adjusting volume of music over HDMI?  IS there something obvious (or not) i might have missed?

---

### Post by Riaku on 2009-08-15
what about your frontend?

---

### Post by geekyhawkes on 2009-08-15
sorry i probably didnt make it clear this is on a combined front/back end system.  I can see the volume slider going up and down in the music gui but the volume is unchanged.

It appears it is not unique to the music section of my myth install.  I am not able to change the volume of dvds or livetv either.

I have tried changing from PCM/master volume but with no difference.

---

### Post by capcadetjc on 2009-08-15
> **geekyhawkes said:**
> sorry i probably didnt make it clear this is on a combined front/back end system.  I can see the volume slider going up and down in the music gui but the volume is unchanged.

It appears it is not unique to the music section of my myth install.  I am not able to change the volume of dvds or livetv either.

I have tried changing from PCM/master volume but with no difference.

Make sure you change your device in Utilities/Setup> >Setup> General. Then hit next till you get to the Audio Page. My Audio output device is ALSA:default. So I had to set the Mixer Device to ALSA:default.

Make sure you have the Mixer Device set. I had the same problem and that fixed it.

---

### Post by jyavenard on 2009-08-15
You can not adjust the volume from mythtv if using a digital output.
You do that on the amplifier or your TV..

If you want to be able to change the volume on mythtv instead, you will need to apply the following mythv patches:

ticket 5900
[http://svn.mythtv.org/trac/ticket/5900](http://svn.mythtv.org/trac/ticket/5900)

and ticket 6279
[http://svn.mythtv.org/trac/ticket/6279](http://svn.mythtv.org/trac/ticket/6279)

There will be a slight loss in audio quality as mythtv needs to decode the AC3 signal, apply volume change, then re-encode the AC3 signal to output over digital.

---

### Post by geekyhawkes on 2009-08-17
Thanks for the reply.  Would the loss of ac3 audio quality be apparnt even though i dont have an ac3 amp at the moment?  Im just trying to bin my tv remote and currently i only use it for volume control.

---

### Post by xinix on 2009-08-20
I'm no audiophile, but I don't think you would notice much of a difference.  It sounds like your audio is coming out of the tv which is most likely good old fashioned stereo.  AC3 is nice if you have the extra speakers.  Another option, one that I used for a long time, would be to use your tv remote to control mythtv and just use that remote.  This of course depends on the remotes capabilities.  Mine had the option to use it as a DVD remote too, so I programmed those buttons into lirc and stopped using the streamzap remote.

---

### Post by geekyhawkes on 2009-08-20
Thanks, it appears these 2 ticket items have made it into the last update of myth.  Strangly they still didnt let me change the volume of the audio but i will look a bit more closly at the weekend.  

My TV is just stero so to be honest its good news that i wont hear much differnce.

THanks

---

