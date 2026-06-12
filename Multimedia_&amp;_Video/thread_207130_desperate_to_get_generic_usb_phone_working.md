---
title: "desperate to get generic usb phone working"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by theslut on 2006-07-01
I'm using Ubuntu 6.06 and have everything working right except my USB phone.

It's a sumvision phone and works with a generic sound driver in Windows.

Since moving to Ubuntu , plugging the phone into the USB I get a popup notifcation saying a new audio device was plugged in and must be configured.

In the sound control panel it comes up as USB Device 0x4101:0x1302 and is selecable as an ALSA audio device in the new skype beta.

Interesting, pressing the volume button up and down on the phone controls the main volume panel on my desktop taskbar.

However, I cannot seem to get it to work either playing back audio or recording through it.

In skype i get "problem with sound device" error message.

I am so sure this will work and when i get it working i will be extremely happy! Has anyone got any tips or advice on how to get it working?

---

### Post by rpalyvoda on 2006-07-01
Hi,

I had the same problem. Do the following:
a) use Nautilus as a root to delete file /etc/asound.conf
b) then, configure Skype 1.3 to use ALSA
c) reboot

It should now work!

---

### Post by theslut on 2006-07-02
unfortunately, that file is nowhere to be seen :(

---

