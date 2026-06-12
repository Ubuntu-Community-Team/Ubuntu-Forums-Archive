---
title: "USB headset - no volume control whatsoever"
date: 2006-01-23
forum: Multimedia &amp; Video
---

### Post by kjkrum on 2006-01-23
My Logitech USB headset was detected automatically, and it works.  However, there is absolutely no volume control for it.  I found some other threads suggesting that PCM control works where Master does not, but it doesn't work for me.

Running Breezy, fully patched...

---

### Post by FarEast on 2006-01-24
I have a USB sound adapter with C-media sound chip.
I do not have volume control, either :)

BTW Would you please tell me which model it is?
It must be a good item for those who have troubles in configuring
their sound cards.

---

### Post by synd7 on 2006-01-24
sorry wrong thread

---

### Post by encoe on 2006-01-24
same problem here with trust 640U silverline usb headset

---

### Post by FarEast on 2006-01-25
I am not sure, but it may be a 'feature' of low-price USB sound devices.
When I try to decrease volume with main volume on the upper panel,
then sound is off.

I think that it is analog circuits that adjust volume.  I wonder if low-
price USB devices have circuits with capability of gradual volume control.

---

### Post by kjkrum on 2006-01-25
The hardware is definitely capable.  It works in that other OS...

---

### Post by FarEast on 2006-01-25
Hi kjkrum;) ,

My hypothesis may be wrong.
It proved that I have volume control... Only the lower area of the volume slider has no effect.

EDIT:
How about giving a try, if other attempts are not successful?
[http://www.kolmann.at/philipp/linux/usb-headset-buttons/](http://www.kolmann.at/philipp/linux/usb-headset-buttons/)

---

### Post by mpvano on 2006-01-25
Before you give up, try opening a terminal window and using the "official" ALSA mixer. You start it by typing "alsamixer -c n" where "n" is the card number. (0 for the first sound card, 1, for the second, etc.) Your usb device is probably device 1. Once the ugly curses based mixer appears, type "F5" (the function key, that is) to expose ALL the controls. It's possible the volume control has an unexpected name. A common variation is that it's called PCM and ALSA can't figure out if it's the record or playback volume... Many other variations occur, including multiple controls with identical names that don't all show up in simpler mixers....

If any of the controls there vary the volume then there's such a capability available and a smarter mixer than the one built in to gnome may be able to use it.

Also, in some cases the "gnome-volume-control" applet may know about the control name, but just chooses not to display it - try looking in the preferences menu to see if there's an un-enabled control that may be what you need. Do this in both the ALSA and OSS flavors of the mixer.

Unfortunately, many USB devices have no hardware volume controls - the volume control in windows is provided as software for them by windows itself. Not all USB devices in ALSA currently provide such a "software" volume control at the moment.

hope this helps you figure out what's going on...

Mario

---

### Post by vav on 2006-02-01
I got a c-media based usb audio adapter and it's volume control is by going to volume contol device selection and changing the device from the previous (for me intel under alsa) to the new one (for me c-media usb with alsa mixer).

However, even after doing this I was unable to configure my main volume control to control the usb device volume - I have to open up the full audio mixer control to adjust volume.

--vav

---

### Post by FarEast on 2006-02-02
> I was unable to configure my main volume control to control the usb device
> volume - I have to open up the full audio mixer control to adjust volume.

It is the same to you here :).
And there is only one slider(PCM) in the full audio mixer...

---

### Post by kjkrum on 2006-02-05
[QUOTE=mpvano]Also, in some cases the "gnome-volume-control" applet may know about the control name, but just chooses not to display it - try looking in the preferences menu to see if there's an un-enabled control that may be what you need.[/QUOTE]

That was it!  I never noticed that there was a preferences menu.  After changing gnome-volume-control to the correct device and channel, it works.

I wish I could apply the mixer controls to all available devices... oh well.

---

