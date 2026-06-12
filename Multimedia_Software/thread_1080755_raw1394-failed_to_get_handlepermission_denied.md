---
title: "raw1394-failed to get handle:permission denied"
date: 2009-02-25
forum: Multimedia Software
---

### Post by POWMS on 2009-02-25
Hello
I have loaded dvgrab along with Kino and Kdenlive. Kino says 'raw1394 not loaded' and Kden says device not detected.
I have all the necessary firewire drives loaded under sys/ and various other folders but neither the above will connect thru the firewire.
Running 'dvgrab --frames 200 myfilm-' (Kino help)
I get the following error 'raw1394 - failed to get handle: Permission denied.'
Is there a setting I have failed to check/set?
Thanks.

---

### Post by bolex100 on 2009-03-01
Thing 1:-  I just realized:- Kino is rubbish and freezes.  Even the newest V1.3.2 
Thing 2:- That error means that your firewire doesn't work.  Go here [http://ubuntuforums.org/showthread.php?t=946708&highlight=firewire]("http://ubuntuforums.org/showthread.php?t=946708&highlight=firewire")

---

### Post by POWMS on 2009-03-24
For those with Xubuntu that cannot get the firewire to work as suggested for Ubuntu, try opening Kino thru the terminal as sudo and permission is granted to use raw1394.
I don't know how to change the settings for raw1394 in Xubuntu, but at least now I can download video for editing, yay!!!!!!!!!

---

