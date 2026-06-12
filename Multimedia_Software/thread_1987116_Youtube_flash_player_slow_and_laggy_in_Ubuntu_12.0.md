---
title: "Youtube flash player slow and laggy in Ubuntu 12.04 LTS"
date: 2012-05-25
forum: Multimedia Software
---

### Post by Vinnizz on 2012-05-25
[size=3][COLOR="#FF0000"]**Moderator note.** If you have found this forum thread from a google or other search, please be warned: there appears to be no logical reason why this should work. The method appears elsewhere, although it is impossible to tell where it started, and seems to have become some sort of internet version of a folk remedy for flash problems. Despite the claims that some in this thread have made that it has solved their flash problem, the forum staff urge caution in its use. Use at your own risk. It may have adverse effects on your system. In particular, be careful to add in the extra code properly otherwise you may break the functionality of the package and update managers.[/COLOR][/size]


So I've had the same problem as a lot of people, youtube was extremely laggy even when I played 240p videos and I tried everything, html5 youtube, flash-aid plugin for firefox and whatnot, and they didn't work for me.
Then I enabled "Override automatic cache management" on firefox. It got a little better but still a bit laggy on fullscreen.

Then I thought I'd let Ubuntu use more cache . So if you have the same problem just try this:

sudo gedit /etc/apt/apt.conf.d/70debconf.

Then put this code,:
 APT::Cache-Limit "100000000";
 on that file and then save it. 

Next type this code on your terminal
sudo apt-get clean && sudo apt-get update --fix-missing
and you won’t find apt cache limit again in the next time.

It worked for me!!! :D

---

### Post by Damien Doe on 2012-06-01
After trying some of the same things as you, I thought I'd give this a try.

It worked!

Thanks!
-J.C.

---

### Post by Myon87 on 2012-06-06
Worked for me aswell!

---

### Post by rearentry on 2012-06-14
This isn't just a fix this is an improvement. It seems Ubuntu is holding the cache back for some reason. I haven't actually had any major problems with flash but looked this up for a friend and tested it just to make sure it wouldn't crash and holy high definition video! It even improved the function of VLC and and streaming HD 1080p from my server over my Wifi is a breeze.
If you're reading this do it even if you don't have problems with flash.
Thanks!!! (there is no emoticon for how I feel so this will have to do) 
:guitar: :guitar: :guitar:

---

### Post by polyethlene on 2012-07-27
Thank you so much for this solution!  It was so frustrating to have the lag issues when watching videos online.  This SOLVED my problem.  Thank you!!!

---

### Post by pqwoerituytrueiwoq on 2012-07-27
how could changing how much space is allowed for apt to store packages (deb files) possibly affect video performance?

---

### Post by michael-wd21 on 2012-08-03
> **pqwoerituytrueiwoq said:**
> how could changing how much space is allowed for apt to store packages (deb files) possibly affect video performance?


Exactly, what's going on here?

Maybe the flash-aid plugin is what's helping. I'm going to give that a try.

Or this bit:

> Then I enabled "Override automatic cache management" on firefox

I don't see how that would help either though, this refers to disk cache for web content.

---

### Post by LaptopU on 2012-08-04
Fantastic, just logging in to say this has solved my laggy flash video playback too. :D

Thank you :)

---

### Post by kino2984 on 2012-08-08
Thanks :)

---

### Post by SterlingM on 2012-08-15
Hey guys, my flash is still laggy and my wifi will cut out when I stream it after about 1-1.5 minutes. I've tried all the suggestions here...does anyone have any other ideas I could check for?

---

### Post by WEPrechaun on 2012-09-28
For some reason, my Flash playback works fine only when fullscreen is running. Why?

---

### Post by vasa1 on 2012-09-28
> **pqwoerituytrueiwoq said:**
> how could changing how much space is allowed for apt to store packages (deb files) possibly affect video performance?
There's something *odd* about this thread.

---

### Post by GRFrones on 2012-10-09
Well... it's worked for a few people, already... I didn't know computers were also susceptible to placebo. hehe

I'm also having problems with flash player in both of my ubuntu systems. They get laggy in youtube, flash games, etc.

Does anyone know of a solution unrelated to placebo? haha

Best Regards,
Gabriel.

---

### Post by derklempner on 2012-10-10
> **Vinnizz said:**
> So I've had the same problem as a lot of people, youtube was extremely laggy even when I played 240p videos and I tried everything, html5 youtube, flash-aid plugin for firefox and whatnot, and they didn't work for me.
Then I enabled "Override automatic cache management" on firefox. It got a little better but still a bit laggy on fullscreen.

