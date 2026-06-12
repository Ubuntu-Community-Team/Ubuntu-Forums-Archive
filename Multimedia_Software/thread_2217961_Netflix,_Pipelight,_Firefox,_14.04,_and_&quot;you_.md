---
title: "Netflix, Pipelight, Firefox, 14.04, and &quot;you must enable ActiveX&quot;"
date: 2014-04-19
forum: Multimedia Software
---

### Post by Roasted on 2014-04-19
Hello friends. I just installed Pipelight as per these instructions:

[http://www.itworld.com/software/414056/install-silverlight-alternative-pipelight-ubuntu-1404](http://www.itworld.com/software/414056/install-silverlight-alternative-pipelight-ubuntu-1404)

But when I go to Netflix and try to play a video I get:

The Netflix Movie Viewer requires ActiveX to be enabled. Please verify in your Internet Explorer security settings that ActiveX is enabled, then reload this page to try again.
You may need to disable firewall or anti-virus software to enable ActiveX.

If I use Chrome, everything works. Any ideas?

---

### Post by monkeybrain20122 on 2014-04-19
What did you set your user agent to? I always use Firefox Windows and it works. 

BTW, it won't work in Chrome after the next Chrome update and google will drop support to all NAPAI plugins, pipelight included.

---

### Post by David D. on 2014-04-19
The instructions you followed installs Pipelight, but neglects to have you install the User Agent Overrider add-on for Firefox.  

Here is a link to that add-0n.  [https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/")

---

### Post by Habitual on 2014-04-19
I installed User Agent Switcher 0.7.3 for Firefox
pipelight-plugin --enable silverlight
choose Firefox15.0a1 Win7 64 for your Agent. 
Test it at [http://fds-team.de/pipelight/](http://fds-team.de/pipelight/)

---

### Post by Roasted on 2014-04-19
User Agent Switcher did not work. I only had options for IE 6, 7, 8. Didn't have many other options. Tried all 3 and none got me past the ActiveX error. I installed User Agent Overrider and that worked wonderfully. Also, good to know about the Chrome thing. Not to get into a Chrome vs Firefox debate but I've been growing increasingly frustrated with Chrome, so you telling me they're yanking that capability isn't exactly a surprise. I wonder though... will there be some sort of work around for it? After all, I *never* suspected that there would be a work around for Netflix/Silverlight on Linux to begin with, and here we have one. Maybe a new Chrome add-on will pop up that works?

Also, you guys out there who have used Pipelight/Netflix/Ubuntu since the beginning of time... How reliable is it? I'm thinking of doing a dual boot on my HTPC. Ubuntu for primary, and Windows 7 for a backup... just in case I'm away at work or whatever and my wife calls saying that Netflix is broken, she can reboot without me getting an earfull - ha! But anyway, has it ever 'broken' for you guys via updates? Or is it typically a set-it-and-forget-it thing?

Thanks for the quick assistance!

EDIT - Now this is going to get irritating. I closed Firefox a few times and reopened to Netflix to test, but now it's giving me the system requirements page each time. In the preferences of User Agent Overrider, it looks like it's just a text file with a bunch of entries in it that I didn't touch. What on earth changed - already?

---

### Post by David D. on 2014-04-19
Is the User Agent Overrider icon in the upper right of Firefox blue or grey?  If it is grey (i.e. turned off), left-click on it to turn it on.  If it is blue, it is on/active.  If User Agent Overrider is on/active and you are still having the problem, I no ideas on a fix right now.

---

### Post by oldos2er on 2014-04-19
Moved to Multimedia & Video.

User Agent Switcher never worked for me, but User Agent Overrider does, see [https://answers.launchpad.net/pipelight/+faq/2351](https://answers.launchpad.net/pipelight/+faq/2351)

---

### Post by SeijiSensei on 2014-04-19
I got dumped to the System Requirements page when going simply to [www.netflix.com](www.netflix.com), but I discovered that if I go to [http://www.netflix.com/WiHome](http://www.netflix.com/WiHome), I can watch videos with pipelight installed.  I have [UAControl]("https://addons.mozilla.org/en-US/firefox/addon/uacontrol/") installed with this User-Agent string associated to Netflix: Mozilla/5.0 (Windows NT 6.1; rv:23.0) Gecko/20131011 Firefox/23.0.

I also told pipelight to [install the Windows version of Flash Player]("http://fds-team.de/cms/pipelight-installation.html#section_2_3").  Some places now check for Version 12 of Flash which will never be released for Linux.

---

### Post by Roasted on 2014-04-19
> **David D. said:**
> Is the User Agent Overrider icon in the upper right of Firefox blue or grey?  If it is grey (i.e. turned off), left-click on it to turn it on.  If it is blue, it is on/active.  If User Agent Overrider is on/active and you are still having the problem, I no ideas on a fix right now.

Ah, derp. I hadn't noticed that it added that icon there. Thanks for that.

Man I hope the inevitable Netflix/HTML5 future brings a better experience to Linux. While I was troubleshooting this, I simultaneously booted up Android X86 on a spare desktop, and even there Netflix wouldn't run. It would open but just insta-crash.

I'm starting to wonder if Netflix on the computer is just an epic fail. I mean, I know it's kind of a fail, but I'm giving more thought about just buying an Android stick/box/gizmo to utilize at a HTPC. Most of my tech friends I speak to don't understand why I fuss with Netflix the way that I do, but they all have Roku/PS3's/etc. I'm glad that I have Netflix working on my laptop and will use it, but I'm not sure I'll utilize it at the HTPC - but only because the fan in it sure sounded a LOT quieter in my office than when I set it up behind the TV in the living room... so either way I want to look for another gizmo to do that job. 

I do have a Chromecast... but I retired it after it couldn't do local streaming over something like Samba. I have almost 2 TB of videos on my server and being locked out of that was a headache. Anybody know if the Chromecast supports local streaming yet? That alone would be a no-cost solution since I already have one...

---

### Post by monkeybrain20122 on 2014-04-19
> Man I hope the inevitable Netflix/HTML5 future brings a better experience to Linux. 
Well but it is not plain html5, it has drm modules that don't work on Linux, so something like pipelight will still be necessary.

You asked how reliable pipelight is, I have been using pipelight for five months and it has worked very well and reliable on two of my computers (intel and Nvidia), I mean as smooth and reliable as watching videos on Youtube. Neither of them are high end. Now I am setting it up on an amd netbook for a friend, it doesn't work as well (machine is weak) but good enough after some tweaking (even fast action kung fu films play ok, though not on full screen) So I am quite confident to recommend it if you have not too out of date hadware. Next I will try getting netflix on my roommate's 8 year old hp laptop which I have installed lubuntu on.

Actually I am more interested in pipelight than netflix. I pay a monthly $8 just to play with pipelight, the selections on netflix are quite forgettable IMO. I watched only a few films from beginning to end and none of them are very good. I can find better films on Youtube, at least before they got reported and taken down. :) 

Now that XP is dead and a few friends are inquiring about Linux, pipelight helps a lot in converting these computers to *buntu as many of their owners watch netflix.

---

### Post by monkeybrain20122 on 2014-04-19
> **SeijiSensei said:**
> I got dumped to the System Requirements page when going simply to [www.netflix.com]("http://www.netflix.com"), but I discovered that if I go to [http://www.netflix.com/WiHome](http://www.netflix.com/WiHome), I can watch videos with pipelight installed.  I have [UAControl]("https://addons.mozilla.org/en-US/firefox/addon/uacontrol/") installed with this User-Agent string associated to Netflix: Mozilla/5.0 (Windows NT 6.1; rv:23.0) Gecko/20131011 Firefox/23.0.

I also told pipelight to [install the Windows version of Flash Player]("http://fds-team.de/cms/pipelight-installation.html#section_2_3").  Some places now check for Version 12 of Flash which will never be released for Linux.

Even if you don't actually need flash 12 and Windows flash you should still install it (without actually switching to it) beause of widedivne [http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html](http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html)  Installing pipelight-flash brings in widedevine which enables plain old flash 11.2 to decode certain drmed flash streams that even pepper-flash does not play (as long as flash version is not the issue)  However I would not recomend switching to pipelight-flash as the default because it is slower than native flash if both work (probably 99% of the time)and certain features are missing in pipelight-flash (e.g hardeware acceleration if you have the driver for it)

---

### Post by SeijiSensei on 2014-04-20
Well, I can't seem to get this arrangement of software to move in and out of full-screen mode correctly.  Using the Windows version of Flashplayer via pipelight, switching to full-screen displays a black screen.  Worse, I can only stop the Flash process by killing it from top or the command line.  I made the change recommended in the article you cited, copying /usr/share/pipelight/configs/pipelight-flash to ~/.config/pipelight and setting "linuxWindowlessMode = true".  

That article had incorrect instructions, though, since there is no "/usr/share/pipelight/pipelight," just the config subdirectory with a whole bunch of alternate configuration files.  I created a corresponding pipelight directory in .config and put the edited file under that.  Maybe it should just be a file called pipelight instead?  Most applications create a subdirectory under .config, so I assumed that is how pipelight works as well, but maybe that is wrong?

I don't need to watch Netflix in a browser as I much prefer my PS3 for that task.  So I'm probably going to dump Windows flash and just use ordinary Linux Flash 11 which works without a hitch.

Update: I reverted to Linux Flash by using:
```
sudo update-alternatives --remove mozilla-flashplugin /usr/lib/pipelight/libpipelight-flash.so
```
and now I again have no problems with full-screen mode.

Update 2: Even using the Linux plug-in, I can still watch Netflix if I start from [http://www.netflix.com/WiHome](http://www.netflix.com/WiHome) as I mentioned before.

---

### Post by monkeybrain20122 on 2014-04-20
That article is old, I just cited it for widedivine. This is the up to date one for the location of the config file [https://answers.launchpad.net/pipelight/+faq/2356](https://answers.launchpad.net/pipelight/+faq/2356)

You don't have to remove the pipelight alternative, to switch back and forth run
```
sudo update-alternatives --config mozilla-flashplugin
```
and choose the flash version (in kde there is a gui for switching called kalternatives) As I said I find it less smooth and almost never use it, but did test it on some sites and it works (some embedded flash video shows up as a blackbox, click the blackbox and the video loads. With native flash there is a little preview)

Also see this for linux windowsless mode
[https://launchpad.net/pipelight/+announcement/12364](https://launchpad.net/pipelight/+announcement/12364)
 Article also mentions that it is possible to install widedivine without installing pipelight flash now.

Not sure why pipelight flash doesn't work for you in full screen, may have something to do with hardware acceleration. You may find the info you need here
[https://answers.launchpad.net/pipelight](https://answers.launchpad.net/pipelight) The devs are very helpful and fast in answering questions, it is best to ask them if you encounter problems.
> 
Update 2: Even using the Linux plug-in, I can still watch Netflix if I start from [http://www.netflix.com/WiHome](http://www.netflix.com/WiHome) as I mentioned before.                 
I can go to the log in page or the main page (netflix.com), either way it works. I have done this on 3 machines (Ubuntu 13.10 on two and 14.04 on two, one machine already sold)

Edited: Just check again, indeed pipelight flash doesn't work in fullscreen for one machine with amd card plus open driver, on the intel machine it works fine. On both netflix works on fullscreen.

---

### Post by SeijiSensei on 2014-04-20
My full-screen problems were not Netflix-related.  I had them watching videos on other sites like [Crunchyroll](http://www.crunchyroll.com/) that have always displayed correctly with the native Linux flashplayer.  As I say, for what I need that option works for me.  I can also start from [www.netflix.com](www.netflix.com).

This machine has an ATI Radeon 6770M with the proprietary driver installed.

---

### Post by monkeybrain20122 on 2014-04-20
Ok, I fixed the pipelight-flash fullscreen problem on the AMD machine (HD6310 with open driver). Pipelight-flash has gpuacceleration enabled by default and this doesn't play well with AMD cards apparently
run
```
/usr/share/pipelight/scripts/configure-flash
```
then type "disable" followed by "abort"
and then restart firfox. Now pipelight-flash works on fullscreen as well. I doubt that I would need it but it is still nice that it works.

---

### Post by NTL2009 on 2014-04-26
Sorry if this is slightly off-topic (it appears to be a separate app that uses a FireFox window or something) , but I just followed the instructions here and it worked right off:

[http://itsfoss.com/netflix-ubuntu-1404-desktop-app/](http://itsfoss.com/netflix-ubuntu-1404-desktop-app/)

Basically - Install Pipelight:

```

sudo apt-add-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install pipelight-multi
sudo pipelight-plugin --enable silverlight

```

There will be two conditions to accept.

To install the Netflix desktop app, use the following command:


```
sudo apt-get install netflix-desktop
```


So netflix showed up as an app in the App Menu / Multimedia – I clicked, it went through some setup stuff with the WINE component installs. It offered to install MONO and GECKO, but also said best to get from my own repositories, so I just skipped them.


The Netflix App opened a fullscreen Firefox window and ran! It did do a bunch of WINE configuration on the first start. But it doesn't run in my regular FF browser, so I guess this desktop app has configured that FireFox window to work with this? So this maybe skips some of the issues people have with the user agent?  All I can say is it worked for me with no futzing.

-NTL2009

---

### Post by monkeybrain20122 on 2014-04-26
If you have pipelight you go to netflix on your regular browser, the netflix app is basically a Windows version of FF run in wine, you don't need that any more and it has stopped developing because the developers have gone to pipelight. Also you should install pipelight following instructions from its own webpage. Many online tutorials by random people are outdated.
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

---

### Post by compholio on 2014-06-04
> **monkeybrain20122 said:**
> If you have pipelight you go to netflix on your regular browser, the netflix app is basically a Windows version of FF run in wine, you don't need that any more and it has stopped developing because the developers have gone to pipelight. Also you should install pipelight following instructions from its own webpage. Many online tutorials by random people are outdated.
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)

The netflix-desktop app has been updated several times to include a variety of "behind the scenes" features.  I don't have a lot of time to work on it, but it does integrate with pipelight and use the Linux Firefox when they are installed.  When run with the Linux Firefox it creates its own browser session, so it does not interfere with your normal browser.  In addition, this allows us to automatically configure it with the appropriate UA string (and a variety of other tweaks).  We will likely be doing some more significant updates in the near future and rebranding netflix-desktop due to Chrome dropping NPAPI support.

---

