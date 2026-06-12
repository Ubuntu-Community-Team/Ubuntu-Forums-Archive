---
title: "Can anyone view this webpage properly from Ubuntu?"
date: 2008-04-23
forum: Multimedia Software
---

### Post by zvbxrpl on 2008-04-23
I've just replaced Windows XP with Ubuntu on my brother's laptop.  However, he can't access the online tutorials he needs for law school.  He's given me one week to find out a way to do it, or I'll have to wipe Ubuntu and put Windows back on.  Here's an example of the tutorials:

[http://apps.lawcol.com/ITutorial/webcast/index.htm](http://apps.lawcol.com/ITutorial/webcast/index.htm)

This page only seems to work with IE and Windows.  I cannot find any way to make this page load properly in Ubuntu whatsoever: it always give the 'You require Windows Media Player..." message.   As far as I can tell, the page requires Flash and a Windows Media plugin. 

In Windows XP, If I try Firefox with Microsoft's own WMP plugin for Firefox, it doesn't work.  But if I load the IE rendering engine within Firefox by using the IETab extension for Firefox, it works fine.

In Ubuntu, I have flash (Adobe) and the mplayer plugin for Firefox installed and working just fine, but the page won't load properly.  I tried installing IEs4Linux (IE6 running under Wine) but it doesn't work.  I tried adding WMP 9 in wine, which works (fairly) well as a standalone app, but doesn't help with the page.

All I can conclude is that the page checks for BOTH IE AND Microsoft's own WMP plugin, and if it doesn't find either of them, it won't start the video stream. 

I understand one can load XP within Ubuntu using qemu (?) but I don't think his laptop will be up to that, as it's only a 700MHz box with 256Mb RAM, and a fairly small hard disk.

Any ideas?

---

### Post by rouge568 on 2008-04-23
I can see it fine, but I can't click on anything and there is a grey box that says that I need that darn Windows Media Player. It might just be that this page was designed specifically for Windows and Internet Explorer. You might want to try installing IE and WMP through wine. Using Firefox 3.

---

### Post by margni on 2008-04-23
I just watched your video on of all things Vista SP1 + Internet Explorer 7, and the Video window was cut off with say... 2/3 of it showing.  Second there was no way to expand the window, or refresh it correctly by maximizing the screen...  Maybe it's me, but ???

Sorry for tainting the forum with Vista, I just got this box and I'm waiting to 'lobotomize' vista for Hardy...

---

### Post by earthman on 2008-04-24
A shining example of a poorly coded page that is inaccessible to anyone without specific hardware/software. These developers get an F. The web should be hardware and OS independent.

---

### Post by nicedude on 2008-04-24
That's really poorly coded and showcases why Microsoft's best in only 2 things Revenue & False Ads claiming superiority. But you could use Wine like someone else said and according to that page you don't need WMP9 just WMP7 so it might run better with WMP7. But in a situation such as this I would have to probably say maybe dualboot with XP (Not Vista as its more trouble & XP can at least be made stable) & Ubuntu for you. Or a Virtual Machine install of XP would work also. Sad that a school would force you to use the illegal monopoly garbage OS just because they cant hire someone who can use flash.

---

### Post by CREEPING DEATH on 2008-04-24
I'd find out who is responsible for the page - outside of the IT department - and complain that it is not accessible and not W3C compliant.  Not W3C compliant = not web accessible = possible breach of contract of the part of the school.  They're lawyers, they'll understand.

CD

---

### Post by mk_kano on 2008-04-24
I can't figure out a way to get it up either. I really do hate websites that are prejudice against browsers / OSes. Try having firefox tell the site it is IE7 maybe? Do this by changing your user agent string:

   1. Type about:config in the Mozilla Firefox address bar and press ENTER,
       
   2. Type general.useragent.extra.firefox in the Filter bar,
       
   3. Double-click on the returned Firefox setting, where you can change or spoof a user agent string to overwrite the default “Firefox/2.0.0.4&#8243;!

"MSIE 7.0" is what you want to type to spoof IE7. 

However the WMP 7.0+ looks to be a bigger problem... CrossOver Office allows you to run the WMP plugin but looks to cost $40, so unfortunately I wont be able to test that out for you :P

---

### Post by zvbxrpl on 2008-04-24
Many thanks for all your messages, everyone - I wasn't expecting such a good response!

@rouge568

> I can see it fine, but I can't click on anything and there is a
> grey box that says that I need that darn Windows Media Player.

Apologies, that's what I meant.  I can see the Flash content on the page but can't get rid of the grey box.

> You might want to try installing IE and WMP through wine.

I did try this (IEs4linux) but had the same problem.  According to the IEs4Linux developers, the WMP plugin isn't supported yet.  I thought I'd try my luck by installing WMP9 in wine anyway, and although I can invoke WMP by clicking a .wmv link in IE6, embedded video doesn't play.

@nicedude

> But you could use Wine like someone else said and according to 
> that page you don't need WMP9 just WMP7 so it might run better with WMP7.

The instructions I found only covered WMP9 and 10:

[http://wine-review.blogspot.com/2007/09/windows-media-player-9-10-on-linux-with.html](http://wine-review.blogspot.com/2007/09/windows-media-player-9-10-on-linux-with.html)

If anyone knows a similar guide for WMP7 I'd be interested to hear from you, but I'm not sure it will solve my problem as I think the issue is that WMP plugins aren't supported in IEs4Linux yet.

@mk_kano:

> Try having firefox tell the site it is IE7 maybe?

I tried doing this (there's even a FF plugin for this now) but it didn't make any difference.  I think the page is trying to detect the WMP plugin and failing.

Thanks again for all your help - I'd be grateful for any further ideas...

---

### Post by moonpup on 2008-04-24
Speaking of poor webpages... is it me or is the flash on [http://www.toyota.com](http://www.toyota.com) poorly coded as well. The initial screen comes up okay, but anything after that is just plain broken when you click on it.

Can anyone confirm it's just not me and is there a fix :)

---

### Post by mk_kano on 2008-04-24
> **moonpup said:**
> Speaking of poor webpages... is it me or is the flash on [http://www.toyota.com](http://www.toyota.com) poorly coded as well. The initial screen comes up okay, but anything after that is just plain broken when you click on it.

Can anyone confirm it's just not me and is there a fix :)

The toyota page works fine for me, all the links work. The dell customize page screws up on me though and I have to go to list view :( I was looking at getting an Ubuntu laptop from them, with their 25% coupon it's the best deal in town I can find on open source laptops.

---

