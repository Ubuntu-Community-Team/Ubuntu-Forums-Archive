---
title: "How can I read audio cd wav files from command line?"
date: 2009-10-17
forum: Multimedia Software
---

### Post by blavv on 2009-10-17
Hello,

I would like to do the following things from command line:

[LIST=1]
[*]Tell whether a cd media is inserted into the drive (/dev/cdrom).

[*]If the inserted cd is an audio cd, then list its tracks (i.e. wav files).
[/LIST]
From GUI, I can use nautilus to access the wav files (Track 1.wav, Track 2.wav, ... Track n.wav) under "cdda://sr0" -- I can even copy these wav files to another directory by drag-and-drop, but I have no idea how I can access this location from command line. Couldn't find them in /media/cdrom , either.

Isn't there any easy way to do this like so?

```
$ ls -la cdda://sr0
```

Thank you in advance!


Brandon

---

### Post by pastalavista on 2009-10-17
> **blavv said:**
> Hello,

I would like to do the following things from command line:

[LIST=1]
[*]Tell whether a cd media is inserted into the drive (/dev/cdrom).

[*]If the inserted cd is an audio cd, then list its tracks (i.e. wav files).
[/LIST]
From GUI, I can use nautilus to access the wav files (Track 1.wav, Track 2.wav, ... Track n.wav) under "cdda://sr0" -- I can even copy these wav files to another directory by drag-and-drop, but I have no idea how I can access this location from command line. Couldn't find them in /media/cdrom , either.

Isn't there any easy way to do this like so?

```
$ ls -la cdda://sr0
```

Thank you in advance!


Brandon

The CD drive is mounted (usually) in the /media directory so you should probably try ```
ls -la /media/cdrom
``` or possibly```
ls -la /media/cdrom0
```

---

### Post by mc4man on 2009-10-17
not sure what the point is but using ls it would be more like (or sr1)
```
ls -la ~/.gvfs"/cdda mount on sr0"
```

---

### Post by blavv on 2009-10-17
Hello guys, thanks so much for quick replies. =)

I am writing a little ruby script for audio extractions.
# I am aware of great tools like cdparanoia for that exact purpose, but I am doing this more for learning purposes.

I have tried

```
$ ls -la /media/cdrom
```

or 

```
$ ls -la /media/cdrom0
```

but they did not return the Track*.wav files - instead, if the audio cd is an enhanced disc, then the above commands list the data tracks, but no wav files...

Then I tried

```
$ ls -la ~/.gvfs/"cdda mount on sr0"
```

yet it says there is no such directory, but then I realized that my locale is Japanese, so the correct directory name was "cdda &#12364; sr0 &#12395;&#12510;&#12454;&#12531;&#12488;&#12375;&#12414;&#12375;&#12383;" which means the same as "cdda mount on sr0".

Finally,

```
$ ls -la ~/.gvfs/"cdda &#12364; sr0 &#12395;&#12510;&#12454;&#12531;&#12488;&#12375;&#12414;&#12375;&#12383;"
```

This gave me the list of wav files! I can also confirm where the disc is inserted or not by testing if this dir exists or not.

It feels kind of awkward to see a sentence as a directory name like that, but it did solve my problem.

Thank you all again!

---

