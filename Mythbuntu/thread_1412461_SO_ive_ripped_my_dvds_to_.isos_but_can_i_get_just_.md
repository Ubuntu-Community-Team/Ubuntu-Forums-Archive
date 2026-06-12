---
title: "SO ive ripped my dvds to .isos but can i get just the film out?"
date: 2010-02-21
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-02-21
Pretty much as per the title really guys.  I have used myth to rip all of my dvds but ive ended up with all the .iso and a very full HDD when all i really want is to rip the actual movie itself from the dvd.  

Is there an easy way i can get myth to take the movie out of the isos and encoded it into some form of DIVX/MP4 (without quality loss?)

Thanks

---

### Post by SiHa on 2010-02-21
Not from within Myth, I think, but I've found DVD:Rip to be pretty good. I'm fairly sure it will let you just rip the main movie, and the encoding options are very configurable. It also has a useful preview feature, where you can just transcode, say, 30s to check the parameters before comitting 1 1/2hrs. Fairly sure it will directly open .iso's, otherwise you'll have to mount them (not sure how you do this in Ubuntu).

One other really useful feature, if you have more than one Ubuntu system on the network, is the ability to spread the processing over these systems as well.

---

### Post by williammanda on 2010-02-21
First you can within mythtv rip the the video from the dvd. Select "perfect" instead of iso. This will rip what mythtv thinks is the main movie off the dvd.
Second, you can use a third party program called mkvtoolnix (its in synaptic) to rip the video from the iso file. Now the format will not be vob or mpeg2 but the mkv format will work in mythtv.

---

### Post by geekyhawkes on 2010-02-21
both seem good answers thanks.  I think il give the mkv a go as Im only interested in playing the ripped files from myth.

---

### Post by elgordo123 on 2010-02-23
I have handbrake installed on my mythbox and use it for that reason.  I normally use the "Normal" setting, set video bitrate to 1500 and use the h.264 (ffmpeg) encoder.   The movies look great, are a little over 1 gig each and will play on my android phone.

---

### Post by nickrout on 2010-02-23
avidemux will also do what you want.

---

### Post by geekyhawkes on 2010-02-23
Great thanks, do any of the above intergrate with myth / start automatically?  Im after a simple (waf proof) dvd rip that requires little more than just putting a new disc in to the machine.

Thanks

---

### Post by nickrout on 2010-02-23
there are different ripping profiles which (assuming they work) would be the most integrated.

---

### Post by Thomas Garman on 2010-02-23
I use Acidrip and when it loads the dvd to be ripped it lists all of the parts of it that could be ripped and you get to select which you want and then select the format to rip into.  So... it will show a list of sections on the dvd that have the running time of the section next to it and I always just choose the longest segment (which is the part that contains just the movie).

---

### Post by kja999 on 2010-02-27
Handbrake is easy to use with a little helper script, as per the link, I have an icon which runs the script from the xfce menu:
[http://ubuntuforums.org/showthread.php?t=1334233](http://ubuntuforums.org/showthread.php?t=1334233)

---

### Post by geekyhawkes on 2010-02-28
Ive gone for handbrake to convert all the current ISOs i have.  Thanks for the last post kja999, next time i have some free time il try and get handbrake working from within myth (for the final solution).

Nearly got my myth setup 90% complete...

---

### Post by TheMiz on 2010-03-01
> **SiHa said:**
> One other really useful feature, if you have more than one Ubuntu system on the network, is the ability to spread the processing over these systems as well.

Explain please... how do you do this?

---

### Post by nickrout on 2010-03-01
> **TheMiz said:**
> Explain please... how do you do this?

You do it by reading the DVD::rip docs, which you can access from their web page [http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)

---

### Post by TheMiz on 2010-03-02
> **nickrout said:**
> you do it by reading the dvd::rip docs, which you can access from their web page [http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)

lol

---

### Post by SiHa on 2010-03-03
It's quiet simple really. The hardest bit (for me) was setting up paswordless ssh authorization, but that was more down my ineptitude, getting 'Remote' and 'Host' mixed up and putting the RSA keys on the wrong machine. Duh.

As nickrout says, read the docs, it's not hard.

---

