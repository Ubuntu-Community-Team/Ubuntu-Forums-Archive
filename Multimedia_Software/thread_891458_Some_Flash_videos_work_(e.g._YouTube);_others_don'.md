---
title: "Some Flash videos work (e.g. YouTube); others don't (e.g., Daily Show)"
date: 2008-08-16
forum: Multimedia Software
---

### Post by adasiak on 2008-08-16
(Running Firefox 3.01 on Kubuntu 8.04 "Hardy".)

I'm getting inconsistent performance on Flash videos.  While nearly everything I try works -- including BBC, CNN, and YouTube -- I cannot get the short segments of The Daily Show to play.

Surprisingly, full episodes will load and play just fine (for example, [http://www.thedailyshow.com/full-episodes/index.jhtml?episodeId=179231](http://www.thedailyshow.com/full-episodes/index.jhtml?episodeId=179231)).  It's just the shorts that will not play (for example, [http://www.thedailyshow.com/video/index.jhtml?videoId=179655&title=recap-week-of-8/11/08](http://www.thedailyshow.com/video/index.jhtml?videoId=179655&title=recap-week-of-8/11/08)).  A status bar appears on a black window, indicating "Loading" -- but when the bar reaches the right side, the window goes entirely black, and nothing else appears.

Has anybody else had this problem?  Or, more importantly, has anybody else had *and overcome* this problem?  I'd be grateful to see your solution -- or to have suggestions from anybody who has them.

---

### Post by _Lazy_ on 2008-08-17
I'm having the same problem with the Daily Show clips with Firefox 2 and Ubuntu 7.10.

Weird thing is that it still worked last week. But they seemed to have changed their video hosting to something like mtvnservices.com, which is the same that South Park Studios uses and the South Park videos don't work for me either.

---

### Post by 164747 on 2008-08-17
I am experiencing the same problem as you, I have problems looking at som streamed flash videos. I could also not look at your linked flash media. If you want, should file a bug report at launchpad 

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

as your bug is so easy to reproduce.

---

### Post by brian mcgee on 2008-08-17
> **adasiak said:**
> I'm getting inconsistent performance on Flash videos.  While nearly everything I try works -- including BBC, CNN, and YouTube -- I cannot get the short segments of The Daily Show to play.

If the only flash videos you have trouble with are from the Daily Show's website, then it's more likely a problem on their end, not with your configuration. I've noticed similar issues with their site from time to time. When you have a problem, try accessing the same video in the same way from other computers you have access to. Oftentimes, these videos are linked to from Digg posts etc., so the Daily Show server(s) might just be choking. 

Also, full episodes might work ok b/c they're probably streamed from a different source, or the configuration is different. Maybe write them an email?

---

### Post by adasiak on 2008-08-18
I think _Lazy_ and brian mcgee are on to something: if everything else in the world works, it's probably a problem on their end.  And it seemed to be because of where they were streaming from: in this case, something called mtvnservices.com -- which *doesn't* push their full episodes.

However, the problem has passed for me.  It looks like somebody on their end fixed it.  I hadn't tried South Park before, but it looks like both their episodes and their clips are coming through just fine.

Thanks for the input, gang.

---

### Post by erixoltan on 2008-08-18
I am also having this problem with the Daily Show site, and it hasn't gone away.  Also a problem with South Park Studios.  On my system it is for all their videos.  Other video/Flash sites work.  Problem occurs in Konqueror, Opera and Firefox.  Other sites work.  I'm not getting any sound either.

These sites work on my wife's Windows Vista laptop in Firefox.  But I won't sink to the level of watching them there LOL.

This has been reported by several others as a bug in launchpad. 
[https://bugs.launchpad.net/ubuntu/+bug/258899](https://bugs.launchpad.net/ubuntu/+bug/258899)

---

### Post by _Lazy_ on 2008-08-19
The problem hasn't gone away for me either.

---

### Post by erixoltan on 2008-08-20
I was just able to reproduce this problem on a clean install of Ubuntu 8.04 (64 bit) that I had downloaded today from ubuntu.com.  I reported earlier that it affected hulu.com as well, but that appears to have been some missing codecs in Kubuntu.

---

### Post by HebrewTheHammer on 2008-08-21
does anyone here also have trouble with "gametrailers.com"

i do and am going out of my mind...i however was able view flash from them on 7.10.

---

### Post by _Lazy_ on 2008-08-21
OK, I solved the problem with South Park and Daily Show for me.

Seems like it was the Add-on "RefControl" which lets you block the browser referer header part.

I had already allowed the referer for the Daily Show and South Park but since it didn't solve the problem, I thought the cause would be something else.

But after allowing referers for mtvnservices.com, the playback worked again.

So, if you have playback trouble it could be some browser header modification you have installed, but then there's still the problem with the above mentioned clean install not working.

---

### Post by lklk on 2008-08-26
I can't watch the full episodes of the Colbert Report/Daily Show (it has be like this for months). I have Ad-block Plus and Phishtank installed in Firefox 3 and I have disabled them but still nothing. I run Ubuntu 8.04 64 bit. I watched South Park a few weeks ago with no problems, but I don't know if it still works or not nor do I care. g

---

### Post by rashly on 2008-08-27
I have the same problem. While most sites are alright, I will occasionally find one with this problem. Upgrading to the Ibex version of Flash didn't help. Nothing loads. It's just a gray/white box where the Flash video should be.

Ubuntu 8.04 64-bit.

---

### Post by Irtsi on 2008-08-27
This is how I solved the problem:
Open *about:config* in Firefox and set the value of *network.http.sendRefererHeader* to **2**

---

### Post by pzs on 2008-08-29
I have the same problem - BBC and YouTube work but Daily Show does not. I've disabled adblocker and made the about:config change suggested but I still get grey boxes where the videos should be. I'm running Hardy 64. I'm pretty sure this used to work.

And during the Democratic convention too. Bad timing.

---

### Post by Adahn on 2008-08-29
here too.  I'm using hardy64 and the recent flash plugin.

The other PC in the house (hardy32) works fine at DailyShow.com

---

### Post by Tomy on 2008-08-31
> **Irtsi said:**
> This is how I solved the problem:
Open *about:config* in Firefox and set the value of *network.http.sendRefererHeader* to **2**
 
I have a recent fresh install of Hardy 32bit and  *network.http.sendRefererHeader* was already set to 2.

I have flashplugin-nonfree (flash 9) installed.

Video clips from [http://www.thedailyshow.com](http://www.thedailyshow.com) will not play -- the video appears to start loading and stops with a black background.

Are there any other suggestions to solve this?

update: The "full show" videos do play. The short clips do not.

---

### Post by _Lazy_ on 2008-09-03
> **Tomy said:**
> I have a recent fresh install of Hardy 32bit and  *network.http.sendRefererHeader* was already set to 2.

I have flashplugin-nonfree (flash 9) installed.

Video clips from [http://www.thedailyshow.com](http://www.thedailyshow.com) will not play -- the video appears to start loading and stops with a black background.

Are there any other suggestions to solve this?

update: The "full show" videos do play. The short clips do not.

I had the same error a few days ago, but was working again today.

---

### Post by kerry_s on 2008-09-03
works fine here. but then i'm using etch.

---

### Post by reader4 on 2008-09-03
I'm also having problems with Hardy 64, but not Hardy 32 on a different box.

---

### Post by pzs on 2008-09-04
Mine doesn't work on Hardy32 either. Also, launching the page destroys any existing flash process - if I'm listening to last.fm and try to hit the Daily Show page, the last.fm flash dies and I have to restart Firefox.

---

### Post by junkbar on 2008-09-05
I'm also having problem viewing these videos on Hardy 32. As a temporary work-around, I've been using the Greasemonkey script found [here]("http://wvarner.blogspot.com/2008/08/problem-viewing-daily-show-videos-on.html").

---

### Post by rashly on 2008-09-05
> **Irtsi said:**
> This is how I solved the problem:
Open *about:config* in Firefox and set the value of *network.http.sendRefererHeader* to **2**

Mine was already set to 2. Still doesn't work.

---

### Post by kkinder on 2008-09-08
For me with general Flash it's inconsistent. Sometimes Youtube does not work, but after I restart the browser, it will again.

TheDailyShow.com simply does not work for me.

The only thing I can think of is that I did this for crashing:

[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

---

### Post by giruzz on 2008-09-19
> **rashly said:**
> Mine was already set to 2. Still doesn't work.

same issue here.

giruzz

---

### Post by rashly on 2008-09-19
I found a solution!

I reinstalled flash player using these instructions:
[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

For 64-bit, run these commands in a terminal, or save as a .sh file and run it:
```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# More Super minor updates by Alejandro Cuervo 3[at]cuervo[dot]net
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10 RC"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz
tar zxvf flashplayer10_install_linux_091508.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "Yoy may re-start Firefox now"
```
The above was modified from: [http://www.queleimporta.com/how-to-install-flash-10-rc-on-ubuntu-64-bits-with-2-clicks/en/](http://www.queleimporta.com/how-to-install-flash-10-rc-on-ubuntu-64-bits-with-2-clicks/en/)




Now that will just reinstall the latest RC of flash player, the actual problem was relating to the libflashplayer.so not being copied into the firefox plugins directory. Here is how to fix it:

1) Download [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz)
2) Extract the file
3) Copy libflashplayer.so to /home/yourusername/.mozilla/plugins (you might have to create this plugins folder). The problem for me, was that there was no plugins folder here. You might also have a firefox folder inside of /home/yourusername/.mozilla/ . Go into that folder, and there will be another folder for profiles with some random characters. Go into there, and create a plugins folder, and copy the libflashplayer.so into there.

That should be it. I'm pretty sure only one of the two plugin folders that I listed above needs the libflashplayer.so file, but I'm not sure which one. I put it in both.

That should do it. The "bug" seems to be the flash player installer not copying the libflashplayer.so into the plugins directory.

---

### Post by Pharohs on 2008-09-19
BTW, this message appeared at the end of that first installation:

```
NOTE: Please ask your administrator to remove the xpti.dat from the components directory of the Mozilla or Netscape browser.
```

I'm new, so I looked around the file system and couldn't find it.

This is so frustrating.  Using Ubuntu is like owning a car and having to reconfigure the engine and transmission because you want to drive to a different place.  Everything you do is complicated and frustrating.  Nothing "just works". :(

---

### Post by rashly on 2008-09-21
Just try the second part, copying the libflashplayer.so to the plugins directory and see if it works.

---

### Post by vamped on 2008-09-29
Yes! Finally! The Daily Show works. Youtube works. (it was intermittent before)

I have 8.04-64 bit installed. Using gnome and Firefox.

The scripts appear to be non-malicious: the flash10rc.sh and the getlibs-all.

---

### Post by odoketa on 2008-10-06
> **rashly said:**
> I found a solution!

You, sir or madam, rock. That solved the problem for me.

I do think this is one of those killers that must be fixed - I was rebooting into xp for the Daily Show and Colbert Report alone. I think ubuntu could crash and burn in all respects but the web browser, and people would be fine, but segments of the web browser not working will lead people to abandon the system.

I don't really have the knowledge of where to begin to track down the root cause of this not working - it seems like it's a three vendor problem, including one closed source, but at the very least could the big flash sites be incorporated into the testing scheme before an update goes out?

---

### Post by Melk79 on 2008-10-13
Thank a million.  All I did was run the script and Daily Show played.

---

### Post by Seashellshannon on 2008-11-14
hi. serious beginner here. i created a profile just so i could post a question on this thread. i have been trying....desperately...and unsuccessfully...to watch the daily show online for the last few months (it used to work fine for me and then out of the blue one day it just stopped)...i've installed and reinstalled adobe a **** ton of times...it sounds like i'm having the same problems you guys are talking about (black screen, video not loading, not getting short clips or full episodes) but i do not have the knowledge necessary to understand what you people are talking about re: a solution. i do not know how to "run a script". is there anyone who can provide me with a solution or series of really basic steps that i can follow and understand...please forgive my ignorance...i googled for help and this was the only website i found where people were actually saying they had the same problem as me and proposing solutions...i just wish i understood what you guys were talking about. any help is much appreciated. thanks...(i really miss the daily show...it was really the only television i ever want to watch)

---

### Post by Adahn on 2008-11-14
I actually finally got Daily show working, in Hardy, though I don't recall how, and it's broken again in Intrepid.

One strange thing:  the 'properties' in the video window lists swfdec as my in-browser flash player, but I don't have swfdec installed ( I have the adobe non-free flash 10 plugin in the repos, along with the restricted extra package).



Edit:

correction, swfdec-gnome was uninstalled.
Once I removed swfdec-mozilla in synaptic, Daily Show indeed plays!

---

### Post by ds3 on 2008-11-14
I'm not sure if anyone on this thread can help me, but first a comment:
The Daily Show's website does not work with Firefox, regardless of your operating system. I cannot get it to load in Windows unless I use Internet Explorer, so this is not an Ubuntu or Linux problem.
However sometime in the last week or so, I have stopped being able to use Hulu in Ubuntu. I'm using Firefox 3.0.3 and Hardy on an AMD64 system so Flash is running through nspluginwrapper, but Hulu used to work, and other Flash sites still work. Has anyone else seen problems with Hulu lately? It now just sits there "loading" in the Flash window, like people are describing for NBC's website.
Thanks.

---

### Post by eksabajt on 2008-12-15
@ds3: This is not the case for me.

I have a Windows XP virtual machine for VirtualBox and mtvnservices.com videos work fine using FF3 there.  However, they do not work for me in FF3 with Intrepid.  Hulu works for me in Intrepid intermittently.  Same for Youtube.

---

### Post by T_W on 2009-03-01
Try running Firefox 2.  Switching to 2 seems to make this work.

---

### Post by Adahn on 2009-03-01
> **ds3 said:**
> I'm not sure if anyone on this thread can help me, but first a comment:
The Daily Show's website does not work with Firefox, regardless of your operating system. I cannot get it to load in Windows unless I use Internet Explorer, so this is not an Ubuntu or Linux problem.
However sometime in the last week or so, I have stopped being able to use Hulu in Ubuntu. I'm using Firefox 3.0.3 and Hardy on an AMD64 system so Flash is running through nspluginwrapper, but Hulu used to work, and other Flash sites still work. Has anyone else seen problems with Hulu lately? It now just sits there "loading" in the Flash window, like people are describing for NBC's website.
Thanks.


I don't know why, but creating a login fixed Hulu for me on my AMD64 install.  A thread elsewhere mentioned something about Hulu's cookies, and I'll bet it's DRM related.
I can't get Daily Show to work on this particular PC, where once it had.
Both work fine on my 32bit rig.
nonfree-plugin in both cases.

---

### Post by mrjane on 2009-03-04
The script works .Thanks rashly.

---

### Post by Jinx-Wolf on 2009-03-15
Yay! I can finally watch South Park on Ubuntu. Thanks rashly! Script worked great. ^-^

---

### Post by Ze MoreiRa on 2009-03-16
rashly for president! :D
it works

---

### Post by greenjumper on 2009-04-23
Unfortunately although the script ran fine, and I copied the library into both directories I still can't watch the south park vids. It's a bit weird because up until about 3 weeks ago it worked fine. 
Any ideas anyone?

---

