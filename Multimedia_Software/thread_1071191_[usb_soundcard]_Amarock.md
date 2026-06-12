---
title: "[usb soundcard] Amarock"
date: 2009-02-15
forum: Multimedia Software
---

### Post by Phulerock on 2009-02-15
I have just DIY the usbsoundcard use Texas Instrument TI PCM2706. I use ubuntu 8.10 upgraded
I configre in Preference > sound > USB DAC > test OK
Trouble: 
- Amarok only get laptop's speaker out, it can't handle use even though I configure in Confiure Amarok Engin many way.
- login sound still use speaker out !??!

p/s: VLC, Movie player, Banshee etc.. are OK with this usbsound.

I want to ask anyone know how to find the physical device of this usbsoundcard (example: /dev/usbTI). 'Cause I want to start Amarok in command line with output device parameter, can I do this ?

---

### Post by fabietto0102 on 2009-02-16
Hi, I have the same problem, I have a USB-DAC and can't get Amarok to output the sound via the USB-DAC. Instead, it goes out via the pc speakers.
If you solve the issue do you mind update the post please?
Thanks!

---

### Post by markbuntu on 2009-02-16
Try this


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by Phulerock on 2009-02-16
I will try this artical, Thanks super man !
@fabieto: I will update this thread when I success.

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

