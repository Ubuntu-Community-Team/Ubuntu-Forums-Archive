---
title: "recordMyDesktop - How to install + find and select USB audio device."
date: 2009-04-06
forum: Multimedia Software
---

### Post by webkris on 2009-04-06
Great desktop recorder!
Get it by typing:

Terminal:
```
sudo apt-get install recordmydesktop
```

Now get the GUI - gtk-recordMyDesktop (*a search for recordmy found it under all applications*)
Applications - Add / Remove Programs:
[IMG]http://planetkris.com/misc/Ubuntu/recordmydesktop_add.png[/IMG]

Plug in your USB Mic and configure your sound preferences:
[IMG]http://planetkris.com/misc/Ubuntu/recordmydesktop_soundpref.png[/IMG]

You want your sound capture to come from the USB Headset. If it doesn't show up here, recordmydesktop won't see it, and you need to get that running before continuing (beyond the scope of this how to)

Set your microphone capture volume. You may have to add the recording tab under preferences.
[IMG]http://planetkris.com/misc/Ubuntu/recordmydesktop_micvol.png[/IMG]

At this point I tested my device with Sound Recorder. Tested Okay!

Now, this is the part that took me 2 hours to figure out. :D
You don't need a JACK audio server, you just need to select the device via the ALSA hardware ID, which is NOT apparent in this GUI.

To find it, type: **arecord -l**  (*useful future command: aplay -l shows you players, amidi -l shows midi devices, etc.*)

```
kris@phobosx:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kris@phobosx:~$ 

```

Now I know that my Headset is at hw:1,0 - yours may differ.
Pop that into the Sound tab under the recordMyDesktop: Advanced settings - Applications / Sound and Video / gtk-recordMyDesktop
[IMG]http://planetkris.com/misc/Ubuntu/recordmydesktop_advanced.png[/IMG]

...and that's how to get recordMyDesktop working with a USB Headset - without installing jack.

- Kris

---

### Post by rmcellig on 2009-09-08
I am a Mac user trying to get used to Ubuntu. Your description helped me big time!! The only problem I get sometimes is static on my voice when recording a screencast. What could be causing this. Works fine in Sound Recorder.

---

### Post by AlexGrim on 2009-10-04
I'm actually a deticated Fedora user, but trying to find how to use my studio mic with gtk-r* has been bugging the sht out of me for months. I came across this post, and owe you a thanx.

---

### Post by libster on 2012-02-13
Thank you x 10, Kris!  Still timely after almost 3 years. You probably saved me
way more than 2 hours :) your instructions worked perfectly getting sound from
my HP Deluxe WebCam.

Libster
(still on 10.4 - goal to upgrade this year!)

---

