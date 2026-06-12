---
title: "Sound to quiet even on full volume"
date: 2008-09-02
forum: Multimedia Software
---

### Post by MiloStrife on 2008-09-02
help eepp!!

i've installed every media playing softwear that is in add remove but i cant get proper sound i have to have my speakers turned up full and still i can barley hear it? i've got a 4.1 system and everything is turned up to full???? i've even tried changing the eq on some softwear but to no avail. any help would be apprectiated.

---

### Post by Avoozl on 2008-09-02
This may sound stupid but are you sure you've hooked the speakers up correctly?  My computer actually has both "line out" and "spk out" and one of them is much quieter than the other as I've discovered by hooking my own speakers up incorrectly in the past (I think the one is meant for headphones or something?)

Also make sure you've double checked all the software volume sliders.

---

### Post by django0909 on 2008-09-02
Try this:

```
sudo alsamixer
```

Enter your password when it asks you, and you should be able to change levels using the alsamixer utility. Use the left/right keys to switch between faders and the up/down keys to alter the volume.

--django

---

### Post by stevef51 on 2008-10-22
I had similar problem, playing MP3's thru Rhythmbox it did not sound full volume, Windows produced much more volume.  Anyway I tried the alsamixer and hey presto it works.  Why are things like this hidden in Ubuntu ?  I would never have worked this out on my own.  Cheers anyway.

---

### Post by 22-250 on 2008-10-22
I was having a similar problem when watching videos on youtube, finally realized that even though I had the volume slider on screen up all the way, I had the physical volume buttons on the laptop turned down, for some reason the onscreen slider wasn't overriding the buttons. I was able to bring up the volume by adjusting the physical button.

---

### Post by TerrapinCB on 2008-11-04
Folks, I've had extremely quiet sound since I first installed Ubuntu.  I have tried all remedies that I have been able to search here in the forums, google, etc.  I have all alsamixer controls full volume.  I have all gnome sound options to full volume.  I have everything to full volume.

Dell 1525 laptop.  Currently 8.10, but no change in sound.  Any OTHER suggestions?  Oh yeah, pcm is full too, etc...

---

### Post by not a pipe on 2008-11-06
same problem with alsamixer at 100% -_-
meh, hopefully someone doesn't tell me to buy a copy of windows as a solution.

---

### Post by fenderjaguar on 2008-11-07
Same here. Sound is really quiet with everything up full.

---

### Post by not a pipe on 2008-11-09
Got it working, apparently there is more to alsamixer than typing "aslamixer" in terminal >_< (doing this only allows me to control master vol). Installed Gamix and that did the trick.

---

### Post by Steve_Barker on 2008-11-29
> **django0909 said:**
> Try this:

```
sudo alsamixer
```

--django

Thank You that was very helpful:)

---

### Post by Zeroberry on 2009-01-04
Although the sudo alsamixer told me I had it on max using Gamix I was able to get it up a bit more. Also the Playback header and one other let me get it up to a normal level. Thanks for the help! Gamix ftw

---

### Post by Amerinidiot1231 on 2009-01-10
> **TerrapinCB said:**
> Folks, I've had extremely quiet sound since I first installed Ubuntu.  I have tried all remedies that I have been able to search here in the forums, google, etc.  I have all alsamixer controls full volume.  I have all gnome sound options to full volume.  I have everything to full volume.

Dell 1525 laptop.  Currently 8.10, but no change in sound.  Any OTHER suggestions?  Oh yeah, pcm is full too, etc...


I am having the same problem on my 1525, none of the solution I have found worked.  

:-({|=
*sad song (which I can barely hear)*

---

### Post by linux_tech on 2009-01-10
First try installing gnome alsamixer, then run it and check all settings.
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type

```
gnome-alsamixer

```
Also install these for intrepid:

```
sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```

---

### Post by Amerinidiot1231 on 2009-01-10
Everything was set to full volume, except the captures.  The plug-ins were already installed.  Any more ideas?

I mean its a very noticeable difference.  In linux it seems I always have the volume at full, and in vista I would fear of blowing out the speakers at full volume.

---

### Post by linux_tech on 2009-01-10
In System->Preferences->sound,  what is sound Playback currently set to?
Have you already tried other settings- Auto detect & alsa?

Try disabling pulse audio, then test sound again
```
killall pulseaudio
```

install esound
```
 sudo apt-get install esound


```
Also stop and restart alsa

```

sudo /etc/init.d/alsa-utils stop

sudo alsa force-reload

sudo /etc/init.d/alsa-utils start

```



open volume control, type:
```
gnome-volume-control

```
check settings increase volume controls 

then test sound again

---

### Post by Amerinidiot1231 on 2009-01-24
It got a little louder, but still not very loud.

---

### Post by Zigon on 2009-06-06
Gamix did the trick for me, thanks for your help!

---

