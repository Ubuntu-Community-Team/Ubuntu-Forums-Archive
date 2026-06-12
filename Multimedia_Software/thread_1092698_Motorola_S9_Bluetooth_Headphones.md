---
title: "Motorola S9 Bluetooth Headphones"
date: 2009-03-10
forum: Multimedia Software
---

### Post by dob99 on 2009-03-10
I recently acquired a pair of Motorola S9 bluetooth headphones. However, I am unable to pair them with my computer - I wish to use them as an alternative to using wired headphones for listening to music and watching movies.

I have Ubuntu 8.10 on my laptop - an Eee PC 901 - and Kubuntu 8.10 on my desktop (with a USB Bluetooth dongle). On Ubuntu, using gnome-bluetooth, I simply get the error message "Pairing with Motorola S9 failed". On Kubuntu, using KBluetooth, the option for an "audio device" (not necessarily the exact phrase) is grayed out. (I checked the code and this is simply hard-coded.)

I have managed to pair the headphones with my phone and a separate computer running Windoze XP (with a different dongle). I can also pair both the laptop and the Kubuntu desktop with my phone for file transfers.

Any help would be greatly appreciated.

---

### Post by resplin on 2009-03-18
I bought the Motorola S9 yesterday. I've spent way too much time tinkering, but I have partial success.

First, I was able to pair by right-clicking on KBluetooth, and selecting Configuration->Input Devices. With the headphones in pairing mode (solid blue light just after turning them on), I clicked on "Add New Devices". It then asked me for the passcode (0000), and paired the device.

With that done, I got music playing through Amarok using the instructions here:
[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

I didn't have to install bluetooth-alsa or bluetooth-btsco. I just had to add the device to .asoundrc and change Amarok to use the Alsa bluetooth device.

I also had to enable additional channels in alsamixer.

The stereo quality (music) is not as good as I expected, but mono (podcasts) is pretty good.

Now if I can just get Ekiga working.

Edit: Forgot to mention that I'm using Kubuntu Hardy 8.04 x64

---

### Post by resplin on 2009-03-18
It looks like ekiga doesn't support bluetooth headsets currently:

[http://wiki.ekiga.org/index.php/Tested_hardware](http://wiki.ekiga.org/index.php/Tested_hardware)
[http://www.mail-archive.com/ekiga-list@gnome.org/msg03135.html](http://www.mail-archive.com/ekiga-list@gnome.org/msg03135.html)

I don't see anything more recent that suggests such support has been added.

I've also noticed that the stereo audio quality has to do with the type of music I'm listening too--the more complex the music the worse it sounds. I don't think it is a connection issue because I'm right next to my laptop (less than two feet from the transmitter). I think it's the compression they use to send the stream to the headphones.

---

