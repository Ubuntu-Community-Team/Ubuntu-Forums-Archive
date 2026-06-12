---
title: "Ubuntu Hardy 8.04 max sound volume too low"
date: 2008-05-18
forum: Multimedia Software
---

### Post by madiyaan on 2008-05-18
Hello:

I am running Ubuntu 8.04 on my M1530 laptop. The laptop boots both vista and ubuntu 8.04. The maximum volume in vista is much louder than the maximum volume in ubuntu. 

How can I increase the maximum volume in ubuntu significantly to match it up with the maximum volume in vista?

I am running Gnome, if that matters.

Regards,

---

### Post by empthollow on 2008-05-18
double click on the volume control at the top right of the screen.  Make sure your PCM volume is turned up as well as the master.

---

### Post by madiyaan on 2008-05-20
> **empthollow said:**
> double click on the volume control at the top right of the screen.  Make sure your PCM volume is turned up as well as the master.


Hello:

I did this already. PCM is maxed out as are "Master" and "Front" and still the volume is too low.

Any other knob that I have to adjust? Does anyone have any other suggestions?

Regards,

---

### Post by balserodeluxe on 2008-05-20
I am experiencing the same problem. This is a Clean Hardy Heron install. At first it did not recognize the on-board sound card and I had to force it.

Volume is so low that I have to crank my stereo to 1/2 volume to have an appropriate listening volume. Sad part is that HD and other noises come through when music is not on.

---

### Post by bishboria on 2008-05-24
> **empthollow said:**
> double click on the volume control at the top right of the screen.  Make sure your PCM volume is turned up as well as the master.

I had the low volume problem too, can't believe I didn't think of double clicking the bloody volume icon!  Turns out it the "front" volume slider was between .5 and .75 of the way up. Now it's cranked all the way to Eleven :)

---

### Post by justleen on 2008-05-26
> **empthollow said:**
> double click on the volume control at the top right of the screen.  Make sure your PCM volume is turned up as well as the master.



*bangs head against wall*

thanks a bunch!
(all my line-outs are being used default in hardy.. I needed to turn up the "front" one to get my volume up... duh!)

---

### Post by acidsolution on 2008-06-06
i had same problem and i installed 
```

sudo apt-get install alsamixer

```

and than 
```

sudo apt-get install alsamixergui

```
and increase tha sound to maximum from alsamixer gui in 
Applications-->Sound & Videos ->Alsamixergui
this must help [:)]

---

### Post by Yarbo on 2008-06-06
I was able to fix this problem. I had to download the gnome-alsamixer.  Once this was installed, I simply raised the volume on the one labeled "SIDE" and all of a sudden my maximum volume was boosted significantly.  Fixing the volume problem :)

---

### Post by sankz on 2008-06-16
> **madiyaan said:**
> Hello:

I am running Ubuntu 8.04 on my M1530 laptop. The laptop boots both vista and ubuntu 8.04. The maximum volume in vista is much louder than the maximum volume in ubuntu. 

How can I increase the maximum volume in ubuntu significantly to match it up with the maximum volume in vista?

Regards,

I had a similar problem here...
Went to System >> Preferences >> Sound

Selecting Autodelect gave me this error:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

Default Playback was 'Alsa' with device 'HDA Intel Alsa Mixer'
In Windows Xp I had 'Sigmatel Audio'

Changed it to 'OSS' with device 'Sigmatel STAC9211 A1 OSS Mixer'

Works like a dream... Get better volume as well as quality in Hardy now!

---

### Post by wrighteap on 2008-06-23
Re: Ubuntu Hardy 8.04 max sound volume too low
I was able to fix this problem. I had to download the gnome-alsamixer. Once this was installed, I simply raised the volume on the one labeled "SIDE" and all of a sudden my maximum volume was boosted significantly. Fixing the volume problem 

I have an XPS M1330 and I installed the gnome alsamixer but I can't find a volume control labeled 'SIDE'. Any suggestions?

---

### Post by wrighteap on 2008-06-23
> **wrighteap said:**
> 
I was able to fix this problem. I had to download the gnome-alsamixer. Once this was installed, I simply raised the volume on the one labeled "SIDE" and all of a sudden my maximum volume was boosted significantly. Fixing the volume problem

I have an XPS M1330 and I installed the gnome alsamixer but I can't find a volume control labeled 'SIDE'. Any suggestions?

---

