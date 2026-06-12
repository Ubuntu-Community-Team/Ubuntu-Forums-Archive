---
title: "infrared remote"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by cristi.falcas on 2007-05-15
Hy, can someone help me with configuring my remote control?

If I do "input-events 4" (4 is my remote) I can see that all my keys from the remote are working. Example: 
15:01:31.919029: EV_KEY KEY_CHANNELDOWN pressed
15:01:31.919032: EV_SYN code=0 value=0
15:01:31.920040: EV_KEY KEY_CHANNELDOWN released
15:01:31.920041: EV_SYN code=0 value=0
15:01:35.025256: EV_KEY KEY_CHANNELUP pressed
15:01:35.025259: EV_SYN code=0 value=0
15:01:35.027256: EV_KEY KEY_CHANNELUP released
15:01:35.027258: EV_SYN code=0 value=0
15:01:35.940029: EV_KEY KEY_VOLUMEDOWN pressed
15:01:35.940032: EV_SYN code=0 value=0
15:01:35.941029: EV_KEY KEY_VOLUMEDOWN released
15:01:35.941030: EV_SYN code=0 value=0

But if I test it with "showkey -u", only very few keys work: volume, play/pause, stop and the number. Those keys are working also in gnome in various programs. 

How can I configure the keys to do specific things? For example, if I press the Video button to start a program (kdetv for me) or if I press "Full screen" to set the programs in full screen mode. Those 2 keys are not recognixed by gnome. Or to change the movie in totem if I press CH_UP or CH_DOWN. 

Do I have to do something with setkeycodes? How do I take the codes of the keys I press?

One more thing. Until now, when I pressed the media key, rhythmbox was started. I went to "Keyboard shortcuts" and changed the "Lauch Music Player" from the default with what I had the remote was sending and it stopped working. Can I put the defaults back somehow? 

I don't know if I made myself clear, but any help is wolcome.

Thank you.

---

### Post by barney_1 on 2007-05-15
You need to make your own lircd.conf file:

[https://help.ubuntu.com/community/Install_Lirc_Feisty?highlight=%28lirc%29#head-df5eb79017ad18224d2f5a517ca4ba2ef446e373](https://help.ubuntu.com/community/Install_Lirc_Feisty?highlight=%28lirc%29#head-df5eb79017ad18224d2f5a517ca4ba2ef446e373)

---

### Post by cristi.falcas on 2007-05-15
I have the configuration file from lirc page. 
I don't know why showkey -u shows only a few keys working.
How can I see the codes from the other buttons?

---

### Post by cristi.falcas on 2007-05-19
I put my remote as a keyboard in xorg.conf. Now it seems that xev can see all my keys. 
I have to play from here now.

---

### Post by RawMustard on 2007-05-21
> 
I put my remote as a keyboard in xorg.conf. Now it seems that xev can see all my keys.
I have to play from here now.

That's interesting!  How did you find the correct driver for to put into xorg.conf and what layout did you pick to start with?

I'm trying a similar thing with an Asus remote that has 95% of keys working without even installing lirc.  Would love to get the remaining keys seen to xev at least so I can try to re-map them.

---

### Post by cristi.falcas on 2007-05-22
This is the config I use:

Section "InputDevice"
         Identifier  "remote"
         Driver      "evdev"
         Option      "Name" "cx88 IR (Leadtek Winfast 2000XP"
         Option      "Device" "/dev/input/event4"
EndSection

Section "ServerLayout"
....
    InputDevice    "remote" "SendCoreEvents" "True"
EndSection

Now xev recognized the keys sent by my remote, but input-events and lirc don't. And I have some codes overlapping: POWER and ZOOM and some other 2.

So, still working on it.

---

### Post by RawMustard on 2007-05-23
Hmm That didn't work for me unfortunately.  Back to the drawing board!

---

