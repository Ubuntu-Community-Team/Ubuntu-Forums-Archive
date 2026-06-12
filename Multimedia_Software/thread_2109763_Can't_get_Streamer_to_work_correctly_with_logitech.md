---
title: "Can't get Streamer to work correctly with logitech quickcam"
date: 2013-01-28
forum: Multimedia Software
---

### Post by grey1beard on 2013-01-28
Trying to set up a simple time-lapse webcam for vole watching (!!!) using a logitech quickcam with toshiba satellite A30,2.6Ghz running 12.04LTS, 0-36 kernel. I've set the webcam up using GUVCViewer, and it seems to work OK at 640x480.

I've used *sudo apt-get install streamer*, created a directory on the Desktop to save the pics in, but if I run 
> **streamer -o 0000.jpeg -s 640x480 -j 100 -t 2000 -r 1** 

all I get on Terminal is streams of error-type messages.

I tried reducing the value of t to 120 to try and reduce the data stream, but just got more errors.
I then tried reducing the value of the resolution to 300x200.
This time, I checked my home folder and found a series of jpegs were being saved there, at 1 second intervals.

I'd be most grateful for some help in sorting this out, as we're keen to see what is going on in our conservatory overnight. 
We know we have a vole, as we actually feed it, but it has taken to collecting anything left overnight on the conservatory table, and storing it in a polythene bag.
It must have some "jackdaw" in its ancestry.;)

John

---

### Post by grey1beard on 2013-01-28
I've just tried setting t to 20, and here is a screenshot. It has put 5 jpegs in my home folder by the time I killed it after about 2 mins.> 

---

### Post by grey1beard on 2013-01-28
If I set the terminal with

**streamer -o ~/Desktop/cap/0000.jpeg -s 300x200 -j 100 -t 20 -r 4**

it stores 20 jpegs in the cap folder on the desktop.

If I slow down the capture rate, the following lines appear in Terminal, 

[B]files / video: JPEG (JFIF) / audio: none
v4l2: oops: select timeouts [0], a/v: -0.00s [0][/B]

then the **v4l2: oops: select timeouts** keeps repeating.

So it's telling me to select a timeout ?
How, and where ?

---

### Post by grey1beard on 2013-01-29
Now given up streamer and using VLC, where I've found a workable method.

So I'm marking this as "Solved".

---

### Post by tgalati4 on 2013-01-29
I like to use motion or zoneminder for this kind of stuff.  You can set "detect" zones and it will only capture frames when something moves in the "detect" zone.  Saves on diskspace and you can customize the "detect" zones to reduce extra motion triggers.

---

### Post by grey1beard on 2013-01-29
Yes, I'd spotted motion in my earlier reading, and that would be a good next step for a better picture of the nocturnal "rodent" that's the object of the exercise.
However, it does look like a fair bit of concentrated thought to set up, for me at least, so if I run into probs, then I'll be back with a new thread !

Regards
John

---

### Post by dlw on 2013-04-25
> **grey1beard said:**
> Now given up streamer and using VLC, where I've found a workable method.

So I'm marking this as "Solved".

How did you get it working?

d

---

### Post by grey1beard on 2013-04-25
Hi dlw.
Just picked up your query, but as it was several months ago, and one laptop ago, I'm going to need a little time to work out what I did !
My instant response is that using VLC just worked out of the box with the webcam I was using, but I'll check it out, and hopefully give you more info soon.

John

---

### Post by grey1beard on 2013-04-25
dlw, could you indicate what problem you're having using vlc ?
I'm no expert, but perhaps two heads are better than one ?

John
PS about to hit the sack here, so I'll come back tomorrow :)

---

