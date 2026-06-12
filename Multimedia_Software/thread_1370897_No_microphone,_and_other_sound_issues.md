---
title: "No microphone, and other sound issues"
date: 2010-01-02
forum: Multimedia Software
---

### Post by philippe75 on 2010-01-02
Hi,

I tried hard this afternoon to make my microphone work - with no luck: I think I have tested all the hints I could find over different forums, at some point I even destroyed the sound card, but the script AlsaUpgrade restored the sound.

So now, sound works great, earphones are also working but the laptop speakers stay up if I use earphones (!!!) and microphone just doesn't work (but it did a little bit this afternoon, I can't really remember how I did that).

I would be happy to have some more hints if any, the no mic issue is quite bad, skype won't work and so the computer is usable the way I way I'd like.

By the way, my laptop is a toshiba A215-S4747.
My sound card: 
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I add this at the end of alsa-base.conf, as suggested by someone on the forum:
```

options snd-hda-intel model=toshiba

```Thanks a lot!!

Phil

---

### Post by philippe75 on 2010-01-03
hum ok, this morning I tried a little bit more...

and I have noticed I could choose between 2 microphones in the sound preferences / input...
so I chose the second one, and here is it, everything works well!:)

I really don't understand why this is working, why I have 2 microphones...
the input sound is low, so I tried to play with alsamixer: if I increase the input level of the microphone (like this is often suggested) it is worst, the recording has a very poor quality with strange noises in the background.
Here again, everything is doubled: I see in alsamixer 2 front mics, 2 line in boost's and 2 mic boost's.:confused:

any idea how I can see what is really installed on my computer? some commands that could explain this?

thnaks a lot!!

---

### Post by mn_voyageur on 2010-01-03
I have struggled with PusleAudio since I upgraded.  Everything works except my mic in Skype.  

The mic, Philips SPC 900NC PC Camera, shows on the input. Is selected under Sound Preferences > Input.  Input Level varies appropriately.  

[INDENT]Cannot record using Sound Recorder.  
Camera works fine with Cheese.[/INDENT]

This would indicate to me that the hardware is identified and should be working.

Any help would be appreciated.

Thanks,
MN

---

### Post by chaanakya_chiraag on 2010-01-03
@philippe75: The reason is that one is the line-in port on your laptop and the other is the internal mike.  Took me a while to figure that one out too :D

@mn_voyageur: Which Ubuntu version are you using?  Karmic is much better with PulseAudio.  Are you using the latest (beta) Skype?  That one actually supports PulseAudio!!! :D  The link (for Ubuntu 8.10 and above):
[http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)
That will take you right to the download (a box will popup asking you to save the file).  Please post if this doesn't work or if you still have problems.

---

### Post by chaanakya_chiraag on 2010-01-03
Edit: looked at your signature.  Use this link instead:[URL="http://www.skype.com/go/getskype-linux-beta-ubuntu-64"]
http://www.skype.com/go/getskype-linux-beta-ubuntu-64[/URL]

---

### Post by mn_voyageur on 2010-01-03
chaanakya_chiraag:

I have downloaded and installed the file.

My Skype worked until I upgraded to Karmic.  Once I upgraded, I lost my ability to use Skype.

The system knows the hardware is there.  I just can't use the mic.

MN

---

### Post by GalloGlas on 2010-01-03
> **mn_voyageur said:**
> chaanakya_chiraag:

I have downloaded and installed the file.

My Skype worked until I upgraded to Karmic.  Once I upgraded, I lost my ability to use Skype.

The system knows the hardware is there.  I just can't use the mic.

MN


Have you tried running alsamixer from your terminal?  Make sure your inputs aren't muted.

---