### Post by jvcastle on 2008-06-23
> **wrighteap said:**
> I have an XPS M1330 and I installed the gnome alsamixer but I can't find a volume control labeled 'SIDE'. Any suggestions?
I find it less confusing to just double click on the volume control, making sure the Master, PCM and Front are turned up -  Also check/edit preferences making sure Master, PCM and Front are checked as well as Digital and Digital Input Source are checked to turn on the microphone input (then select Digital Mike 1 in options). ALSO make sure the volume setting in the app (Amarok, whatever) is turned up as these are not linked to the system setting.

---

### Post by wrighteap on 2008-06-26
> **jvcastle said:**
> I find it less confusing to just double click on the volume control, making sure the Master, PCM and Front are turned up -  Also check/edit preferences making sure Master, PCM and Front are checked as well as Digital and Digital Input Source are checked to turn on the microphone input (then select Digital Mike 1 in options). ALSO make sure the volume setting in the app (Amarok, whatever) is turned up as these are not linked to the system setting.

That was the first thing I tried! I recently installed kubuntu just to see what it looked like and in KSoundMixer I think it was called there were two Fronts which when turned up gave me a volume range similar to what I got in vista :o Can't find that in ubuntu though :(

---

### Post by wfp on 2008-07-22
Was haveing same problem. I also listen to all my music with headphones but master volume was to low. Installed gnome-alsamixer. open a terminal sudo apt-get install gnome-alsamixer. Then i opened gnome-alsamixer and noticed pcm was not set to max so raised it to max, and big difference now my volume is really nice and loud. hope this helps someone.

---

### Post by Roasted on 2008-07-26
Sadly, PCM often puts distortion into music beyond the 75-80% range.

I'm running an onboard realtek card, so yeah, it sucks. But I also have a full blown stereo system hooked up... and uh, XP definitely gets a bit louder.

I'm wondering if a new sound card would benefit me, by perhaps giving me better volume levels?

---

### Post by seizer on 2008-07-28
After some updates in generic kernel package I've started to have this problem. PulseAudio Volumne Meter bar is in the middle while all bars in pavucontrol and alsamixer are on 100%. In System->Preferences->Audio I've set all to PulseAduio server (on ALSA sound is also too quiet). I'm using Audacious.

```

kamil@kamil-laptop:~$ aplay -l
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: Intel [HDA Intel], urz&#261;dzenie 0: CONEXANT Analog [CONEXANT Analog]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 0: Intel [HDA Intel], urz&#261;dzenie 1: Conexant Digital [Conexant Digital]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0

```
```

kamil@kamil-laptop:~$ uname -r
2.6.24-19-generic

```

Anyone tried to compile newer kernel or alsa-driver (the newest stable is 1.0.17, while in Ubuntu repo 1.0.16), or any other suggestions?

---

### Post by seizer on 2008-07-29
I find out problem: Audacious.:lolflag: If anyone has similiar problem to me, try other player such as rhythmbox. Music is louder right now.

---

### Post by Roasted on 2008-07-29
Yeah, Audacious' default volume level is kind of low. I noticed a few things, though... Let's compare Audacious to Amarok...

With Audacious, things seem to be clearer when you have volume 100% and PCM 100%.

With Amarok, things seem to get choppy when you have volume 100% and PCM 100%. This sounds best with PCM remaining around 80% or so.

So with Audacious, you make up the "extra ground" Amarok has on it with the additional PCM it can handle without distortion. Thing is, do you want to change the PCM level every time? 

Instead, I prefer Amarok... I think it's a better program anyway, but I prefer letting my PCM level @ 75%, having Amarok's volume @ 100%, and changing my system volume accordingly to what level I want. Again, with certain controls, you can get Audacious to compete volume-wise with Amarok.... but why bother?

---

### Post by zccpop on 2008-07-30
> **wrighteap said:**
> I have an XPS M1330 and I installed the gnome alsamixer but I can't find a volume control labeled 'SIDE'. Any suggestions?

My laptop is also XPS M1330 (red) . How is yours about temperature of keyboard.

---

### Post by frankstrudel on 2008-08-01
Well i had that problem, but it fixed itself. And I mean by itself; no-one was in the room; suddenly the house was shaking with volumes never before heard more than 2 miles from a military proving ground :lolflag:

The music (amarok) that i had had playing (then i left the room), for no reason - mid-song - shot up to v. high volume for a second or two, back down, then back to v. high where it remained until i turned down the speakers. :confused: Any explanation?

Thanks
Frank

---

### Post by FLCL on 2008-08-07
I downloaded the alsamixer+the gui for it, but i dont see any option for "Front" or "Side" that everyone keeps talking about. Any help?

---

