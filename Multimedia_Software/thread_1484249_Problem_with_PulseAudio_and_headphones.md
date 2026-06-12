---
title: "Problem with PulseAudio and headphones"
date: 2010-05-15
forum: Multimedia Software
---

### Post by 9a3bdz on 2010-05-15
Hello all.
I know everybody is probably fed up with posts like this, but it seems i cannot find any solution to my problem.
When i am using volume control from PulseAudio it seems to move multiple bars in alsamixer. There comes my problem, since when my headphones are plugged in and i use PulseAudio volume control if i lower my volume too much, in alsamixer PCM and Front also move. And if i even barely touch Front, my speakers start playing music together with headphones, which is very irritating becouse i have to unplug and plug in my headphones again. 

So my question here is, is there a way to make PulseAudio volume control affect only Master Front in alsamixer?

Here is a screenshot of my alsamixer:
[IMG]http://i42.tinypic.com/20r5hq8.png[/IMG]

Oh, and btw, i am using laptop Asus K50AB.

---

### Post by tommcd on 2010-05-16
> I know everybody is probably fed up with posts like this, but it seems i cannot find any solution to my problem.
There is no problem at all in asking this question. The only thing I am fed up with is *pulseaudio* itself!

I would suggest removing pulse audio and try using alsa to configure sound. With alsa in control, all the volume levels in alsamixer can easily be controlled independently of each other. Pulseaudio is also a *huge* resource hog compared to alsa. See this long running thread about how to remove pulse audio:
[http://ubuntuforums.org/showthread.php?t=1313253&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=1313253&highlight=pulseaudio)
Note that you may not even need to install any of the extra esound and alsa packages that are discussed in that thread.
 I just removed **pulseaudio** and **gstreamer0.10-puseaudio**. Then I ran **gstreamer-properties** in the terminal and set everyhing to alsa.
Installing the esound and extra alsa packages will not hurt though; and it does give some extra GUI configuration tools for sound properties.
If you wish to reinstall pulseaudio for any reason, just run in the terminal:
```
sudo apt-get install pulseaudio
```
and you will be back to using pulseaudio.
Write back if you need more help with this.

And welcome to the Ubuntu forums! Welcome to the cool side of computing!

---

### Post by yadayada2 on 2010-05-16
But even if this might be a little bit off-topic, why did the change to pulseaudio occur at all? The people in charge have to be convinced by this system for some reason, don't they?

---

### Post by 9a3bdz on 2010-05-16
Thank you very much for fast response tommcd. I have successfully removed PulseAudio from my computer, and now everything works as it should.

---

### Post by tommcd on 2010-05-18
> **yadayada2 said:**
> But even if this might be a little bit off-topic, why did the change to pulseaudio occur at all? The people in charge have to be convinced by this system for some reason, don't they?
I have also wondered about this myself. I have also (unlike many other people around here!!!) taken the opportunity to search for answers to this question. 
It does seem that pulseaudio is the future linux sound server whether we like it or not:
[http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it](http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it)
[http://arstechnica.com/open-source/news/2007/10/pulseaudio-to-bring-earcandy-to-linux.ars](http://arstechnica.com/open-source/news/2007/10/pulseaudio-to-bring-earcandy-to-linux.ars)
Bu a lot of people still prefer alsa:
[http://www.linuxtoday.com/news_story.php3?ltsn=2010-04-03-001-35-MM-HL-UB](http://www.linuxtoday.com/news_story.php3?ltsn=2010-04-03-001-35-MM-HL-UB)

---

