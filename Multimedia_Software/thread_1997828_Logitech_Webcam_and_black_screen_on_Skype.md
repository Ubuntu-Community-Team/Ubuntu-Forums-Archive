---
title: "Logitech Webcam and black screen on Skype"
date: 2012-06-05
forum: Multimedia Software
---

### Post by enricox on 2012-06-05
[FONT=Times New Roman, serif]I am using Ubuntu 10.04.4 32 bit Lucid Lynx Logitech Quickcam E35000 .The problem is about visualizing video using my webcam on skype.
Using lsusb e lsmod | grep videodev I can see that the webcam is recognized and the driver uvcvideo are installed.
When I use skype,uvc parameters and id are correct, la webcam is on, but the screen is black.
Just to give you an idea about the problem:[/FONT]
 [FONT=Times New Roman, serif]lsusb:
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:002a Hewlett-Packard
Bus 002 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
 [FONT=Times New Roman, serif]lsmod | grep videodev:[/FONT]
 [FONT=Times New Roman, serif]videodev               34457  1 uvcvideo[/FONT]
 [FONT=Times New Roman, serif]v4l1_compat            13251  2 uvcvideo,videodev[/FONT]
 [FONT=Times New Roman, serif]On Internet I found this solution and it seems the only one:
preload this library LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype[/FONT]
 [FONT=Times New Roman, serif]The point is that it doesn't works.[/FONT]
 [FONT=Times New Roman, serif]locate v4l1compat.so:
/usr/lib/libv4l/v4l1compat.so[/FONT]
 [FONT=Times New Roman, serif]It seems that it cannot preload the library launching skype.[/FONT]
 [FONT=Times New Roman, serif]Any suggestion is welcome?[/FONT]
 [FONT=Times New Roman, serif]Thanks![/FONT]
 [FONT=Times New Roman, serif]Enrico[/FONT]

---

### Post by onecrustybaker on 2012-06-09
Hi i found this usefull workaround while trying to get my webcam working, it worked for me, hope it works for you.

First you will need to make sure you have 
libv4l-0 installed.

If you have installed Ubuntu restricted extras 
then you should already have it if not open Software 
Centre and install Ubuntu restricted extras from there.

Once this is done open a Terminal and copy 
and paste the following command

sudo gedit /usr/share/applications/skype.desktop

After you have provided your password a 
text editor will open. Line 4 should look like this

Exec=skype

Replace with this text

Exec=bash -c 'LD_PRELOAD=
/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'

Save and exit the text editor and close the terminal. 
Now you can open Skype and test your 
webcam via 'options' then 'video devices'

---

