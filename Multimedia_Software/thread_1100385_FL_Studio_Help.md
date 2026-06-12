---
title: "FL Studio Help"
date: 2009-03-19
forum: Multimedia Software
---

### Post by djbushido on 2009-03-19
Okay, I got FL Studio up via wine, and even got my registry key in. So I have the ability to save songs.
The problem is that FL Studio apparently uses some weird type of wav file, that it now can't open on Linux. I checked file permissions, and ugo=rwx. So it can't open it's own wav files, but I also checked against mp3's and they can open.
Weird huh? Well, I also tried lmms, and that can open the wav files. The problem is that: 1) I don't want to use lmms, because FL Studio really is nicer, and 2) i don't have the time to go in and render out all of the wav files into potentially something FL Studio can use.
Any ideas or help? BTW, the FL Studio is installed to ~/.wine/drive_c/Program\ Files/Image\ Line/FL\ Studio\ 7/. I didn't know if the ".wine" hidden directory could cause an issue.

---

### Post by jbrevik on 2009-03-19
Are you saving your projects as a FLStudio proprietary  file  or are you exporting them as .wav?

---

### Post by djbushido on 2009-03-19
projects get saved as .flp files.
No, what I meant was that FL Studio can't open the waveform files of the samples that came included with it. I can play them using another program, but FL Studio can't, and that is a very big problem.

---

### Post by jbrevik on 2009-03-19
> **djbushido said:**
> projects get saved as .flp files.
No, what I meant was that FL Studio can't open the waveform files of the samples that came included with it. I can play them using another program, but FL Studio can't, and that is a very big problem.


Take a look at this:
[http://www.winehq.org/pipermail/wine-bugs/2007-August/066693.html](http://www.winehq.org/pipermail/wine-bugs/2007-August/066693.html)

---

### Post by djbushido on 2009-03-20
Thanks, that fixed it!

---

### Post by sparker653 on 2009-03-26
help! i am running fl studio 7 on ubuntu 8.1 through wine.  i am only able to run in demo mode as i am unsure how to incorporate the regkey i have been provided. any help would be greatly appreciated>

---

### Post by djbushido on 2009-03-27
in a terminal, do command "regedit"
This will bring up the wine registry editor, under the file menu, there will be an option to import key, then select the key you have been given.

---

