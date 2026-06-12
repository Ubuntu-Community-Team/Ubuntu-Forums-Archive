---
title: "Rhythmbox convert mp3"
date: 2010-09-15
forum: Multimedia Software
---

### Post by jmdlcar on 2010-09-15
Can Rhythmbox convert mp3 files? If so how. I found mp3 in the edit part but don't know how to add it.

---

### Post by howefield on 2010-09-15
> **jmdlcar said:**
> Can Rhythmbox convert mp3 files? If so how. I found mp3 in the edit part but don't know how to add it.

What format do you want to convert your mp3 files to ?

---

### Post by jmdlcar on 2010-09-15
I want to convert my cd to mp3.

---

### Post by howefield on 2010-09-15
> **jmdlcar said:**
> I want to convert my cd to mp3.

So you have been into the Edit menu and selected Preferences, then in the Music tab, selected your Preferred format (CD Quality, MP3 (.MP3 type).

Then with the tracks on your CD selected for copying, press the Copy button on the toolbar, (far right)

---

### Post by jmdlcar on 2010-09-15
> So you have been into the Edit menu and selected Preferences, then in the Music tab, selected your Preferred format (CD Quality, MP3 (.MP3 type).

Then with the tracks on your CD selected for copying, press the Copy button on the toolbar, (far right) 

When I click on "(CD Quality, MP3 (.MP3 type)" do I click on New or Edit or what do I do from here cause I can't get to from that point on.

---

### Post by howefield on 2010-09-15
> **jmdlcar said:**
> When I click on "(CD Quality, MP3 (.MP3 type)" do I click on New or Edit or what do I do from here cause I can't get to from that point on.

Click close, that's you selected the format for copying the track. You only need to press the Edit button if you want to change the default parameters for that selection.

---

### Post by jmdlcar on 2010-09-15
Let me start all over.

1. Went to Edit menu and selected Preferences, then in the Music tab, selected your Preferred format I don't see this (CD Quality, MP3 (.MP3 type). 

2. All I see is flac, ogg, wav and spx.

3 Now how can I add CD Quality, MP3 cause it not there.

---

### Post by Yellow Pasque on 2010-09-15
You'll need gstreamer-plugins-bad package to do that (or even better, enable the "partner" repository in System->Administration->Software Sources, and get the gstreamer-plugins-fluendo-mp3 package, assuming it's legal in your country ;) )

---

### Post by jmdlcar on 2010-09-15
Went there I don't see enable the "partner" repository.

---

### Post by howefield on 2010-09-15
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Go to System > Administration > Software Sources.

Go into the Other Software tab, and place a check mark beside the partner repository, probably the top one in the list. 

Then reload your package sources.

---

### Post by jmdlcar on 2010-09-15
I didn't get it to work yet so right now I'm just going to convert them to FLAC.

---

### Post by Tweak42 on 2010-09-29
I had the same problem and fixed it by installing ubuntu-restricted-extras package.  I think you need to enable the repository labeled "Software restricted by copyright or legal issues (multiverse)" for the package to show up.

Clue was in this thread:
[http://ubuntuforums.org/showthread.php?t=1190425](http://ubuntuforums.org/showthread.php?t=1190425)

---

