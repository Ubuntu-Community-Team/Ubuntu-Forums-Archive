---
title: "Full screen Flash on amd64 not working properly"
date: 2009-12-21
forum: Multimedia Software
---

### Post by xv1700 on 2009-12-21
I have recently installed a clean 64 bit Karmic on an AMD Athlon powered box with an Nvidia 6800 GT. After experiencing the normal teething problems I followed the latest instructions to get Flash installed which worked fine. I can now watch youtube and standard flash movies in the browser or in full screen.

My one remaining problem is that on some sites full screen does not work. A good example is Demand 5 ([http://demand.five.tv/](http://demand.five.tv/)) where I have been trying to watch some catchup episodes of Flash Forward. They have a specialised viewer based on Flash that works on all other operating systems and 32 bit Ubuntu fine. I have tried disabling compiz as that has been listed as a possible problem. Now I am out of ideas.

When I say does not work, this is what happens:
1. Hit the full screen button.
2. Black full screen pops up.
3. A message at the top of the page appears saying that the advertising will be finished in 60 seconds.
4. The message starts trying to do its count down but the seconds are not repainted properly.
5. No video ever appears.

---

### Post by pkinetics on 2009-12-21
I read in a previous article that Desktop Visual Effects might be the cause of this. 

Go to System -> Preferences -> Appearance -> Visual Effects (tab)

---

### Post by Yellow Pasque on 2009-12-21
ARe you running the actual 64-bit Flash or the 32-bit version through nspluginwrapper? Maybe start firefox from the terminal and see if Flash outputs errors..

---

### Post by HappyFeet on 2009-12-21
Although most sites will full screen flash fine, I have found a few that won't. Maybe there is a solution, or not, by I have accepted it for what it is. It may have to do with something about the 64bit plugin.

---

### Post by xv1700 on 2009-12-22
I am using the 64 bit client. All desktop effects and compiz are off.

Just done some other experimenting: looks like it might be something to do with movies that have adverts and a countdown timer injected into them. I did see that full screen had only recently been added to the 64bit plugin and Adobe were looking for feedback but I could not find somewhere to report feedback. Anyone got any ideas?

---

### Post by lovinglinux on 2009-12-22
> **xv1700 said:**
> I am using the 64 bit client. All desktop effects and compiz are off.

Just done some other experimenting: looks like it might be something to do with movies that have adverts and a countdown timer injected into them. I did see that full screen had only recently been added to the 64bit plugin and Adobe were looking for feedback but I could not find somewhere to report feedback. Anyone got any ideas?

Use [Adblock Plus](https://addons.mozilla.org/en-US/firefox/addon/722), it also blocks the adverts from videos. Sometimes is required to watch the advert to make the video work, so in this case you need to disable Adblock or create an exception.

---

### Post by xv1700 on 2009-12-22
Ok so I gave Adblock Plus a shot: didn't read into it much but it appears to be messing with JavaScript in the page and it breaks flash player and most of the the website, don't think it is going to do the trick.

---

### Post by chenxiaolong on 2009-12-22
The Ubuntu packaged version of flash has a lot of bugs in it. You should try using the native 64bit version of flash:

1. Remove the [COLOR="Blue"]flashplugin-nonfree flashplugin-installer[/COLOR] packages.

2. Download [COLOR="SeaGreen"]http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz[/COLOR]

3. Extract [COLOR="DarkOrchid"]libflashplayer-*.linux-x86_64.so.tar.gz[/COLOR]. It will extract [COLOR="DarkOrchid"]libflashplayer.so[/COLOR] (could be in a subfolder).

4. Copy [COLOR="DarkOrchid"]libflashplayer.so[/COLOR] to [COLOR="DarkOrchid"]~/.mozilla/plugins[/COLOR]. If you don't have that folder, create it.

---

### Post by xv1700 on 2009-12-23
I am already running the native 64 bit Flash, slightly different install procedure but same results and version:

[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

Tried the same problematic site with Windows Vista machine and it had similar odd issues until I updated to the very latest Flash 10. I am now pretty sure it is an Adobe fault and ubuntu is behaving nicely.

---

### Post by The Judderman on 2010-02-08
I'm having a similar issue and wondered if anybody has got a solution, or how I can report it back to Adobe? It definitely seems to be a flash issue. I have only got this problem with the demand.five.tv website. In small view, it works fine, but as soon as I try to go to Full Screen, I get the black screen as described in the first post.

I'm using the native 64-bit version and it happens whether or not compiz is switched on or disabled.

Does anybody have a solution? I have to boot up windoze in order to watch my favourite programs, and that is frustrating!!!

Cheers,

The Judderman

---

### Post by lovinglinux on 2010-02-08
> **The Judderman said:**
> I'm having a similar issue and wondered if ...

See [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by foresthill on 2010-02-08
This worked for me, and looks a little simpler:

[http://ubuntuforums.org/showthread.php?t=1401723](http://ubuntuforums.org/showthread.php?t=1401723)

I was having big problems with embedded flash videos not playing at all and videos viewed on YouTube playing extremely choppy. So far, it seems to be working.

* knocks on wood *

---

### Post by lovinglinux on 2010-02-08
> **foresthill said:**
> This worked for me, and looks a little simpler:

[http://ubuntuforums.org/showthread.php?t=1401723](http://ubuntuforums.org/showthread.php?t=1401723)

I was having big problems with embedded flash videos not playing at all and videos viewed on YouTube playing extremely choppy. So far, it seems to be working.

* knocks on wood *

Yes it's simpler, but that installs it only for Firefox and only for the user performing the installation.

---

### Post by The Judderman on 2010-02-12
Thanks for the link. I had tried that link initially when I installed Flash, but it didn't work. I followed [this how-to]("http://ubuntuforums.org/showthread.php?t=766683") which worked absolutely fine, except demand.five.tv full screen. That is the only site that I've had problems with! Not sure what the solution is. Whether it is flash, or five.tv!

Thanks for your help!

The Judderman

---

### Post by chenxiaolong on 2010-02-13
There's an even easier way to do this now:

1. Remove the packages "flashplugin-installer" and "flashplugin-nonfree."

2. Add this PPA to your APT sources. If you have Ubuntu 9.10 Karmic, you can just run "sudo addaptrepository ppa:sevenmachines/flash" to do it automatically.

3. Run "sudo apt-get update."

4. Install the package "flashplugin64-nonfree."

5. Restart Firefox and enjoy 64 bit flash!

---

