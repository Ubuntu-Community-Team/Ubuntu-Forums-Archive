---
title: "Miro not working at all in Karmic"
date: 2010-02-11
forum: Multimedia Software
---

### Post by JoJerome on 2010-02-11
- Does not play videos. When I press 'play' the status says "Playing video" but it's not playing and never does.

- Takes an extremely long time to search for videos.

- "Internal Error" crash screen on each startup.

- Have attempted to uninstall and reinstall several times, both from the shell and from KPackageKit. I noticed in the later, there seem to be two versions of Miro: An AMD64 version and an 'all' version. I've tried installing one but not the other to no avail. When I do that, both seem to auto-install.

- Have installed ubuntu-restricted-extras. No change.

Help? I've got my user really addicted to Miro!

---

### Post by JoJerome on 2010-02-12
... And yes, was on a working 'net connection.

- Videos play fine in Dragon Player (though Dragon will not play DVDs - whole other issue).

- Looked under KPackageEdit for "Miro" thinking there might be a codecs package. Nope. Just Miro itself.

Really frustrating as it's worked perfectly on any other system I've installed it on.

---

### Post by monraaf on 2010-02-12
Might be that the database from a previous installation is causing problems. Just rename your ~/.miro directory to something else and let Miro create a new one. e.g.:

```

mv ~/.miro ~/.miro.bak

```

Also Miro has 2 backends for playback, gstreamer and xine. If one is giving you problems try the other one. 

Video->Options->Playback->Video renderer

---

### Post by 2hot6ft2 on 2010-02-12
It works fine on mine but I'm using ubuntu 9.10 so sorry I can't be any help. Like has been mentioned it's probably a codec issue.

---

### Post by JoJerome on 2010-02-12
Thanks all. In an attempt to solve some other issues as well, I'm in the midst of a fresh install. I did a lot of playing around with the network drivers and may have inadvertently screwed something. If I have the same issues, I'll know what to try now!

Although while we're on the subject, DragonPlayer hangs trying to play DVDs. I thought it was just this one laptop (Vaio), but I've installed Karmic on a different laptop (Dell) and exact same thing. Even freezes at the same place about a minute into the FBI warnings. 

Plays movies off the hard drive just fine. But DVDs? No go.

Grrrrrrrrrrrr...........

---

