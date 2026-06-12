---
title: "[SOLVED] 8.04 + VLC + no subtitle"
date: 2008-04-30
forum: Multimedia Software
---

### Post by potam on 2008-04-30
Hello guys,
I have a problem with my VLC media player since I upgraded to 8.04.
Let's see, I have a regular video file in a regular directory (no special characters in the name, no space, etc...) with a subtitle. When I double click the video files it starts playing, but without subtitle. When I open VLC and drag the video file to the VLC window it plays it with the subtitle. Even if I dragged only the video file! Now the question is, why is the difference? And how can I fix this behaviour?

---

### Post by potam on 2008-05-01
The ultimate solution is: open with -> custom command, and type "**vlc %m**" without the quotes.
Now subtitles are loaded, so the problem is **almost** solved. The question is: why is the %m parameter missing in the new Nautilus?

---

### Post by potam on 2008-05-01
LoL, got the final solution very fast:
for some reason in vlc.desktop the command is **vlc %U** (yes, U and not u), which is incorrect, 'cause U means the username. The 'u' is the URI, and we need this.
So go to /usr/share/applications and do sudo gedit vlc.desktop, and change Exec=vlc %U to Exec=vlc %u , and problem solved forever!

OMG, I solved a bug in Ubuntu for the first time :guitar:

---

### Post by elgoog on 2008-05-04
> **potam said:**
> LoL, got the final solution very fast:
for some reason in vlc.desktop the command is **vlc %U** (yes, U and not u), which is incorrect, 'cause U means the username. The 'u' is the URI, and we need this.
So go to /usr/share/applications and do sudo gedit vlc.desktop, and change Exec=vlc %U to Exec=vlc %u , and problem solved forever!

OMG, I solved a bug in Ubuntu for the first time :guitar:

Mate, I tried what you've posted here. Din't work out. Try out something.

---

### Post by potam on 2008-05-07
Then try %m instead of %u, they almost the same. If still does not work, then there is a problem with your VLC settings, eg. the charset of the subtitle.

---

### Post by Xiong Chiamiov on 2008-05-07
Or you can just select the sub from video -> subtitles.  A pain, perhaps, but it's not really that big a deal.

That said, what are you playing?  Is it a Matroska file (.mkv)?  Do you happen to know what kind of subs they are (styled or plain)?

---

### Post by kevlarRelic on 2008-05-12
Thanks for your work on this Potam! 

