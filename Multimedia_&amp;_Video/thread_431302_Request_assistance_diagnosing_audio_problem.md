---
title: "Request assistance diagnosing audio problem"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by OmahaVike on 2007-05-02
I'd really love some help/direction to diagnose an audio problem I'm having.  Thanks to anyone who can point me north/south/east/west.

Set up 6.06 LTS with one user, and can only hear the intro congas.  Once I log in, there is no sound available.  Rules out soundcard.  Just to prove it, I added another user and logged in as that person.  Sound fully works, including after login.  Soundcard is operational.

Thus, it has to be somewhere in the settings for my primary user.  Compared settings between the two users in System/Pref/Sound and also in the speaker icon up in the panel.  Both users match up.

So, I'm stuck.  Would someone be so kind as to help me look in other spots for comparison?  I'd love to get down into shell to compare user settings, but don't even know where to begin looking.

Very much appreciated for any and all help you might provide.

---

### Post by Richard Kut on 2007-05-04
Hey Omaha, you could take a look in the panel menu under System--> Administration --> Users and Groups. Select a user and click on the Properties button. Select the tab entitled User Privileges. Now make sure that the selected user has a check mark next to the item entitled Use Audio Devices. Save the changes and exit the user applet. Then logout and back in as the user. Please update this post with your findings. Goos luck! :)

---

### Post by OmahaVike on 2007-05-09
Thanks Richard.  No discrepancies between users in which you mentiond.  _However, check this out..._

Did a find on "sound" to see the discrepancies between users:

User that has audio:
```

cd .gnome
root@mainmachine:/home/kris/.gnome# ls
gnome-vfs

(change over to gnome2)

root@mainmachine:/home/kris/.gnome2# ls
accels  keyrings  nautilus-scripts  panel2.d  share


```

User that does NOT have audio
```

pfinn@mainmachine:~/.gnome$ ls
apps  gnome-vfs  sound

(change over to gnome2)

pfinn@mainmachine:~/.gnome2$ ls
Dia          evince                gnomebaker          panel2.d      yelp.d
EtherApe     file-roller           hal-device-manager  share
accels       gedit-2               keyrings            sound
alacarte     gedit-metadata.xml    main                totem-addons
bug-buddy.d  gnome-volume-control  nautilus-scripts    yelp

```

Notice how the user who does NOT have audio actually has a subdirectly called "sound"?  Wierd.  Thinking I may just wax and reproduce the settings for the vanilla user (the one that works) over to the one that doesn't.

Any thoughts before I proceed (okay, other than the sarcastic "backup before you do it" comments).

Any and all input is extremely appreciated.  

Of course, if you need more directory comparisons, I'm happy to oblige....

---

### Post by Richard Kut on 2007-05-10
Hey Omaha! How about deleting the sound sub-directory from the user that has the no-sound problem? I figure that it might be the cause of the problem.

Another option would be to drop and then re-create the account of the user that has no sound.

Please let me know which way you decide to go. Good luck!

---

### Post by OmahaVike on 2007-05-27
This is *totally* out of left field.  Was planning on trying your fix if I found the time, but rather recently audio on that one user started working again.  The only explanation could be an update of some sort.  Did not go in and modify anything.  Entirely strange, but in a good way.  Thanks for trying to help Richard.  If it rears its ugly head again, I anticipate I will try your suggested fix.

---

