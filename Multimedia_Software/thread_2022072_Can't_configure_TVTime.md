---
title: "Can't configure TVTime"
date: 2012-07-10
forum: Multimedia Software
---

### Post by pooky2483 on 2012-07-10
I'm trying to get TVTime working but I am not getting anywhere. I am using a PEAK 138508AGPK DVB-T Digital TV Hybrid PCI Card TV Card.
I have connected it to my video recorder which has a Virgin TiVo box connected. It can't detect a signal, what do I need to do as I am completely stumped.
To help, for any settings needed, I am in UK.

---

### Post by cintiaarosales on 2012-07-10
Hey pooky2483,
Maybe give some more details about your setup…
I would first check for the obvious, i.e. settings. In Media, go to Open capture device and check that it appears there. Now go to Input Configuration > Change Video Source and make sure your source is set. In Channel management, go to Change Frequency table > Select new table and setup your frequencies table; next, go to Scan channels for signal.
That should at least give you some indication where your error is (process of elimination ;)). Also, have you tries the tvtime site – the help and faq & common errors sections are pretty useful.
Hope this helps (or you’ve already solved it…), Cintia

---

### Post by Merrattic on 2012-07-10
tvtime doesn't work with dvb afaik, but perhaps if you have a hybrid card you are trying to grab an analog signal from somewhere, or perhaps a composite signal? What are your video devices in /dev/video? You will probably need to set the composite input from within tvtime to get a picture from your video recorder.

---

### Post by pooky2483 on 2012-12-15
> **Merrattic said:**
> tvtime doesn't work with dvb afaik, but perhaps if you have a hybrid  card you are trying to grab an analog signal from somewhere, or perhaps a  composite signal? What are your video devices in /dev/video? You will  probably need to set the composite input from within tvtime to get a  picture from your video recorder.

It worked ok when I had Window$ but I don't use that any more.
I am using an analog signal.
How can I find out what's in /dev/video

---

