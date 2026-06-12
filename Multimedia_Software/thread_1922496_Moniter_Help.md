---
title: "Moniter Help"
date: 2012-02-08
forum: Multimedia Software
---

### Post by RogueALM on 2012-02-08
I  have a dual moniter setup on a GeForce 120 1gb.  Works great on my  Ubuntu 11.10.  But when I play Vendetta I either have to diasable one of  the moniters in the Nvidia CP, or try to play Vendetta Dual Screen,  which isnt bad, but not what I would like.  

What I am after, is how to put Vendetta on one of my monitors, while  leaving a desktop on the other.  *now - in the game settings for  Vendetta you can select window mode.  The problem here is when I am in  dual screen mode, it automatically sets the game resolution to match  2000+ x 1600+ or whatever the actual resolution is. So the end result is  the window (while in window mode) is too large to fit onto one screen,  and there is no option to change the window resolution.  

I have tried a few basic things but I still fairly uneducated with the Ubuntu System.  Any help would be great.  

(If you can put a seperate desktop on each screen, instead of the twinview or extended desktop more, that would be sweet.)

Thank you.
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=11674234")

---

### Post by papibe on 2012-02-08
> **RogueALM said:**
> (If you can put a seperate desktop on each screen, instead of the twinview or extended desktop more, that would be sweet.)
You can do that with 'Nvidia X Server Settings' (nvidia-settings).

First save your current xorg.conf, just in case:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Then run nvidia-settings as root:
```
gksudo nvidia-settings
```
Once open click on 'X Server Display Configuration' at the left. Then on the right press 'Configure' and select 'Separate X Screen'. Then set resolutions and other settings as you need it. Once you are happy with the configuration, save the settings by pressing 'Save to X Configuration File'.

Restart to check if the settings were set correctly. In case you run into problems, recover your old settings by doing:
```
sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```
I hope it helps, and tell us how it goes.
Regards.

---

### Post by RogueALM on 2012-02-09
This is a feature I am familiar with already.  I use it to obtain the twin view that I used because it works successfully.  The Separate X does not.  Or at least thats the impression I get.  When I select the separate x mode, it no longer allows to change monitor positions (in terms of left and right).  It turns one of my screens into a solid white canvas, and when I move my mouse onto there, the pointer becomes a X.  Now if I start trying to drag windows to the white canvas or right click in its vicinity, sometimes the screen image of the white canvas will alter.  Sometimes a wallpaper, most of the time whiteness.  Lots and lots of whiteness.

**EDIT**

I fixed it!  After a couple of days of constantly changing settings and attempting code and *freezing* up my computer a couple of times and really getting some fun monitor reactions, I finally have the setup I desire.  Currently as I type this I have a VO on one monitor and my desktop on the other off of one GPU via AGP and DVI. What finally fixed it? I do not know.  The last time I changed it back, and it worked.  I haven't restarted the computer yet, but its working now and my guess continue too. Thank all of you for your support.

---

### Post by RogueALM on 2012-02-13
Well, I finally restarted, same problem.  But, its ok.  Because I am about to side install windows, and get SWTOR.  And then I will face even newer problems Im sure.

---

