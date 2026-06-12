---
title: "video playback slow in ubuntu 11.04"
date: 2011-04-28
forum: Multimedia Software
---

### Post by psychok7 on 2011-04-28
Hi, i just intalled ubuntu 11.04 unity and i installed all the necessary codecs (gstreamer) to playback video. 
The thing is i notice its a little slow then when i used 10.10, so my first guess would be there is somethng wrong with gstreamer or unity itself, does anyone know how i can solve this problem??

---

### Post by cdrKeene on 2011-04-28
I am having the same issue. I have a dual boot with windows XP, and 64bit Ubuntu 11.04 is running graphics way slower than it did, even slower than the 32 bit XP on this machine. 

I have a radeon 9250, if that has anything to do with it. I installed Ubuntu for the performance, so I'd like to know anything, as well, related to how to get "back to where thing were", speedwise.

thanks

---

### Post by psychok7 on 2011-04-29
> **cdrKeene said:**
> I am having the same issue. I have a dual boot with windows XP, and 64bit Ubuntu 11.04 is running graphics way slower than it did, even slower than the 32 bit XP on this machine. 

I have a radeon 9250, if that has anything to do with it. I installed Ubuntu for the performance, so I'd like to know anything, as well, related to how to get "back to where thing were", speedwise.

thanks

i also have 64bit with dual boot. my graphic card is a ATI RAD HD5770

---

### Post by ShadowKyuzo on 2011-04-29
I'm having the same issue.
Have a dual-boot with 64-bits Ubuntu 11.04. 
My graphics card: ATI HD5650

Video playback is "laggy" and not smooth as it should be...

---

### Post by psychok7 on 2011-04-29
> **ShadowKyuzo said:**
> I'm having the same issue.
Have a dual-boot with 64-bits Ubuntu 11.04. 
My graphics card: ATI HD5650

Video playback is "laggy" and not smooth as it should be...

yes thats exactly it... do you know if there is a bug report about this? have you guys tried uninstalling the proprietary drivers?

---

### Post by ShadowKyuzo on 2011-04-29
> **psychok7 said:**
> yes thats exactly it... do you know if there is a bug report about this? have you guys tried uninstalling the proprietary drivers?

Don't know if theres a bug report, the only related thing i found was this topic...

But i think i just solved it here on my pc.
Do you have Compiz Settings Manager?

I did this and video playback seems normal now:

1. Go to Compiz Settings Manager
2. On the "general" options, go to COMPOSITE
3. Disable "Detect Refresh Rate"
4. Set "Refresh Rate" to 60 (or your monitor's refresh rate)
5. Go back to the "general" options and now go to "OpenGL"
6. Disable "Synchronize to VBlank"

Give it a try.

---

### Post by psychok7 on 2011-04-29
> **ShadowKyuzo said:**
> Don't know if theres a bug report, the only related thing i found was this topic...

But i think i just solved it here on my pc.
Do you have Compiz Settings Manager?

I did this and video playback seems normal now:

1. Go to Compiz Settings Manager
2. On the "general" options, go to COMPOSITE
3. Disable "Detect Refresh Rate"
4. Set "Refresh Rate" to 60 (or your monitor's refresh rate)
5. Go back to the "general" options and now go to "OpenGL"
6. Disable "Synchronize to VBlank"

Give it a try.

YES!!! IT WORKED :) thanks... by the way some guy suggested me to change video settings on compiz manager i just didnt know where to go.. how did u find the solution?? by the way where can i find my monitors refresh rate?

---

### Post by ShadowKyuzo on 2011-04-29
> **psychok7 said:**
> YES!!! IT WORKED :) thanks... by the way some guy suggested me to change video settings on compiz manager i just didnt know where to go.. how did u find the solution?? by the way where can i find my monitors refresh rate?

Good to know it worked for you too! 
I had a feeling the problem was related to vertical synchronization, so i remembered i had changed some settings related to this in the compiz. Just a lucky guess, haha.

To find your refresh rate, go to "Monitors" and you'll see your screen resolution and your current refresh rate.
Most LCD monitors have a 60 hz refresh rate.

---

### Post by psychok7 on 2011-04-29
> **ShadowKyuzo said:**
> Good to know it worked for you too! 
I had a feeling the problem was related to vertical synchronization, so i remembered i had changed some settings related to this in the compiz. Just a lucky guess, haha.

To find your refresh rate, go to "Monitors" and you'll see your screen resolution and your current refresh rate.
Most LCD monitors have a 60 hz refresh rate.

yes thats exactly it.. this is what i love about the community, helping each other out :) marking this thread as solved
cheers

---

### Post by cdrKeene on 2011-04-29
[COLOR=Red]Are you folks running the 3d desktop?.

I don't know how to launch compiz settings. There is a compiz installed in synaptic. Do I need to run it through terminal? or add additonal packages?

[COLOR=Black]... Ah, I've found it: compizconfig-settings-manager. 

I'll see what happens next.
[/COLOR][/COLOR]

