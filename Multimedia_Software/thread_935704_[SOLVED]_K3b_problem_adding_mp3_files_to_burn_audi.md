---
title: "[SOLVED] K3b problem adding mp3 files to burn audio CD"
date: 2008-10-01
forum: Multimedia Software
---

### Post by cybrsaylr on 2008-10-01
I'm using Ubuntu8.04 and trying to burn an audio CD.
When I go to load the mp3 files into K3b they won't load and I get this:

Sorry - K3b

> Problems while adding files to the project.

Details
Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.

Usually the mp3s just load and burn.
What could be causing this error message?

I then used Brasero and it burned those same mp3s with no problem that wouldn't load into K3b.

---

### Post by Drakkor on 2008-10-03
Getting same problem and can't even use Brasero ! :(

---

### Post by snakattak on 2008-10-04
Same for me with K3b. Bump for assistance.

---

### Post by jpmswiss on 2008-10-05
Same here!

---

### Post by xc3RnbFO8P on 2008-10-05
In Synaptic Package Manager install:

libk3b2
libk3b2-extracodecs
**it seem you cant have both**
libk3b3
libk3b3-exracodecs

---

### Post by Drakkor on 2008-10-05
Have the first 2,but libk3b3-exracodecs is not found in synaptic

---

### Post by xc3RnbFO8P on 2008-10-05
Yes something has changes,
do you got these packages installed:
libmad0
libmad0-dev
mpeglib

---

### Post by jpmswiss on 2008-10-06
Hmmm...still not working.

---

### Post by cybrsaylr on 2008-10-18
> **Ringi said:**
> In Synaptic Package Manager install:

libk3b2
libk3b2-extracodecs
**it seem you cant have both**
libk3b3
libk3b3-exracodecs

I installed:
libk3b2-extracodecs

and the mp3 files now load like Brasero!

Couldn't find, libk3b3, or libk3b3-exracodecs, in synaptic.

Thanks it looks like the problem is solved but I haven't burned a CD as yet to give it a full test.

---

### Post by cybrsaylr on 2008-10-18
Just burned an audio CD and all appears well.
K3B added those mp3 files then burned with no problems.
Thanks for the help.

---

### Post by dskyracer on 2008-10-26
I was having the same problem and getting the same error message..unable to load mp3s. I went to the synaptic package manager and marked a package called libk3b3-extracodecs for installation and after installing it my mp3 files loaded perfectly into K3bs audio cd project window. I had recently upgraded from Gutsy Gibbon to 64bit Hardy Heron. Before the upgrade I had no problem in handling mp3s with K3b.  I love what one can do with K3b. It's a great burning program. :guitar:

---

### Post by ricardisimo on 2008-12-22
libk3b3-extracodecs solves the problem. Thanks.

---

### Post by Emilie on 2010-01-11
I had to install libk3b6-extracodecs, ha, maybe just install all the "libk3bX-extracodecs" packages there are :)

It did solve it for me though!

---

### Post by Razmear on 2010-05-17
Hi,
Getting this same error message after upgrade to 10.4. worked fine before burning audio disks. 
I had the same problem after my last upgrade to 9.10 and had to install something or enable something, not 100% sure what fixed it then. 
I checked Synaptic and libk3b6-extracodecs is installed.

Any help appreciated,
eb

Edit: 
Disregard, other smaller files are burning fine. It was an old complete album mp3 popping this error message.

---

### Post by biloyp on 2010-06-02
I upgraded to Karmic and had to install libk3b6-extracodecs to get K3B to burn mp3 to a CD. Kinda frustrating to have to go through this whenever I upgrade to the newest ubuntu version but the forums are great, because I can find an answer.

---

### Post by areskz on 2010-07-13
> **cybrsaylr said:**
> I installed:
libk3b2-extracodecs
It solved the problem!
Thank you.

---

