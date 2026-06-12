---
title: "Flash player crashes -  black square"
date: 2010-06-13
forum: Multimedia Software
---

### Post by leithon on 2010-06-13
Hi all!

I used to listen music online from baidu mp3 or youku/youtube, but some days ago, I have noticed that I am watching a video or listening to a song and flash player crashes, instead I just see a black square everywhere there is a flash web application.

I appreciate any help!

I am using Chromium but it also crashes on Firefox (less frequently)

lucid lynx 64 bits

---

### Post by Deadite81 on 2010-06-13
I had this same exact problem.

When it happened to me I had sound from flash videos, but all black where there should have been video.  Normally there would be a notification of a crash, but Chromium just kept on going, as if everything were functioning properly.

At the same time I had Google Chrome dev installed just to checkout, in which flash would crash altogether, giving the yellow error bar at the top (I've since uninstalled it).  Flash was also only working sporadically in Firefox (basically not at all).

What seemed to fix the problem for me was that I was running Firefox 3.6.4.  They've pushed the release back now, but at the time it was supposed to be pushed out around a week from when I installed it.  So I grabbed it early to check it out, along with the latest Thunderbird.

Anyway, what fixed the problem was downgrading back to Firefox 3.6.3 and removing that Mozilla ppa.  I don't know if it was FF, xulrunner, or something else, but completely purging that ppa and reverting to the official packages fixed my Chromium flash problem.

If you don't run Firefox 3.6.4 then I don't know, but sure would like to because it could happen to me again then!

---

### Post by lovinglinux on 2010-06-13
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Please let me know if it still crashes after that. It probably will, but at least we will be able to discard some possible culprits.

---

### Post by leithon on 2010-06-13
Hi,

@[Deadite81]("http://ubuntuforums.org/member.php?u=996614") Thank you for providing more information about the problem. Yes, it's the same. But I am running FF 3.6.3, maybe that's why problem is less frequent in FF than in Chromium. 
Is there anything I should purge then?

@loveinlinux: thank you for the advice, i'll try it

btw, grooveshark.com also crashes.

---

### Post by lovinglinux on 2010-06-13
> **leithon said:**
> Hi,

Thank you for providing more information about the problem. Yes, it's the same. But I am running FF 3.6.3, maybe that's why problem is less frequent in FF than in Chromium. 
Is there anything I should purge then?

btw, grooveshark.com also crashes.

Check if you have **libmoon** package installed. If yes, then remove it. It is known to cause such crashes when viewing flash.

Also type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by Deadite81 on 2010-06-13
Linux can be so weird sometimes.  Downgrading Firefox clearly solved the problem for me, and here you are with the exact same problem, but with the "official" FF.

lovinglinux sounds like he's delt with this before.  I have heard about the libmoon package wreaking havoc on Flash.  Perhaps his possible solutions will help.

Here's what I don't get:  When my Flash was going wonky it didn't work in Firefox or Chromium (which is possible because they are all symbolically linked), but it didn't work in Google Chrome either.  Chrome is installed in a directory all its own (/opt/Google...) and comes with its very own independent Flash installation.  That is, Flash is installed with Chrome in the same directory.

I'm not trying to make more out of this than is there, but I've never had the libmoon package installed and I suffered the exact same problem, *including* in a browser that has nothing to do with Mozilla (as far as I know).  I wish I could figure out which switch I flipped!

I hope lovinglinux's solutions help because I'm stumped!

---

### Post by leithon on 2010-06-18
Hi, 

Sorry to reply late, i was in a trip...
Well, back to ubuntu:

I've tried what lovinglinux said, but it did not work, I tried the code version, not the addon for firefox.
libmoon is not installed.

And I followed the last procedure, this is the result:

**Shockwave Flash**

 File:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.1 r53   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes  [B]
[/B]



Thank you for your help!

---

### Post by lovinglinux on 2010-06-19
> **leithon said:**
> Hi, 

Sorry to reply late, i was in a trip...
Well, back to ubuntu:

I've tried what lovinglinux said, but it did not work, I tried the code version, not the addon for firefox.
libmoon is not installed.

And I followed the last procedure, this is the result:

**Shockwave Flash**

 File:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.1 r53   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes  [B]
[/B]



Thank you for your help!

You have the latest version.

Try this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

Also try this:

```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```

---

### Post by leithon on 2010-06-20
> Try this:

 	Code:
 	gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer 
Add the following line before the last line of the file opened by  the previous command:

 	Code:
 	export GDK_NATIVE_WINDOWS=1 
Save and restart the browser.




Thank you so much lovinglinux, that solved the problem for me.

Can you please explain to me what was wrong then?
I watched a 1 hour long movie and listen for more than 2 hours music and everything worked fine.

---

### Post by lovinglinux on 2010-06-21
> **leithon said:**
> Thank you so much lovinglinux, that solved the problem for me.

Can you please explain to me what was wrong then?
I watched a 1 hour long movie and listen for more than 2 hours music and everything worked fine.

It's a know bug in the 32bit plugin wrapper used on 64bit systems.

---

### Post by leithon on 2010-06-24
solved :guitar:

---

### Post by euloiix on 2012-01-05
Is this thread still up ? 

I am having the exact same problem, but none of the solutions proposed here worked for me. 

I am running on Lucid 10.04 x64.

---

### Post by euloiix on 2012-01-05
Solved it. What worked for me was to install the beta flash plugin via the firefox addon

---

