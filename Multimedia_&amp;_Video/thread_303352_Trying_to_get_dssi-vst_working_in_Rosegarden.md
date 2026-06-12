---
title: "Trying to get dssi-vst working in Rosegarden"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by auricle on 2006-11-20
Hi,

I am making my first tentative steps into the world of Linux music. I need to play some vst instruments in Rosegarden.

I am using Kubuntu Edgy

I have installed Rosegarden 1.4 (from a deb file I found somewhere), dssi (including some synths) from the Edgy repositories. It all works great with the dssi plugins showing and working in Rosegarden.

The dssi-vst package I installed (taken from [http://www.ubuntuforums.org/showthread.php?t=220398&highlight=dssi-vst](http://www.ubuntuforums.org/showthread.php?t=220398&highlight=dssi-vst)) works if I call a vsti using 

```
any@thing:~$ vsthost exampleinstrument.dll
```

It shows and plays the vsti wonderfully but it does not show up in Rosegarden as a plugin.

Looking around the directories, I noticed that the dssi-vst.deb package installs to a different directory than the other dssi synths (dssi-vst installs to /usr/local/lib and the working soft synths install to /usr/lib) so I copied the dssi-vst files to the same location as the working dssi files but Rosegarden still does not notice the vst plugins.

Has anyone any ideas of how to get this working?

---

### Post by Cylence on 2006-11-23
Yeah, I also tried the same way with no results. Anyone?

---

### Post by pussi on 2006-11-23
You have to put the vst-instruments in /usr/lib/vst
If you want to keep them in your home directory you can symlink it to /usr/lib/vst, for example if your vst .dlls are in /home/auricle/vst:

sudo ln -s /home/auricle/vst /usr/lib/vst

I'm using gentoo so it's possible that the vst-directory is different in ubuntu, but I doubt that. I've also noticed that Rosegarden doesn't recognize vst's if there's some characters in the filename. At least "-" did that, so if you have any problems like that, try renaming the .dll-file.

I hope this helped.
cheers

---

### Post by auricle on 2006-11-23
I have managed to work it out.

There was no need to paste any of the dssi-vst stuff anywhere else.

Here is what I did:

Make sure that all your VSTi instruments are in the folder: /home/*NAME*/vst 

Navigate to the dssi-vst folder

```
cd /usr/local/lib/dssi/dssi-vst
```

Then you need to run the dssi-vst-scanner script while passing the location of your VSTi instruments:

```
VST_PATH=/home/*NAME*/vst ./dssi-vst-scanner
```

You should see the terminal output a load of text. Then, start jack, run Rosegarden and voila! Your instruments should be there ready to record the next hit!

---

### Post by luneo on 2006-11-28
If someone needs Ardour2, Audacity 1.3.2, and some... just go to my site, i have made edgy packages... [http://luneo.zendurl.com]("http://luneo.zendurl.com")

---

### Post by Cylence on 2006-12-04
Thank you, dssi-vst-scanner solved the problem and all my vst plugins showed up. I'm having trouble running Absynth 3 (it works in dssi-vst but hangs Rosegarden), I'll try installing the newest version of Rosegarden and see if that fixes it.

---

### Post by auricle on 2006-12-04
You're welcome.

Absynth works for me but I am having problems with FM7, it does not work at all :(

Also, there are a whole galaxy of free VST instruments over at [www.kvraudio.com](www.kvraudio.com) Plenty of experimentation without wasting money seeing if it works in wine or not.

---

