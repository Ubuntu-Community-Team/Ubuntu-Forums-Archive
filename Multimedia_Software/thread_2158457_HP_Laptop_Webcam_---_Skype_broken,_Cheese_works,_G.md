---
title: "HP Laptop Webcam --- Skype broken, Cheese works, Google Talk works, GStreamer broken"
date: 2013-06-29
forum: Multimedia Software
---

### Post by jewels. on 2013-06-29
HP Pavilion Laptop
Ubuntu 13.04 Raring Ringtail (UEFI dual boot Win8 & Ubuntu) 
64-bit system

The onboard webcam shows black in Skype.

ATTEMPS TO FIX:
1. Test Cheese - onboard webcam works great.
2. Test Google Talk/Chat - onboard webcam works great.  No issues.
3. Install Skype from the Software Center - webcam still shows black in Skype.
4. Remove previous Skype version completely.
```
>sudo apt-get autoremove --purge skype
cd /var/cache/apt/archives/
ls
sudo rm *skype*.deb
```
5. Download Ubuntu 12.04 multiarch .deb file directly from Skype - webcam shows black in Skype.
6. Remove previous Skype version completely.
```
>sudo apt-get autoremove --purge skype
cd /var/cache/apt/archives/
ls
sudo rm *skype*.deb
```
7. Install earlier version of Skype 4.0, and force Synaptic to not upgrade - webcam shows black in Skype.
```
>sudo wget -O skype [http://download.skype.com/linux/skype-ubuntu_4.0.0.8-1_amd64.deb](http://download.skype.com/linux/skype-ubuntu_4.0.0.8-1_amd64.deb)
sudo apt-get install libxss1 lib32stdc++6 lib32asound2 ia32-libs libc6-i386 lib32gcc1
sudo dpkg -i skype
sudo apt-get -f install && sudo rm skype
```
8. Try this command to startup Skype - webcam still shows black in Skype.
```
>LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l1compat.so skype 
```
9. Attempted to force Skype to use older architecture - webcam still shows black in Skype
```
>sudo dpkg -i --force-architecture skype-ubuntu*.deb 
```
10. Again attempting to force - webcam still shows black in Skype
```
>sudo dpkg --add-architecture i386
```
11. Ran gstreamer-properties to test video function.
```
> gstreamer-properties

(gstreamer-properties:31001): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:31001): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'

```
Clicking the VIDEO tab, using all possible combinations, webcam is black.
So, obviously, gstreamer is not functioning correctly.  

Here is where I'm stuck.  Gstreamer shows the problem.  How do I fix it?
Does anyone have any suggestions as to what I can do next?

Please be gentle, as I'm not over-experienced in Linux. 
Thanks!
~jewels

---

