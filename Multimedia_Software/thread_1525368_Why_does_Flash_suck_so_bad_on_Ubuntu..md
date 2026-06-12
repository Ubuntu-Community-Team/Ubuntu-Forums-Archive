---
title: "Why does Flash suck so bad on Ubuntu."
date: 2010-07-06
forum: Multimedia Software
---

### Post by NobleSavage on 2010-07-06
I just upgraded from the last LTS version to 10.04 Lucid Linux and Flash just totally sucks. 

I keep trying to watch videos at [http://www.ted.com/](http://www.ted.com/)  and the videos play for about 1 minutes then it locks up and gives me this error: "Unable to play the video specified: rtmp:1935//streaming.ted.com/talks/dynamic/MichaelPollan_2007-high"

I have followed all of suggestions in the "Comprehensive Multimedia & Video Howto" by ubuntu-freak and I'm still having major problems with Flash videos.

Any help or advice is much appreciated.

---

### Post by bliffle on 2010-07-06
You can try 'gnash', the linux opensource version of Flash.

I do not install any Macromedia Flash program. My experience is that Flash contains code to send your data back to Macromedia (or whomever), and which is a gateway for hackers. Years ago I had a seriously hacked windows XP system whose troubles I tracked down to Flash. Ergo, I NEVER install their stuff.

I use a Download Helper for Youtube stuff, and for anything else I learn to live without it. I also write emails of complaint to the crooks who want to compel me to install Flash. There's nothing I need so badly that I would chance turning my PC into a mailbot.

The army of Child Website Creators unleashed in the last few years seem not to understand what they are doing, and just say "everybody else is doing it".

---

### Post by ajgreeny on 2010-07-06
> **bliffle said:**
> You can try 'gnash', the linux opensource version of Flash.

I do not install any Macromedia Flash program. My experience is that Flash contains code to send your data back to Macromedia (or whomever), and which is a gateway for hackers. Years ago I had a seriously hacked windows XP system whose troubles I tracked down to Flash. Ergo, I NEVER install their stuff.

I use a Download Helper for Youtube stuff, and for anything else I learn to live without it. I also write emails of complaint to the crooks who want to compel me to install Flash. There's nothing I need so badly that I would chance turning my PC into a mailbot.

The army of Child Website Creators unleashed in the last few years seem not to understand what they are doing, and just say "everybody else is doing it".
Whilst I accept some of what you say, it seems to me you are "cutting of your nose to spite your face", to use a well known English homily.

I would avoid gnash as it is very poor in comparison with Adobe flash, and performance will be even worse than the adobe version which you are already complaining about.

I fear the relatively poor flash available for all lunux distros is simply because adobe flash linux port, is not as good yet as it is for windows.  It's getting better, but still has some way to go.  It is nothing to do with Ubuntu, or it's flash version compared with other linux distros.

---

### Post by v1ad on 2010-07-06
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

install that add-on for firefox. it takes care of chrome & firefox. it re installs the flash player. never had any problems since.

---

### Post by snowpine on 2010-07-06
Flash is "closed source" (or "proprietary") software developed by the Adobe Corporation. There is nothing that Canonical, the creators of Ubuntu, can do to improve your Flash experience, as they do not have access to the source code. :(

I personally have had better luck downloading videos to my hard drive first, rather than trying to watch them streaming from the web. There are many "youtube downloaders" out there, but I find the simplest solution is to simply play the video in my browser, hit Pause, and then navigate to the /tmp directory, find the video, wait for it to finish buffering, and copy it to my /home/snowpine/videos folder.

---

### Post by ajgreeny on 2010-07-06
> **snowpine said:**
> Flash is "closed source" (or "proprietary") software developed by the Adobe Corporation. There is nothing that Canonical, the creators of Ubuntu, can do to improve your Flash experience, as they do not have access to the source code. :(

I personally have had better luck downloading videos to my hard drive first, rather than trying to watch them streaming from the web. There are many "youtube downloaders" out there, but I find the simplest solution is to simply play the video in my browser, hit Pause, and then navigate to the /tmp directory, find the video, wait for it to finish buffering, and copy it to my /home/snowpine/videos folder.
+1
This is what I also do and have a simple script in my panel to do the copying job.
```
#!/bin/bash
cp /tmp/Flash* /home/username/YTMovies
```

---

### Post by snowpine on 2010-07-06
> **ajgreeny said:**
> +1
This is what I also do and have a simple script in my panel to do the copying job.
```
#!/bin/bash
cp /tmp/Flash* /home/username/YTMovies
```

Brilliant! :popcorn:

---

### Post by lovinglinux on 2010-07-09
> **snowpine said:**
> Flash is "closed source" (or "proprietary") software developed by the Adobe Corporation. There is nothing that Canonical, the creators of Ubuntu, can do to improve your Flash experience, as they do not have access to the source code. :(

I personally have had better luck downloading videos to my hard drive first, rather than trying to watch them streaming from the web. There are many "youtube downloaders" out there, but I find the simplest solution is to simply play the video in my browser, hit Pause, and then navigate to the /tmp directory, find the video, wait for it to finish buffering, and copy it to my /home/snowpine/videos folder.

Have you tried my [FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/161869) extension? It replaces the video on the site, allowing you to watch it with other plugins like gecko mediaplayer, gxine, kaffeine, mozplugger, totem and xine plugins.

It works on a couple of sites for now, but I'm implementing support for more sites, that should be available on version 1.0.2. [Version 1.0.1](https://addons.mozilla.org/en-US/firefox/addon/161869/versions/) has already been released, but hasn't been approved by Mozilla yet.

---

### Post by NobleSavage on 2010-07-11
> **lovinglinux said:**
> Have you tried my [FlashVideoReplacer](https://addons.mozilla.org/en-US/firefox/addon/161869) extension? It replaces the video on the site, allowing you to watch it with other plugins like gecko mediaplayer, gxine, kaffeine, mozplugger, totem and xine plugins.

It works on a couple of sites for now, but I'm implementing support for more sites, that should be available on version 1.0.2. [Version 1.0.1](https://addons.mozilla.org/en-US/firefox/addon/161869/versions/) has already been released, but hasn't been approved by Mozilla yet.

Hey lovinglinux,  I just tried your plugin but it doesn't seem to work on ted.com

What I don't understand is this:  I have 3 computers running Ubuntu. On is 8.04 or the old LTS and (with your prior help) it plays flash perfect even on ted.com.  Now I just installed 10.04 on an older computer that my neighbor was gonna pitch and it works perfect on all sites including ted.com

Now, I have 10.04 installed on my laptop and flash seems to work everywhere but ted.com  The video will play for 1-2 minutes then I keep getting this error:

Unable to play the video specified: rtmp:1935//streaming.ted.com/talks/dynamic/EllenGustafson_2010X-high

---

### Post by NobleSavage on 2010-07-11
Well, I just solved my problem.  I the laptop was hoked up to the net via WiFi... and with a weak signal. 

I plugged the laptop directly into the router and Ted.com works perfect.  I guess their streaming software sucks at buffering, and just chokes up.

---

### Post by lovinglinux on 2010-07-11
> **NobleSavage said:**
> Hey lovinglinux,  I just tried your plugin but it doesn't seem to work on ted.com


Currently it only supportd YouTube, Vimeo and Blip.tv. More sites will be added to version 1.0.2. Version 1.0.1 has bug fixes only and is waiting for Mozilla approval.

---

### Post by efflandt on 2010-07-12
You might want to mark this thread solved.

I have a remote friend whose flash video and audio started pausing every few seconds on a new Dell Inspiron 1545 in 64-bit Win7.  I could not understand that because on my old slow desktop it would simply drop frames if it could not keep up, but sound did not pause.  It turned out that her economy RoadRunner 768/128 was not up to the task.  She got that bumped up to 6 Mbps and all is well.

So I could see how a weak wireless signal could cause frustration.

I just got a Dell XPS 8100 with i5 3.2 GHz and nVidia GT220 and Hulu Desktop in 64-bit 10.04 (just using 32-bit flash in flashplugin-installer) is very smooth.

---

### Post by Chriske on 2011-05-15
Something I noticed is that Flash runs "perfectly" in Puppy Linux.

I installed Puppy for testing purposes and was amazed at how much better Flash performed: no choppiness, poor audio synchronisation, or (worst of all) the computer freezes/crashes I experience when I watch a Flash video in Ubuntu.

I wonder why this is?

I wish there were a way to sort it out because as of now I boot into Puppy when I want to watch any online video over a couple of minutes long. :(

---

### Post by Sworddragon on 2011-05-15
VDPAU increases the performance heavily if you have the right graphics card (most of GeForce 8xxx and all higher versions). But it seems that libvdpau1 is not working in the current version.

---

