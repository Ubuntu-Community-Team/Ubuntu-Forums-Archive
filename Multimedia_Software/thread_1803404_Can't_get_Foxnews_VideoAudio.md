---
title: "Can't get Foxnews Video/Audio"
date: 2011-07-13
forum: Multimedia Software
---

### Post by loybanks on 2011-07-13
I'm able to get YouTube without any issues. But I'm not able to receive Video/Audio from FoxNews and other Video Sources. The on screen gizmo just keeps spinning without downloading any video or audio. Any ideas? Thanks.

I use Ubuntu 11.4 on Toshiba Notebook NB505

---

### Post by Maxthrust on 2011-07-13
I'm having a similar issue.  I have Ubuntu 11.04 (64-bit) and can't get Foxnews videos to play.  In fact, I don't even get the spinning load icon, nothing, just blank.   I don't seem to be having issues on any other video sites like Youtube and the like.  I can't play Foxnews videos in Firefox, Chrome, or Epiphany.  I'm using Grease Monkey and Flash-aid.  I had ad-block plus, but disabled it.  I was able to get a Foxnews video to play one time, but I have no clue how I did it.

---

### Post by jerrrys on 2011-07-13
try this:

open up a new user account and try foxnews.  OR navigate to /home>.mozilla amd rename it.  example: rename it ".mozilla original". this will force FF to a fresh/vanilla state and all your custom settings  can be restored by replacing the original folder.

---

### Post by Maxthrust on 2011-07-13
> **jerrrys said:**
> try this:

open up a new user account and try foxnews.  OR navigate to /home>.mozilla amd rename it.  example: rename it ".mozilla original". this will force FF to a fresh/vanilla state and all your custom settings  can be restored by replacing the original folder.


I tried this (and liked the simplicity) however, it didn't work.  Same issue.  I can basically watch any video on any website except Foxnews.  I can even watch videos on clarkhoward.com, but no Foxnews.

I'll have to hold my nose and try cnn.com.....ack, it works fine also.

---

### Post by oldos2er on 2011-07-13
Works fine for me in Chrome. Are you using Firefox?

---

### Post by John-B on 2011-07-13
I just tried foxnews and with Ubuntu 11.04 - Firefox 5 with Shockwave flash 10.3 and the videos run fine.  Are you using the these or newer?

---

### Post by loybanks on 2011-07-14
> **loybanks said:**
> I'm able to get YouTube without any issues. But I'm not able to receive Video/Audio from FoxNews and other Video Sources. The on screen gizmo just keeps spinning without downloading any video or audio. Any ideas? Thanks.

I use Ubuntu 11.4 on Toshiba Notebook NB505


I did solve the problem by going into Firefox Add-Ons/Plug In, installing Shockwave Flash or maybe it's already installed. Then when I go to Foxnews/Videos I have no problem watching them.

Hope this helps.

---

### Post by Maxthrust on 2011-07-18
> **John-B said:**
> I just tried foxnews and with Ubuntu 11.04 - Firefox 5 with Shockwave flash 10.3 and the videos run fine.  Are you using the these or newer?


I'm running Shockwave Flash 10.3 d162 with Firefox 5.0 on Ubuntu 11.04(64).  I have tried the latest version of Chrome and Epiphany just for fun, no joy on any of them.  I can watch every other video from any news or video site on the web, just not Foxnews.  I have a Windows computer next to me that I can watch Foxnews videos without problem.  It's even a semi-restricted system on XP with IE7...works fine.

I did get Foxnews videos to play once...I watched one video and then it reverted again.  Grrrrr.

---

### Post by Maxthrust on 2011-07-18
I've completely uninstalled, then reinstalled Shockwave Flash.  I now have Shockwave Flash 11.0 d1 and still the same issue.  I can view videos on any website except Foxnews.  I also have now removed Grease Monkey, Flash-Aid, and Ad-Block.  Nothing has helped.  This is something that can really ruin an experience.  I can play Foxnews videos on everything I own, even my ancient cell phone, but not on my brand-spanky-new copy of Ubuntu.  GRRRR!!!

---

### Post by Maxthrust on 2011-07-18
I get it...it's a conspiracy.  It's far too conservative for the Ubuntu crowd....lol.

---

### Post by Maxthrust on 2011-07-19
I've now tried User Agent Switcher and IE Tab+, both with no joy either.

Someone must know how to resolve this issue.  It's very odd that Foxnews are the only videos I can't play...and only on my Ubuntu system.  All other systems on this network display Foxnews videos without issue.

---

### Post by jerenept on 2011-07-19
> **Maxthrust said:**
> I've now tried User Agent Switcher and IE Tab+, both with no joy either.

Someone must know how to resolve this issue.  It's very odd that Foxnews are the only videos I can't play...and only on my Ubuntu system.  All other systems on this network display Foxnews videos without issue.

IE Tab does not work on any system that does not have Internet Explorer installed. addons.mozilla.org should have said "Not Available for Your Platform". Report it as a bug please.

---

### Post by jerrrys on 2011-07-19
ok maxthrust, i just finished a fresh build of 11o4.  at the moment its  just gnome-core and ubuntu restricted extras.  and NO foxnews...

i will be working on this today, i hope.  wife has just handed me my  todo list, so im heading out the door and hope to get back on this  project this afternoon.  will post back, hopefully with an answer...

---

### Post by varx on 2011-07-19
Consider yourself blessed. :P

---

### Post by Maxthrust on 2011-07-19
> **varx said:**
> Consider yourself blessed. :P

That's not really helpful.  I can't stand CNN, however, I won't bash anyone that wants to watch that tripe and I will defend your right to view any news you would like.  I see a lot of Fox News bashing on this site...and find it less than helpful.  Issues like this can really queer a person from using a particular OS.

