---
title: "Very rough guide ibm r31 wpa with atheros"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by Ryuhayabusa on 2009-04-21
I have had some success lately with my beloved r31 and will share.

For wpa it seems you have to use a 2.6.24 kernel. I was using the 2.6.15 previously and it did not go well.

At first i encountered the same bug as this

[http://bugzilla.kernel.org/show_bug.cgi?id=10135](http://bugzilla.kernel.org/show_bug.cgi?id=10135)

and found a fix here

[https://wiki.blue-it.org/Thinkpad_R31#General_Info](https://wiki.blue-it.org/Thinkpad_R31#General_Info)


I have implemented the recommended kernel parameters on the generic 2.6.24 kernel. This is done by adding to the list of words after the 'kernel' line.

After upgrading to the new kernel things are running smoothly with network-manager-gnome applet.

I hope this helps anyone with an r31

---

### Post by Ryuhayabusa on 2009-04-23
well i actually spoke too soon. I have had some of the crashes mentioned in the bug. sudden stop of mouse, no response no error message. Unable to logout by ctrl-alt-bkspc.

And i have had some wpa issues as well. It's working at my home with wpa and psk but i can't get it at uni with wpa-enterprise tkip and phase ...V2.

---

### Post by Ryuhayabusa on 2009-04-23
I've changed the home router to WEP and the lockup issues seem to be resolved. We'll see if i get another crash.

---

