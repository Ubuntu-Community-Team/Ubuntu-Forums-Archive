---
title: "Firefox crashing playing BBC videos"
date: 2008-07-25
forum: Multimedia Software
---

### Post by rossmoore on 2008-07-25
Hi,

I'm not sure if I'm alone with this problem or if it is a recognised bug:

Often when I point Firefox (version 3 - I'm on Hardy) at a video on the BBC news website, I get the circling dots indicating that buffering is going on, and then FF crashes. I start FF again, and click "Continue previous session". I get the circling dots again, and then the video plays.

It's not a huge problem - in the end I get the result I want (a smoothly playing video from the BBC) - but it is a bit annoying.

Any ideas on what the bug might be - Pulse? FF? The embedded video player (is it Flash based?)?

All thoughts and pointers much appreciated.

---

### Post by rolnics on 2008-07-25
I get the dots with the bbc's iplayer, I usually get annoyed and leave it! I thought it was probably my connection, but if you are having the same problem then it probably isn't. I don't think that the iplayer is fully compatible with Linux anyway.

As for a fix, I don't have one.

---

### Post by rossmoore on 2008-07-25
I've had the dots, but then it does play successfully. iPlayer isn't fully compatible, in that you can't download the files (you can only watch a stream). But the video streams should (and do) play. My problem is that more often than not, on the first attempt to play them FF crashes. On the second attempt eveything is fine.

Weird, huh?

---

### Post by crane on 2008-08-02
I'm having the same problem. It seems to be something with flash but no matter what I try it crashes. I am averaging probably about 30 crashes a day. Very Annoying.

---

### Post by tseligkas on 2008-09-09
Hello everyone! (Sorry for reviving the topic but I still haven't found a solution)

I don't get it. It is just a flash player, isn't it. I can play all flash videos from popular sites around (youtube, metacafe, dailymotion etc.) but BBC still... I would guess it's a programming error with the player, but I cannot understand its platform preference orientation...

And personally restarting the browser does not solve the problem. I always get the loading circles revolving when I hit the play button.

Using: Hardy, Firefox & Shockwave Flash 9.0 r124 (according to the about:plugins page)

Any ideas?

---

### Post by Casper Hansen on 2008-09-09
Try to install libflashsupport:

```
sudo apt-get install libflashsupport
```

---

### Post by tseligkas on 2008-09-09
> **Casper Hansen said:**
> Try to install libflashsupport:

```
sudo apt-get install libflashsupport
```

Thanks, but I have already installed it as a means of supporting audio playback for flash videos.

---

### Post by rossmoore on 2008-09-09
I still get this problem. I think I have libflashsupport. I can always get a video to play, but they do sometimes make FF crash - in particular BBC ones, but I get this with other video sites too.

tseligkas - are you completely unable to play BBC videos at all, or are you just finding it crashes sometimes like it does with me?

---

### Post by tseligkas on 2008-09-09
> **rossmoore said:**
> I still get this problem. I think I have libflashsupport. I can always get a video to play, but they do sometimes make FF crash - in particular BBC ones, but I get this with other video sites too.

tseligkas - are you completely unable to play BBC videos at all, or are you just finding it crashes sometimes like it does with me?

No crashes with BBC or any other sites, though I see some slow downs when more than 3 tabs with videos are opened. The browser seems to crash (window becomes grey with compiz) but comes back again.

It is the BBC site only that has its videos not playing. Any video clicked to play seems to load eternally. I discovered this when I tried to access [this]("http://news.bbc.co.uk/2/hi/technology/7598527.stm") page.

---

### Post by tseligkas on 2008-09-09
Update: I installed and tested the same site with the Opera browser. After a while I get a message from the video player saying: "This doesn't seem to be working. Try again later."

It could be BBC's streaming site problem then...

---

### Post by tseligkas on 2008-09-09
rossmore, the flash plugin for linux is poorly coded (example: go to adobe.com and try to look at the top menus - they pop below the main animation). We hope version 10 which is about to come will solve most linux issues. Also Firefox seems to not take heavy browser usage very well in linux, especially when loaded with extensions.

For your case, however, I'd suggest removing the flashplugin-nonfree from synaptics and try to install it again. I must warn you however that reinstallation a.t.m. cannot be done from synaptics because the program points to the old macromedia.com site. You should get the plugin from [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BUIGP") as tar.gz file, extract its contents and put the .so file inside /usr/lib/firefox/ . And make sure you have libflashsupport installed.

If the above fails, I'd say it's a moderately old machine you have. You could try Swiftfox (optimized Firefox) or Opera browser (no extensions).

---

### Post by rossmoore on 2008-09-09
tseligkas - thanks. My machine is pretty new and fairly powerful for a laptop (2.6Ghz Intel Duo, Nvidia 8600 video), so I don't think that's the problem.

I'll have a look at reinstalling the plugin, but as you say it might be that I need to wait for version 10. If reinstalling works, I'll be sure to post back and mark this thread as solved.

---

### Post by moss901 on 2009-04-01
I can't get videos on iPlayer or BBC News to work at all!

It begins to load for a while (5 seconds) then freezes up.  I have tried disabling all plugins except adobeflash but this doesn't help.  Have even tried re-installing the plugin.

Has anyone found a solution yet?

---

### Post by rossmoore on 2009-05-07
I don't have any problems any more - I should have set this to fixed. I followed the multimedia howto sticky in the multimedia section of this forum to get flash working. Have you tried that?

---