Then I thought I'd let Ubuntu use more cache . So if you have the same problem just try this:

sudo gedit /etc/apt/apt.conf.d/70debconf.

Then put this code,:
 APT::Cache-Limit "100000000";
 on that file and then save it. 

Next type this code on your terminal
sudo apt-get clean && sudo apt-get update --fix-missing
and you won’t find apt cache limit again in the next time.

It worked for me!!! :D
Unbelievable.  Not only did this fix the laggy Flash videos in Firefox for me, but it also stopped Flash videos in Chrome from playing too fast.

Canonical should really change **70debconf** to add this line.  It completely fixed all of my issues with Flash videos.

---

### Post by JoZ3 on 2012-11-20
> **Vinnizz said:**
> So I've had the same problem as a lot of people, youtube was extremely laggy even when I played 240p videos and I tried everything, html5 youtube, flash-aid plugin for firefox and whatnot, and they didn't work for me.
Then I enabled "Override automatic cache management" on firefox. It got a little better but still a bit laggy on fullscreen.

Then I thought I'd let Ubuntu use more cache . So if you have the same problem just try this:

sudo gedit /etc/apt/apt.conf.d/70debconf.

Then put this code,:
 APT::Cache-Limit "100000000";
 on that file and then save it. 

Next type this code on your terminal
sudo apt-get clean && sudo apt-get update --fix-missing
and you won’t find apt cache limit again in the next time.

It worked for me!!! :D

Thanks!!! work fine in ubuntu 12.10 :guitar:

---

### Post by detlev24 on 2012-11-29
hi, i tried a lot of things and this is what finally _**worked**_ on **linux mint 14 64-bit** and **32-bit** (which is based on ubuntu 12.10); with amd catalyst 12.11 beta for radeon hd 7470m graphics card:

