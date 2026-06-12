---
title: "Using computer through bluetooth to play music from phone"
date: 2009-05-29
forum: Multimedia Software
---

### Post by ahickey on 2009-05-29
I use my phone as an MP3 player and would like when I'm at my computer running 8.04 to have the phone play through the speakers on my computer using bluetooth

The phone is a Nokia 6300 and is seen over Bluetooth as a storage device and is classified as Phone.

Is this possible with Ubuntu.


Effectively use my computer a bluetooth headset.

---

### Post by Keith_Beef on 2009-05-29
I paired my Nokia 5800 with my Ubuntu 9.04 Sony Vaio. I can right-click on the Gnome Bluetooth applet and select "Browse files on device..." to open a list of paired devices.

In the list, I select "Nokia 5800" then select "Connect".

Nautilus opens a file browser window with the "obex://" protocol, showing two folders, named "C:" and "E:".

The E: folder represents the microSD card, where I have a folder containing a few mp3 files.

If I double click on one of those files, Totem opens, as if it going to play the file, but then an alert pops up.
```
Could not open location; you might not have permissions to open the file.
```

When I right-click on the file and look at its properties, permissions, I get another message.
```
The permissions of "Poem_of_off_and_on.mp3" could not be determined.
```

This looks similar to a problem I have with connecting my Sansa e280, that the permissions cannot be determined...


K.

---

