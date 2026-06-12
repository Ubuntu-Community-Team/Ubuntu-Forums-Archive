---
title: "[SOLVED] Flash and Shockwave not working"
date: 2008-09-12
forum: Multimedia Software
---

### Post by Ghliofris on 2008-09-12
Ok, been dealing with this for a month now, searching the forums, google, yahoo and the likes. I use to be able to watch youtube and play flash games. Now they don't work. Installed Opera and no dice. I cant say for certain, but I think it was after an update.:confused: Embedded music on MySpace doesn't work anymore.

I don't think it is the video card (Nvidia MX400) because it worked before. Could not get my Radeon 9000 pro (another 2 month project).

I think it maybe something not installed or uninstalled on an update, but have no idea what.

If anymore info is needed let me know and I will post it.

Ubuntu 8.04 Hardy
AMD 2000
1 gig RAM
Nvidia MX400 64meg

---

### Post by SunnyRabbiera on 2008-09-12
well shockwave games I can see not working.
did you install flashplayer nonfree?

---

### Post by Ghliofris on 2008-09-12
> **SunnyRabbiera said:**
> well shockwave games I can see not working.
did you install flashplayer nonfree?

yeah, uninstalled it and reinstalled it. used purge when I uninstalled it to make sure.

---

### Post by IanW on 2008-09-12
I've been having similar problems lately with Flash & Firefox.

Try this:-
```

Open Firefox
Click Edit / Preferences
Click the Applications tab
Search for "flash"
Ensure Action is set to "Use Shockwave Flash (in Firefox)"
```

---

### Post by markbuntu on 2008-09-12
If you are using flash 9, you need to get the package

libflashsupport

for it to work properly.
If you have flash 10, you need to remove libflashsupport if you have it installed.

---

### Post by Ghliofris on 2008-09-12
> **IanW said:**
> I've been having similar problems lately with Flash & Firefox.

Try this:-
```

Open Firefox
Click Edit / Preferences
Click the Applications tab
Search for "flash"
Ensure Action is set to "Use Shockwave Flash (in Firefox)"
```

yup, it is marked. Still nogo.

---

### Post by Ghliofris on 2008-09-12
> **markbuntu said:**
> If you are using flash 9, you need to get the package

libflashsupport

for it to work properly.
If you have flash 10, you need to remove libflashsupport if you have it installed.

Yeah, running flash 9 and it is installed, still no go.

---

### Post by markbuntu on 2008-09-13
Is this strictly a flash problem or do you have sound issues with other programs as well?

Are you using 64 bit or 32 bit?

---

### Post by ronnielsen1 on 2008-09-13
If you run the Windows version of firefox in wine you can run shockwave

---

### Post by Ghliofris on 2008-09-13
> **markbuntu said:**
> Is this strictly a flash problem or do you have sound issues with other programs as well?

Are you using 64 bit or 32 bit?

Flash. shockwave  I can listen to other audio files <mp3s) being brodcasted off of web sites ([http://sounds.wavcentral.com/movies/tmbstone/bleed.mp3](http://sounds.wavcentral.com/movies/tmbstone/bleed.mp3))


64 or 32 bit good question. excuse my ignorance, but how can I tell?

---

### Post by poliltimmy on 2008-09-15
Will installing libflashsupport stop the freezing up of my desktop while playing flash? I use 8.04 AMD 64 version

---

### Post by poliltimmy on 2008-09-15
Anyone home?

---

### Post by gandaran on 2008-09-15
> **poliltimmy said:**
> Will installing libflashsupport stop the freezing up of my desktop while playing flash? I use 8.04 AMD 64 version

libflashsupport is only needed if you have a flash 9 sound problem, if you don't have any flash sound problem don't install it, it'll just make things worse.
about the desktop freezes, what is the computer RAM and swap?

---

### Post by poliltimmy on 2008-09-15
2G ram Swap is 3.32G

---

### Post by wesley_of_course on 2008-09-15
Afternoon ;  system - administration - partition editor   will show what you have and how much. Hope this is what your looking for .

---

### Post by poliltimmy on 2008-09-15
i had to install gParted 2G ram swap 3.32G

---

### Post by Ghliofris on 2008-09-17
Got it fixed finally.=D> Thanks to all that replied to this post. 

Followed this: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
Then removed Gnash completely, anything that had to do with Gnash that was installed through Synaptic Package Manager.

Logged off then back on. Got all sounds to work now, system and other sound files, flash and embedded sounds.

---

### Post by wcarr on 2008-09-30
Heres a petition for a linux-friendly shockwave player... [http://www.gopetition.com/petitions/shockwave-on-linux.html](http://www.gopetition.com/petitions/shockwave-on-linux.html)

Spread it around and maybe it will happen!

---

### Post by ralphmcknight on 2009-09-04
i have finally got this working: :-) by comparing 2 systems and finding the difference, as flash / shockwave worked on one and not the other!
anyway, the solution for me was to remove the following:

libswfdec-0.8-0
swfdec-gnome
swfdec-mozilla

these can easily be removed by going into 
system / admin / synaptic package manager.

once these are removed everything may start to work, if it doesnt, remove all the adobe packages ysing the package manager again, then go to the adobe main site and download flash again, i think its the 8.04+ .deb version, just click on the link on their site.  You can then update to a later version, via the package manager again if you like.

the version of shockwave will then show as shockwave flash 10.0 r22.
you can see this in firefox browser / tools / add-ons, in the plugins tab.

then all will work, including tube8.

---