### Post by chaanakya_chiraag on 2010-01-03
Hmmm...That's really weird because I'm also using Skype and it works.  Try the following:
1) Install PulseAudio Manager and all that good stuff:
```
sudo aptitude install paman pulseaudio-utils paprefs pavumeter pavucontrol
```
2) Go to Applications->Sound and Video -> Pulse Audio Device Chooser
3) Click on the icon that appears in the system tray and click Preferences...
4) Select "Start Applet on session login" and close the window
5) Click again on the PulseAudio icon and select Volume Control
6) Click on the "Input Devices" tab and try each and every setting.
Please post back with your results using this technique of "trial and error" :)

---

### Post by mn_voyageur on 2010-01-03
I think it is not muted.

---

### Post by philippe75 on 2010-01-03
For what it's worth, I think actually that all my mics I see are muted in alsamixer.:confused::confused:
(see the screenshot)

But I play in the sound preference gui, and there I actually enable the mic (but the sound is crapy, and if I change some parameters in alsamixer it is even worse).

Is there any other gui we can use to modify and test these preferences?

---

### Post by mn_voyageur on 2010-01-03
> **chaanakya_chiraag said:**
> Hmmm...That's really weird because I'm also using Skype and it works.  Try the following:
1) Install PulseAudio Manager and all that good stuff:
```
sudo aptitude install paman pulseaudio-utils paprefs pavumeter pavucontrol
```
2) Go to Applications->Sound and Video -> Pulse Audio Device Chooser
3) Click on the icon that appears in the system tray and click Preferences...
4) Select "Start Applet on session login" and close the window
5) Click again on the PulseAudio icon and select Volume Control
6) Click on the "Input Devices" tab and try each and every setting.
Please post back with your results using this technique of "trial and error" :)

The mic is listed and the meter does respond as expected.  

I checked Sound Recorder and still cannot record.
Skype, when trying to make a test call, indicates "Problem with Audio Capture"

MN

---

### Post by chaanakya_chiraag on 2010-01-03
What's selected in Skype for the input?

---

### Post by mn_voyageur on 2010-01-04
PulseAudio is my only option.

MN

---

### Post by GalloGlas on 2010-01-04
> **philippe75 said:**
> For what it's worth, I think actually that all my mics I see are muted in alsamixer.:confused::confused:
(see the screenshot)

But I play in the sound preference gui, and there I actually enable the mic (but the sound is crapy, and if I change some parameters in alsamixer it is even worse).

Is there any other gui we can use to modify and test these preferences?


There is K-mix.  I use that even tho I'm not KDE.   But it's pretty much the same thing as alsamixer just prettier to look at.  

You said your having sound quality issues?  Run alsamixer again and adjust the volumes down.  I noticed you have some of your volume levels piping all the way up.  Ubuntu doesn't like that in my experience.  Try and keep the levels out of the Red if you can.  If you absolutely need to turn it up that high keep it away from the top.  Bring those volumes down and turn your physical speakers up. 

If all else fails, do what I did.  Get a cheap-o Logitech USB headphone & mic headset.  Its simple enough in design you can use it for skype but still retain your big soundcard for music/movies.

---

### Post by philippe75 on 2010-01-04
> **GalloGlas said:**
> There is K-mix.  I use that even tho I'm not KDE.   But it's pretty much the same thing as alsamixer just prettier to look at.  

You said your having sound quality issues?  Run alsamixer again and adjust the volumes down.  I noticed you have some of your volume levels piping all the way up.  Ubuntu doesn't like that in my experience.  Try and keep the levels out of the Red if you can.  If you absolutely need to turn it up that high keep it away from the top.  Bring those volumes down and turn your physical speakers up. 

If all else fails, do what I did.  Get a cheap-o Logitech USB headphone & mic headset.  Its simple enough in design you can use it for skype but still retain your big soundcard for music/movies.

Thanks for the advise on K-mix, I will have a look at this.
For the sound quality, I have already noticed that if I put all the levels up in alsamixer, the mic is just recording crap (speakers are ok)... so I'll try to fine tune and find an intermediate position - it is working so so now, but far better than nothing!

Thanks!

---

### Post by chirlugste on 2010-01-04
thank you very muck!

---

