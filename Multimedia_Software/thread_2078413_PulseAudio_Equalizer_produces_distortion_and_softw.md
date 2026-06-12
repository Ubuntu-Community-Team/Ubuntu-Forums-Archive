---
title: "PulseAudio Equalizer produces distortion and software clipping"
date: 2012-10-30
forum: Multimedia Software
---

### Post by rectec794613 on 2012-10-30
Hello. I've already made a [[COLOR="LightBlue"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1957640") about this a little under 7 months ago, but received no replies. I think I could've been a little bit more clear.

Simply put: I love music, I want that music to sound as best as possible. I know I can get the most out of my headphones than what is provided by default, so in Windows and Android I can use equalizers and bass boosters to enhance the audio system-wide. If I were to ask how to do this in Ubuntu, I'd probably be told to use PulseAudio-Equalizer. 

Ok, then. I'd install it from the Webupd8 PPA, launch it, and turn the EQ on. I'd first raise the lower frequencies, and that's where the problem begins. Even the slightest raise produces *awful* distortion/software clipping. It makes my listening experience unenjoyable at best.

Unfortunately, PA-EQ is the only option I have. It is a very old and unmaintained piece of software that performs below expectations. There is at least one other person ([[COLOR="LightBlue"]Naike[/COLOR]]("http://ubuntuforums.org/member.php?u=265653")) with this problem, probably much more. Why do I say this? I've had this same problem with *four* different sound cards on four completely different motherboards.

So we must do something about this! I miss having deep bass and clear treble, and I'm sure others would *love* to have nice audio with Ubuntu that lives up to the capabilities of their hardware.

 I'm running Ubuntu 12.10 with pulseaudio 2.1 and pulseaudio-equalizer 2.7. I'd love to get some help with this. Please be sure to read my old [[COLOR="LightBlue"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1957640") if you need more info. The versions are different but the problem remains the same. Thanks!

---

### Post by rectec794613 on 2012-11-02
[FONT="Impact"][SIZE="4"]Bump.[/SIZE][/FONT]

---

### Post by MikeEx on 2012-11-09
I may have a workaround for your distorted PA equalizer.
Install EarCandy and set the maximum volume for each program that appears in the list to 60-80% & the default sink to LADSPA.
Programs(even browsers) should appear in the EarCandy list once they open an audio stream.

Edit: [found a build for quantal]("http://launchpadlibrarian.net/70829945/earcandy_0.9%2Bbzr12-2_all.deb")

---

### Post by rectec794613 on 2012-11-09
> **MikeEx said:**
> I may have a workaround for your distorted PA equalizer.
Install EarCandy and set the maximum volume for each program that appears in the list to 60-80% & the default sink to LADSPA.
Programs(even browsers) should appear in the EarCandy list once they open an audio stream.

Edit: [found a build for quantal]("http://launchpadlibrarian.net/70829945/earcandy_0.9%2Bbzr12-2_all.deb")

OMG I think it worked. It sounds excellent. So far so good. I'll notify you if the problem comes back. Otherwise, I'll mark this as solved. Thank you so much. :)

---

### Post by rectec794613 on 2012-11-09
Sigh. Scratch that. The problem is back. The distortion comes back after say, another song starts playing or another video starts playing. This is ridiculous. I just want good sound.

Any ideas?

EDIT: It seems to have mostly fixed the problem. About 60% of the songs that are playing in my music player have no distortion, so it's better than nothing. I suppose I'll mark this as solved again in a little while.

---

### Post by MikeEx on 2012-11-09
Yeah, for some reason a song change will reset the volume and sometimes it will work as it should and keep volume settings. Try restarting.

---

### Post by rectec794613 on 2012-11-09
**Easy fix!**
I can't believe I haven't found this out already. The easiest way to work around this problem is to simply *turn down* the volume of the individual application! For YouTube videos, just turn down the volume of the video player. For media players like VLC, do the same thing. Of course you won't be able to adjust the volume of everything, but it's still better than nothing.

---

### Post by GreenWanderer on 2012-11-11
I had the same problem. I managed to make pulseaudio-equalizer preamp visible and functional, but it is not affecting sound. My dream is to create system equalizer which allows to create really custom preset (similar to sound engineering software, where you can create custom lines). But as I am new in Linux, don't really know where to start... :confused:

PS. Have you been successful in using any sort of convolver in Ubuntu?

---

### Post by rectec794613 on 2012-11-11
> **GreenWanderer said:**
> I had the same problem. I managed to make pulseaudio-equalizer preamp visible and functional, but it is not affecting sound. My dream is to create system equalizer which allows to create really custom preset (similar to sound engineering software, where you can create custom lines). But as I am new in Linux, don't really know where to start... :confused:


I'd like to fix some bugs with the equalizer LADSPA plugin (the backend for Pulseaudio Equalizer. But alas, I'm only a beginner when it comes to fixing bugs and programming. If you have the skill, you could try and take a look at pulseaudio-equalizer's code or something.

> 
PS. Have you been successful in using any sort of convolver in Ubuntu? 
Sorry. No idea what that is. I can't help you.

---

