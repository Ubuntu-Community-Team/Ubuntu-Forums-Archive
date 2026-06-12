---
title: "New camera blues"
date: 2005-12-27
forum: Multimedia &amp; Video
---

### Post by Brigrat on 2005-12-27
Hey,

     I sure hope someone here has an idea.  I am new to linux (ubuntu) and got a new digital camera a KODAK Z700 for Christmas.  Plugged it in and based on a very quick search used the Gthumb viewer.  It does not recognize the camera plugged in via the docling station.  Any suggestions????

---

### Post by Lord Illidan on 2005-12-27
Hi...
Try this site : [http://howtos.linux.com/howtos/USB-Digital-Camera-HOWTO/index.shtml](http://howtos.linux.com/howtos/USB-Digital-Camera-HOWTO/index.shtml)

---

### Post by Brigrat on 2005-12-27
My KODAK uses PTP transfer and I have not found, so far, any software that runs on ubuntu that supports this format.  Any suggestions?

---

### Post by Nightwind on 2005-12-27
[QUOTE=Brigrat]Hey,

     I sure hope someone here has an idea.  I am new to linux (ubuntu) and got a new digital camera a KODAK Z700 for Christmas.  Plugged it in and based on a very quick search used the Gthumb viewer.  It does not recognize the camera plugged in via the docling station.  Any suggestions????[/QUOTE]
Try this site 
[http://www.gphoto.org/doc/manual/](http://www.gphoto.org/doc/manual/)
Let us know if it works!

---

### Post by Nightwind on 2005-12-29
[QUOTE=Lord Illidan]Hi...
Try this site : [http://howtos.linux.com/howtos/USB-Digital-Camera-HOWTO/index.shtml](http://howtos.linux.com/howtos/USB-Digital-Camera-HOWTO/index.shtml)[/QUOTE]
I think you are the only Maltese user on the forum just like I think I am the only Great Dane user on here, but we could be wrong.
The link to the docs on the camera worked for that one  but my Intel Web camera now that's another story.

---

### Post by az on 2005-12-29
[QUOTE=Brigrat]My KODAK uses PTP transfer and I have not found, so far, any software that runs on ubuntu that supports this format.  Any suggestions?[/QUOTE]
gphoto2 is an implementatino of that protocol.  My brother's kodak needs to be put in the docking station and it wakes up ubuntu by pressing the powere button on the docking station.  Is this the case for you?

You have a very recent model.  You can try manually telling it it is another kodak camera and see if that works.  It is all the same protocol.

At the very least, you can access your photos by reading the card with a usb memory card reader.  But it should work with gphoto (Ubuntu uses HAL and HAL known about gphoto2 cameras)

---

### Post by canadianwriterman on 2005-12-29
I have a Kodak C330 that uses PTP. When I plugged it in, then turned on the camera, I got a dialogue that asked if I wanted to download the pictures. I said yes and they opened up in the gthumb viewer beautifully.

However, if you're having problems, try this:

Download and install digikam through Synaptic. I think you need to enable all the repositories. Plug in your camera, open digikam, then turn your camera on. In digikam, go to the camera menu where you select your type of camera. It may be listed. However, if it's not, simply click on the detect camera button and it should find your camera for you.

I think that may work fine for you.

---

### Post by Brigrat on 2006-01-07
Thanks to all on the help.  Got the camera up and running some time agao, just now got around to answering this post.  I'll look at the digikam, even though I got it through another prg.  Again thanks!

If anyone has an Idea to fix my ubuntu install to a cranky old server with a scsi cd, please let me know, even if by a PM.

---

### Post by az on 2006-01-07
[QUOTE=Brigrat]Thanks to all on the help.  Got the camera up and running some time agao, just now got around to answering this post.  I'll look at the digikam, even though I got it through another prg.  Again thanks!

If anyone has an Idea to fix my ubuntu install to a cranky old server with a scsi cd, please let me know, even if by a PM.[/QUOTE]
How did you get your camera working?

Please start another thread about your other box.

---