I'm having the same problem, which so far I've worked around by opening the movie and dragging the subtitle file over the movie window (easier than browsing for it in the preferences, as Xiong Chiamiov's said). 

I'm new to linux, so your solution doesn't make sense to me, but I'll try it anyway and post the results here.

---

### Post by kevlarRelic on 2008-05-12
I changed Exec=vlc %U to Exec=vlc %m and it worked (%u didn't work for me). Thanks again Potam. 

In regards to this fix not working for you elgoog, I also thought it wasn't working for me at first. It just turned out that I had changed the subtitle fuzziness under Video->Subtitles->Advanced in my previous efforts to fix the problem. Resetting the preferences to default made everything better.

---

### Post by potam on 2008-05-15
> **kevlarRelic said:**
> I changed Exec=vlc %U to Exec=vlc %m and it worked (%u didn't work for me).

I just realized that using %m is perfect for autorun, I don't need 3 seperate .desktop files. :)

---

### Post by woyzeckswoe on 2008-05-18
it worked for me too (%m),thanks a lot!

---

### Post by cgrenier on 2008-06-15
You are a hero, potam.  %m works (I didn't try %u).

---

### Post by jastonas on 2008-06-15
Nice! All this time i had been annoyed by vlc...

---

### Post by Eridor on 2008-06-18
Hello, the same issue appeared with my vlc player too so I tried the following notes(replace with m, u, I've tried notes to replace with F or erase everything a let there just vlc) but none of them worked. Also, when I had there m or u, when trying to play more items(like about ten songs - they are usually put into one playlist), somehow happened that many windows with vlc player opened and I couldn't shut them down any way so I had to switch off the whole computer(even restart didn't work). Didn't try with F or just vlc but expect the same.

Any clues?:confused:I would be much thankful to you.

---

### Post by potam on 2008-06-21
Strange issue. %m is the only right solution, forget %u and others. And these works only if you use Nautilus, 'cause %m and others are the part of Nautilus. I tried to open a lot of mp3, and yes, vlc %m puts them into one playlist.

---

### Post by Eridor on 2008-06-23
I tried it once more but it was just the same. Subtitles don't work properly(even when the film and subtitles has the same name, even without spaces), then I tried to open more mp3 using nautilus and I had to restart my machine - I shut all the processes called vlc down but the sound didn't stop but still it was like ten songs playing together - just mess. There was no running vlc process but it was still playing. I have no idea why is this happening.:confused::confused::confused:

---

### Post by whitewidow01 on 2008-08-03
the reason vlc dont show the subtitle auto. is because the searchpad folder is set to ./subtitle so it looks only there, now i want it to look in the same folder as were i loaded the movie (in windows this is the case..)
iam sure there is a command for this and i would like to know it..
what i can do is make a folder and put all my subtitles in there then it will load auto. when i open a movie but idont want this..

So anybody know the simple command for vlc/ubuntu to look in the same folder as were i loaded the movie?? 

whitewidow01

---

### Post by whitewidow01 on 2008-08-03
lol also vlc cant handly [ ] when it loads subs auto.
but when u manualy load a sub file, with [ ] in it, it does work...
ihad blabla[2006].srt  and didnt work
ichanged blabla2006.srt   and worked..
but when i load manualy blabla[2006].srt it also works..

now i created a folder /home/whitewidow/subtitles/
and put this in searchfolder for subtitles in vlc
ican put all subs in there (whitout [ ] in the name)
and it loads automaticly.
but.. ididnt want this, iwant it to load out of the folder were i loaded the movie (whitout manualy selecting the sub ofc.)

weird things with vlc... iwould use totem but it showed weird lines in some movies, geuss the codec didnt work correct (yes i installed divx vidx codecs)

---

### Post by davidw89 on 2008-08-05
Where is Open ---> with

---

### Post by whitewidow01 on 2008-08-05
open with?
   what u wanne do?

---

### Post by fujikofujio on 2008-08-17
OMG!!! Thanks a million, I've been having this problem on ubuntu and I was close to tears you guys saved me :)

---

### Post by legends2k on 2008-09-21
It worked for me. Thanks a lot! :)

---

### Post by detroit/zero on 2008-10-07
%u didn't work at all, but %m worked like a charm for me.

---

### Post by chirucam on 2009-02-12
hello guys, im new to ubuntu.. please let me know how to do this---- go to/usr/share/applications.  i have the same problem of vlc not playing the subtitles.. thaks a lot.

---

### Post by mc4man on 2009-02-12
If you are using **8.04**  there is no reason to go to /usr/share to change launch command.

In a terminal run this 
```
alacarte
```

In the pop up on the left side scroll down and highlight Sound & Video . On the right side right click on vlc -> properties.
Change the command from vlc %U to either of these

```
vlc %f
```

```
vlc %m
```


Edit: if you wish to have vlc be the default (autorun) player for dvd video disks the easiest way for beginners is here for 8.04  ( there is a link out for how to do additional players, different default actions (more for when your comfortable

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

defaults are switched in 'file management' (can be enabled when your in alacarte in the 'Preferences' listing. (then found in System -> preferences -> file managenent

Or run this in a terminal
```
nautilus-file-management-properties
```

---

### Post by detroit/zero on 2009-02-12
> **chirucam said:**
> hello guys, im new to ubuntu.. please let me know how to do this---- go to/usr/share/applications.  i have the same problem of vlc not playing the subtitles.. thaks a lot.
You need to edit the VLC launcher file which is located in /usr/share/applications. [The third post in the thread]("http://ubuntuforums.org/showpost.php?p=4851259&postcount=3") has instructions. If **%u** doesn't work, use **%m** instead. (That's what I had to do.)

---

### Post by chirucam on 2009-02-12
wow, it worked absolutely fine..thanks everyone.. thanks mc4man.

---

### Post by potam on 2009-02-13
I just wondering that this problem / bug still exists. Almost a year old problem, lol.

---

### Post by Manikandanc on 2009-02-25
I use 8.10. I too had the same problem. The font file specified in the Preferences->Subtitles&OSD was not in place. Updated the path and got it working.

Hope this helps.

---

