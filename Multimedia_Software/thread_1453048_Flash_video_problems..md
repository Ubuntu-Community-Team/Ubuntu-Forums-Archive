---
title: "Flash video problems."
date: 2010-04-12
forum: Multimedia Software
---

### Post by A Traveller on 2010-04-12
Hi All.

I have just downloaded and installed Ubuntu 9.10 Karmic Koala on a blank hard drive. I've installed Adobe Flash plugin for Mozilla via Firefox (tried to play a video on YouTube and clicked the plugin required button that appeared). It states version 10.0.45.2ubuntu0.9.10.1 (flashplugin-installer) if I go to Ubuntu Software Centre via the Applications menu. I have a 64bit AMD system with an nVidia graphics card and have also just installed the 185 drivers via System, Administration, Hardware Drivers. I have two monitors and have them set as Separate X-Screens. I have selected 'None' in System, Preferences, Appearance, Visual Effects (which, from what I understand disables Compiz).

The problem is that if I view a video on YouTube (or any other Flash video site), the video does not fill the entire window that appears on the YouTube page. The video fills the window vertically but not horizontally. The video is not distorted or anything, but is more of a square shape, whereas the window provided on the YouTube page to play the video in is more rectangular in shape, so there is a black bar at the left and right sides of the video. If I switch to fullscreen, the problem is still there. The video does not fill my whole screen. It does so vertically but not horizontally, so there is a black bar at the left and right sides of the video.

Another problem is that whilst in fullscreen, if I move the mouse to the right edge of the monitor, the video exits fullscreen mode. I don't know if this has anything to do with the fact that my second screen is to the right of my main one. I never had any of these problems with my previous version of Ubuntu and I don't know if I am being paranoid or not, but I am wondering if the quality of video (online and on my pc) is significantly reduced as well. As I've said, I may be imagining this, I don't know for sure.

Should I just go back to my older Ubuntu version? Is there anyway to have streaming video open in VLC without having to copy and paste the link into VLC?

If anyone has any suggestions, they would be very appreciated!

Thanks.

---

### Post by WinterRain on 2010-04-12
> **A Traveller said:**
> I have a 64bit AMD system
Are you using 64bit ubuntu?
> **A Traveller said:**
> Is there anyway to have streaming video open in VLC without having to copy and paste the link into VLC?
You could install the firefox vlc plugin.

---

### Post by lovinglinux on 2010-04-12
I also recommend the 64bit flash. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by WinterRain on 2010-04-12
> **lovinglinux said:**
> I also recommend the 64bit flash.

He said he had a 64bit system, not necessarily 64bit ubuntu, hence my question. I'm sure we'll get him sorted. :)

---

### Post by A Traveller on 2010-04-13
Thanks for the replies.

WinterRain, yes, I am using 64bit Ubuntu and I am also using a 64bit processor (from what I can remember!).

lovinglinux, my Firefox version is the one that came with Karmic 9.10 (Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.1.9) Gecko/20100402 Ubuntu/9.10 (karmic) Firefox/3.5.9). Does that mean that I still need to install the 3.6 version indicated from one of the links provided in the instructions or just start from installing the Get64bitFlash-0.2.3.tar.gz script?

Is there any difference between running 'metacity --replace &' and selecting 'None' in Visual Effects? If I go to the Software Centre and click to remove Compiz, it states that to remove Compiz,  the gnome session manager must be removed as well. That doesn't sound like a good idea, as the Gnome Session Manager sounds like it may be something important that the system requires??

I don't understand the statement "You could do that yourself, but it is easier to simply use that script." which is found in the 64bit section of the optimisation page linked to. Do what yourself and use which script?

Thanks.

Ps. Thanks for the firefox vlc plugin suggestion.

---

### Post by WinterRain on 2010-04-13
First remove any flash you may have installed.
[Here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz") is the 64bit flash plugin. Put it on your desktop. Right click it and **extract here**. Then open a terminal (Ctrl+Alt+T) and do: (copy and paste code below into terminal, hit enter, then password, then enter. Done)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Restart firefox if open.

---

### Post by lovinglinux on 2010-04-13
> **A Traveller said:**
> lovinglinux, my Firefox version is the one that came with Karmic 9.10 (Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.1.9) Gecko/20100402 Ubuntu/9.10 (karmic) Firefox/3.5.9). Does that mean that I still need to install the 3.6 version indicated from one of the links provided in the instructions or just start from installing the Get64bitFlash-0.2.3.tar.gz script

You don't need to upgrade Firefox. Just install the 64bit version of flash.

> **A Traveller said:**
> I don't understand the statement "You could do that yourself, but it is easier to simply use that script." which is found in the 64bit section of the optimisation page linked to. Do what yourself and use which script?

Sorry, my English is not so good and it was late when I wrote that. I meant you could download flash manually, remove the existing version and extract the new one to the proper location, but the script from Get64bitFlash-0.2.3.tar.gz do all that for you in one batch.

---

### Post by A Traveller on 2010-04-13
Ok, thanks for the replies.

