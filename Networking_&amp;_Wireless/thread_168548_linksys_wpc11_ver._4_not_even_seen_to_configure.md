---
title: "linksys wpc11 ver. 4 not even seen to configure"
date: 2006-04-30
forum: Networking &amp; Wireless
---

### Post by mrgumby on 2006-04-30
I downloaded today, my other copy being 5 months old.
My Linksys wpc11 ver 4 will not even come up on the networking services screen.
I dont have an "add" button like it says in the help area.

When I look at device manager, it is there as a realtek (how it came up on the windoze machine) but I dont see it elsewhere.

Is there a reason I dont even have the add button on the network services screen?
ifconfig shows only the onboard.

Laptop is a sotec afina 820p. I could not find anything specific to that model about this either.
In other posts, I see that people are saying the driver is right in the build and works perfectly...but not for me. Any ideas folks??

Help me Obi-Wans, you all are my my only hope...

---

### Post by Titus A Duxass on 2006-05-01
This card works fine with ndiswrapper, do a search on these forums and you will find lots of information and howto advice.

---

### Post by mrgumby on 2006-05-01
I saw that, but the driver was supposed to be in the new build according to more than one poster.

I just thought I was doing something wrong.

I gues I will try the other way...I was just hoping this would load without getting into that, so I could send it elsewhere for an even less savvy user than myself.

---

### Post by monomaniacpat on 2006-05-01
I have exactly the same card and a couple of days ago I got it working using [these](http://www.cwelug.org/cgi-bin/wiki.cgi?Wpc11v4#source) instructions. Unfortunately, as you can see from my thread it no longer works, but I think this is a specific issue for me. Basically, follow those instructions up to the point where you have finished inserting the modules and a wireless card should appear in your network setting dialogue box. You may need to wlan0 scan in order to get the SSID to turn up in network settings.

Hope this helps! Any problems just PM me.

---

### Post by mrgumby on 2006-05-10
I did it and it seems to be working great!
I am nervous about updating "too" much, but we will see what happens. 
All part of learning!
Thanks for the help!

---

