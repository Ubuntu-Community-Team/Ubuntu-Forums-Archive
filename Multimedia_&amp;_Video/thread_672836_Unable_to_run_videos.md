---
title: "Unable to run videos"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by HuBaghdadi on 2008-01-20
Hi.
I installed GStreamer codecs for my Ubuntu 7.10 but till now I'm unable to run video files (mpeg, mpg, ogg...).
I tried also VLC, MPlayer without any success (the player's windows disappears immediatly upon double clicking on a movie file).
Any ideas?

---

### Post by c0met on 2008-01-20
Rather than double clicking, have you tried starting up the player (say VLC)  and then opening the mpg (etc) through the program?

---

### Post by HuBaghdadi on 2008-01-20
Yes, the application (any video application) closes immediately.

---

### Post by c0met on 2008-01-20
What is your system? Often problems like this can be traced back to a video card or sound card.

---

### Post by HuBaghdadi on 2008-01-20
DELL Inspiron 1520
I have no problems with MP3 files...

---

### Post by disturbed1 on 2008-01-20
> **HuBaghdadi said:**
> Yes, the application (any video application) closes immediately.

Open a terminal, type vlc to launch vlc. Then open the video file (from inside vlc ;) ). Once it crashes an error report will appear in the terminal. Post that here.

---

### Post by HuBaghdadi on 2008-01-20
What is the complete command line please?

---

### Post by disturbed1 on 2008-01-20
vlc

---

### Post by HuBaghdadi on 2008-01-20
Just? no command line arguments?
Well, sorry but I don't carry my laptop now...

---

### Post by bharadwaj on 2008-01-20
was the installation successful? try installing ffmpeg from applications->Add remove

---

### Post by HuBaghdadi on 2008-01-21
From the command line:
VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

---

### Post by c0met on 2008-01-21
With your computer, how much RAM do you have? What is the processor speed?

---

### Post by HuBaghdadi on 2008-01-21
Intel Core2Duo (2 GH)
2 GB of RAM

---

### Post by c0met on 2008-01-21
Can I suggest that you have a look under System >> Administration >> System Monitor and see how much of your resources are being used? You certainly have more than enough computing power but it seems as though something might be using it up. Just an idea and I might be wrong :)

---

### Post by eye208 on 2008-01-21
> **HuBaghdadi said:**
> Major opcode of failed request:  140 (XVideo)
Are you using an ATI graphics adapter? Then you probably forgot to enable XVideo in the driver.

---

### Post by HuBaghdadi on 2008-01-21
My graphic card is Intel Accelerator X3100
How to enable XVideo in it?

---

### Post by disturbed1 on 2008-01-21
> **HuBaghdadi said:**
> From the command line:
VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

The XV overlay is not available.
This is caused from several things. Another process has *taken* that overlay, such as compiz, a wine application, another application displaying video. Or it is a bad driver setting, or the overlay just isn't available for the driver you are using.

(see screen shot below)
For a quick fix, launch vlc, click on settings, choose preferences. Bottom right hand corner check advanced settings, drill down to Video/Output Modules, choose X11 Video Output.

To fix the XV issue, if you are running compiz, turn it off. If this isn't the case, I'd start a new thread detailing the problem with your graphics device and xv issue. You could also search here [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/) to see if the documentation is already available.

---

### Post by Riverside on 2008-01-21
There is an issue with VLC on Ubuntu 7.10.  I have been running VLC perfectly well for over a year on a Dell Inspiron 6400 laptop with Ubuntu 6.06.1 installed, however after installing (fresh install) 7.10 this weekend, I experienced exactly the same issue as HuBaghdadi.

Spec:

210-16213 Inspiron 6400 Duo Processor T2250 1.73 GHz, 2 MB L2 cache, 533 MHz FSB)
200-40408 List N08646 - DHS 6400 (2)
230-10036 15.4" Wide Screen WXGA (1280 x 800) TFT Display
236-10072 Memory Upgrade from 512MB to 1024MB

Plenty of system resource there.

xine wouldn't run properly on 7.10 either.  Switching to full screen resulted in a system lock up which necessitated a hard reboot (I couldn't even Ctrl+Alt+Delete to kill the X server, nor Ctrl+Alt+F* to switch to a virtual console), even though it runs faultlessly on the same machine on 6.06.1.

---

### Post by HuBaghdadi on 2008-01-22
Your tips works perfectly.
Why another players aren't working (Movie Player and MPlayer)?
Any ideas how to fix them?

---

### Post by disturbed1 on 2008-01-22
For mplayer, you would right click on the application, choose preference, and change the video output that way.

For Movie Player (Totem) you need to run Multimedia Systems Selector from the main System -> Preferences. If it's not there you can launch it from this command in the terminal.

gstreamer-properties

---

### Post by alonge on 2008-01-22
Hi HuBaghdadi
I am having the same problem. I have gone to forums and tried to do everything everyone mentions to do. When this computer had Windows XP on it there was no problem viewing any media files or watching movies. If you find an answer to this one, can you let me know?
Thanks
Barb
[email]balonge@gmail.com[/email]

---

### Post by HuBaghdadi on 2008-01-22
Hi.
Check disturbed1 tip in this thread, it works for me.

---

### Post by dhiral09 on 2008-03-08
yaa it worked for vlc ...
but not for movie player .

how to fix this problem .. 
i dont want to turn compiz off , what should i do to run videos on movie player ,compiz being on

---

