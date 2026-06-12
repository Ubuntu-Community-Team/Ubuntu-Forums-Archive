---
title: "Sound everywhere.. except firefox."
date: 2008-05-20
forum: Multimedia Software
---

### Post by DavidGX on 2008-05-20
I use a USB headset. Audio works everywhere else, linux sound effects, VLC media player, etc. The one area it doesn't work is firefox. I don't hear sound from youtube, flash or anything else.

In the sound settings I have everything set to "USB Audio" and the mixer set to "Microsoft LifeChat LX-3000 (Alsa mixer)"

I'm on Hardy Herron, AMD64. I'm using the Microsoft LifeChat LX-3000 USB headset.

Any ideas on how I can tell firefox to use the headset?

---

### Post by Yellow Pasque on 2008-05-20
Try:
```
sudo apt-get install libflashsupport
```

If that doesn't work, try starting firefox from the terminal to see if it's outputting error messages.

---

### Post by DavidGX on 2008-05-20
I installed libflashsupport, restarted and still nothing. I started firefox via a terminal and got no error messages while normal browsing or attempting to watch a youtube video.

---

### Post by DavidGX on 2008-05-22
After un-muting the laptops speakers, it seems that's what firefox seems to want to use. Is there any way to tell firefox to use my USB headset?

---

### Post by DavidGX on 2008-05-24
So.... any ideas?

---

### Post by DavidGX on 2008-05-25
Nothing yet..

---

### Post by DavidGX on 2008-05-27
Nothing yet.

---

### Post by swiftacle on 2008-05-29
I'm having the same issue, except I have a desktop with the audio going through my JVC amplifier. Totem and Rhythmbox work great, VLC and Firefox for some reason shoot the sound through the headphones plug on the front of the machine.

I tried running Firefox through the terminal and got these errors (over and over again):

(npviewer.bin:8265): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:8265): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

Any help?

---

### Post by minky311 on 2008-08-30
I had this same problem except with a usb sound adapter. 
I just changed the default sound device by following this guide [http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound)
It is about halfway down the page where it says configuring default sound cards.

---

