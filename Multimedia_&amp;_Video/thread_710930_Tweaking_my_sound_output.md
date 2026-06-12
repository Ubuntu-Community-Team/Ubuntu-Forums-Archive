---
title: "Tweaking my sound output"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by other guy on 2008-02-29
I got my sound output sort of the the way I like it. Now I want it to be under my spell that much more. I have two minute things I would like to address.* I hope this is not to confusing.*


**First up**
I have the output[s] working good. All the jacks work as they should, as does the keyboard control. I want to be able to give a little more to one speaker and *not* have it default to the same level as the rest of the active sliders.
Pretty much lock the orientation of each slider. So when I use my keyboard volume they all move together.Since I have one speaker that is not as loud due to physical placement. When I manually set a spot, next time I use the keyboard control. It defaults to the same as the rest.

I can set darn near a perfect sweet spot. Next time i adjust the volume. It all goes way.

[B]Next:
[Found acceptable solution in Audacious/Gxine + OSS support via players preferances]
[/B][COLOR=Gray] Since the sound works and is peachy. I want to be able control the volume with the keyboard for the media players I use. I think this is something simple I missed here. Using software sliders is not fun or easy. If I have to mute quickly. Finding the desktop the app is on can take a second or two.

My last sound card took some work to get going and it controlled the volume on anything I ran. Here is the output for my card I currently am using.[/COLOR] 

```
 sudo lshw -C sound
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

---

### Post by Bubba64 on 2008-03-01
Open the volume control and depending on your set up chances are you have two sliders that control the overall volume and only one is connected to the volume control you use to adjust the volume,  unlock the dual sliders on the secondary volume control adjust and everything should work. you could also install Gnome alsa mixer from add remove or there are probably other mixers in add remove if you click on all packages available.

---

### Post by other guy on 2008-03-01
I have tried that.

Here is basically what i am looking for. I set front to lets say level 5, left/right rear to 6 & 8.. and so on. For the 'sweet spot' surround effect.

It all works dandy, until I use the volume on the keyboard or volume control in the GUI. Pretty much the levels all revert to the same. i.e.- Level 5 right/left front 5 center 5... they all move in unison, but I lose my sweet spot.

I tried to figure out a way to keep the levels how I like them according to the sweet spot. All the speakers work. I just want more out of it, in terms of custom and not having it reset everything when I make a slight volume adjustment.

---

### Post by erginemr on 2008-03-01
You are right. I am also using my keyboard multimedia buttons to adjust the volue. I have experimented with it by setting different levels to the speakers, but when I used the button, all levels are normalized to the same value. So, this is not a bug, but is a feature (or rather, lack of feature for that matter).

---

### Post by other guy on 2008-03-01
> **erginemr said:**
> You are right. I am also using my keyboard multimedia buttons to adjust the volue. I have experimented with it by setting different levels to the speakers, but when I used the button, all levels are normalized to the same value. So, this is not a bug, but is a feature (or rather, lack of feature for that matter).

Any groovy work around you know of?

This is my last lil nit for having a (near) perfect OS.

---

