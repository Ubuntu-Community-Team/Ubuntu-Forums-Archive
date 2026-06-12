---
title: "Miro crashing often &amp; high CPU load without activities ?"
date: 2012-01-09
forum: Multimedia Software
---

### Post by HolgerB on 2012-01-09
Hi there,

I am currently experimenting a bit with Miro (the link and media aggregator). I use the version from the official Ubuntu 11.10 repos. I guess it is 3.5x. On my AMD E-350 dualcore (2x1.6 GHz) Miro has the tendency to behave really sluggish at start. I can even see up to 100% CPU-load in top. After a while (if the UI has been rendered) the CPU load drops a bit. Nevertheless I often see 40% load for the Miro main-process and another 30-35% for a python sub-process. And all this without even doing anything inside Miro. Simply browsing the webpages inside Miro or starting multiple torrent downloads result first in a non-responding program and often enough I see the Miro process vanish in the second place.

I really like the idea of Miro having all my media in one place and would really like to install it to my media PC which is connected to our 32" flatbed TV but not in the current state of the program.

Has anyone of you had similar issues with Miro ?

TIA,
Holger

---

### Post by jerrrys on 2012-01-11
I have Miro installed in 10o4 and yes, it uses a lot of resources and videos will not always download.  But I still like it.

Wont be long before a new media player is out that may replace Miro in my box.

[http://www.ubuntu.com/tv](http://www.ubuntu.com/tv)

---

### Post by bluexrider on 2012-01-11
I used Miro for a short time and found it to be resource-hungry-memory-hog. Although it has nice features I elected to find other alternatives for my needs. I currently use Pithos for Internet radio and VLC for video. Works for me.

---

### Post by HolgerB on 2012-01-11
I think to some aspect the sluggish behaviour comes from the miro website which is loaded. Even from my fast www connection at home (16 MBit) the page is horrible slow.

On the other hand Miro itself is either written incredible bad or uses badly optimized libraries / components. Nothing should ever slow down a system like my dualcore (2x1.6GHz) as this thing. 

The sad thing for me is that Miro really nicely integrates a lot of websites into one GUI. Some features such as Youtube integration are not that great but there is always room for improvement in every application.  I am somewhat unshure on what to use as replacement for Miro. May be flexget plus the rss feeds of all the website linked in Miro ? There is an incredible amount of free content in the www but I find the mayor competition is that someone prefilters all this stuff :)

The other competition is to provde easy access to content at low cost for the provider: Libre Vox for example has an incredible rich library of free audiobooks but access to the books is quite complicate. At least if you (like I did) want to grab all Horror / Ghost stories available or may be all audio books from Arthur Conan Doyle. I spent some hours tinkering with bash scripts (namely with sed, grep and awk) to download the stuff I wanted. Here it would be nicer if the search engine of their webpage provided an option to generate a rss feed for my search results which lets me get all media files via torrent automagically.

OK, enough rant....

---

### Post by jerrrys on 2012-01-11
"Miro really nicely integrates a lot of websites into one GUI."

very true.  and miro search engine does a great job

---

### Post by bluexrider on 2012-01-11
> **HolgerB said:**
> I think to some aspect the sluggish behaviour comes from the miro website which is loaded. Even from my fast www connection at home (16 MBit) the page is horrible slow.

On the other hand Miro itself is either written incredible bad or uses badly optimized libraries / components. Nothing should ever slow down a system like my dualcore (2x1.6GHz) as this thing. 

The sad thing for me is that Miro really nicely integrates a lot of websites into one GUI. Some features such as Youtube integration are not that great but there is always room for improvement in every application.  I am somewhat unshure on what to use as replacement for Miro. May be flexget plus the rss feeds of all the website linked in Miro ? There is an incredible amount of free content in the www but I find the mayor competition is that someone prefilters all this stuff :)

The other competition is to provde easy access to content at low cost for the provider: Libre Vox for example has an incredible rich library of free audiobooks but access to the books is quite complicate. At least if you (like I did) want to grab all Horror / Ghost stories available or may be all audio books from Arthur Conan Doyle. I spent some hours tinkering with bash scripts (namely with sed, grep and awk) to download the stuff I wanted. Here it would be nicer if the search engine of their webpage provided an option to generate a rss feed for my search results which lets me get all media files via torrent automagically.

