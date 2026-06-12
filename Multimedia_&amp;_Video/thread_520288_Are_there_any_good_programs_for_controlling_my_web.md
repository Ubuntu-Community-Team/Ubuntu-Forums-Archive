---
title: "Are there any good programs for controlling my webcam?"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by ownaginatious on 2007-08-08
I have a logitech orbit quickcam (not the megapixel one with all the cool features :() and I've been wondering if there are any programs that would allow me to record video, take pictures.etc, while also having support for the pan and tilt features that the webcam possesses.

What would be really neat, which I couldn't find even in windows (although I didn't look very hard) is some sort of server application that would allow me to view my webcam through a browser window and control the pan and tilt. It's was always a hassle having to go through some RDC program from some other computer to view my webcam when I used windows :p.

[SIZE="4"]Any suggestions would be much appreciated, thanks :)[/SIZE]

---

### Post by kevinlyfellow on 2007-08-08
> **ownaginatious said:**
> I have a logitech orbit quickcam (not the megapixel one with all the cool features :() and I've been wondering if there are any programs that would allow me to record video, take pictures.etc, while also having support for the pan and tilt features that the webcam possesses.

What would be really neat, which I couldn't find even in windows (although I didn't look very hard) is some sort of server application that would allow me to view my webcam through a browser window and control the pan and tilt. It's was always a hassle having to go through some RDC program from some other computer to view my webcam when I used windows :p.

[SIZE="4"]Any suggestions would be much appreciated, thanks :)[/SIZE]

Any suggestions?  Well, I use the command line program streamer.

---

### Post by ownaginatious on 2007-08-08
> **kevinlyfellow said:**
> Any suggestions?  Well, I use the command line program streamer.

...I have no idea what that is :p Sorry, I'm new to this linux stuff :p

---

### Post by kevinlyfellow on 2007-08-08
:-) [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
you can install it by the command 
```
sudo apt-get install streamer
```

Then there are tons of settings for it
```
streamer --help
```

Unfortunately, this is the only program that I've found for linux that succeeds in recording video from my webcam

I usually record doing this (nice and easy huh?).  This particular command records video for 1 minute.
```
streamer -r 23 -j 75 -s 640x480 -t 00:01:00 -o movie.avi -f jpeg -F mono16
```

For quick check to see if your camera works, install camorama
```
sudo apt-get install camorama
```

---

### Post by foxholeunder on 2007-08-08
For myself, I do not use a webcam... However, I recently set my sister up with an Ubuntu box and she was wondering the same thing of which I unfortunately did not have an answer for.

However, here was our temporary solution (assuming your Webcam came with a software disc):

Install Wine (open up a terminal and type)
```

sudo apt-get install wine

```

enter your password when prompted
and press 'y' when prompted to continue installing

```

sudo apt-get update

``` 

Once wine is installed insert the cd with your webcam software. A window should pop up showing you the contents of the webcam software cd. Identify the file used for installation. Probably called setup.exe or install.exe or similar.

For this next example we are going to assume the file is called setup.exe and that your cdrom location is /media/cdrom0 


In the terminal type:

```

wine /media/cdrom0/setup.exe

```

The webcam software install program should startup. Install like normal on Windows

You can then access the software from Applications > Wine > Programs > Name of Software Vendor > Name of Software Program

This worked as a temporary fix for my sisters webcam untill we locate *nix-equivalents.

I hope this helps at least temporarily. I will be subscribing to this thread to find out what others have to say and will post back my own findings of *nixified webcam software.

---