Now, the post above yours at least offers some hope.  And thanks for mentioning a brand-spanky-new install of 11.04.  I was seriously considering starting over, but will refrain for now.

BTW, I've updated to Adobe Flash version LNX 11,0,1,60 (64) and still no joy.  I also rebooted and kept all other programs off (Evolution, etc) and only opened one tab.  I simply get a black rectangle where the video should be located.  No controls, no spinning icon, nothing.  I also can't find any error messages.  With the communities attitude towards Fox News I'm starting to think it might be deeper than our little attempts at resolving the issue.

I really love Ubuntu, but I can't play my favorite online game with it and although I could jump through hoops and make it happen I don't feel like it so I keep a few Windows systems around for just that.  I also have issues with my Hauppauge DVR (Windows Media in WIN7 rocks for this) and I can't view Fox News videos.  The Linux community really needs to address some of these issues if they want to get more users on board.  Also, if my mom can't watch what she wants you'll never convince her to change, ever.  I think that's true with many people, issues like this are annoying to them and the simple solution is to use an OS that does work for them, even if it has other issues.

---

### Post by varx on 2011-07-19
> **Maxthrust said:**
> That's not really helpful.  I can't stand CNN, however, I won't bash anyone that wants to watch that tripe and I will defend your right to view any news you would like.  I see a lot of Fox News bashing on this site...and find it less than helpful.  Issues like this can really queer a person from using a particular OS.

Sorry for the offense. You're right.

---

### Post by Maxthrust on 2011-07-19
> **varx said:**
> Sorry for the offense. You're right.


Wow!  Accepted...

---

### Post by jerrrys on 2011-07-19
well, here's the news:

in my haste to get out of here, i forgot one thing.  a restart.  im afraid thats all it took for me.

foxnews has two links.  one for video and one for streaming.  both work for me.  the pic below is all the plugins im running.

i notice that you said that your on a network.  could you have a firewall messing with you?

[ATTACH]197825[/ATTACH]

and preferences

[ATTACH]197826[/ATTACH]
[ATTACH]197827[/ATTACH]

---

### Post by Maxthrust on 2011-07-19
> **jerrrys said:**
> well, here's the news:

in my haste to get out of here, i forgot one thing.  a restart.  im afraid thats all it took for me.

foxnews has two links.  one for video and one for streaming.  both work for me.  the pic below is all the plugins im running.

i notice that you said that your on a network.  could you have a firewall messing with you?

[ATTACH]197825[/ATTACH]

and preferences

[ATTACH]197826[/ATTACH]
[ATTACH]197827[/ATTACH]


I thought of the firewall issue long ago and hence why I was careful to mention that the Windows systems on this exact network (VLAN really) have no problems getting Foxnews videos to play.  I can play any video from any site, except for Foxnews.

I will study your plug-ins and see if they match up with mine.

Thank you for the response.

---

### Post by Maxthrust on 2011-07-19
> **jerrrys said:**
> well, here's the news:

in my haste to get out of here, i forgot one thing.  a restart.  im afraid thats all it took for me.

foxnews has two links.  one for video and one for streaming.  both work for me.  the pic below is all the plugins im running.

i notice that you said that your on a network.  could you have a firewall messing with you?

[ATTACH]197825[/ATTACH]

and preferences

[ATTACH]197826[/ATTACH]
[ATTACH]197827[/ATTACH]

OK...because you mentioned it and curiosity was killing me, I changed to one of the other networks in my office.  (I'm the admin and have three of them.)  I switched to a subnet under my primary VLAN and instantly Foxnews Videos loaded and played.  How very odd.

I've also maintained that the Windows systems on this network could display the videos without issue.  Here's the rub, I've been working this issue so hard, so long, that I went on old information.  I just checked 4 different Windows systems on the same network....they cannot display Foxnews videos any longer.  One lady knew it was an issue, the rest were shocked, with the exception of one who said, "it's as it should be."  It appears as if it's being blocked by The-Powers-That-Be.  HMPF!

So, it appears that if I want to view Foxnews videos from this location I have to use a system on my VLAN.  Go figure.

Thanks to all who replied with positive information and help.

I also apologize for being so stuck on this issue that I didn't go back and re-visit information that I had already checked.

---

### Post by jerrrys on 2011-07-19
EDIT didn't see that last post.  your making headway, good luck
[]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by Maxthrust on 2011-07-19
OK, further testing.  There is an ad that loads on the right side of the page, however, many ad sites are blocked on this network.  When I switched to the other network the ad loaded and subsequently the videos.  I then switched cables again and left that page alone.  I can now load any Foxnews video I want, they are still playing as I type this.  That's very interesting and maybe a clue for someone working on this problem.  I have seen many others with this issue.  It's firewall related, but not directly.  From my observation it's that ad not loading that keeps it from displaying.  I wonder what happens if that page now attempts to refresh that ad?

---

### Post by Maxthrust on 2011-07-20
> **Maxthrust said:**
> OK, further testing.  There is an ad that loads on the right side of the page, however, many ad sites are blocked on this network.  When I switched to the other network the ad loaded and subsequently the videos.  I then switched cables again and left that page alone.  I can now load any Foxnews video I want, they are still playing as I type this.  That's very interesting and maybe a clue for someone working on this problem.  I have seen many others with this issue.  It's firewall related, but not directly.  From my observation it's that ad not loading that keeps it from displaying.  I wonder what happens if that page now attempts to refresh that ad?


I was correct, refreshing the page killed my ability to play videos.  How very interesting.

For me, the issue is solved.

Now if I could just get my favorite Windows games to work correctly...lol.

---

