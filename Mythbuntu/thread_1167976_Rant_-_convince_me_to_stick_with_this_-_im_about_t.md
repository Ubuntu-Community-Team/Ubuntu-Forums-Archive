---
title: "Rant - convince me to stick with this - im about to go to MCE"
date: 2009-05-23
forum: Mythbuntu
---

### Post by scottac on 2009-05-23
alright so I am very frustrated. for the last two weeks I have been tirelessly working on getting a mythbackend/mythfrontend box set up. I have gotten absolutely nothing accomplished and I feel like I am about to give up and go back to windows.

Here is my hardware-
motherboard - intel975xbx2
cpu - intel q6600
video card - nvidia 9500gt (w hdmi out)
Hardrives - 74 GB WD Raptor
            3 1TB WD drives (want to put into raid5 but can't get anything to work)
Capture card - SiliconDust HDHomerun

I know for a fact that I have hardware that is verified to work with linux/myth yet I can't get anything to work. 

I am not a complete linux noob. I have been using some variation of ubuntu on all my machines for about 7 months now and am a CS EE major. I have even taken classes specifically about software development in linux/unix systems and gotten a's and b's in all of them.  I am not an idiot and I am not afraid to wade through the details of computer systems and software that I am not familiar with. 

So I have all this hardware that I know is supposed to work with mythbuntu and mythtv yet I can't get anything working.

The documentation for linux distributions just doesn't seem complete anywhere I look, specifically with regards to troubleshooting. and troubleshooting seems to be all I do. I can't get the tuner to work, I can't get the raid array set up. I can't get the video card to display a quality picture. I can't even get mythtv to play a damn .avi file that I have in the var/lib/mythtv/videos directory.

My objective in setting this system up was to become more familiar with linux systems and how they work. But at the same time I want a working media center pc and it seems that at every turn I am not able to accomplish anything and feel like setting myself on fire.  

So as much as it pains me to admit this. I am seriously thinking about going back to a windows MCE OS which while not stable, I can at least get to work. mythtv is just making me feel like a complete retard and I am getting sick of it.

No replies necessary just sharing my thoughts. However if anybody has any words of encouragement please feel free to convince me to stick with it.

Fredo

---

### Post by Triptol on 2009-05-23
With Windows MCE you don't own your recordings. You are only allowed to play them on your Windows MCE and not take them with you (on your laptop).

Building your own box and configuring every part of it is a GREAT feeling (I had my ups and my downs with my box as well).

Even if you don't want answers, I am still curious what you can't get to work.

---

### Post by scottac on 2009-05-23
I can't get the tuner to display any channels.  I get errors with this constantly in my log.  I also can't seem to get help with this. I have posted the logs both here and other forums and I suppose the logs are just as cryptic to everybody else as they are to me..

I can't get a raid array set up and mounted. I have thus far been able to create the array, format the array (once). but was unable to mount the array. So I started over again (with a clean install) and now when it tries to create the array it tells me the devices are busy. 

video card. I have been screwing around with this for months now prior to my attempt a few weeks ago to get myth set up. I can't get the 180.xx or  the 177.xx driver to display a quality HD picture. I was so jealous yesterday when my roommate bought a 27" HD tv for his room and all he had to do was plug in the HDMI cable and voila HD video immediately.  

Why cant the Nvidia-settings GUI just set up the xorg.conf file for the user automatically.  Why is this so difficult to program correctly. 

Uggghhh..  I had forgotten about this nvidia problem for the last two weeks while I have been trying to get everything else working and now I am getting pissed all over again. I even bought a new video card cause I and others on this forum and a few otheres were convinced that my card was faulty but again the same problem.  

So to answer your question. pretty much everything I have tried to set up properly I have thus far failed at. And that is why I am getting so frustrated...

---

### Post by glotz on 2009-05-23
Give up man, I know you want to!

*You'll* never make it anyway.

---

### Post by kcaj on 2009-05-23
I also had a problem getting the display to properly be recognized by the system. I am switching my system through an Onkyo HT amp and when I booted the system the amp was on the satellite box instead of the PC. Booting with the amp switched to the PC and the TV on solved the problem of recognizing and properly setting the display. 

On my system (Mythbuntu 8.10) the raid software is not installed. If you type *mdadm* you will get something like:

```

The program 'mdadm' is currently not installed.  You can install it by typing:
sudo apt-get install mdadm

```Jack

---

### Post by tgm4883 on 2009-05-23
First things first.  It's not my job to convince you to stick with Mythbuntu or any other OS.  

There are not unique Troubleshooting techniques for Linux, the techniques are the same across all OS's.  Check logs, test situations, isolate problem, etc.

Now lets get started.

I don't have a HDHomerun myself, so I'm going to have to ask some questions i've seen posted other places.  Basic troubleshooting stuff.

RE: HDHomeRun
> Have you upgraded to the latest firmware? Will it capture to a
file for you with hdhomerun_config save?

See if it's a MythTV problem, or a OS problem.  Then we can troubleshoot from there.  IIRC, the first HDHomeRun units had to be initialized in Windows first.  I don't think you have to do initialize them anymore, if you do though, you don't have to do it in Windows.

RE: Playing back AVI's
If you play an AVI on a fresh Windows install what happens. WMP complains about codecs.  Same here.  Please use MCC to install the restricted codecs.

RE: RAID
Do you have a RAID controller?  If so, does it have it's own setup options during boot?  If not, are you talking about software RAID?

RE: Video card
What do you mean it doesn't display a "quality picture"?  Is the resolution bad, or is it in black and white?  Is there multiple pictures on the screen or is it out of aspect ratio?

---

### Post by Kheos on 2009-05-23
> **scottac said:**
> alright so I am very frustrated. for the last two weeks I have been tirelessly working on getting a mythbackend/mythfrontend box set up. I have gotten absolutely nothing accomplished and I feel like I am about to give up and go back to windows.

Here is my hardware-
motherboard - intel975xbx2
cpu - intel q6600
video card - nvidia 9500gt (w hdmi out)
Hardrives - 74 GB WD Raptor
            3 1TB WD drives (want to put into raid5 but can't get anything to work)
Capture card - SiliconDust HDHomerun

I know for a fact that I have hardware that is verified to work with linux/myth yet I can't get anything to work. 

I am not a complete linux noob. I have been using some variation of ubuntu on all my machines for about 7 months now and am a CS EE major. I have even taken classes specifically about software development in linux/unix systems and gotten a's and b's in all of them.  I am not an idiot and I am not afraid to wade through the details of computer systems and software that I am not familiar with. 

So I have all this hardware that I know is supposed to work with mythbuntu and mythtv yet I can't get anything working.

The documentation for linux distributions just doesn't seem complete anywhere I look, specifically with regards to troubleshooting. and troubleshooting seems to be all I do. I can't get the tuner to work, I can't get the raid array set up. I can't get the video card to display a quality picture. I can't even get mythtv to play a damn .avi file that I have in the var/lib/mythtv/videos directory.

My objective in setting this system up was to become more familiar with linux systems and how they work. But at the same time I want a working media center pc and it seems that at every turn I am not able to accomplish anything and feel like setting myself on fire.  

So as much as it pains me to admit this. I am seriously thinking about going back to a windows MCE OS which while not stable, I can at least get to work. mythtv is just making me feel like a complete retard and I am getting sick of it.

No replies necessary just sharing my thoughts. However if anybody has any words of encouragement please feel free to convince me to stick with it.

Fredo
I know exactly what you mean, man. 
First I tried 8.10 and while I got quite far, I still had a ******** of issues(no sound, couldn't get the vfd or lcd or whatever to work...) so I just whiped my harddrive and tried again, but the resolution was all ****** up. Finally I tried the 9.4 but now i don't get it running al together. At this moment I don't feel MythBuntu is better than MCE or even an alternative. I will give another try, and another and another but I'm quite discouraged and disappointed my MythBuntu. I didn't expect a walk in the park, but I didn't expect a 3-months-survival-being-chased-by-guerilla-troops-carefull-for-the-venomous-snakes-sleep-with-one-eye-open-expedition-either

---

