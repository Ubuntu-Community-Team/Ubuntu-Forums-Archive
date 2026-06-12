---
title: "How to burn my tv recordings to dvd myth 8.04"
date: 2008-11-19
forum: Mythbuntu
---

### Post by zf3636 on 2008-11-19
Hi can anyone explain the steps needed to burn my tv recording to dvd i have tried using cd/dvd option archive utilities by using myth 8.04

---

### Post by Cresho on 2008-11-19
devede
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

that link shows latest version.

all you need to do is add the files and burn.  Nothing else needed.  it takes almost anything you can throw at it.  I drop my high definition files into it, and it burns my movies just fine.  This program creates an iso file.  Use k3b from "add remove programs" or the latest brasero from getdeb.net (not the one built into the ubuntu cuz its outdated) and burn the iso to dvd.

---

### Post by dmfrey on 2008-11-19
here is the quick and easy...

1. ssh into your account and create the directory in you home folder: mytharchive/temp

2. Go into the MythArchive setup and set this directory as the working directory for MythArchive: /home/<user>/mytharchive/temp

3. If you want to remove commercials go into each recording and start playing it, bring up the menu and select edit.  While in the edit menu, press z to load the cutlist (assuming you have ran commercial flagging on the recording).

4. Go into MythArchive on the Optical Disc menu, select create DVD, add your recordings, selection your disc format and any transcoding options, press finish and wait.

5. and wait
6. and wait :)

After a few hours (depending on your hardware) you newly created dvd should pop out.

Some Notes
==========
1. If you get intermittent audio silence on the dvd, look for and set Always reencode to AC3.
2. In step 2, you need to specify a directory in which your frontend can write to so you set this in your home directory.

I hope this helps you out.

---

### Post by zf3636 on 2008-11-19
Hi thankyou for quick reply will act on the info given both sound good

---

