---
title: "Problems with Sound Juicer/ Rythmbox - Please Help"
date: 2011-05-19
forum: Multimedia Software
---

### Post by plinx on 2011-05-19
Hey all,  Sound Juicer and Rythmbox have suddenly both stopped retrieving track names on any CD.  I have checked and it is not working for cds which are listed on Music Brains. I uninstalled/reinstalled Sound Juicer and this made no difference. Does anyone know how to fix this?  BTW Asunder will retrieve the names, but I have found that it will freeze often with older cd's I'm ripping.    Thanks for any help, Colin

---

### Post by Howie Spitz on 2011-05-22
I have the same problem. Sound Juicer/Rhythmbox just try to retrieve track listings. Then if I try to submit album on MusicBrainz it points me to the release I am looking for! Rhythmbox 0.12.8/Sound Juicer 2.28.1.
:confused: Ubuntu 10.4

---

### Post by Howie Spitz on 2011-05-29
[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/788921](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/788921)

This is what I'm experiencing. SJ/RB worked fine in May then stopped retrieving album info last week.

---

### Post by karrank% on 2011-05-29
yeah, i just noticed this too, anyone else? Is it a Soundjuicer thing (would other rippers work)exclusively or...?

---

### Post by Yellow Pasque on 2011-05-29
Start sound-juicer from the terminal and see what it says when metadata retrieval fails.

---

### Post by karrank% on 2011-05-29
> **Temüjin said:**
> Start sound-juicer from the terminal and see what it says when metadata retrieval fails.

This CD could not be queried: Cannot find musicbrainz pages on server. Check your server name and port settings.

---

### Post by Yellow Pasque on 2011-05-29
Follow the bug report. That's a pretty serious issue, so I'm sure the Ubuntu devs will get an update out soon.

---

### Post by karrank% on 2011-05-29
> **Temüjin said:**
> Follow the bug report. That's a pretty serious issue, so I'm sure the Ubuntu devs will get an update out soon.

Thanks, started doing just that when I noticed this. Could there be some disagreement between MusicBrainz & Ubuntu? Could that impinge on the long-term loss of this feature? 

Excuse the ignorance, but I'm unacquainted with how these things work. or don't.

---

### Post by Yellow Pasque on 2011-05-29
Well, I guess MusicBrainz changed their address for some reason and that address was a compile time option, which means a package update is needed. It's not a big disagreement or anything like that. Hopefully, Ubuntu will roll out a quick fix and/or change the address to something user-configurable if they think address changes will become common on MusicBrainz's part.

---

### Post by aikiwolfie on 2011-06-02
Sound Juicer works fine for me right now. Rhythmbox can't get CD info. Pretty stupid design to lock these settings away in Rhythmbox. Sound Juicer seems to be configurable through the Configuration Editor.

---

### Post by bayvista on 2011-08-21
You could try 'ripperx'. It seems to use a different data base to sound juicer and I have found it to be OK.

---

### Post by wvandoorne on 2011-08-25
This worked for me:

1. uninstall sound-juicer:
sudo apt-get remove sound-juicer
(or use the Ubuntu-Software-Center)

2. add a new line in the repository. The line reads:
"deb [http://ppa.launchpad.net/phw/musicbrainz/ubuntu](http://ppa.launchpad.net/phw/musicbrainz/ubuntu) lucid main"
(replace the word "lucid" with the version you use if different)

3. reinstall sound-juicer using the Ubuntu-Software-Center

The titels of the songs on my CD showed again because a different Musicbrainz service is used now.
Since the titels are valid now, sound-juicer can handle them again.

---

