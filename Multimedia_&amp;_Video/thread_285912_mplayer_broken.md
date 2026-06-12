---
title: "mplayer broken"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by BlueStreak on 2006-10-27
mplayer was working fine but suddenly when I try to play a video file it will start to open (the mplayer windows will pop up briefly) then just disappear with no errors.  I'm not sure what to do from here so any help is appreciated.

---

### Post by n00b0id on 2006-10-27
start it from a console=terminal by typing 'mplayer &' and try to get it to disappear again, then reply here with the error message thats printed

---

### Post by BlueStreak on 2006-10-27
I tried that and i got a bunch of info that looked similar to a man page, no errors listed.

---

### Post by dik666 on 2006-10-27
Take a look to see if you have any zombie mplayer processes running.  If you do, kill them and see if this fixes the problem.

---

### Post by BlueStreak on 2006-10-27
Tried that, couldn't find anything.  Rebooted just for the heck of it, no luck.

---

### Post by tnasniv on 2006-10-27
had the same prob:
sudo apt-get install mplayer --reinstall then worked

---

### Post by skymt on 2006-10-27
> **BlueStreak said:**
> I tried that and i got a bunch of info that looked similar to a man page, no errors listed.

You want "gmplayer" not "mplayer", assuming you want the GUI version of mplayer.

---

### Post by BlueStreak on 2006-10-27
well just went with the windows style repair of re-installing and it works fine now.  Thanks

---

