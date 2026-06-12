---
title: "Black screen and trouble loading video"
date: 2014-11-29
forum: Multimedia Software
---

### Post by trevor_2 on 2014-11-29
Hi, this is my last resort to understanding my problem with my newly installed OS Ubuntu. Quick history: I was using windows 7, put ubuntu to test out on a usb somehow it still ended up wiping my os even though it said no os was found when I was trying to install.. yeah anyway I've just bit the bullet and decided to learn ubuntu and how to use it since I wanna go into cyber security. Now onto my problem..Recently I've been trying to watch the shows I normally watch on my regular sites and to my surprise they are not working correctly. for example crunchyroll gives me just a black screen for endless amounts of time sometimes it starts after 10min sometimes not. and other video streaming sites would work fine..hulu works flawlessly (Don't watch hulu) and yeah. And another issue that I think is tied to this is the fact that the shows that I watch on other websites the ones that usually preload or load while ur watching they work..but take forever to start. 

And this is my good pc has 8gbs of ram and 2tbs of space..

I want to blame the internet but even though my speeds go up and down from 15+Mbps to 3Mbps. My crappy ass hp pavilion laptop loads crunchyroll and my other sites in a flash.. soo Idk whats wrong idk its firefox or chromium (switch through both) or is it my flash? ive downloaded the latest adobe and pepper flash so idk what else to do besides re installing ubuntu and trying over from scratch. ANY HELP if you stayed this long after my rant would be much appreciated :(

---

### Post by ajgreeny on 2014-11-29
> **trevor_2 said:**
> I want to blame the internet but even though my speeds go up and down from 15+Mbps to 3Mbps. My crappy ass hp pavilion laptop loads crunchyroll and my other sites in a flash.. soo Idk whats wrong idk its firefox or chromium (switch through both) or is it my flash? ive downloaded the latest adobe and pepper flash so idk what else to do besides re installing ubuntu and trying over from scratch. ANY HELP if you stayed this long after my rant would be much appreciated :(
How have you downloaded and installed the flash plugins?

You need to do all that using the **software-centre** (or **synaptic**) or using the command-line ```
sudo apt-get install *packagename*
```which for Firefox flash is **flashplugin-installer** and for chromium is **pepperflashplugin-nonfree**.

---

### Post by trevor_2 on 2014-11-29
I have installed both flashes using the Terminal first i installed adobe from the site...it worked but it only allowed the stuff to be seen and interacted with the video players themselves werent playing or if they played they played super slow or loaded and just kept loading. so i then installed a flash through Terminal..still wasn't acting right so i switched to chronium and heard u need pepper flash so then went into terminal and downloaded that.. Now don't get me wrong.. its an improvement the crunchyroll videos only stay at a black screen for about 3min or so then it starts but thats still hella long and makes no sense for my expensive ass computer

---

### Post by trevor_2 on 2014-11-29
> **trevor_2 said:**
> I have installed both flashes using the Terminal first i installed adobe from the site...it worked but it only allowed the stuff to be seen and interacted with the video players themselves werent playing or if they played they played super slow or loaded and just kept loading. so i then installed a flash through Terminal..still wasn't acting right so i switched to chronium and heard u need pepper flash so then went into terminal and downloaded that.. Now don't get me wrong.. its an improvement the crunchyroll videos only stay at a black screen for about 3min or so then it starts but thats still hella long and makes no sense for my expensive ass computer

Quick update: So as of today in Chronium I can load certain kinds of videos just fine now..I don't understand how but they load fine now. Now my only problem is Crunchyroll because that still just leaves me at a black screen for more than 10minutes of me sitting and staring at it. Which I will take up with them because maybe its some issue they can fix themselves hopefully.. as of this morning this is how Its going will check back when I get word from them.

---

### Post by ajgreeny on 2014-11-30
You again say you "downloaded pepperflash" but don't say how.
You should always add these things through the repositories, not going direct to Adobe, so if your version was added direct, try again with software-centre.

---

### Post by trevor_2 on 2014-11-30
I downloaded pepperflash through the terminal and adobe through the site itself.

---

### Post by carlwsnyder on 2014-12-01
When you go to the [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) website, with chromium/pepperflash, you should see the animation at the top, and it should report 15.0.0.239 as the version of Flash installed.

For Firefox/flashplugin the version report should be 11.2.202.424 for flash.

When I went to the crunchyroll.com website and viewed either standard definition or 480p, I had only a few seconds delay before the animation starts, with 10Mbps download speed, Chromium with pepperflash as reported, Xubuntu Vivid daily update.

---

