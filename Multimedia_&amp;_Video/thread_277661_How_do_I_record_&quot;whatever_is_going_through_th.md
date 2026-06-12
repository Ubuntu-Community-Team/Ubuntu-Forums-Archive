---
title: "How do I record &quot;whatever is going through the soundcard&quot;?"
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by em3raldxiii on 2006-10-15
I'll give you an example:  I want to peel off a copy of something that plays on myspace.  Since the player uses Flash, I don't actually get a URL, so I can't rip the stream using other methods documented on this forum.

There are other times when stuff is coming thru my soundcard that I want to record.  Does anyone have a way to do this?

I have used Ardour + Jack for other things, but I cannot seem to configure it to record the audio when it's playing thru a website ... it only seems to like when I use the line-in.  I have attempted to muddle my way through alsa-mixer, but I can't seem to click on the right things LOL ...

So any help would be appreciated.  Thanks a lot. :D

---

### Post by adwait on 2006-10-15
Well if you have one of those systems which have headphone and mic jacks on the front as well........you could simply connect a wire between the 2 :)

---

### Post by em3raldxiii on 2006-10-15
Ya, thought of that ... hesitant to do so, though ... they're crappy little 1/8 jacks, and as such have lower signal quality.  I'll do it if I have to though.

---

### Post by TheWizzard on 2006-10-15
you can record any sound with audacity

---

### Post by mrhelpman on 2006-10-15
I use Sound recorder and set the record from input drop down to: capture.  However I suspect that the various options that are visible in the drop down list will depend on your sound card.

John T.

---

### Post by em3raldxiii on 2006-10-16
mrhelpman:  Thanks ... I'll give that a try as soon as I can.

TheWizzard:  I realize you are trying to help LOL ... but your post is kinda useless ;).  I am fully aware that Audacity has some pretty fabulous capabilities, considering I use it to mix my wife's music ([www.anxietyofinfluence.ca)](www.anxietyofinfluence.ca)), go have a quick listen ... I promise you won't be disappointed.  But anyway, if you are well-versed with Audacity, perhaps you can help me figure out how to configure Jack to use the "whatever goes through my soundcard" as an input to Audacity.  That would be quite fabulous.  I am thoroughly convinced that it can indeed do this, but I don't quite know how.

Thanks all :D

---

### Post by TheWizzard on 2006-10-16
> TheWizzard: I realize you are trying to help LOL ... but your post is kinda useless . I am fully aware that Audacity has some pretty fabulous capabilities, considering I use it to mix my wife's music ([www.anxietyofinfluence.ca)](www.anxietyofinfluence.ca)), go have a quick listen ... I promise you won't be disappointed. But anyway, if you are well-versed with Audacity, perhaps you can help me figure out how to configure Jack to use the "whatever goes through my soundcard" as an input to Audacity. That would be quite fabulous. I am thoroughly convinced that it can indeed do this, but I don't quite know how.

mmm, i did use audacity to record streaming stuff. the only 'problems' i can remember is that i needed to enable input devices with KMix. but that is specific for kde.

---

### Post by TheWizzard on 2006-10-16
hi em3raldxiii
your wife's website is unreachable at the moment. i'll try that later.

i just did an install of audacity on a standard kubuntu box. i did run into a  ["Error Opening Sound Device"]("http://audacityteam.org/wiki/index.php?title=LinuxIssues") issue. this i remembered :-k 
the problem is that the kde soundsystem hijacks the sound card. setting back the auto-suspend time back from 60 to 5 seconds did the trick. 
in audacity, just use "Vol" as the input device. now i can record from myspace :D 

does this help?

---

### Post by konungursvia on 2007-05-15
Strange, when I open Sound Recorder, it says that IO could not be initialized, and I need to fix my Multimedia settings. However, I can't identify which mm settings to change.

---

### Post by crazybilly on 2007-10-31
I can use Sound Recorder and use "Mix" as the input device, rather than 'capture'.  Capture didn't work for me, but mix seems to work just fine.  I played around with a couple others that didn't work too. 

I'd recommend trying Sound Recorder first, playing around with the options--I'd be suprised if one of them didn't work for you.

---

### Post by em3raldxiii on 2008-02-10
Thanks for the feedback everyone.  This thread is really old, and I seem to have forgotten to subscribe to my own thread ... :oops:

Anyway, I think I achieved what I wanted to way back then, I simply forgot what it is that I did.  I have a feeling I probably configured audacity and JACK to do what I wanted.

Cheers!

Mike

---

### Post by Chappy7777 on 2008-02-12
> **mrhelpman said:**
> I use Sound recorder and set the record from input drop down to: capture.  However I suspect that the various options that are visible in the drop down list will depend on your sound card.

John T.
=======================
that is what I am trying to do, use Sound recorder. I have it set at the default, "Capture" and 
as "CD MP3". When I click on record it seems to start, but when I go to save it, I get an error message. Now, I have played around w/it to the point where it freezes. It was working, just not recording, or else it was recording (as the slider was moving and keeping track of my time) buy when I stopped the record and hit Play, no sound came out. There is no problem w/sound on any other device.

Where do I find Audacity?

---

### Post by em3raldxiii on 2008-02-13
Hmm, odd problem.  Not sure what's causing that, but ...

```
sudo aptitude install audacity
```

should automatically install it for you.  Alternatively, you can go to [b]system > administration > synaptic package manager
[/b] and search for audacity.

Finally, you can also try an application called **ardour** which is a HUGE Digital Audio Workstation (robust enough for serious production) but it might be overkill.  Plus it's not quite as straight-forward as some of these other apps.  Audacity is probably your best bet. 

 One of these days when I am back home (I am at work for the next week or so), I will try my hand at this again.

Good luck!

---

