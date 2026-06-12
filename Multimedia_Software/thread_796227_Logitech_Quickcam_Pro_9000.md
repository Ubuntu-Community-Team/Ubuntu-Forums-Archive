---
title: "Logitech Quickcam Pro 9000"
date: 2008-05-16
forum: Multimedia Software
---

### Post by Roger D on 2008-05-16
Hi

Just bought a Logitech Quickcam Pro 9000 - planned use will be mostly for Skype. I'm told this will work with Hardy, 'out of the box'. I've got Cheese installed, and managed to take one photograph, but now I just get a blank screen.

All advice very welcome. Do I need to install any other pieces of software?

Roger D

---

### Post by hermes0710 on 2008-05-16
Any case the device is already in use?

---

### Post by Roger D on 2008-05-16
Thanks for the response. What do you mean? Are you suggesting it's being used by some other application? How would I tell?

Roger D

---

### Post by hermes0710 on 2008-05-16
In which application do you get the black screen? Have you tried rebooting, running cheese again? Is it still black?

---

### Post by Roger D on 2008-05-16
I rebooted. It sort of worked at first - I managed to record a video, but the time-delay was terrible, and took another picture. But it's stopped working again. I re-boot, start cheese, the activity light comes on the 9000, then goes off, leaving me with a white screen in Cheese.

I'm beginning to wonder whether my processor is up to this sort of task. It's a single core AMD athalon

---

### Post by hermes0710 on 2008-05-16
Reboot and start cheese through a terminal and play with you cam until it messes up. Post the output from the terminal to see what is going on

---

### Post by Roger D on 2008-05-16
He we go. Didn't get far:

roger@roger-desktop-new:~$ cheese
** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/roger/.gnome2/cheese/media/0003.ogg'
Reason: Stream contains no data..

** (cheese:6204): WARNING **: could not load /home/roger/.gnome2/cheese/media/0003.ogg (application/ogg)

---

### Post by hermes0710 on 2008-05-16
Have you any ogg support installed? It seems you are missing something. Can you playback other ogg files? I don't know the packages' names you need but you can proceed searching in Synaptic Package Manager with "Name" filter and "ogg" as mask. Try this and get back to me

PS>If this is the case then just taking photos should not create any problems though... Post your dmesg output as well

---

### Post by vaibshah on 2008-06-17
Hi everyone!

I am new to Ubuntu environment, and am using 6.06 version, which I just upgraded by commands 

sudo apt-get update

sudo apt-get dist-upgrade


How to install the Logitech Quickcam Pro 9000 on this computer?

Thanks ahead!

---

### Post by markbuntu on 2008-06-17
Try using ekiga instead of cheese. It can autodetect your camera and tell you. I had a problem with my logitech Quickcam and found out with ekiga that V4l2 would not detect it. So I got V4l with synaptic and when I selected that in ekiga and clicked detect or whatever, it found it right away with the right name and everything.

V4l is Video for Linux and is the webcam driver.

---

### Post by matkam on 2008-07-05
I am having the same problem. The UVC driver works the first time, but stops working until the next boot. I don't have access to the computer I'm trying to set up at the moment, but dmesg provides a UVC connection error. I suspect the problem may be in the USB audio kernel module, but I'm not sure.

---

### Post by matkam on 2008-07-20
I just upgraded UVC to the latest SVN and I am still getting the same error. I am attaching the shortened dmesg output.

---

### Post by matkam on 2008-07-28
Turns out there is a bug in the webcam where it crashes after a few uses with certain usb controllers (more info [http://www.quickcamteam.net/hcl/linux/logitech-webcams](http://www.quickcamteam.net/hcl/linux/logitech-webcams) ). I solved the problem by connecting the webcam to another usb card.

---

### Post by pandan on 2009-05-02
My error is

> The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 45 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.

Maybe My system is too slow.  It's an AthlonXP 1.6 GHz with 768MB RAM running ubuntu 9.04.
Skype video test works however (Medibuntu, packages: skype-common, skype-static)

---