---

### Post by cdrKeene on 2011-04-29
Hmmm, I must have a different issue. This didn't work out for me. I'm using Synfig's ink tool, and Blender 3D's edit mode to judge graphics performance, and 32bit XP still mysteriously beats 64bit Ubuntu hands down. I have no proprietary drivers installed or available.

I tried to check my refresh rate, I thought it was 75htz, but that must be something different? I tried 60 too with the same results.

---

### Post by ShadowKyuzo on 2011-04-30
> **cdrKeene said:**
> Hmmm, I must have a different issue. This didn't work out for me. I'm using Synfig's ink tool, and Blender 3D's edit mode to judge graphics performance, and 32bit XP still mysteriously beats 64bit Ubuntu hands down. I have no proprietary drivers installed or available.

I tried to check my refresh rate, I thought it was 75htz, but that must be something different? I tried 60 too with the same results.

What's your graphics card? 
I don't notice much graphics performance difference between Ubuntu 64 bits and Windows 7 64 bits. 
I never tested any game on Ubuntu, but Blender, 3D Cube and other desktop effects run fine. 

About the video playback: you could try changing the video output driver of your media player (which one do you use?), to see if it helps.

---

### Post by auron12 on 2011-05-06
Thanks, worked and for me!You are the best!Great forum!!

---

### Post by SlugO on 2011-05-10
I tried the instructions posted in this thread but they didn't work.

I have to tell you that I have never seen video playback in such a bad shape in Ubuntu. I have NVIDIA 6800 GT with the latest closed drivers but video playback is just terrible.

Totem crashes every time I try to make it go fullscreen and sometimes when I just start the video. Same with Banshee since they both use Gstreamer. VLC only shows something in fullscreen when I turn off Hardware acceleration (overlay), and even then the playback is quite bad since it seems to be skipping frames.

Of course full screen Flash is no better. I only see a small single colored box in the upper left corner of my display. It tries to mimic a color or two from the video but that's it.

All these problems go away if I login to the old Gnome desktop without Unity. At the moment Unity feels very much like beta software. Too bad, I mostly like it.

Are there even bug reports for all these problems? I found one related to the Totem crash [here]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/769290") but haven't found the others. And does anyone have any ideas on how to fix these?

---

### Post by HanDez on 2011-06-12
Thank You! For me it was all about the refresh rate, upped to 60 hz...playing perfectly now.

---

### Post by mitsumits on 2011-06-13
Thanx a lot!!! One less reason to boot on windows. For me... this was the last!!! Only Ubuntu from now on! Thanx again.

---

### Post by henrique_rauen on 2011-06-13
It really helped to unselect Vsync, but it still don't works as it should.
It's still a little bit 'laggy'... The sound is perfect, but the image sometimes kind of makes a little jump... Its almost unperceivable, but you know something is wrong, that its not smooth as it should. Comparing to win7 (i have a dual boot) the difference is clear.

Running ubuntu 11.04 64 bit in a intel i5-750 with Asus P7P55D PRO and ATI HD5750 (looks like some kind of driver issue). I have the fglrx prop driver downloaded from the additional drivers app in ubuntu. Everything else works fine (unity etc).

Any ideas?

Thanks!

---

### Post by Fat-n00b on 2011-06-14
[QUOTE=BasioMeusPuga;10937670]
b) Set the Powermizer to maximum performance in X server settings (Something that has to be repeated after each reboot).[QUOTE]
 
[COLOR=black][FONT=Verdana]Can you save that setting in a "profile" and then set that as the default profile?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]In windows with my ATI card I had a similar issue... And was able to get around having to open and change the setting with each reboot by enabling "profiles" and then saving a custom profile, then setting that profile as my preferred/default profile.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Not sure if nVidia and Ubuntu have a similar setup or not...[/FONT][/COLOR]

---

### Post by ankit28595 on 2011-06-14
That is it. Thank you it worked for me too!

---

### Post by henrique_rauen on 2011-06-17
I finally got good video quality, with the open source driver (radeon). Unfortunately, i can't manage to get sound over hdmi with that, so it all came to choose between quality playback without sound over HDMI (open source driver) or laggy playback with sound over HDMI cable (AMD prop driver).

So far I decided to use the open source driver... The sound comes through my pc speakers, which is not great, but better than the laggy video.

If i find a solution that makes everything work I'll post it here.

---

### Post by errrn on 2011-11-14
> **ShadowKyuzo said:**
> Don't know if theres a bug report, the only related thing i found was this topic...

But i think i just solved it here on my pc.
Do you have Compiz Settings Manager?

I did this and video playback seems normal now:

1. Go to Compiz Settings Manager
2. On the "general" options, go to COMPOSITE
3. Disable "Detect Refresh Rate"
4. Set "Refresh Rate" to 60 (or your monitor's refresh rate)
5. Go back to the "general" options and now go to "OpenGL"
6. Disable "Synchronize to VBlank"

Give it a try.

you made my day.
thank you!

---

