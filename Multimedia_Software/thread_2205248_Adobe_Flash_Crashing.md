---
title: "Adobe Flash Crashing"
date: 2014-02-12
forum: Multimedia Software
---

### Post by Bedpan.ca on 2014-02-12
I am running a clean install of 64bit Kubuntu 13.10. Whenever I try to play any videos on YouTube, it starts to play however there is no sound, and after a second or two the flashplugin crashes and I get no video.

When first setting up my system I had no sound whatsoever, and the computer was running very slow. I had to specify a special option in my /etc/modprobe.d/alsa-base.conf file, which resolved the sound issue and the computer runs smoothly now, however I still have no working flash. I don't know if these two issues are related.

I can still access the flashplugin settings, however if I click on the microphone tab it crashes, and if I click on the webcam video box in the webcam tab, it also crashes.

I tried with Chromium and the flashplugin runs the same way. I set up pepperflash and that works without any problems, but I would like to get Firefox working.

I am running Firefox 27.0 with adobe-flashplugin:
    File: libflashplayer.so
    Path: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 11.2.202.336
    State: Enabled
    Shockwave Flash 11.2 r202

I have tried reinstalling firefox and flash, but still no joy. Any help would be appreciated.

---

### Post by Yellow Pasque on 2014-02-12
Try clearing the cache (which stays in your homme folder even after you purge Flash):
```
rm -r ~/.adobe
```

---

### Post by Bedpan.ca on 2014-02-12
Thanks for the thought, but it made no difference.

---

### Post by Jonor on 2014-02-13
What other plugins are Always Active besides Shockwave Flash in Firefox ?
Firefox volunteered a warning notice at the bottom of the browser window, that it was starting too slow and some stuff should be checked.
When the [COLOR="#B22222"]top[/COLOR] command was run in a terminal an Itunes plugin was taking a significant CPU percentage, so seeing i never knowingly use anything
Itunes it got removed using Synaptic and everything speeded up a bit, or so it seemed. Every plugin other than Flash is set to Ask To Activate.
Annoyingly, attempts to reduce Flash demands further by adjusting down the video quality in things like Youtube, never seem to stick for more than the current video being watched.

---

### Post by Bedpan.ca on 2014-02-13
As far as plugins go, I only have Flash and VLC installed. I tried deleting my ~/.mozilla folder and starting with a clean new everything, and disabled everything except for flash, but I still cannot play YouTube.

---

### Post by Jonor on 2014-02-13
Would you give *very rough* %CPU  and %MEM usages for both [COLOR="#B22222"]firefox[/COLOR] and the [COLOR="#B22222"]plugin-containe[/COLOR] when [COLOR="#B22222"]top[/COLOR] is run in a terminal *while* trying to to use Youtube ?

---

### Post by Bedpan.ca on 2014-02-13
firefox
  %CPU: 40-60
  %MEM: 2ish
plugin-containe
  %CPU: 15-70
  %MEM: 0.5ish

---

### Post by Bedpan.ca on 2014-02-13
Okay. Weird thing: I clicked on a 15 second video, and it played normally. Everything else still crashes...

---

### Post by Jonor on 2014-02-14
With those %CPU levels i don't think there is anything much you can do right now short of overclocking.
There are threads such as [this]("http://ubuntuforums.org/showthread.php?t=2198551") indicating that there will be a shake up with Flash shortly so i would wait and see 
as Youtube might work well on your hardware after that.

---

### Post by Bedpan.ca on 2014-02-14
What I don't get is that before my clean install, I was running the same software with the same version of kubuntu and everything worked. My quad core 2.8ghz didn't struggle with my old motherboard, but with the new one it does.

---

### Post by Bedpan.ca on 2014-02-14
Movie trailers on IMDB play without crashing, but there is no audio...

---

### Post by Jonor on 2014-02-15
Obviously your CPU should easily manage Youtube if it is not faulty, i suggest you use a log file viewer to look at some files such as /var/log/dmesg or /var/log/syslog. Use intuition to try and determine if there are any serious problem messages and then Google them and/or post them here.

---

### Post by d-cosner on 2014-02-16
I turn off hardware acceleration in Firefox first because as I understand it is not supported under Linux. Next, I open a YouTube video in full screen, right click on it and take away the check mark in settings for hardware acceleration. For some reason the video needs to be in full screen for this to work. Restart Firefox and YouTube videos should play without crashing.

I have used this method on several computers and it has worked every time. Unfortunately, sometimes there will be a slight hesitation once in a while while playing a video but it is not too bad and at least videos play half way decent. 

MiniTube will play YouTube videos without problems as long as you install the current version. You can get minitube from the authors web site or from the software center. In the software center the current version is called minitube-ubuntu. The older version simply labeled as minitube will not work, so if you decide to go this route it is important to install the current version so that it will run on your system.

---

### Post by Bedpan.ca on 2014-02-16
Thanks for your guess, but even with hardware acceleration disabled from a fullscreen movie, my problem persists.
I still have my money on it being an ALSA issue, but I havent found anything that helps yet.

---

### Post by Bedpan.ca on 2014-02-20
Firefox updated yesterday, flashplugin updated today. Youtube still crashes. I tried with a new clean profile, still no luck...

---

### Post by monkeybrain20122 on 2014-02-20
You keep talking about Youtube, does it mean videos work on other flash sites?  It is not clear from your posts whether you have a flash problem or a Youtube problem. Youtube != flash !

If other sites work then it is probably not a flash problem but your Firefox profile being corrupted or something. Try clear all your cookies and restart Firefox and see if it works. If still crashing create a new profile and test again.

BTW, you can play all Youtube videos in html5 (among MANY non flash solutions) so if Youtube is all you care about you don't even need flash.[https://addons.mozilla.org/en-US/firefox/addon/youtube-flash-to-HTML5/](https://addons.mozilla.org/en-US/firefox/addon/youtube-flash-to-HTML5/) (flash does have to be disabled if you use this)

---

### Post by Bedpan.ca on 2014-02-20
I say Youtube because its the quickest place I could think of to easily test flash. Its a mixed bag as far as other websites go. imdb i know plays the videos fine, but no audio. I  don't think I have heard any sound through flash on any site.

As mentioned in my last post, I have tried with a new clean profile and it made no difference.

And HTML5 for Youtube is just putting a band-aid on the problem. Im hoping to resolve it.

---

### Post by Bedpan.ca on 2014-03-10
HTML5 still has no audio either.

I tried getting XBMC going the other day and noticed that it too has no audio, so I a leaning towards this being an ALSA issue, but I still haven't made any progress.

---

