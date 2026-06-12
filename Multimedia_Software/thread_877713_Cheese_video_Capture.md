---
title: "Cheese video Capture"
date: 2008-08-02
forum: Multimedia Software
---

### Post by Lilszamora on 2008-08-02
ok when I try and use cheese for video capture I have to force quite it to get the video to stop recording then the video is really messed up no audio and the rate of the video changes...

thanks in advance if anyone can help

---

### Post by collinp on 2008-08-02
Terminal is the best debug tool, so always try to run the program in terminal and see if it outputs a error. So, for now, run cheese in terminal and post what it outputs here.

---

### Post by flybye88 on 2008-08-12
> **Hellow said:**
> Terminal is the best debug tool, so always try to run the program in terminal and see if it outputs a error. So, for now, run cheese in terminal and post what it outputs here.

I have the same problem, here is the output from starting in terminal:-
[http://paste.ubuntu.com/36755/](http://paste.ubuntu.com/36755/)

ron b

Edit: Pefrhaps better here the text directly:-
~$ cheese

** (gnome-video-thumbnailer:9282): WARNING **: Could not take screenshot: no video info

** (gnome-video-thumbnailer:9282): WARNING **: Could not take screenshot: no video info

** (gnome-video-thumbnailer:9282): WARNING **: Could not take screenshot: no video info

** (gnome-video-thumbnailer:9282): WARNING **: Could not take screenshot: no video info

** (gnome-video-thumbnailer:9282): WARNING **: Could not take screenshot: no video info
totem-video-thumbnailer couldn't get a picture from 'file:///home/ron/.gnome2/cheese/media/0002.ogg'

** (cheese:9280): WARNING **: could not load /home/ron/.gnome2/cheese/media/0002.ogg (video/x-theora+ogg)


(gnome-video-thumbnailer:9290): GStreamer-CRITICAL **: gst_event_new_new_segment_full: assertion `start != -1' failed

(gnome-video-thumbnailer:9290): GStreamer-CRITICAL **: gst_event_new_new_segment_full: assertion `start != -1' failed
gnome-video-thumbnailer couldn't process file: 'file:///home/ron/.gnome2/cheese/media/0003.ogg'
Reason: Took too much time to process.

** (cheese:9280): WARNING **: could not load /home/ron/.gnome2/cheese/media/0003.ogg (video/x-theora+ogg)

---

### Post by ajmctaggart on 2008-08-12
What version of gstreamer do you have installed?  In Synaptic, you should be able to tell...

The reason is, I noticed that initially the latest gstreamer was giving me problems with Cheese for awhile, affecting my cam's communication w/ the app...possibly similar. 

Thanks

---

### Post by balaji.ramasubramanian on 2008-11-15
> **ajmctaggart said:**
> What version of gstreamer do you have installed?  In Synaptic, you should be able to tell...

The reason is, I noticed that initially the latest gstreamer was giving me problems with Cheese for awhile, affecting my cam's communication w/ the app...possibly similar. 

Thanks

What should it be? How do you fix it? Don't just write an open ended thing there. Tell us what it should be and how do we fix this problem.

---

### Post by ajmctaggart on 2009-01-15
Wow, I apologize for my lack of specifics, but I assumed my question would be followed by an answer that would lead a bit further into a solution...

Considering we all uses variants of Ubuntu and different distros, I simply stated I had a SIMILAR PROBLEM...I exhibited the problem using Opensuse in Yast, I had not been in Synaptic for quite some time...

Nevertheless, since the original poster never replied, it doesn't matter...

---

