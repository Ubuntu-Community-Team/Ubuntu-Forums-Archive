---
title: "Run a script when exiting mythfrontend"
date: 2012-05-30
forum: Mythbuntu
---

### Post by someitalian123 on 2012-05-30
I found this 

[http://www.mythtv.org/wiki/Delete_recordings.py](http://www.mythtv.org/wiki/Delete_recordings.py)

Is there anyway I can use this script to automatically delete livetv recordings every time I exit mythfrontend?

---

### Post by nickrout on 2012-05-30
Why? They get deleted within a day or 2 anyway. let the system do it's thing.

---

### Post by someitalian123 on 2012-05-30
Yes but they take up a lot of hard disk space for that two days, I don't have a very big hard drive and more of half of my hard disk is used for my windows partition.

---

### Post by anonymousdog on 2012-05-30
Looks like 'delete_recordings.py --livetv=True --force' will auto-delete the LiveTV recordings without a prompt, but I'd experiment to ensure that's the right command line.  Then write a small script that runs the command and configure a system event handler (possibly for 'client disconnected from master backend') in FrontEnd Setup to kick the script.  I think that'd work.

---

### Post by nickrout on 2012-05-30
> **someitalian123 said:**
> Yes but they take up a lot of hard disk space for that two days, I don't have a very big hard drive and more of half of my hard disk is used for my windows partition.

Hard drives are cheap!

---

### Post by someitalian123 on 2012-05-31
> **anonymousdog said:**
> Looks like 'delete_recordings.py --livetv=True --force' will auto-delete the LiveTV recordings without a prompt, but I'd experiment to ensure that's the right command line.  Then write a small script that runs the command and configure a system event handler (possibly for 'client disconnected from master backend') in FrontEnd Setup to kick the script.  I think that'd work.

That almost worked. That deletes every recording, not just livetv ones, so I can't use it.

I need something that will delete the recordings this script list when using --livetv, while excluding the ones it lists with --playbackgroup="Default". I tried '/home/anthony/.mc2xml/delete_recordings.py ' --livetv --int playgroup="Default" But all that did was produce an error.

---

### Post by anonymousdog on 2012-05-31
'delete_recordings.py --recgroup=LiveTV' should select the right recordings too (but doesn't).  :-?

---

### Post by nickrout on 2012-05-31
what version of mythtv are you using? That script is listed as compatible with 0.24.

---

### Post by someitalian123 on 2012-05-31
.25, the version in the ubuntu repos

---

### Post by nickrout on 2012-05-31
> **someitalian123 said:**
> .25, the version in the ubuntu repos


OK well you might like to email the author and check that the script is valid for 0.25. Or post on mythtv-users mailing list as Raymond certainly hangs out there.

---

