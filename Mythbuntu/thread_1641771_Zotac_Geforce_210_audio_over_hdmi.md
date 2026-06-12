---
title: "Zotac Geforce 210 audio over hdmi"
date: 2010-12-09
forum: Mythbuntu
---

### Post by intelquadcore on 2010-12-09
Hey
Just wanted to thank LowSky for his tutorial... It helped me solve my problem, which was that I was not able to get any audio over my graphics/video card. My graphics card is a Zotac Geforce 210 1GB

After a fresh install of Mythbuntu 10.10 I ran all the updates.

To unmute my video card's hdmi I ran alsamixer in terminal and pressed the right arrow key over each s/pdif figure and subsequently pressed "m" to unmute them

```

alsamixer

```After doing that this is what my alsamixer looked like...

[IMG]http://i16.photobucket.com/albums/b12/PillsburyBoy/Screenshot.png[/IMG]

After that I went to Applications -> Multimedia -> Mixer 
Made sure the items were checked off

[IMG]http://i16.photobucket.com/albums/b12/PillsburyBoy/Screenshot-4.png[/IMG]

I then created an asound.conf file by typing this code into terminal

```
sudo nano /etc/asound.conf
```after accessing the terminal I pasted this code into the asound.conf

```

pcm.!default {
type hw
card 0
device 7
}

```When I was done this is what the asound.conf in terminal looked like...

[IMG]http://i16.photobucket.com/albums/b12/PillsburyBoy/Screenshot-1.png[/IMG]


After that setup was done I then had to configure the front end setup of Mythbuntu, the screen when you first turn your HTPC (or can be accessed by Applications ->Multimedia -> MythTV Frontend)
Utilities/Setup -> Setup -> General
press "Alt + N" 3 times till you get to the "Audio System" page

I changed the Audio output device to ALSAplughw:0,7 (option wasn't there, I typed it in)
Chose 5.1 as the speaker configuration
and for Digital output device I chose ALSAplughw:0,7 (again the option wasn't there, I typed it in)

After the configuration was complete this is what my Audio system page looked like...


[IMG]http://i16.photobucket.com/albums/b12/PillsburyBoy/Screenshot-2.png[/IMG]


The reason why I chose 0,7 was because many other users had luck with that combination... I read many posts lol. I wasn't able to figure out how to make the Zotac Gefore 210 show up as 1 device. When I type 
```
aplay -l
```my Zotac Geforce 210 shows up as 4 devices

[IMG]http://i16.photobucket.com/albums/b12/PillsburyBoy/Screenshot-3.png[/IMG]


So I just ended up using the combination 0,7 and it worked.
Just a side note I disabled my onboard HD audio, and removed my pci sound card...


Hope this will help people out who have the Zotac Geforce 210 and have mythbuntu 10.10

---

### Post by Neon Dusk on 2010-12-09
> **intelquadcore said:**
> 
...

The reason why I chose 0,7 was because many other users had luck with that combination... I read many posts lol. I wasn't able to figure out how to make the Zotac Gefore 210 show up as 1 device. When I type 

...

So I just ended up using the combination 0,7 and it worked.
Just a side note I disabled my onboard HD audio, and removed my pci sound card...


I think the key to getting only 1 hdmi device to appear is to use probe_mask option of snd-hda-intel.

So you would create /etc/modprobe.d/sound.conf containing
```

options snd-hda-intel enable_msi=0 probe_mask=0xfff2

```
(This is if the HDMI device you want to use show up on card 0 in aplay -l)

If the HDMI device in on card 1 you would use
```

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

```

If the If the HDMI device in on card 2 you would use
```

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xffff,0xfff2

```

etc..

You can then just use Alsa:hdmi in mythtv

---

### Post by intelquadcore on 2010-12-09
Hey,
When I tried it your way I am not getting any audio. 
I did a fresh install, ran updates, used your code, ran aplay -l, and the only device
that showed was the graphics card. Went to front end and chose hdmi and no luck.

The way I did it originally gave me audio, no clue why.

Your way should work, anyways I am just going to revert to my previous settings that I had

---

### Post by mGSz on 2010-12-10
I got audio working by following [[COLOR="Blue"]this[/COLOR]]("http://forum.xbmc.org/showpost.php?p=641477&postcount=31") guide

---

### Post by Neon Dusk on 2010-12-10
@intelquadcore
Not sure why it didn't work for you. 

I've just tried it again here - without the probe_mask option I get the same devices listed in aplay -l as you (devices 3,7,8,9 - ALSA: plughw:0,7 gives audio in myth). 

With the probe_mask option I get one HDMI device listed (card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]). Within mythtv scanning for audio devices (I'm running myth 0.24 although it shouldn't make any difference) and picking ALSA:hdmi gives working audio.

You say that you did a fresh install - did you remember to unmute the S/PDIF device in alsamixer after the install?

I suppose it doesn't matter about the duplicate HDMI devices if ALSA: plughw:0,7 is working for you.

---

### Post by intelquadcore on 2010-12-11
Yea I made sure its was unmuted lol... It's really weird, even after using that code you gave me and running aplay -l in terminal it correctly lists 1 device. Then when I restart and go to the front end to choose hdmi it doesn't work.

It works with 0,7 though lol so I'm happy :]

---

### Post by newlinux on 2010-12-11
> **intelquadcore said:**
> Yea I made sure its was unmuted lol... It's really weird, even after using that code you gave me and running aplay -l in terminal it correctly lists 1 device. Then when I restart and go to the front end to choose hdmi it doesn't work.

It works with 0,7 though lol so I'm happy :]


I went through the same thing with a 210. I could use the module options to get it down to one device (and it was unmuted), but no matter what I tried I could not get sound when I had only one device in alsamixer. Not sure why, I spent a lot of time on it, but in the end I too have stuck with the 4 devices.

---

### Post by bigredc2 on 2011-01-09
When you say you "ran all the updates" do you just mean the regular system updates after a fresh install or do you mean you specifically updated alsa using one of the methods  you found on the internet?  

Basically I'm wondering if I need to manually update alsa beyond what comes with 10.10.

Thanks for the great tutorial I'm going to try it as soon as I can.

---

### Post by intelquadcore on 2011-01-21
> **bigredc2 said:**
> When you say you "ran all the updates" do you just mean the regular system updates after a fresh install or do you mean you specifically updated alsa using one of the methods  you found on the internet?  

Basically I'm wondering if I need to manually update alsa beyond what comes with 10.10.

Thanks for the great tutorial I'm going to try it as soon as I can.

Hey,
Sorry for the late reply. I just saw this post. 
I updated via the system updates. 

Out of curiosity I also updated to mythTV 0.24 via [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
I wanted to see if the "scan for audio" option in mythTV 0.24 would correct the problem I was encountering. It did not however.

If I can recall you do not need to update alsa to the latest version. The alsa version from mythbuntu 10.10 should suffice.
  If you just follow my steps from the first post above it *should* work lol

---

### Post by AngelMasters on 2012-01-27
:popcorn:After a few months of looking over this solution, today I tried this and WOW, my TV started blooming up with clear sound.:popcorn:

---

### Post by SCrid2000 on 2012-09-01
Thanks a lot OP!
I used 
alsamixer
to mute everything from my built in sound card, disabled it in sound settings, and set the Zotac audio to #7, and it's finally working :)

---

