---
title: "External dvd-rw drive won't play dvds (but still works otherwise)"
date: 2008-11-08
forum: Multimedia Software
---

### Post by mr.z on 2008-11-08
As the title really..

External usb2 drive. I know it works because it writes dvds no problem and plays data (avi files, and whatever else)

It picks the dvd up and a message "Could not read from resource" is what i'll get on totem. The same goes for 3 other media players i've tried..

So I'm guessing its the old external things rights to do things issue again.

Any ideas as to where to start? surely somebody has had this issue before? (I've looked but not found anything)

Thanks for reading :)

---

### Post by mr.z on 2008-11-08
+ Yes i do have all the relevant dvd restricted extras installed

---

### Post by mc4man on 2008-11-08
Shouldn't be a problem. You haven't mentioned whether your using hardy, intrepid or earlier. Overall doesn't matter but can affect some things.

Most players (exceptions totem and vlc) need the correct dvd device set in their settings/ preferences. Vlc would need you to enter the correct one in file -> open disc (/dev/scdx) unless you used the right click -> 'open with' on the dvd icon.

You'll only see apps that are choices for default dvd movie player in the r. click -> 'open with' unless you go to 'computer' and right click on the icon there. Your given the extra option in 'computer' - 'open with other application'

Run with the drive connected and a dvd inserted to get /dev links

```
sudo lshw -C disk
```

I have noticed that some titles will not play from an external in totem (gstreamer or xine) but will in vlc, mplayer ect. So I'd use vlc to figure out why you can't playback. either pointing it to correct /dev or r. click in computer on the icon

---

