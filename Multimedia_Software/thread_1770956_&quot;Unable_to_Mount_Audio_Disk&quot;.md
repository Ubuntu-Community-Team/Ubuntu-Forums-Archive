---
title: "&quot;Unable to Mount Audio Disk&quot;"
date: 2011-05-29
forum: Multimedia Software
---

### Post by wbee on 2011-05-29
Hello,

((I Googled this issue and checked Launchpad and could find nothing current.))

Using Lucid,Rhythmbox,when I insert a compact disk,instead of getting the audio cd icon on the desktop,I get.

Unable to mount audio disk.DBus error freedesktop.DBus.Error.NoReply.:Message did not receive a reply.(timeout by message bus)

Yes,all the hardware connections are correct.

Anybody have any ideas before I submit this as a bug?

------------

Thanks.

---

### Post by wolfen69 on 2011-05-29
If you change the preferences to open with another media player, does it still happen?

---

### Post by wbee on 2011-05-29
wolfen69,

yesbut.:-)

When I changed the preference to VLC,I got the same "unable to mount,etc....." notification.

But when I manually opened VLC,the CD playback works perfectly.

With the preference set to either VLC or Rhythmbox,I can't manually open rhythmbox.

So,thank you for the  work-around to play CDs,but I'm still curious why it malfunctioned.

------------

wbee

---

### Post by edwardoclese on 2011-11-21
I solved this on my machine (broken after upgrade) by installing [FONT=Courier New]gvfs-backends[/FONT] from the Ubuntu Software Center.

---

