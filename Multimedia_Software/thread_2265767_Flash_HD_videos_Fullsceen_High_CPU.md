---
title: "Flash HD videos Fullsceen High CPU"
date: 2015-02-17
forum: Multimedia Software
---

### Post by udomoody on 2015-02-17
Hey,
I'm on Ubuntu 14.04 and everytime I want to watch Videos on Youtube or Twitch for example in HD and in Fullscreen, my CPU usage gets pretty high and my laptop becomes hotter, which results in the fan getting really loud. When I boot into Windows everything works normal. I hope someone knows a solution for that, because it gets really annoying and that's probably the only reason I still got Windows on my laptop.

---

### Post by ajgreeny on 2015-02-17
It's not totally unexpected, I'm afraid as flash is notorious in Linux for using a lot more resources than in Windows, and now,of course, adobe has stopped developing flash for Linux and is just adding security fixes for the 11.2.202 version that we use in Firefox.

Make sure your machine is fully updated and if possible, install any proprietary graphic driver from Additional Drivers.  Apart from that there is little else to offer you other than to make sure you have accepted the option to use html5 instead of flash when it is available for the videos you watch.
[YouTube - HTML5 trial]("https://www.youtube.com/html5")

---

### Post by monkeybrain20122 on 2015-02-17
What are your computer's specs? Well if your system is too weak to play flash (instead of some graphic driver problem) html5 likely wouldn't work any better (still high cpu load if not higher) but streaming through mplayer would improve things quite dramatically. 

Try using gecko-mediaplayer and Viewtube (install gecko-mediaplayer from repo, install the grease-monkey addon for Firefox, then restart Firefox and install Viewtube [http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en), you can adjust the playback resolution. It works on Youtube and a few other sites too.

---

### Post by monkeybrain20122 on 2015-02-17
> **ajgreeny said:**
> 
Make sure your machine is fully updated and if possible, install any proprietary graphic driver from Additional Drivers.  Apart from that there is little else to offer you other than to make sure you have accepted the option to use html5 instead of flash when it is available for the videos you watch.
[YouTube - HTML5 trial]("https://www.youtube.com/html5")

It is no longer a trial, Youtube has switched to html5 by default. [http://techcrunch.com/2015/01/27/youtube-goes-html5-flash-is-now-deader/](http://techcrunch.com/2015/01/27/youtube-goes-html5-flash-is-now-deader/)

Actually it has been that way on Chrome for quite a while. I find html5 streaming a lot smoother on Chrome than Firefox for machines with weak cpu but decent graphic cards, it seems that it uses some kind of hardware acceleration that doesn't work in FF.

---

### Post by udomoody on 2015-02-17
> **monkeybrain20122 said:**
> What are your computer's specs? Well if your system is too weak to play flash (instead of some graphic driver problem) html5 likely wouldn't work any better (still high cpu load if not higher) but streaming through mplayer would improve things quite dramatically. 

Try using gecko-mediaplayer and Viewtube (install gecko-mediaplayer from repo, install the grease-monkey addon for Firefox, then restart Firefox and install Viewtube [http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en), you can adjust the playback resolution. It works on Youtube and a few other sites too.

Actually HTML5 works better than flash, but the CPU usage is still pretty high. I just tried Viewtube and it works great I think I will continue to use that. Thank you all for your help.

---

