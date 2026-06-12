---
title: "No video after Restricted-extras install for xubuntu/lubuntu 12.04"
date: 2012-09-07
forum: Multimedia Software
---

### Post by resander on 2012-09-07
I wanted to make use of an old (8-10 years) spare Athlon desktop and initially installed ubuntu 12.04 on it. It worked but was very slow, so I installed xubuntu 12.04 and lubuntu 12.04 as dual boot instead. They were much faster and worked very well, so installed the restricted-extras packages on both and expected videos to show. They did not not. I tried:

1.  Jan Joahansson - Swedish jazz pianist playing Visa fran Utanmyra (old folk music). [http://www.youtube.com/watch?v=LMgitKv-78I](http://www.youtube.com/watch?v=LMgitKv-78I)

2.  accessing the first page of [www.inquirer.net](www.inquirer.net) (a daily newspaper) that always contains a ticker-type style video montage at the top showing the main news events. 

Both show fine from Firefox on my main desktop that runs ubuntu 10.04 LTS and as far as I can remember also worked for earlier main Ubuntus after installation of restricted-extras.

I accessed 1 and 2 above from Firefox on xubuntu and lubuntu and also 1 from Google Chrome on lubuntu. 

I have always used main ubuntu and have (re)installed it many times on several computers and have always been able to view videos from the web.

What is different on xubuntu/lubuntu? (I have never used these before).

Hoping for advice...

Ken

---

### Post by resander on 2012-09-10
The PC is an Athlon 1.6GHz with 512MB RAM and 40GB hard disk. 

On my main desktop (2.4GHz, 2GB ram) running Ubuntu 10.04 LTS the 'ticker-type' display at the Daily Inquirer ([www.inquirer.net](www.inquirer.net)) shows all 10 items, videos and images (about half-half), but Ubuntu 10.04 LTS, Ubuntu 12.04, Xubuntu 12.04 and Lubuntu 12.04 (Quad-boot) on the Athlon only showed the images. The video window containing a triangular 'Start' button never appeared for Firefox, Chromium, Opera and Arora browsers.

Other observations for the Athlon:

The Chromium browser reports 'shockwave flash plugin crashed' for all distros.

Arora only worked in text-mode for Lubuntu and crashed after a few minutes from Xubuntu 12.04.

Firefox on Ubuntu 10.04 complains about missing plugin, but did not tell which one, when playing many youtube videos.

Firefox on 10.04 could play some youtube videos, but the same videos did not render on the other distros with Firefox. 

Movie players work well for playing avi video files on Ubuntu 10.04/12.04 and Xububtu 10.04.

I am beginning to think 512MB is not enough for (streaming) videos from inside the browser.   

Q1. can I request log info from the browsers to help to pinpoint this problem, or can I get Firefox to tell me which plugin is missing?

Q2. anyone got streaming videos to work with 512MB memory?

---

### Post by factsheet on 2012-09-15
Same problem here.. I successfully installed lubuntu-restricted-extras.. Some videos play, some don't.. Which is more frustrating than before because I expected that there would be no more problems playing videos on YouTube..

Eight plug-ins are currently installed on both Chromium and Firefox..
Remoting Viewer
Shockwave Flash 11.2 r202
IcedTea-Web Plugin (using IcedTea-Web 1.2 (1.2-2ubuntu1.2))
DivX Browser Plug-In
QuickTime Plug-in 7.6.9
RealPlayer 9
Windows Media Player Plug-in
mplayerplug-in is now gecko-mediaplayer 1.0.4

If I tick on the checkbox for Flash under chrome://plugins and then go back to the video page, it would ask permission to run the Flash plugin "Always run on this site" and "Run this time".. I clicked one, didn't work.. I clicked on the other one, still didn't work..

I hope someone could help us..

---

### Post by Bucky Ball on 2012-09-15
*Moved to **Multimedia & Video***

---

### Post by factsheet on 2012-09-15
Heya! Sorry for double posting.. I finally managed to get YouTube videos working now, even the one you posted.. What I did was downgrade the Flash version..

Here's the link to the thread [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

