---
title: "jackrec misunderstanding"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by titanik837 on 2006-08-23
now i am finding it hard to undestand jackrec -f filename [ -d second ] [ -b bitdepth ] [ -B bufsize ] port1 [ port2 ... ]
Please tell me what bitdepth means and bufsize and port1 port2 'oh' and the           [ -d second]  .

---

### Post by zettberlin on 2006-08-24
> **titanik837 said:**
> now i am finding it hard to undestand jackrec -f filename [ -d second ] [ -b bitdepth ] [ -B bufsize ] port1 [ port2 ... ]
Please tell me what bitdepth means and bufsize and port1 port2 'oh' and the           [ -d second]  .


Do you relly need jackrec? There are a host of pretty graphical recorders for jack. I use to record with qarecord --jack. Mhw, ardour and rezound (and some dozens others) can also be used...

---

### Post by titanik837 on 2006-08-24
no man 
i just wanna know how to perifraze this jackrec -f filename [ -d second ] [ -b bitdepth ] [ -B bufsize ] port1 [ port2 ... ]

---

### Post by floogy on 2006-08-24
man jackrec
[http://www.google.com/search?q=jackrec](http://www.google.com/search?q=jackrec)

---

### Post by titanik837 on 2006-08-24
^ do you really think that i've not already tryed that :confused:

---

### Post by floogy on 2006-08-25
Sorry, I looked at the man page. It's really [disapointing]("http://xgen.iit.edu/cgi-bin/man/man2html?jackrec+1")...
But its a sample implementation, I think it's not intended to be used by users, but to give an example how things could be implemented with jack. At least I think so. Maybe beacause of that the information is that hard to find. You might find the answer in the sourcecode ;-)

> jackrec -f filename [ -d second ] [ [-b bitdepth ]("http://www.sounddevices.com/tech/dataspeeds.htm")] [ -B bufsize ] port1 [ port2 ... ]

I think that's quite self-explantory, but you're right: I'm not sure about that either:

-f seems to be the output filename
-d the duration of recording in seconds
[-b]("http://www.sounddevices.com/tech/dataspeeds.htm") [bit depth]("http://en.wikipedia.org/wiki/PCM") (8, 16 (cdda), 20 (?), 24, 32 bit etc.) I don't know why there is no switch for the samplingrate...
-B Buffersize this is the cache which is used for the stream, to avoid interrupts, klicks etc. I don't know if that s in bytes, but a good start is maybe 4096 (8192, 16384 ...)
port1 source port of the capture device (capture_1 ??)

You'll might test this, and look at the qjackctl Message Windows and the Connect Window during testing the above parameters.

[http://userpages.umbc.edu/~berman3/capture.pdf#search=%22jack%20ports%22](http://userpages.umbc.edu/~berman3/capture.pdf#search=%22jack%20ports%22)

> .capture_client -f test.wav -d 20 alsa_pcm:in_1
The example client in this case is.capture_client instead of jackrec (I think it's maybe the antecedent of jackrec).

[http://ccrma-mail.stanford.edu/pipermail/planetccrma/2006-February/011275.html](http://ccrma-mail.stanford.edu/pipermail/planetccrma/2006-February/011275.html)

[http://plugin.org.uk/timemachine/](http://plugin.org.uk/timemachine/)

---

### Post by titanik837 on 2006-08-25
very Thanx for the insformation it's good to know bout bitdepth and bufsize . my guitar just broked :confused:  seems i will use your useful information later ,

---

