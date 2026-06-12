---
title: "Pandora Troubles with Flash 9 Beta"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by jlh on 2006-10-26
I'm running Dapper on a Thinkpad T30. I installed Flash 9 beta yesterday.  My experience is that it Flash 9 does not play nicely with Pandora.  I have almost constant Pandora freezes, and that is so whether I use launch Pandora in Firefox or Flock.  Pandora launches fine, and begins to play.  However, within short order, if I navigate to a website, Pandora freezes.  

Sometimes, I can reload Pandora, and get it to launch correctly again.  However, more likely, I have to quit Firefox or Flock, re-launch the browser, and re-launch Pandora.  That's pretty useless, however, because Pandora will freeze again before long.

I'm pretty sure it's a Flash 9 issue because I encounter no such trouble when I remove the Flash 9 plugin and re-install Flash 7.

Anyone else having this difficulty?  Or, any idea how to fix it?

Thanks.

---

### Post by magicfab on 2006-10-26
What is Pandora ? I am guessing Pandora.com... if so, i would ask them:
[http://www.pandora.com/customer_service/](http://www.pandora.com/customer_service/)

They suggest using Flash 7 or 8 in their FAQ.

---

### Post by d3v1ant_0n3 on 2006-10-26
I just loaded Pandora up, started a playlist, opened some tabs and browsed around while it was playing. Couldn't replicate your problem.

*edit* Pandora just described Tool as having 'extensive vamping'. Gotta love their descriptions.

---

### Post by dakini on 2006-10-27
I've had the same problem with pandora and youtube.  It's a bit difficult to confirm because it's random behavior.  I also went back to flash 7, and the problem went away.

---

### Post by jlh on 2006-10-27
I agree there is a random quality to the problem.  

I ran Pandora for maybe 15 minutes last night in Firefox before opening my file browser caused it to freeze - that is, stop playing.  Re-loading the Pandora page did not help.  I closed Firefox, and after it launched, tried to re-launch Pandora.  The website then would not load, however.  Occasionally that has happened, or it takes an excessive amount of time for Pandora to load.

I gave up on loading.  I launched Flock, however, where I've replaced the Flash 9 plugin with Flash 7.  Pandora then worked fine.  I surfed in Firefox - which still has the Flash 9 plugin - while simultaneously running Pandora using Flock.  It's a lousy work-around.

---

### Post by slugkilla on 2006-10-27
I have the same issue. Any thing flash related stops when I pull something up in a new tab or move to a differnt program. I'm going back to flash 7 untill they work this out.

---

### Post by Greg T. on 2006-11-05
I'm in the same boat. Unfortunately, downgrading to Flash 7 hasn't helped me. I've also tried running Flash 9 for Windows (using Wine) and overclocking, to no avail. 

It's beta quality software, so there are going to be problems, and you've touched on one. I very much recommend that you provide [feedback]("http://www.adobe.com/cfusion/mmform/index.cfm?name=fp_beta_feedback") about this to Adobe.

---

### Post by jlh on 2006-11-06
Good idea on the Adobe feedback suggestion.  I've submitted a report.

---

### Post by RobsterUK on 2006-11-20
I've had this same problem with Pandora. Its annoying because I only upgraded to Flash 9 because of a problem with YouTube which it has fixed.

Can someone direct me to a Howto on reverting to Flash 7? Thanks

---

### Post by RobsterUK on 2006-11-21
Anyone?

---

### Post by jlh on 2006-11-21
I'm not real geeky, but I think this will work.  

Your browser should have a plugins folder.  Depending on how Flash was installed, that plugin folder will apply to all users, or just to you.  In the latter situation, it will be in something like /home/YourName/firefox/plugins.  In the former look in /user/lib/firefox, or maybe /opt or /etc.  

You'll need to remove the Flash 9 plugin - libflashplayer.so - from that plugin folder.  I believe that remove to trash will do it.  If you are dealing with a file outside your home directory, you'll need to be the root or sudo for Ubuntu.

You then need to install Flash 7 again.  You should be able to do that by going to their download page, or else using Synaptic if you have right repository enabled.

---

### Post by RobsterUK on 2006-11-22
I've found out there is a new version of the Flash 9 beta to fix problems with audio.

See the Penguin SWF Blog [http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/)

I updated by using automatix to uninstall and reinstall.

So far it seems to have fixed the problem with Pandora.

---

### Post by jlh on 2006-11-23
I installed Beta 2.  Audio on Pandora skips, or freezes momentarily, with annoying regularity.  

Anyone else experiencing this?

---

### Post by LaneLester on 2006-12-21
I installed the flash 9 beta, and then browsed to Pandora. My whole system went crazy, and after failing to get control back, I rebooted. Now all of my windows for every program have no borders and no title bar!

What do I need to do to heal my system? I don't think just uninstalling the plugin is going to do the job.

**Later: **I accidentally discovered that my problem was that metacity was no longer running. I only had to start it from the terminal to get things going again. 

But now I've lost the ability to use Pandora, and I don't like that at all. I deleted the flash libraries, but left gnash installed. Something else must be needed to get Pandora again.
[B]
Later Still[/B]: I used synaptic to delete gnash and another flash stuff. Then I went to Pandora and let Firefox install the plugin. Pandora's back!

Lane

---

