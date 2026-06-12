---
title: "wifi connection between ubuntu and olympus om-d"
date: 2015-06-26
forum: Multimedia Software
---

### Post by al.adab on 2015-06-26
hello,

i have an Olympus OM-D EM-10 which I can connect (wifi) to a smartphone (to use the latter as a remote control, to upload pics to the phone, etc). 

I can obviously establish a wifi connection between the camera and Ubuntu 14.04...though I don't know whether there's anything i can do with it...

...for instance: would a wifi connection allow me to browse the camera's memory card + upload photos to the pc? if it would, what kind of software would i need to make it work?

thanks in advance

---

### Post by al.adab on 2015-06-26
OK, I got somewhere: 

a) I connect Ubuntu to the Olympus wifi,
b) I type on Firefox the address 192.168.0.10
c) and I see what you see at the pic in attachment (the photos stored in the camera's memory card). 

though it's hardly a great solution: I can view the photos in the browser all right, though I can't batch-upload them to the pc (only one by one and after opening each of them). 

is there a chance i can do that through "browse network > windows network"? I tried but when i double-click on windows network nothing happens...

---

### Post by Parleur on 2015-12-25
Hi, i have the same problem.
There is a nice guy "Mauricio Jost" who has writen a script to download the files direct from the camera. All type of files!
I have found him on a forum at "DPreview".
He publiced his work on "github"
He owns a M10 as well.
Google for it.
We are still in conversation by email, he wants to improve some functions.
My camera is a Olympus OM D E M10 mark 2, computer is desktop with Ubuntu 14.04.3 LTS 64. I use a temporary usb dongle for communication with the camera. You have to establish peer to peer communication. Not by home network.

---

### Post by coldraven on 2015-12-25
You could try using gPhoto it does support some Olympus cameras or you could follow the instructions and email  the developers.
> To report a not yet supported camera to the gphoto development team follow the instructions below: 
[LIST]
[*]If it a USB mass storage based camera (appearing like a USB stick or  USB drive) it is mounted by your operating system and not gphoto2. In  this case a report to us is not necessary.
[*]Record the output of lsusb to get the USB ids.
[*]Record the output of gphoto2 --auto-detect to see if it is detected in a generic way, or by another name. If it is detected already, run the steps below:
[*]Record the output of LANG=C gphoto2 --summary >summary.txt to get generic summary information into the summary.txt file.
[*]Record the output of LANG=C gphoto2 --list-all-config >config.txt to get the configuration tree into the config.txt file.
[*]Record the output of gphoto2 --capture-image to see if capture works already.
[/LIST]
 Mail the output results with the camera name to [email]gphoto-devel@lists.sourceforge.net[/email].

[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

---

### Post by Bucky Ball on 2015-12-25
Maybe see if you can discover the protocol it uses to transfer files to the phone. FTP? Samba? Or something else ... :-k

gPhoto shows promise.

---

### Post by al.adab on 2016-05-11
a very belated thanx tons for suggestions and ideas - was away and couldn't reply sooner. 
I'm going to look into gPhoto and Mauricio Jost. Will post feedback when I can.

---