Well I've followed the instructions but all the problems are still there. This is what I did:-

Went to Ubuntu Software Centre, Installed Software, Adobe Flash, Remove to remove the Adobe Flash.

Restarted my pc.

Downloaded the following file to my desktop.

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Ctrl Alt T didn't bring anything up so I brought up the terminal from Applications, Accessories.

I copied and pasted the following into the terminal:-

sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins

I pressed Enter, typed my password and pressed Enter again. The terminal didn't say anything at all; it just brought up another prompt for typing; don't know if this is what is supposed to happen.

I also tried to follow the instructions found at the webpage linked to earlier, however, steps 4 and 5 didn't work for me because double clicking the file only opened it; have no idea where the 'Run in Terminal' option comes from.

Anyhow, I went to the Adobe link provided and it stated that I have version 10,0,45,2 installed; no idea if it's 64bit though.

Could anyone tell me how I could completely remove all flash from my pc using the info at the following link (what do I do with the info that's provided?):-

[http://ubuntuforums.org/showpost.php?p=8666948&postcount=72](http://ubuntuforums.org/showpost.php?p=8666948&postcount=72)

Thanks.

---

### Post by lovinglinux on 2010-04-13
> **A Traveller said:**
> I pressed Enter, typed my password and pressed Enter again. The terminal didn't say anything at all; it just brought up another prompt for typing; don't know if this is what is supposed to happen.

That's normal behavior. It means the command worked and didn't output any errors. Not all commands output messages when running or when completed. So if you get a new line ready for typing, then it worked.


> **A Traveller said:**
> I also tried to follow the instructions found at the webpage linked to earlier, however, steps 4 and 5 didn't work for me because double clicking the file only opened it; have no idea where the 'Run in Terminal' option comes from.

You need to extract the file from the downloaded archive, then drag it to a terminal or type the path to that file in a terminal. It will execute then.

> **A Traveller said:**
> Anyhow, I went to the Adobe link provided and it stated that I have version 10,0,45,2 installed; no idea if it's 64bit though.

You can type **about[noparse]:[/noparse]plugins** in the address bar to see what plugins are recognized and loaded with Firefox.

---

### Post by WinterRain on 2010-04-13
Did you extract the file to your desktop before doing the command?

---

### Post by A Traveller on 2010-04-13
Thanks lovinglinux.

According to the about:plugins, I already have VLC Multimedia Plugin!

Anyhow, the new flash which I installed made the video choppy, the sound lagged and in full screen, moving the mouse caused the video to break up and also crash. I've returned to the original flash I was using and these problems have gone, however, the original problems are still present.

The flash site is still stating that I have version 10,0,45,2 installed. Why is the version I had working better than the new one I tied when they're the same version? Is one 32bit and the other 64bit? If so, how do I tell if I've got 32 or 64?

Any other suggestions as what I could try?

Thanks.

Sorry WinterRain, you posted whilst I was posting so didn't see you post. Anyway, yes, I extracted the file before using the command. I don't think I did anything else incorrectly.

---

### Post by lovinglinux on 2010-04-13
> **A Traveller said:**
> According to the about:plugins, I already have VLC Multimedia Plugin!

Are you trying to play flash videos embedded on YouTube or through standalone VLC Player? BTW, I would replace the VLC plugin with gecko-mediaplayer. See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

> **A Traveller said:**
> The flash site is still stating that I have version 10,0,45,2 installed. Why is the version I had working better than the new one I tied when they're the same version? Is one 32bit and the other 64bit? If so, how do I tell if I've got 32 or 64?

When you install the 32bit version, it also installs nspluginwrapper, which is a compatibility plugin that allows you to run the 32bit version on a 64bit system.

---

### Post by A Traveller on 2010-04-13
Thanks lovinglinux.

All the problems I've described are concerning playing videos embedded at the actual websites, e.g. Youtube. I had just wondered about the options available with playing through VLC, however, this isn't the problem, the main issues are with playing videos directly at their websites, i.e. video not filling the window at the webpage (or my entire screen in full screen mode) and exiting full screen when mouse is moved to right edge of video.

---

### Post by lovinglinux on 2010-04-13
I don't know what else you could do. I also had some weird video glitches in Karmic that weren't fixed during the beta testing, so I just had to live with them until now, with Lucid. One of the problems was that when playing flash games, some parts of the flash video would flicker, exposing the page underneath. This was prevented by disabling Compiz, but you have already done that.

---

### Post by max92 on 2010-04-13
Hey guys I was in a similar situation, and my forum search dropped me here, and I'd like to say this helped me out a lot. However, does anyone know what the problem was? 64-bit OS/computer not using the 64-bit flash lib? My flash videos worked until a recent update, so is it possible that was the problem?

Thanks guys :D

---

### Post by A Traveller on 2010-04-14
Thanks for the help anyway WinterRain/lovinglinux. It is all appreciated. I think I may go back to my old Ubuntu version, as the problems I posted about are too annoying to put up with.

max92, I have no idea what the problem is for me or was for you; sorry.

---