### Post by StrangeWeakness on 2008-08-12
Hi, I just double clicked the volume in my taskbar, maxed out the master, PCM and front volumes. I had the same problem as you. Anyway hope that helped :D

---

### Post by Beyo on 2008-08-24
I have still the same problem on OpenSuse. I use KDE.
PCM and master on 80% and sound still too quiet?
what should I do?
I removed PulseAudio and turned back to Esound but still the same.

On the same machine (acer 5315) I have XP and it is much louder.

---

### Post by knattlhuber on 2008-08-24
> **Yarbo said:**
> I was able to fix this problem. I had to download the gnome-alsamixer.  Once this was installed, I simply raised the volume on the one labeled "SIDE" and all of a sudden my maximum volume was boosted significantly.  Fixing the volume problem :)

And mine as well.. :)

---

### Post by SomeGuyDude on 2008-08-25
No "side", PCM all the way up, OSS gives me an error when I try to select it in sound-properties, sound too quiet.

Three iterations of Ubuntu that I've tried, volume blows in all of them.

Conexant sound card.

---

### Post by mushroomcloudwarrior on 2008-09-15
> **wrighteap said:**
> Re: Ubuntu Hardy 8.04 max sound volume too low
I was able to fix this problem. I had to download the gnome-alsamixer. Once this was installed, I simply raised the volume on the one labeled "SIDE" and all of a sudden my maximum volume was boosted significantly. Fixing the volume problem 

I have an XPS M1330 and I installed the gnome alsamixer but I can't find a volume control labeled 'SIDE'. Any suggestions?

Thanks for that, i kept trying alsamixer-gnome!

---

### Post by thepopasmurf on 2008-09-27
Does anyone know how to get this "SIDE" option to appear? I've installed gnome-alsamixer, alsamixer-gui, reinstalled alsa, and I've been messing around with everything I can find. I'm beginning to run out of ideas.

(I'm using XPS-M1330)

---

### Post by markbuntu on 2008-09-27
FYI Bot audacious and amarok seem to have default volumes set fairly low when compared with xmms. These can be turned up in the equalizer, the furthest left slider is a preamp. Turning that all the way up gets these apps closer to xmms volume levels without distortion.

---

### Post by SlaughterDog on 2008-10-01
I'm also having the problem of low volume. I turned up PCM and front (and side and surround too) in the gnome volume control and still, it isn't as loud as XP. 

Is that the same as the gnome alsamixer you are talking of installing?

---

### Post by c4tly5t on 2008-10-01
> **acidsolution said:**
> i had same problem and i installed 
```

sudo apt-get install alsamixer

```

and than 
```

sudo apt-get install alsamixergui

```
and increase tha sound to maximum from alsamixer gui in 
Applications-->Sound & Videos ->Alsamixergui
this must help [:)]

the eaiser way to do it is double click on volume control
go to edit > Preferences 
and check every one of those

---

### Post by cor2y on 2008-10-01
Tried all those methods and my volume never increased to match the level i hear in XP using vmware/virtualbox.
And this has been through 4 versions of ubuntu, 3 pcs with a change in sound cards twice for one.
When you have speakers with volume controls or headphones with volume controls you won't notice it too much if you are not moving between windows and linux on a regular basis, maybe the need to lower or increase the volume depending on which OS, however with headphones with no volume control built other than on the software side in you really notice the low volume.

---

### Post by SlaughterDog on 2008-10-04
Heh, this is kinda strange. I have since restarted my computer and now the sound is great.

---

### Post by ianbword on 2008-11-12
> **StrangeWeakness said:**
> Hi, I just double clicked the volume in my taskbar, maxed out the master, PCM and front volumes. I had the same problem as you. Anyway hope that helped :D

quick question im new to ubuntu and ive clicked on the volume icon on the top of the screen and I only have one slider am I missing something here lol? 

Ive ran the alsamixer in terminal and the volumes were all up 100% but I didnt see anything labled PCM in there either.

---

### Post by deeflex on 2009-01-14
> **Yarbo said:**
> I was able to fix this problem. I had to download the gnome-alsamixer.  Once this was installed, I simply raised the volume on the one labeled "SIDE" and all of a sudden my maximum volume was boosted significantly.  Fixing the volume problem :)

This solved it for me too! Thanks ):P

---

### Post by yeremiya on 2009-08-17
I had a simmilar problem in 8.04 and I've solved it pretty simple. In my alsa mixer, after turning the volume on all outputs to the max (and muting the mic), I've opened the tab "Switches" and turned off the option "Headphones". :) And now I have the same volume as in WinXP. Nice and easy. ;)

---

