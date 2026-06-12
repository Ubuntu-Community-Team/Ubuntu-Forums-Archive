---
title: "Webcam problems with skype and cheese"
date: 2012-03-06
forum: Multimedia Software
---

### Post by Pinkar on 2012-03-06
Hello Everybody, im new at this (very new). I just installed ubuntu 11.10 and well it works actually pretty nice (except that i cant use netflix) but the main problem right now is my web cam.

I installed Skype and it runs but at first i noticed that i couldnt se her webcam (who is pretty hot so you can relate to my urgency) and she couldnt see mine. 

At some point i could see her but she couldnt see me, and the next call i was back on square one.

so i try to look for some forums and they say that i should install cheese. I did

It doesnt even run. I click on the icon and it just kidna flashes and nothing happens. The forums also say that i should run it from the terminal, but, well... im a noob so i dont know how to run things from the terminal (i already found the terminal). 

At last in a desperate attempt i run camorama webcam and i can see my beautiful face. so at least the cam is working. but i dont know how to conect it to skype.

Thanks in advance!

---

### Post by Script Warlock on 2012-03-06
Hi welcome to ubuntu forums :)

with regards to your issue this [site]("https://help.ubuntu.com/community/Webcam") might help shed some light to your cam problem. and [here]("https://wiki.ubuntu.com/SkypeWebCams")

if you came across with this command
> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
try this on ubuntu 11.10
> LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so.0 /usr/bin/skype

---

### Post by Pinkar on 2012-03-06
yeah!... well i already tried those before, really not a lot of help cause when i reach parts that say try this comand im really lost, like i should put them in the terminal?

like this:
> echo "#! /bin/sh" > skype-cam-fix
echo "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" >> skype-cam-fix
chmod a+x skype-cam-fix
sudo mv skype-cam-fix /usr/local/bin

i read that and my mind goes blank, where can i get like a jump start in ubuntu coding so i get an idea of what does those lines do and where should i stick them?  

(i know im a noob)

---

### Post by Script Warlock on 2012-03-06
ok will do this step by step. first give us the result of lsusb on the terminal.

---

### Post by aleoo on 2012-03-19
Hi, I have the same problem, these are my results:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0402:5602 ALi Corp. M5602 Video Camera Controller
```

---

### Post by Flywaver on 2012-03-28
> **Script Warlock said:**
> Hi welcome to ubuntu forums :)

with regards to your issue this [site]("https://help.ubuntu.com/community/Webcam") might help shed some light to your cam problem. and [here]("https://wiki.ubuntu.com/SkypeWebCams")

if you came across with this command
 
try this on ubuntu 11.10

for some reason with my 11.10 setup I don't have a libv4l folder anywhere and if I check in synaptic it shows libv4l-0 installed :confused:

It's really annoying because the cam works with camorama but not with skype or empathy (3.2.0.1)...and when I run v4l2ucp it says "unable to get menu item for exposure, auto, index=0 will use unknown" and "unable to get menu item for exposure, auto, index=2 will use unknown" but then the app opens and if I go to Start Preview it opens the cam with MPlayer :confused:

---

### Post by aleoo on 2012-04-08
> **aleoo said:**
> Hi, I have the same problem, these are my results:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0402:5602 ALi Corp. M5602 Video Camera Controller
```

Is anybody trying 12.04?

---

### Post by aleoo on 2012-05-01
> **aleoo said:**
> Is anybody trying 12.04?

Can anybody tell me if, using the latest version 12.04, the problem persists?

---

### Post by mörgæs on 2012-05-03
No, but you can tell us. Just try a live boot.

By the way, please don't cross-post.

---

### Post by rich4676 on 2012-05-09
HI - another noob here - having similar problems with webcam on Ubuntu 11.10:

1) Picture is upside down (checking other forums to address this)
2) Cheese not working.  When I run Cheese it flashes for a second and that's it.  When I run from command line I get the following message:

richard@richard-UL30A:~$ cheese

(cheese:17396): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(Same text repeats 5 more times)

(cheese:17396): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:17396): Gdk-WARNING **: The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 950 error_code 9 request_code 137 minor_code 9)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

BTW - Webcam is a (built-in) Suyin on an ASUS X32A

Any help very gratefully received - thanks

---

### Post by Tech226 on 2012-05-09
Perhaps the following is helpful?

[http://ubuntuforums.org/showthread.php?t=1976566](http://ubuntuforums.org/showthread.php?t=1976566)

---

### Post by kimberley on 2012-06-06
I have just upgraded to 12.4 (absolutely no problems) from xubuntu 11.10 but cannot get my Quickcam Messenger webcam to work on either cheese or skype - it worked previously on cheese. The webcam  is v412: USB (046d: 08da) and I have auto detect highlighted.

Can someone please help.:confused:

---

### Post by kimberley on 2012-06-06
> **kimberley said:**
> I have just upgraded to 12.4 (absolutely no problems) from xubuntu 11.10 but cannot get my Quickcam Messenger webcam to work on either cheese or skype - it worked previously on cheese. The webcam  is v412: USB (046d: 08da) and I have auto detect highlighted.

Can someone please help.:confused:
Problem now solved with many thanks to Tech 226

I was a little too quick as problem is only solved if I keep using bin bash code on terminal window as suggested by Tech 226. Webcam still does not work if I launch  Skype.  Does anyone know how to fix this?

---

