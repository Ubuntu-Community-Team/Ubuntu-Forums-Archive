---
title: "How to revert to firefox native streaming"
date: 2011-01-14
forum: Multimedia Software
---

### Post by mystmaiden on 2011-01-14
I'm using 10.04 LTS and I followed these instructions hoping to improve video streaming - ```
**sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin**
 
**sudo apt-get install gnome-mplayer gecko-mediaplayer**


```

I'm having trouble streaming vids now though, they are choppier than they were and when I navigate away, the sound stays on as if the video were still playing, I have to restart to make it stop.  How would I go about un-doing the above?

thanks

mystmaiden

---

### Post by lovinglinux on 2011-01-15
The plugin you have installed is the best plugin in my opinion.

I don't know why you are experiencing such issues, but first I would like to ask what kind of videos you are trying to watch? Are you referring to a YouTube video for example? Because if you are, then it has nothing to do with the plugin you have installed.

---

### Post by mystmaiden on 2011-01-15
Thanks for the reply, linuxlover. I don't have any trouble watching vids on Youtube, the ones I have the most difficulty with are the ones from the streaming video site I pay a monthly fee for - Crunchyroll. I've done some searching around and noticed that some folks who have trouble with streaming let them play and then watch from a tmp file. So far I haven't figured out how to do that though, because I can not seem to find them in the files.

---

### Post by lovinglinux on 2011-01-15
> **mystmaiden said:**
> Thanks for the reply, linuxlover. I don't have any trouble watching vids on Youtube, the ones I have the most difficulty with are the ones from the streaming video site I pay a monthly fee for - Crunchyroll. I've done some searching around and noticed that some folks who have trouble with streaming let them play and then watch from a tmp file. So far I haven't figured out how to do that though, because I can not seem to find them in the files.

Those videos are flash based, so they have nothing to do with the plugin you have installed.

You won't be able to find the videos in the tmp folder, because the site uses RTSP protocol, which prevents the video from being stored in the cache.

Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

You might want to disable Compiz as well and make sure you have the latest video driver for your graphics card.

---

### Post by mystmaiden on 2011-01-15
I thought all streaming videos were pretty much flash based... showing my utter ignorance here.

I haven't got a video card just now. I bought an older model nvidia card and its what started a recent string of difficulties (it and the presence of virtualbox at the same time). I decided to go ahead and upgrade to 10.04 since I was having to deal with so much anyway but I could not get past the kernel panics to get the card working. However, I had been able to watch videos on crunchy with my onboard before but since the change to 10.04 now - not so much. The video card is lying on my other desk waiting for me to tackle that hassle again. 

I tried flash aid yesterday. Without the card is it actually helpful? and if so, how much of the report should I post? 

thanks,

mystmaiden

---

### Post by lovinglinux on 2011-01-16
> **mystmaiden said:**
> I thought all streaming videos were pretty much flash based... showing my utter ignorance here.

There are several ways of streaming videos, flash is the most common. For instance, I develop another extension, called [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/"), that allows to watch YouTube, Vimeo and Metacafe with a different plugin that uses less CPU cycles. However, it doesn't work on the site you want.

> **mystmaiden said:**
> I tried flash aid yesterday. Without the card is it actually helpful? and if so, how much of the report should I post? 

Depends on the onboard card. However the extension is designed to solve other problems too, like conflicting plugins.

Attach the complete report file on a post.

---

### Post by mystmaiden on 2011-01-16
Thanks, linuxlover. I've attached the report here.

---

### Post by lovinglinux on 2011-01-16
Your report looks fine.

I think your problem is indeed the result of the bad flash performance with the video card.

On a side note, the site you want wasn't perfectly smooth on my machine, because of buffering issues. So would try to pause the video and wait to buffer a little bit before playing. Alçso try to disable Compiz.

Perhaps you could also try to disable hardware acceleration. Right-click in the flash video and disable that in flash preferences. Doing that can result in worse performance depending on the system, but works for some people.

---

### Post by mystmaiden on 2011-01-18
Thanks so much for having a look, lovinglinux, I really appreciate it. I disabled hardware acceleration and have been pausing the feed for awhile and it does seem to help.

---

