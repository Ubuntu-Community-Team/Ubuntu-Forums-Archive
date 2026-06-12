---
title: "[SOLVED] Problems with Flash Videos"
date: 2008-07-09
forum: Multimedia Software
---

### Post by Kaneda on 2008-07-09
Well, I'm having problems with flash videos, but only certain flash videos.  I can watch YouTube just fine, but the flash videos that I want to watch are on [http://www.fnn-news.com/]("http://www.fnn-news.com/").  It is a Japanese news website.  The video player comes up just fine, but when I push the play button, nothing happens.

Here is what I have tried so far:
I downloaded nspluginwrapper from [here]("http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb").
I installed libflashsupport using "sudo apt-get install libflashsupport"
I removed flash using "sudo apt-get remove --purge flashplugin-nonfree"
and then reinstalled using "sudo apt-get install flashplugin-nonfree"

That didn't work, so I also tried removing adobe flash and installing swfdec instead.

When I used swfdec and went back to [the site]("http://www.fnn-news.com/") again, the video player didn't come up at all, but a little blue screen came up where the video player normally is and gave me an error in Japanese saying that they only provide windows media format videos.

(I can play all the videos on the site if I download them separately and play them in mplayer, but I'd like to play them through the flash player because it's more convenient and also has a "play all" button so I can go through them all without having to download them one by one.)

So, if anyone has any help or suggestions, I'd appreciate it!  Sorry my example site is in Japanese, I hope that doesn't complicate things.  Thanks!

---

### Post by stats on 2008-07-09
if youtube works its most likely not a flash problem.
Maybe the news site is not even flash video. it could be some other type of streaming video
"error in Japanese saying that they only provide windows media format videos."
seems like you might need to get a browser plugin like totem firefox plugin or mozilla mplayer plugin to play this

---

### Post by CameO73 on 2008-07-09
I'm using Flash 10 (beta) ... for me the videos play OK. Follow the instructions [in this post](http://ubuntuforums.org/showthread.php?p=4928900) and you should be OK.

---

### Post by gandaran on 2008-07-09
> **CameO73 said:**
> I'm using Flash 10 (beta) ... for me the videos play OK. Follow the instructions [in this post](http://ubuntuforums.org/showthread.php?p=4928900) and you should be OK.

did you try the link in Kaneda post? I don't think so! neither flash 9 or flash 10 work!

---

### Post by psyke83 on 2008-07-09
> **gandaran said:**
> did you try the link in Kaneda post? I don't think so! neither flash 9 or flash 10 work!

The videos play fine for me, using beta 2 of Flash v10. Maybe it's a network issue?

---

### Post by Kaneda on 2008-07-10
> **CameO73 said:**
> I'm using Flash 10 (beta) ... for me the videos play OK. Follow the instructions [in this post](http://ubuntuforums.org/showthread.php?p=4928900) and you should be OK.

Hmm... I tried both Flash 10 beta 1 and 2, and neither of them seem to work for me.  But they obviously work for other people...

The video player loads and shows a static picture of the video, but if I actually push the play button, nothing happens (and sometimes firefox crashes).

Any ideas on what else might be the problem?

---

### Post by oneporter on 2008-07-10
I'm using flash v10 b2, and the news link worked fine for me.. It took a good second or two before the video started after I pressed the play button.  Are you just being impatient?  I know I've spent a lot of time scratching my head before when all I needed to do was restart or give the thing long enough to load.

---

### Post by Kaneda on 2008-07-10
> **oneporter said:**
> I'm using flash v10 b2, and the news link worked fine for me.. It took a good second or two before the video started after I pressed the play button.  Are you just being impatient?  I know I've spent a lot of time scratching my head before when all I needed to do was restart or give the thing long enough to load.

