---
title: "Movie Player Constantly Crashes and Exits"
date: 2009-04-25
forum: Multimedia Software
---

### Post by web1b on 2009-04-25
After upgrading from 8.10 to 9.04, I cannot use the Movie Player.
Problems started with the very first multimedia file.
If I open a link to a video or audio file on the web, it opens and immediately closes.
If I insert a DVD, the Movie Player does the same thing.
I have a mp3 on the desktop and if I try to play it, it launches Movie Maker and it crashes, but if I mouse over the mp3 icon, I can hear it playing the audio in the background until I move the mouse pointer away.
It is a Gateway MX6214 laptop.

Is there any fix?

---

### Post by hatalar205 on 2009-04-25
I think you have codec problem. If so, follow the steps in the following link.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by whitefort on 2009-04-25
Just jumping in to say that I have the identical problem.  I've worked through the Medibuntu page (thank you for that link!), but it hasn't changed anything.

I have to say, I started with Dapper Drake, and since then I don't recall a Ubuntu where so much stuff didn't work for me...  Oh well, 'spose I'll get there eventually...

---

### Post by whitefort on 2009-04-25
I found this 'workaround' in another thread.  It seems to have fixed the problem for me.

> 
Workaround to get it working: open gstreamer-properties. Then, Video tab, Default Output section. Change the Plugin from "Autodetect" to "X Window System (No Xv)" and close. This way, totem will play any video format.

That got Movie player working.  For VLC, I had to fix:
Tools->Preferences->Video->Output to X11 Video Output.

Hope this helps somebody!

---

### Post by web1b on 2009-04-25
> **whitefort said:**
> I found this 'workaround' in another thread.  It seems to have fixed the problem for me.



That got Movie player working.  For VLC, I had to fix:stre
Tools->Preferences->Video->Output to X11 Video Output.

Hope this helps somebody!

I don't understand what you are talking about.  
Movie Player launches when I try to play an MP3 file or a video.  I don't see gstreamer anywhere

---

### Post by anico on 2009-04-26
type this in terminal and it should work! i just had the same exact problem.

```
sudo apt-get remove swfdec-mozilla  
```

this should do it!:guitar:

---

### Post by Eupho on 2009-04-26
Hi

I am having the same problem.

If I open any type of movie file on either VLC, Movie player or MPlayer is immediately chrashes.

I just upgraded fro 8.10 and I am using a Eeepc 1000h. I also used the array.org kernel to get all my bits going on 8.10

"Ubuntu 8.10, kernel 2.6.27-8-eeepc" This is still my default kernel for 9.04. I don't think it has anything to do with this problem either. I have tried all the fixes above with no success.

Any help will be greatly appreciated

---

### Post by web1b on 2009-04-26
> **anico said:**
> type this in terminal and it should work! i just had the same exact problem.

```
sudo apt-get remove swfdec-mozilla  
```

this should do it!:guitar:

No, that did not help.  It said that isn't installed so it can't remove it.
The problem I'm having is with Movie Player, not Flash anyway.

---

### Post by Eupho on 2009-04-26
> **web1b said:**
> No, that did not help.  It said that isn't installed so it can't remove it.
The problem I'm having is with Movie Player, not Flash anyway.

Hi again

I had the same outcome as quoted above.

---

### Post by jeshasgoodstinky on 2009-04-26
eee 1000 user here. same problems, ubber gay... tried all sorts of things now. even new video drivers.  (for a min. i thought i fried my screens! :)
  

mk just letting you know its not you

---

### Post by Eupho on 2009-04-26
> **whitefort said:**
> I found this 'workaround' in another thread.  It seems to have fixed the problem for me.



That got Movie player working.  For VLC, I had to fix:
Tools->Preferences->Video->Output to X11 Video Output.

Hope this helps somebody!

I have Tried the fix for VLC and it didnt work.

I cant even find he Video tab  in gstreamer-properties

Sorry if i seem desperate.

I have to show a video this week that all. should never have upgraded......

---

### Post by web1b on 2009-04-26
Is this a problem that only happens with an upgrade so a clean install would fix it?
I don't have any data or apps installed, so I could just reinstall 9.04 clean without much problem.
I will just go back to 8.10 after formatting if that isn't a fix.

Seems like a bug that wasn't caught in the beta testing.