OK, enough rant....

So, I read this about three times and decided that your issues contend to be that you want everything to work without having to work for everything. 

Your DualCore is not impervious to imperfection and neither is my QuadCore. I would like to think so but I would be seriously wrong. 

So, this leaves me to suspect that you might be expecting more than what Miro can can actually deliver.

You never did state how many threads you were trying to pull at the same time 

> starting multiple torrent downloads result first in a non-responding  program and often enough I see the Miro process vanish in the second  place.


I cannot say for sure what your expectations are but this Miro app doesn't work for you. 

I would suppose you should find what works for you.

Good Luck

---

### Post by HolgerB on 2012-01-12
@other: Excuse my OT reply but I want to elaborate things before I mark my thread as solved.

@bluexrider:
> 
So, I read this about three times and decided that your issues contend to be that you want everything to work without having to work for everything.
Well, I read your reply I guess more like 10 times and do not get your point. No, I do not want everything without havething to do anything. It's not like I am awaiting my bank account to fill up with 1000&#8364; each day without leaving the house to go working. If you refer to my last example about easier media access to something like librevox: I just mentioned this as example that one can not easily replace Miro with other apps. I am well able and willing as well to get the stuff I need to get when required. Miro would simply be a tool which makes things easier (similar to flexget).

> 
Your DualCore is not impervious to imperfection and neither is my QuadCore. I would like to think so but I would be seriously wrong.
My dual core (2x1.6GHz) isn't a true powerhorse and with upcoming 10 to 12 core CPUs it will be an IT relic within the next two years but this is not the point (see below).

> 
So, this leaves me to suspect that you might be expecting more than what Miro can can actually deliver.
Miro combines a webbrowser, a podcast client and a torrent client. My system (and I guess pretty much any box out there with at least 1 GHz) can perfectly run Firefox (browser), Transmission (torrent) with tons of concurrent downloads and GPodder (podcast client) with running downloads without any hickup. Usually I even record DVB streams in the background and watch a video clip in parallel without experiencing slow-downs. So, when I start Miro, launch for example three torrent downloads and the window becomes unresponsive / does not refresh, then am I expecting too much from this app ?

> 
You never did state how many threads you were trying to pull at the same time
What do you mean by how many thread I was trying to pull ? Concurrent torrent downloads ? Something like 2-3.

> 
I cannot say for sure what your expectations are but this Miro app doesn't work for you.
Well, my expectations were simply like that: I can start Miro, select a few downloads, minimize it and come back after a while to watch my HD stuff. Seems (as writen above) I was expecting too much.

Edit: Just an example of what I was talking about: Opened up miro, no download running, nothing clicked and here is the output of top:
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
23433 hb        20   0 1948m 138m  36m R  100  1.8   4:18.07 miro.real  

Yeah, nice 100% CPU time for being "idle"....

---

### Post by jerrrys on 2012-01-12
Just downloaded miro in 11.10.  Got five videos downloading, about 3gig worth, going to take 1 hour. No lag being detected and not loading down my processor.  Miro at Idle; cpu's (2) setting at idle.

Will flexget do this better?

---

### Post by HolgerB on 2012-01-12
> **jerrrys said:**
> Just downloaded miro in 11.10.  Got five videos downloading, about 3gig worth, going to take 1 hour. No lag being detected and not loading down my processor.  Miro at Idle; cpu's (2) setting at idle.

Will flexget do this better?
Hm, interesting...I am on Ubuntu 11.10 myself (machine configuration see my footer). Strange. My experience is completely different. May be I should try the deb version from their homepage ?

Not shure how to compare flexget to Miro. Flexget is more the "backend" of miro, e.g. grabbing downloads from webpages, RSS feeds and so on. 

May I ask which hardware you have ?

Edit: OK, just to compare:
Gpodder downloading Hak5 HD stuff via RSS feed with 4 concurrent downloads produces a mere 7-8% CPU load. That is what I would hope to get from Miro as well.

---

### Post by jerrrys on 2012-01-12
I loaded from the repositories.  As for hardware, its all oldware.  IBM running dual Xeon processors @ 3GHz and three gig of ram.

Edit:  32 bit

Edit#2 (got sidetrack):  [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=miro+64+bit&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=miro+64+bit&sa=Search&cof=FORID:9)

---

