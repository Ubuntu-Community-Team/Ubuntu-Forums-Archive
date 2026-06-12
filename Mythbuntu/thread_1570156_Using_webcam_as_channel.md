---
title: "Using webcam as channel?"
date: 2010-09-07
forum: Mythbuntu
---

### Post by pu15e on 2010-09-07
Hi all,

  Trying to set up a webcam on a slave backend to present to the system as a channel (so we can monitor the kids in the living area from the office or wherever using either fullscreen or PIP).

  We have two cameras, of which we'd prefer to use the MS VX-3000 for it's higher / bigger resolution, but they both fail to work with the same backend log messages:

```

2010-09-08 08:54:49.544 Channel(/dev/video0) Error: SetInputAndFormat(7, NTSC) 
			while setting format (v4l v2)
			eno: Invalid argument (22)
2010-09-08 08:54:49.552 Channel(/dev/video0) Error: SetInputAndFormat(7, NTSC) 
			while setting format (v4l v2)
			eno: Invalid argument (22)
2010-09-08 08:54:49.564 Channel(/dev/video0) Error: SetInputAndFormat(7, NTSC) 
			while setting format (v4l v2)
			eno: Invalid argument (22)
2010-09-08 08:54:49.639 Channel(/dev/video0) Error: SetInputAndFormat(7, ATSC) 
			while setting format (v4l v2)
			eno: Invalid argument (22)
2010-09-08 08:54:49.661 Channel(/dev/video0): SetInputAndFormat() failed

```

  Any ideas? Oh - and before anyone says "mythzoneminder", please consider that it can only do PIP in LiveTV (if I'm wrong, I'd love to know) which doesn't suit our use case at all :-)

Cheers,
 Mattt.

---

### Post by DemonBob on 2010-09-07
Don't know if you saw this. 

[http://www.gossamer-threads.com/lists/mythtv/users/287854?nohighlight=1#287854](http://www.gossamer-threads.com/lists/mythtv/users/287854?nohighlight=1#287854)

---

### Post by pu15e on 2010-09-08
I hadn't, but it's a tad old now (this might be a v4l1/v4l2 issue), and both of these cameras work (despite not doing so under myth) and myth picks them up in the setup pages...

  I've added the requisite channel, etc... Myth just doesn't seem to like it as a capture device for some reason...

Cheers,
 Mattt.

---

### Post by novellahub on 2010-09-09
You could set up ZoneMinder on the box and then use MythZoneMinder to tie it into Mythtv.

[http://www.zoneminder.com](http://www.zoneminder.com)

[http://www.mythtv.org/wiki/MythZoneMinder](http://www.mythtv.org/wiki/MythZoneMinder)

---

### Post by pu15e on 2010-09-09
As stated, we need PIP for the camera feed while watching any kind of media. Mythzoneminder can apparently only do PIP during LiveTV which doesn't suit us at all.

Cheers,
 Mattt.

---

### Post by DemonBob on 2010-09-09
I have a webcam, I'll try to give it a shot to see if I can get it to work. It might not be till the weekend.

---

### Post by mythedoff on 2010-09-10
I happened upon this thread and although I can't help with mythbuntu, I can tell you that I do just this thing using linhes 6.03. Perhaps how I do it can be adapted for mythbuntu. And this works no matter where I am whether watching live tv, recordings, videos, viewing pictures. listening to music or just in the menu view.

I run zoneminder on a ubuntu box, although it could also be run on the linhes box, which is then accessed in linhes via firefox which I launch before the frontend starts up. Firefox is setup to use the url to the zoneminder. I then use some code to input username and password and then connect  to the montage view[on my hd master backend-frontend] and cycle view[ on my sd frontend only]. Firefox is then set to full view F11. After this is completed the frontend is started. I then have set a button on the remote and I can view the cameras no matter where I am in linhes. A second press of the button returns me to where I was.

A second possiblity that I have only thought about is running two instances of a frontend with one of them running mythzoneminder. And then somehow alt-tabbing between them.
Good luck

---