---

### Post by jeshasgoodstinky on 2009-04-26
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)   this did it... well part of it.   totem used to load *.iso but not now.  just the regular vids

---

### Post by Eupho on 2009-04-26
> **jeshasgoodstinky said:**
> [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)   this did it... well part of it.   totem used to load *.iso but not now.  just the regular vids

nope, no good for me.:confused: I am going to try a fresh Install, it that doesn't work i will be going back to 8.04.

Thanks for the help.

---

### Post by Eupho on 2009-04-28
well i have gone for a completely fresh install of 9.04 "netbook release"  

All is as it should be :P

Must be some bug to do with the update.

Oh well

---

### Post by commyostrich on 2009-05-01
Ya I also have this one ubuntu 9.04. No matter whether it's vlc or movie player, the program will crash immediately when i try to open a DVD.  Avi files work fine.  Now when I first installed it said I needed codecs (in movie player) so I installed the ubuntu-restricted-extras and ever since then it won't work.  But when I uninstalled the extras, it still doesn't work.  Heeeeelp.

---

### Post by D351 on 2009-05-04
Same problem, is there a way to fix this without reinstalling ubuntu?

---

### Post by acroporas on 2009-05-04
> **D351 said:**
> Same problem, is there a way to fix this without reinstalling ubuntu?


Yet another person who after upgrading, all media players crash immediately.  [http://ubuntuforums.org/showthread.php?t=1147304](http://ubuntuforums.org/showthread.php?t=1147304)


Can anyone confirm that installing a fresh copy of 9.04 fixes the problem?

---

### Post by castlefox on 2009-05-07
I just wanted to jump into this tread to say I am having the same problem.

I also upgraded from 8.10 to 9.04

---

### Post by lixy on 2009-05-09
> **whitefort said:**
> I found this 'workaround' in another thread.  It seems to have fixed the problem for me. 

Thanks, that fixed it.

I had issues with Amarok not playing anything either, and this fixed it.

```
sudo apt-get install phonon-backend-xine libxine1-ffmpeg
```

---

### Post by mariog85 on 2009-10-11
> **jeshasgoodstinky said:**
> [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)   this did it... well part of it.   totem used to load *.iso but not now.  just the regular vids

Hi! 

This helped for my constantly crashing media players! VLC and the standard movie player now work fine!

For detailed info: I run a ubuntu 9.04 server on an Intel D945GSEJT board. Video playback worked out of the box after the clean 9.04 install, but completely stopped working one day. I really don't know which updates were done before the problem occurred the first time, since i don't know when this was. During those "bad days", X11 playback worked in VLC, but was too slow to whatch in full screen...

Tanks for the hint!
Cheers, Mario

---

### Post by sickamore007 on 2009-10-13
> **whitefort said:**
> I found this 'workaround' in another thread.  It seems to have fixed the problem for me.



That got Movie player working.  For VLC, I had to fix:
Tools->Preferences->Video->Output to X11 Video Output.

Hope this helps somebody!


It has helped me also. thats was a issue for me. thank you

---

### Post by webweave on 2009-10-16
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) 

Worked for me.

I have an HP d530cmt which is a tower but I guess it uses the intel laptop chip for the internal video. I might upgrade to a better video card so I'm keeping track of the above web page as it has instructions to remove the fix.

I also did the VLC workaround mentioned above. It worked too but the fix is better as it works for all video programs.

---

### Post by crpd40s on 2009-10-23
> **whitefort said:**
> I found this 'workaround' in another thread.  It seems to have fixed the problem for me.



That got Movie player working.  For VLC, I had to fix:
Tools->Preferences->Video->Output to X11 Video Output.

Hope this helps somebody!
  
Thanx! this fixed my problem!!!:D

BTW I had a fresh install so it wasn't an upgrading problem for 9.04

---

### Post by RandyFulcher on 2009-10-25
Wow, thanks! I've had the same problem (just recently) Thought my daughter or her friends had crashed my system with a virus. Is this going to be addressed in the next version of Ubuntu? Hope so, I'm new to Ubuntu (Linux) and I can see a problem like this turning people back to windows. 
As a sidenote, I have burning DVD's of home movies recently using KDENLive and K3B and having the video pause during playback. Could this problem have caused this?:confused:

---