1. **sudo apt-get install gecko-mediaplayer** (*firefox-plugin for mplayer*)
2. i deactivated all plugins for _totem_ and divx in firefox (*but the new ones*)
3. i installed **greasemonkey** add-on in firefox
4. i installed **viewtube** userscript from [*https://userscripts.org/scripts/show/87011*]("https://userscripts.org/scripts/show/87011")

now at least 720p on youtube is working fine using pre-set configuration.

and what _**did not work**_:

- updating to the latest flash player (also by hand)
- enabling "override automatic cache management" in firefox
- adding _APT::Cache-Limit "100000000";_ to 70debconf via _sudo gedit /etc/apt/apt.conf.d/70debconf_
- [*http://askubuntu.com/questions/117127/flash-video-appears-blue*]("http://askubuntu.com/questions/117127/flash-video-appears-blue")

:guitar:

---

### Post by WackyClash on 2013-01-24
This also Greatly improved my flash performance. This is not a placebo. Thanks a lot for this information. Awesome!

---

### Post by mastergunner on 2013-01-30
By adding this line in APT i lost all flash. After removing the line I got flash to work again but still with the choppy playback. Still need help on this.

---

### Post by cyclothunder on 2013-02-17
Just find this thread, tried it, re-launched chromium and voilá!
It worked!! :D

Many thanks

---

### Post by Whatzit on 2013-03-09
> **detlev24 said:**
> hi, i tried a lot of things and this is what finally _**worked**_ on **linux mint 14 64-bit** and **32-bit** (which is based on ubuntu 12.10); with amd catalyst 12.11 beta for radeon hd 7470m graphics card:

1. **sudo apt-get install gecko-mediaplayer** (*firefox-plugin for mplayer*)
2. i deactivated all plugins for _totem_ and divx in firefox (*but the new ones*)
3. i installed **greasemonkey** add-on in firefox
4. i installed **viewtube** userscript from *[https://userscripts.org/scripts/show/87011](https://userscripts.org/scripts/show/87011)*

now at least 720p on youtube is working fine using pre-set configuration.

and what _**did not work**_:

- updating to the latest flash player (also by hand)
- enabling "override automatic cache management" in firefox
- adding _APT::Cache-Limit "100000000";_ to 70debconf via _sudo gedit /etc/apt/apt.conf.d/70debconf_
- *[http://askubuntu.com/questions/117127/flash-video-appears-blue](http://askubuntu.com/questions/117127/flash-video-appears-blue)*



I tried the cache-limit and it didn't work for me. 

I wondered why it had been working fine before and then just recently it had stopped working. I thought maybe I got a bad flash update.

As it turned out, I had just recently hooked up my laptop to my HD TV via an HDMI cable and I would not get sound from my TV speakers, only the laptop speakers. So, after searching the web I found a solution. I modified etc/default/grub to add this line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1 (link here: [http://community.linuxmint.com/tutorial/view/1051](http://community.linuxmint.com/tutorial/view/1051))

This worked as I could now select under System Settings/Sound my HDMI audio. What I didn't realize was that it was also the cause of my slow flash when I was not connected via HDMI but still had HDMI audio selected.

In the end my solution was to select my built-in speakers under System Settings/Sound.

Now flash video playback is back to normal!

---

### Post by d_in_Conduct on 2013-03-13
After weeks of "trying stuff" and still getting Flash crashes and large CPU loads that dragged down my whole system, I just gave up on Firefox and installed Google Chrome (not Chromium).  Flash works and CPU load is reasonable.  Chromium is all open-source, Chrome is not, but it's still a free download.

---

### Post by cannabis overdose on 2013-03-24
I keep getting a syntax error, I'm new to linux so I'm thinkin I copied the wrong lines or parts of the text wrong.  The first part works.

  [COLOR=#000000]sudo gedit /etc/apt/apt.conf.d/70debconf


Then I modified said file.

   [/COLOR]
Then this terminal cmd "[COLOR=#000000]sudo apt-get clean && sudo apt-get update --fix-missing" [/COLOR] and get the syntax error. What am I doing wrong?  Any help would be appreciated thanks.[COLOR=#000000]
.


[/COLOR]

---

### Post by shantiq on 2013-03-25
> **Vinnizz said:**
> 
sudo gedit /etc/apt/apt.conf.d/70debconf.

Then put this code,:
 APT::Cache-Limit "100000000";
 on that file and then save it. 

Next type this code on your terminal
sudo apt-get clean && sudo apt-get update --fix-missing
and you won’t find apt cache limit again in the next time.

 


Well Vinnizz tried to play 720p and 1080p for the last 2 years and it has never worked

This WORKS on my 13.04 install and for the first time i am able to see 720p perfect ! and 1080p with still a bit of lag

bumped it up to 300000000
and still lags on 1080p   any reason i should not go higher?    thought of trying 500000000

In any case many thanx

---

### Post by n3wbvip3r on 2013-05-29
created an account and logged in just to say +1

works great on my hp mini 110, which is low spec'd and why i thought video was laggy.

one catch. when i move the mouse, video freezes. stop moving it, jumps to where it should be and continues flawlessly until i move the mouse. better than 2fps videos though.. lol.

---

### Post by seanos on 2013-06-03
> **detlev24 said:**
> hi, i tried a lot of things and this is what finally _**worked**_ on **linux mint 14 64-bit** and **32-bit** (which is based on ubuntu 12.10); with amd catalyst 12.11 beta for radeon hd 7470m graphics card:

1. **sudo apt-get install gecko-mediaplayer** (*firefox-plugin for mplayer*)
2. i deactivated all plugins for _totem_ and divx in firefox (*but the new ones*)[COLOR=#ff0000]

[B] 3. i installed greasemonkey add-on in firefox
4. i installed viewtube userscript from [/B][/COLOR]**[[COLOR=#ff0000]https://userscripts.org/scripts/show/87011[/COLOR]]("https://userscripts.org/scripts/show/87011")**

Do this!

You probably already have gecko installed so that's not a big deal.

I'm even thinking of giving this a try in Windows (where  I have no probs with flash).  This script gives you control and lots of  options (e.g. players) to try.

Finally, no more jerk-o-vision!

---

### Post by denmat on 2013-06-04
Agreed. I too used HDMI output the other day (but did not adjust my grub config) and experienced the same problem. Stopping chrome, changing sound output to Analogue Output builtin audio, restarting chrome and setting sound output back to head phones solved my problem.

---

### Post by forreststevens on 2013-06-23
I've tried many, many things in this thread and others and the best solution I found was to use Chrome (not Chromium).  Though I've found the built-in Flash plugin to be unstable and buggy on alternate platforms, in Linux this is simply the only Flash option that produces reasonable performance for me. :(

---

### Post by dennis-mayr-c on 2013-09-08
I experienced the same annoyance under Ubuntu 12.04.3 on my netbook [Asus 1005PE, Intel GMA3150 video chipset, linux-generic-lts-raring kernel + xserver-xorg-video-intel-lts-raring]

In addition to the /etc/adobe/mms.cfg file workaround, I went to compizconfig settings manager (if not installed, sudo apt-get install compizconfig-settings-manager) and completely disabled the "dim windows" option under Effects, at the bottom section.

Less load on the system (without even giving up on Unity), and voilà, fullscreen flash videos don't stutter now.

---

### Post by mikewhatever on 2013-09-08
> **GRFrones said:**
> Well... it's worked for a few people, already... I didn't know computers were also susceptible to placebo. hehe

I'm also having problems with flash player in both of my ubuntu systems. They get laggy in youtube, flash games, etc.

Does anyone know of a solution unrelated to placebo? haha

Best Regards,
Gabriel.

+1, but walking backwads treats a headache for all I know.

---

### Post by darkhole on 2013-10-27
Ok, maybe the APT::Cache-Limit part is just a placebo. That value is used just by apt (when you are installing packages, etc).

But, It really worked! The cache managemente work really well!
Before aI made this, I tested YouTube ([http://www.youtube.com/watch?v=cK3NMZAUKGw](http://www.youtube.com/watch?v=cK3NMZAUKGw))
On Ubuntu + Firefox Nightly + Flash player:
10 FPS on 720p (as much)
On Ubuntu + Firefox Nightly + HTML5:
Choppy video
On Windows + Firefox Nightly + Flash player:
24 FPS with no problem on 720p
On Windows + Firefox Nightly + html5:
24 FPS with no problem on 720p

After deleted and restablished the parameters of cache I got 25 FPS with no problems (html5 and flash) I will test chromium.

---

### Post by Cerberus90 on 2013-12-06
> **Vinnizz said:**
> So I've had the same problem as a lot of people, youtube was extremely laggy even when I played 240p videos and I tried everything, html5 youtube, flash-aid plugin for firefox and whatnot, and they didn't work for me.
Then I enabled "Override automatic cache management" on firefox. It got a little better but still a bit laggy on fullscreen.

Then I thought I'd let Ubuntu use more cache . So if you have the same problem just try this:

sudo gedit /etc/apt/apt.conf.d/70debconf.

Then put this code,:
 APT::Cache-Limit "100000000";
 on that file and then save it. 

Next type this code on your terminal
sudo apt-get clean && sudo apt-get update --fix-missing
and you won’t find apt cache limit again in the next time.

It worked for me!!! :D
What command do what and it is make my videos even worst! I try 3 times this and nothing is better !

---

### Post by cccharles1 on 2014-02-08
> **Vinnizz said:**
> So I've had the same problem as a lot of people, youtube was extremely laggy even when I played 240p videos and I tried everything, html5 youtube, flash-aid plugin for firefox and whatnot, and they didn't work for me.
 Then I enabled "Override automatic cache management" on firefox. It got a little better but still a bit laggy on fullscreen.

Then I thought I'd let Ubuntu use more cache . So if you have the same problem just try this:

 sudo gedit /etc/apt/apt.conf.d/70debconf.

Then put this code,:
 APT::Cache-Limit "100000000";
 on that file and then save it. 

Next type this code on your terminal
 sudo apt-get clean && sudo apt-get update --fix-missing
and you won’t find apt cache limit again in the next time.

It worked for me!!! :D


You, Sir, are a star!!! :KS

If I had a prize to give you, I would. But, I can only give you my thanks for enabling me to finally watch 1080p video on my machine.

Thanks again :)

---

### Post by Ivan_Ongko on 2014-02-11
Wow. it worked dude, Thanks:p!!!

---

### Post by ricardoamercado on 2014-07-15
Thanks Vinnizz! Made it a lot better!

---

### Post by pwoo on 2014-07-20
> **GRFrones said:**
> Well... it's worked for a few people, already... I didn't know computers were also susceptible to placebo. hehe

I'm also having problems with flash player in both of my ubuntu systems. They get laggy in youtube, flash games, etc.

Does anyone know of a solution unrelated to placebo? haha

Best Regards,
Gabriel.

Without really digging into the internals of apt, I wouldn't completely rule out that this is a placebo because it does improve my firefox youtube viewing as well.  Full screen was not usable at all earlier but now, while not perfect, is much better.  It could be that it has nothing related to cache, but simply, the process cleans up some dirty links left over by the flash plugin installation.

---