Hmm... I wish that was it.  I just tried again and waited for about 30 seconds.  Then firefox crashed.  :(

---

### Post by markbuntu on 2008-07-10
It just crashed firefox3.0 and flash10b for me on amd64.

---

### Post by Kaneda on 2008-07-11
> **markbuntu said:**
> It just crashed firefox3.0 and flash10b for me on amd64.

Could it be a problem with Firefox 3.0?  Maybe I should go back to 2.0?  Are any of the people that can play the videos using FF3?

---

### Post by Kaneda on 2008-07-11
Hmm... I just went and manually deleted libflashplayer.so out of the .mozilla/plugins folder.  Normally that should disable flash, right?  Well, even then YouTube, flash games, etc. still work fine (the [FNN site]("http://www.fnn-news.com/") doesn't though).  Then, when I type about:plugins in the Firefox address bar, it says I'm using Shockwave flash using libflashplayer.so.  How is that possible?

---

### Post by NilsE on 2008-07-11
Look in /usr/lib/flashplugin-nonfree since it is probably there if you installed it as flashplugin-nonfree. 

There is also a link to it in /etc/alternatives

You may want to try 10 B1 or go back to 9 since there are a few sites that 10 B2 has problems with that 10 B1 and 9 do not.

UPDATE: I just tried B2 and it failed. Tried 9 and B1 and it worked fine on the site you linked.

---

### Post by Kaneda on 2008-07-12
Hmm... I tried going back and switching over to Flash 10 beta 1.  I was doing things according to [this guide]("http://ubuntuforums.org/showthread.php?p=4928900"), and when I got to the second line of code on Part B #2a, 

```
sudo dpkg -i flashplugin-nonfree_10.0.1.218ubuntu1_i386.deb libasound2_1.0.16-2ubuntu1_i386.deb libasound2-dev_1.0.16-2ubuntu1_i386.deb libasound2-plugins_1.0.16-1ubuntu1_i386.deb
```

Everything goes fine for all the libasound things, but when it gets to Flash, I get a 404 Not Found Error when it tries to download:

```
flashplugin-nonfree (10.0.1.218ubuntu1) &#12434;&#35373;&#23450;&#12375;&#12390;&#12356;&#12414;&#12377; ...
Downloading...
--21:44:57--  http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz
           => `./flashplayer10_install_linux_051508.tar.gz'
download.macromedia.com &#12434;DNS&#12395;&#21839;&#12356;&#12354;&#12431;&#12379;&#12390;&#12356;&#12414;&#12377;... 72.246.47.191
download.macromedia.com|72.246.47.191|:80 &#12395;&#25509;&#32154;&#12375;&#12390;&#12356;&#12414;&#12377;... &#25509;&#32154;&#12375;&#12414;&#12375;&#12383;&#12290;
HTTP &#12395;&#12424;&#12427;&#25509;&#32154;&#35201;&#27714;&#12434;&#36865;&#20449;&#12375;&#12414;&#12375;&#12383;&#12289;&#24540;&#31572;&#12434;&#24453;&#12387;&#12390;&#12356;&#12414;&#12377;... 404 Not Found
21:44:57 &#12456;&#12521;&#12540; 404: Not Found&#12290;

download failed
The Flash plugin is NOT installed.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```
(Sorry about the Japanese)

Anyway, this is probably a pretty simple fix.  Can anyone help me out?  Thanks!

Edit*:
Okay, I found the solution to this problem when I looked through the posts on that guide and found other people who had the same problem.

So, I got Flash 10 beta 1 all installed and up and running, AND!

...it still doesn't work. :(

Any other ideas?

---

### Post by NilsE on 2008-07-12
When you look at the Add-ons what version is it saying is installed?

You may want to do a search for copies of libflashplayer.so and delete therm all then reinstall from Synaptic the flashplugin-nonfree version

---

### Post by Kaneda on 2008-07-13
Hmm... I went in as root, found all the instances of libflashplayer.so and deleted them, and then I reinstalled flashplugin-nonfree from Synaptic.  I still can't see the [FNN videos]("http://www.fnn-news.com/"), and now YouTube videos have no sound.  :(

---

### Post by NilsE on 2008-07-13
> **Kaneda said:**
> Hmm... I went in as root, found all the instances of libflashplayer.so and deleted them, and then I reinstalled flashplugin-nonfree from Synaptic.  I still can't see the [FNN videos]("http://www.fnn-news.com/"), and now YouTube videos have no sound.  :(
Go into Synaptic and completely remove flashplugin-nonfree then reinstall it.  Also make sure libflashsupport is uninstalled.

You should end up with version 9 of flash so look in Tools > add-ons and tell me what it says for Shockwave flash.

If fnn.com does not work with version 9 you want to install version 10 beta 1 (not 2 since it has problems). Beta 1 is the following package which you will have to search for.

flashplayer10_install_linux_051508.tar.gz

Extract the libflashplayer.so to the /usr/lib/flashplugin-nonfree folder.

You will then need to make a link to it in /etc/alternatives called

firefox-flashplugin (replace or rename the one that is there).

---

### Post by Kaneda on 2008-07-14
Wow!  I finally got it working.  It looks like Flash 10 beta 1 is the key.  Although I also got frustrated and did a clean install of ubuntu while I was at it... :oops:

---

### Post by NilsE on 2008-07-14
> **Kaneda said:**
> Wow!  I finally got it working.  It looks like Flash 10 beta 1 is the key.  Although I also got frustrated and did a clean install of ubuntu while I was at it... :oops:Glad you got it working.  Yup, version 10 beta 1 seems to solve a lot of problems.

A fresh install helps with a lot of problems but not this one since it brings version 9 back in.  Tried it myself since I wanted to clean up all the stuff that was in there from beta testing anyway.

---

