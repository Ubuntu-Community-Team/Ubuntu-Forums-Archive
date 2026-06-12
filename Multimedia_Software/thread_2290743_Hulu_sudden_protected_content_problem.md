---
title: "Hulu sudden protected content problem"
date: 2015-08-14
forum: Multimedia Software
---

### Post by efflandt on 2015-08-14
I have been using Firefox with flash for years with Hulu without any issues. And since installing 64-bit Ubuntu 14.04 last January I have been using Google Chrome for Netflix without any issues. Although, since Firefox temporarily blocked flash due to security issues, I was also using Chrome for Hulu.

I was going to check out a series on Hulu Plus from Fox called Empire, but Chrome came up with an error "There was a problem playing this protected content. (Error Code: 3336)". It also said that my browser did not support protected content and suggested using Mozilla Firefox. But Firefox 40.0 would not play it either, it would play the Fox intro, a commercial, then just a black screen (no error message) and the play button became grayed out. I could see tiny thumbnails of various scenes if I put the cursor on the progress bar at the bottom, but none of the videos for that show would play, not even the short clips. Hulu Help had nothing specific about error code 3336, and none of the suggestions about protected content or black screen helped.

It is not an issue of not being allowed to view that content. From Hulu app on my Android phone (Linux based) I can directly stream Empire episodes to a Chromecast device (also Linux based) and play it on my HDTV. It is just that I would rather use my 2.1 speaker system with subwoofer than the TV speakers.

Would anyone know what method is used for "protected content" of just that one show on Hulu (Empire from Fox) and if there is a way to view that in Linux without using wine? The only thing I ever used wine for was the version that came with Netflix Desktop back in 12.04, which would throw some errors about not finding a suitable gecko browser, but would usually still work. There used to be a Hulu Desktop for Linux (which did not use wine), but that was just an experiment by some of their techs that I think was discontinued over a year ago.

PS: Changed subject because it affects more than just one show.

---

### Post by mT5uaEobL3g4 on 2015-08-14
The problem is that Hulu has changed the way that they deliver video content in the last 24 or so hours. I made no changes to my HTPC set-up, Chrome was not logging into my Google user account on that machine, and I got the error on all my Linux machines. The suggestion for using Firefox worked for me (very poorly, I might add). However, my HTPC is set up to use the PPA for HAL (which apparently Amazon Prime requires for playback). That may be why Firefox did not work, at all, for you. 

I raised Holy H3LL with Hulu support over the issue, and got a stock response back (flush Flash cache, power cycle your modem, etc. etc. ... pedestrian garbage for Windows users). Their support is not very helpful. I would recommend threatening to leave their service for Netflix over the issue and drumming up some support in various Linux forums... Maybe the negative publicity will get the attention of their lack-luster web developers...

---

### Post by George_Montgomery on 2015-08-14
Same issue for over a week with all content on Hulu.  There was a twitter post by Hulu support that said their techs were looking into the issue.  Everything else works great, iPad app, Chromebook...just not Linux.

---

### Post by mT5uaEobL3g4 on 2015-08-15
Android works too... One thing to note is that I use the version of Chrome from Google, not from the repositories... It shouldn't matter though. A latest version shouldn't throw the error... Very irritating...

edit:
Oh,... BTW,... Chromebook _***is***_ Linux... I think they base their code on Gentoo, if I'm not mistaken...

---

### Post by efflandt on 2015-08-15
I was thinking that it was just that one show, but I tried another show that is on public ABC television and it does not play either (Error Code: 3336 in Google Chrome and black screen with grayed out play button in Firefox). So maybe whatever Hulu changed disrupted all videos for Linux web browsers.

PS: Netflix still works fine with Google Chrome using HTML5 (I do not have wine or MS Silverlight installed).

---

### Post by JaseP on 2015-08-15
It's not the show... It's Chrome within Linux (maybe just K/X/Ubuntu?!?!)... My problems are under Kubuntu & Xubuntu 12.04,... I haven't tried my Kubuntu 14.04 machine, yet, to verify it...

Edit/Post-Script:
Logged on to my Kubuntu 14.04 machine,... The 3336 error is still present. So, this isn't some isolated Hulu/Ubuntu 12.04 incompatibility,... This is across the board... I'd be interested in seeing if Windows/Mac users are effected...

---

### Post by JaseP on 2015-08-15
Please note: The user, mT5uaEobL3g4, above,... was ***_me_***... Had a slight Ubuntu One issue going on, that one of the Moderators fixed...

---

### Post by kansasnoob on 2015-08-15
Same issue:

[http://ubuntuforums.org/showthread.php?t=2290589](http://ubuntuforums.org/showthread.php?t=2290589)

I'm wondering about trying the Windows version of Firefox in Wine ............. but I've never done that.

Or maybe [the hal hack]("http://www.howtogeek.com/204319/how-to-watch-amazon-instant-video-on-linux/") like is used for Amazon Prime?

I'm going to try and talk to them tomorrow but I'm nearly deaf so their call-back system for support is not_so_good_for_me. At least I can let them know there are many of us effected!

---

### Post by kansasnoob on 2015-08-15
More people effected:

[https://www.reddit.com/r/Hulu/comments/3gaap4/hulu_freezing_after_returning_from_commercial/](https://www.reddit.com/r/Hulu/comments/3gaap4/hulu_freezing_after_returning_from_commercial/)

That started 6 days ago and the latest comment is from 1 day ago. This started for me the morning of the 13th, although I probably hadn't tried Hulu since mid-morning on the 12th and it was still working fine then.

---

### Post by JaseP on 2015-08-15
> **kansasnoob said:**
> Same issue:

[http://ubuntuforums.org/showthread.php?t=2290589](http://ubuntuforums.org/showthread.php?t=2290589)

I'm wondering about trying the Windows version of Firefox in Wine ............. but I've never done that.

Or maybe [the hal hack]("http://www.howtogeek.com/204319/how-to-watch-amazon-instant-video-on-linux/") like is used for Amazon Prime?

I'm going to try and talk to them tomorrow but I'm nearly deaf so their call-back system for support is not_so_good_for_me. At least I can let them know there are many of us effected!

I had the **Hal** hack set up for Amazon Prime, and Hulu works, passably, in Firefox. Playback is lousy though (more stutters, limited rewind capability, unwarranted restarts needed to play back content). Chrome is a bust,... across the board, on all my machines. The Hal hack is as simple as adding a PPA to your repositories... Wine would be more of a problem (for you to set up). 

The bottom line is that Hulu did something in the last few days to alter the playback. My household had watched something last night, on Hulu, without issue, on Chrome. Tonight,... error 3336. This is likely a DRM thing. Some over-zealous web developer probably added JavaScript code to Hulu existing code base to check for some additional thing that only exists in Firefox (or Windows Internet Explorer),...

I wouldn't be beyond believing that content providers wanted to punish Google, and so insisted that Hulu use the same code that Amazon Prime was using. It's always "follow the money" with them...

---

### Post by kansasnoob on 2015-08-15
Oddly I installed the latest Linux Mint Mate this AM and Hulu is working well there in Firefox both before and after updates.

I've not yet tried importing my customized .mozilla to /home. I think I'll sync this Firefox profile first and see what breaks, if nothing breaks then I'll try importing my custom .mozilla and see if I can break things.

No idea what Mint could be doing differently :confused:

---

### Post by Dennis N on 2015-08-15
> **kansasnoob said:**
> No idea what Mint could be doing differently :confused:

For one thing, Linux Mint MATE has HAL installed by default, while Ubuntu does not. That could be the difference. There is a PPA for HAL on Ubuntu and flavors, to provide it. I have to use a system with HAL to use my cable company's video anytime over internet service. Without it, it doesn't play.

---

### Post by kansasnoob on 2015-08-15
> **Dennis N said:**
> For one thing, Linux Mint MATE has HAL installed by default, while Ubuntu does not. That could be the difference. There is a PPA for HAL on Ubuntu and flavors, to provide it. I have to use a system with HAL to use my cable company's video anytime over internet service. Without it, it doesn't play.

No, it's not:

```
lance@lance-AMD-desktop ~ $ lsb_release -a
No LSB modules are available.
Distributor ID:	LinuxMint
Description:	Linux Mint 17.2 Rafaela
Release:	17.2
Codename:	rafaela
lance@lance-AMD-desktop ~ $ apt-cache policy hal
hal:
  Installed: (none)
  Candidate: (none)
  Version table:

```

But maybe Clem found a hack to workaround the hardware abstraction layer??????

BTW the white screen issue I'd had refreshing Hulu on Mint live yesterday turned out to be a nouveau thing with this particular nVidia chip. That issue disappeared after I installed Mint to a spare partition on the same box and installed the nVidia driver.

I'm still playing and I'll share whatever I find out.

---

### Post by Dennis N on 2015-08-15
Well, that's interesting. I got HAL into my head from reading Clem's blog a while back. In particular, this part:
>  Many websites rely on Flash to play videos and use DRM to restrict the content to certain audiences. TV channels in particular are more and more numerous to offer REPLAY and VOD services for free but serve them with DRM.
The problem is that DRM support is not available in Linux versions of Flash (blame Adobe and Google all you want, it doesn't look like it's likely to change).
For a majority of websites, adding HAL support (required for DRM) won't help (_and it's already done in LMDE 2 Betsy and in Linux Mint since version 17.2 Rafaela_).

Source:  [http://community.linuxmint.com/tutorial/view/2028](http://community.linuxmint.com/tutorial/view/2028)

What does he mean here about adding HAL support? The REPLAY and VOD subscriber content work for us in Linux Mint MATE (I assumed it because of was the HAL), while standard Xubuntu wouldn't play them. Then I found Xubuntu + HAL installed also plays this cable subscriber internet content.

---

### Post by JaseP on 2015-08-15
Installing the mjblenner PPA is definitely what fixes it for Firefox (at least for X/Kubuntu 12.04). Without the "dummy" Hal package, the commercials will run, but the shows won't. Here's a nice article on it:
[http://www.howtogeek.com/204319/how-to-watch-amazon-instant-video-on-linux/](http://www.howtogeek.com/204319/how-to-watch-amazon-instant-video-on-linux/)
... However, this might not work forever. Flash is being phased out. Will that mean Hulu will switch to HTML5?!?! ... One can hope...

One possible solution (don't know, haven't tried it yet) might be to use ARC Welder in Chrome to try to install the Android Hulu App. Again, I haven't tried it yet.

Another possibility would be an Android virtual machine. However, your hardware has to be able to support virtualization.

---

### Post by kansasnoob on 2015-08-15
> **JaseP said:**
> Installing the mjblenner PPA is definitely what fixes it for Firefox (at least for X/Kubuntu 12.04). Without the "dummy" Hal package, the commercials will run, but the shows won't. Here's a nice article on it:
[http://www.howtogeek.com/204319/how-to-watch-amazon-instant-video-on-linux/](http://www.howtogeek.com/204319/how-to-watch-amazon-instant-video-on-linux/)
... However, this might not work forever. Flash is being phased out. Will that mean Hulu will switch to HTML5?!?! ... One can hope...

One possible solution (don't know, haven't tried it yet) might be to use ARC Welder in Chrome to try to install the Android Hulu App. Again, I haven't tried it yet.

Another possibility would be an Android virtual machine. However, your hardware has to be able to support virtualization.

Yep, that seems to be the case:

[http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045](http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045)

---

### Post by kansasnoob on 2015-08-15
> **Dennis N said:**
> Well, that's interesting. I got HAL into my head from reading Clem's blog a while back. In particular, this part:

Source:  [http://community.linuxmint.com/tutorial/view/2028](http://community.linuxmint.com/tutorial/view/2028)

What does he mean here about adding HAL support? The REPLAY and VOD subscriber content work for us in Linux Mint MATE (I assumed it because of was the HAL), while standard Xubuntu wouldn't play them. Then I found Xubuntu + HAL installed plays this cable subscriber internet content, which has been great.

I thought the same thing. It would be interesting to know how Clem got that to work without hal.

---

### Post by Robert_P_Ivie on 2015-08-15
I'm running chrome and experiencing the same issue.

I have tried a number of the recommended fixes, but I have found that the best performance is to completely bypass hulu.com altogether.

---

### Post by kansasnoob on 2015-08-15
> **Robert_P_Ivie said:**
> I'm running chrome and experiencing the same issue.

I have tried a number of the recommended fixes, but I have found that the best performance is to completely bypass hulu.com altogether.

Not using Hulu, or anything that doesn't work easily, is always an option. But it's a rather extreme option. Change is constant so we work our way around obstacles as they present themselves :D

---

### Post by SeijiSensei on 2015-08-16
I just installed [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") and configured it to use the Windows version of Adobe FlashPlayer.  I picked some random show at Hulu, and it started running.  It showed the opening commercial then launched into the program.  I didn't have to change my UserAgent string either, as I need to do to watch Netflix via pipelight+Silverlight.

---

### Post by JaseP on 2015-08-16
Hulu contacted me this morning. They are looking into the matter. I gave them all the relevant & requested information (OS, Chrome version, screenshot of the error, known work-arounds, etc.). I let them know that it wasn't an isolated incident & that all Ubuntu users were affected.

---

### Post by kansasnoob on 2015-08-16
> **SeijiSensei said:**
> I just installed [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") and configured it to use the Windows version of Adobe FlashPlayer.  I picked some random show at Hulu, and it started running.  It showed the opening commercial then launched into the program.  I didn't have to change my UserAgent string either, as I need to do to watch Netflix via pipelight+Silverlight.

Cool - it's good to know there is more than one option :D

---

### Post by kansasnoob on 2015-08-16
> **JaseP said:**
> Hulu contacted me this morning. They are looking into the matter. I gave them all the relevant & requested information (OS, Chrome version, screenshot of the error, known work-arounds, etc.). I let them know that it wasn't an isolated incident & that all Ubuntu users were affected.

I also sent them an email. Has anyone tried the "hal" hack in Chrome?

---

### Post by JaseP on 2015-08-16
The Hal hack doesn't affect Chrome, as Chrome uses its own flash player (not the stock Adobe player). It's the Abobe Flash player that looks for the Hardware Abstraction Layer. The problem with Chrome is that their player is not giving Hulu the response that it wants, in terms of DRM. User strings wouldn't affect this either. This has to do with the plug-in. Changes to the user string are pretty transparent, anyway. A little JavaScript is all that is necessary to correctly identify the browser and OS, bypassing the user string.

---

### Post by kansasnoob on 2015-08-16
> **JaseP said:**
> The Hal hack doesn't affect Chrome, as Chrome uses its own flash player (not the stock Adobe player). It's the Abobe Flash player that looks for the Hardware Abstraction Layer. The problem with Chrome is that their player is not giving Hulu the response that it wants, in terms of DRM. User strings wouldn't affect this either. This has to do with the plug-in. Changes to the user string are pretty transparent, anyway. A little JavaScript is all that is necessary to correctly identify the browser and OS, bypassing the user string.

Oddly I had Chrome working earlier - I thought due to adding hal - but now it won't work again. So you're obviously right.

---

### Post by JaseP on 2015-08-16
I've confirmed with people on LinuxQuestions.org that it isn't just Ubuntu that's affected. It's also Debian. It appears our "friends" at Hulu decided that they had to start implementing DRM on the playback. Unfortunately, the Linux Chrome browser builds do not use the same Pepper Flash plug-in that they supply to the (working) ChromeOS. So,... All Chrome browsers on Linux should be affected. 

For the time being, we have only one option (for staying with Ubuntu Linux for playback)... Install the Hal tweak and run Hulu in Firefox (yech!). Hulu ***might*** do some form of work-around on their end (not holding my breath), Google might update the Chrome browser with the same Pepper Flash client that the ChromeOS people enjoy (not holding my breath for that either),... Or we have to figure out a way to side-load the Hulu Android client onto the Chrome ARC Welder plugin for running Android apps in Chrome (which is very hit-n-miss). Other than that, consider getting a ChromeCast, Android TV dongle/set-top-box or look into running a VM with Android or Windows,... Just to play back Hulu content...

Note: Adobe Flash player security updates (but not feature updates) for Linux will go the way of the Dodo in 2017... So, the hal thing should work, at least until then.

---

### Post by kansasnoob on 2015-08-16
I guess there are actually three workarounds; (1) [the "hal hack"]("http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045"), (2) [pipelight]("http://ubuntuforums.org/showthread.php?t=2290589&page=4&p=13345702#post13345702"), and (3) [wine]("http://community.linuxmint.com/tutorial/view/2028"). Since #1 worked well enough for me I'm happy but I can certainly see how this would tick off Chrome users.

---

### Post by defaria on 2015-08-17
> **JaseP said:**
> For the time being, we have only one option (for staying with Ubuntu Linux for playback)... Install the Hal tweak and run Hulu in Firefox (yech!).

Considering my normal mode of operation is to play Hulu (free - I'm not paying this jackasses) videos in a tab then cast the tab to my Chromecast, Firefox is not an acceptable workaround because I cannot cast a tab in Firefox! This blows chunks. Somebody should just write a Flash video -> HTML 5 video streamer...

---

### Post by efflandt on 2015-08-17
I ended up apparently using mjblenner's ppa-hal from a Ask Ubuntu post that I cannot find right now. After removing the contents of ~/.adobe/Flash_Player/ Hulu still did not work in Firefox until I rebooted. But now it appears to work fine.

I don't think Hulu will work with Google Chrome now (other than through Chromecast) since Chrome no longer supports NPAPI (Netscape plugins). Therefore, if you disable Pepper Flash (which does not do protected content) it does not see your regular system flash and you end up with no Flash in Chrome.

So I guess for the present time it will be Firefox with hal (or Chromecast) for Hulu and Google Chrome (or Chromecast) for Netflix.

---

### Post by defaria on 2015-08-18
I don't have a problem with Firefox playing Hulu videos, provided I use the popout player ([IMG]http://static.huluim.com/images/icon-popout-hover.gif?1309930979[/IMG]). I have a problem with Firefox not being able to cast to my Chromecast. My real problem is that I can't use the Chrome browser, which is my normal browser, to play Hulu videos in Chrome so I can cast the tab.

---

### Post by monkeybrain20122 on 2015-08-18
> **kansasnoob said:**
> I guess there are actually three workarounds; (1) [the "hal hack"]("http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045"), (2) [pipelight]("http://ubuntuforums.org/showthread.php?t=2290589&p=13339279#post13339279"), and (3) [wine]("http://community.linuxmint.com/tutorial/view/2028"). Since #1 worked well enough for me I'm happy but I can certainly see how this would tick off Chrome users.

Well for Chrome users there may be a way. Basically extract libepflashplayer.so from a ChromeOS recovery image and swap out the one bundled in Chrome The catch is of course that an update will wipe it out.

See here [https://github.com/i-rinat/freshplayerplugin/issues/13](https://github.com/i-rinat/freshplayerplugin/issues/13) It works for the flashplayerplugin for FF so I think it may work for Chrome proper as well if you replace /opt/google/chrome/PepperFlash/libpepflashplayer.so with the flashplayer from the ChromeOS image.

 I have tried it (with freshplayerplugin on FF) on Adobe's test page (I have no subscription to any paid streaming except Netflix but have cancelled that too) Unfortunately I can't remember how I mounted the .bin file (the ChromeOS image) to extract flash except that it involved some work.

P.S pipelight is WINE. :) A third way for FF would be same as above, use pepperflash from ChromeOS image and then freshplayerplugin as a wrapper.

---

### Post by defaria on 2015-08-18
Perhaps some good news, at least on the Google side. My Google Chrome Beta browser at work on Windows is Version 46.0.2478.0 dev-m (64-bit). On this browser Hulu works. Additionally there is a thing in Settings called Protected Content and "Allow identifiers for protected content". These settings are missing from my Ubuntu 14.04 64 bit machine at home which has Chrome Version 45.x. Both are on Chrome Beta but it seems that while it used to be that the Linux arch would always be out in front, version number-wise, now it's Windows who seems to be the leading edge in the beta channel.

---

### Post by kansasnoob on 2015-08-18
> **defaria said:**
> Perhaps some good news, at least on the Google side. My Google Chrome Beta browser at work on Windows is Version 46.0.2478.0 dev-m (64-bit). On this browser Hulu works. Additionally there is a thing in Settings called Protected Content and "Allow identifiers for protected content". These settings are missing from my Ubuntu 14.04 64 bit machine at home which has Chrome Version 45.x. Both are on Chrome Beta but it seems that while it used to be that the Linux arch would always be out in front, version number-wise, now it's Windows who seems to be the leading edge in the beta channel.

Cool I may have time to try 46.0.2478.0-1 tonight:

[http://www.ubuntuupdates.org/package/google_chrome/stable/main/base/google-chrome-unstable](http://www.ubuntuupdates.org/package/google_chrome/stable/main/base/google-chrome-unstable)

Of course it's unstable ...................... but we don't need no stinking stable packages :lolflag:

---

### Post by monkeybrain20122 on 2015-08-18
> **defaria said:**
> Perhaps some good news, at least on the Google side. My Google Chrome Beta browser at work on Windows is Version 46.0.2478.0 dev-m (64-bit). On this browser Hulu works. Additionally there is a thing in Settings called Protected Content and "Allow identifiers for protected content". These settings are missing from my Ubuntu 14.04 64 bit machine at home which has Chrome Version 45.x. Both are on Chrome Beta but it seems that while it used to be that the Linux arch would always be out in front, version number-wise, now it's Windows who seems to be the leading edge in the beta channel.

It always works on Windows. Pepperflash on Linux is intentionally crippled for licensing reasons I think. Protected contents work on Windows Chrome (also OSX) but not on Linux (except Chromebook, see my post #32) for the same reason that NPAPI flash works on protected contents on Windows but not on Linux (pipelight flash is just NPAPI flashplugin from Windows working through Wine) 

It seems that the issue is not technical but the OS distributor has to pay some kind of licensing fee for this feature to work and MS, Apple and Google have all paid (or actually owning the license). So, unless Canonical pays up,--then there will be special Chrome built just for Ubuntu,-- Chrome is not going to work on sites like Hulu out of the box. I don't think Canonical should pay though because it doesn't make any money off desktop users other than donations.

Sorry for the bad news. :)

---

### Post by mc4man on 2015-08-18
> **monkeybrain20122 said:**
> Well for Chrome users there may be a way. Basically extract libepflashplayer.so from a ChromeOS recovery image and swap out the one bundled in Chrome The catch is of course that an update will wipe it out.
...Unfortunately I can't remember how I mounted the .bin file 

It's all pretty straightforward but I wouldn't think that recovery images would have the latest .so, here in 2 images the highest was 18.0.0.209
(wonder if one can grab from an updated chromebook, will ck. tomorrow - edit, no, called my son he says there is no access to the 'system' files or any files..

---

### Post by zhanai on 2015-08-19
I thought installing HAL had solved all my problems with flash. After upgrading from Ubuntu 14.04 to 15.04 I could not watch content on Hulu. I asked Hulu for answers and they gave me the stock answers which I knew already would not work. Then, they suggested installing HAL. I found an Ubuntu repository called "zombie HAL" which some thoughtful person put up because HAL was no longer used by Ubuntu after version 13.04. Now Hulu works on mozilla browsers but not Opera with a Chrome engine.

---

### Post by TheFu on 2015-08-20
I looked up the **hulu 3336 error code** and was directed to a macromedia site to clear all objects from the flash cache. That worked for me.  I suspect it is just easiest to ```
rm -rf ~/.macromedia ~/.adobe
``` and be done. That is part of my nightly "pre-backup" script.

Sorry, I don't recall if that was for windows or Linux, I tend to use Linux more, but if there is an issue, a quick test on Windows often solves it. Then a few days later, back at Hulu and everything works fine under Linux again.

Hulu will be one of the last Flash holdouts until HTML5 video can support their business model of inserting ads, mid-stream, AND counting how many views actually happened for each ad.  For example, the network guys here block ad-network subnets heavily as a security measure, but hulu ad servers seem to be impacted about 40% of the time. Hulu knows that we don't see some of their ads, so they tee up more and show an "unblock ad blocking software" page.  Last time I checked, a 42 min sitcom on Hulu took over an hour to complete due to the ad blocking.  I don't blame hulu or the network guys. It is, what it is.  Of course, we only watch hulu during non-business hours while we are wait on other things to complete. ;) That's my story.

---

### Post by santosomar on 2015-08-22
FYI: Chrome unstable does not solve the issue. I am using Version 46.0.2486.0 dev (64-bit)

---

### Post by santosomar on 2015-08-22
I was able to fix it in Firefox using the HAL hack by adding this repo and then installing hack.

```
sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update && sudo apt-get install hal
```

The Chrome still a problem for me even with Chrome Beta (unstable) Version 46.0.2486.0 dev (64-bit)

Using firefox for now.. :-/

---

### Post by singularity4 on 2015-08-27
I just tried the HAL hack, and I can now play content again in Firefox. Still getting the error code in Chrome though.

---

### Post by cF6RHpL on 2015-09-27
i have used hulu since it's inception... this is the icing on the cake however.  They can get bent, I'm not running some <snip> windows hack to watch flash videos. Tell them "Suck my <snip>"  and drop your subscriptions.

---

### Post by kansasnoob on 2015-09-27
> **cF6RHpL said:**
> i have used hulu since it's inception... this is the icing on the cake however.  They can get bent, I'm not running some <snip> windows hack to watch flash videos. Tell them "Suck my <snip>"  and drop your subscriptions.

You don't have to use any "windows hack". It works OK with Firefox + hal:

[http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045](http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045)

Asking questions is generally more apt to garner answers than just ranting :)

---

### Post by defaria on 2015-10-18
> **TheFu said:**
> I looked up the **hulu 3336 error code** and was directed to a macromedia site to clear all objects from the flash cache. That worked for me.  I suspect it is just easiest to ```
rm -rf ~/.macromedia ~/.adobe
``` and be done. That is part of my nightly "pre-backup" script.

Sorry, I don't recall if that was for windows or Linux, I tend to use Linux more, but if there is an issue, a quick test on Windows often solves it. Then a few days later, back at Hulu and everything works fine under Linux again.

Hulu will be one of the last Flash holdouts until HTML5 video can support their business model of inserting ads, mid-stream, AND counting how many views actually happened for each ad.  For example, the network guys here block ad-network subnets heavily as a security measure, but hulu ad servers seem to be impacted about 40% of the time. Hulu knows that we don't see some of their ads, so they tee up more and show an "unblock ad blocking software" page.  Last time I checked, a 42 min sitcom on Hulu took over an hour to complete due to the ad blocking.  I don't blame hulu or the network guys. It is, what it is.  Of course, we only watch hulu during non-business hours while we are wait on other things to complete. ;) That's my story.

Sorry but this doesn't do anything.

> **kansasnoob said:**
> You don't have to use any "windows hack". It works OK with Firefox + hal:

[http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045](http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045)

Asking questions is generally more apt to garner answers than just ranting :)

The problem for me is that Firefox cannot cast a tab! I don't want to watch Hulu on my computer - I want to watch it on my large screen TV!

> **santosomar said:**
> I was able to fix it in Firefox using the HAL hack by adding this repo and then installing hack.

```
sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update && sudo apt-get install hal
```

The Chrome still a problem for me even with Chrome Beta (unstable) Version 46.0.2486.0 dev (64-bit)

Using firefox for now.. :-/

This is useless as you can't cast a firefox tab.

---

### Post by will82 on 2015-11-10
Also found this issue. Are there any fixes out yet?

---

### Post by kansasnoob on 2015-11-10
> **will82 said:**
> Also found this issue. Are there any fixes out yet?

The only ways I've found are linked to here:

[http://ubuntuforums.org/showthread.php?t=2290589](http://ubuntuforums.org/showthread.php?t=2290589)

I just use hal in Firefox.

---

### Post by aaron120 on 2015-11-23
**Hulu not working in Linux**?
 Don’t feel alone. America based streaming content provider, [Hulu]("http://www.hulu.com/") has  changed their video playback system which now employs Adobe Flash DRM  technology. This completely messed up the things for Linux users because  Adobe doesn’t support Flash on Linux for some years and Adobe Flash DRM  requires HAL which is also removed from major Linux systems for years  now. This requirement for HAL leaves Hulu unplayable. If you try to [use Hulu in Ubuntu]("http://itsfoss.com/install-hulu-desktop-app-ubuntu-linux/") or Linux Mint, you would get an error like: **“There was a problem playing this protected content. (Error Code: 2203)”**
 So, is there no way you could watch Hulu  videos in Linux. Fortunately, there is and we are going to see how can  we fix protected content issue with Hulu and Linux. [h=2]Watch Hulu on Ubuntu and Linux Mint[/h]  As explained earlier, we need HAL to be  installed explicitly in Ubuntu. Thanks to this PPA, you can easily  install HAL in Ubuntu and Linux Mint. Open a terminal and use the following commands: sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update
sudo apt-get install hal Note that even with HAL installed, Hulu will not work in Chrome or Chromium. The only way possible is to use Mozilla Firefox. Once you have installed HAL, just  refresh the browser window. No need of a restart or log out. It will  start working as previously. 

Credits goes to this Site: [http://itsfoss.com/watch-hulu-ubuntu-linux/](http://itsfoss.com/watch-hulu-ubuntu-linux/)

---

### Post by bathynomusBLUE on 2015-11-29
Frustrated. I sent this to Hulu today.

[FONT=arial]> Please send this feedback to management. [/FONT][FONT=arial]I am very disappointed that your company has still not resolved this problem with Google Chrome on Linux. I do not wish to use Flash, as it is highly insecure, no longer officially supported on Linux and even Adobe, Mozilla and Google have recommended to disable it several times a year due to security exploits. I was so excited to hear that your company now has a commercial-free option. However, you are still using Flash and not the newer HTML5. [/FONT][FONT=arial]My only options appear to be to use HAL with insecure, unsupported and outdated Flash on Firefox. Or I continue to stay with Netflix, which works in Chrome for Linux and uses the more secure and better performance of HTML5.[/FONT]

[FONT=arial]Error:[/FONT]
[FONT=arial]There was a problem playing this protected content. (Error Code: 3336) Your browser does not support protected content playback. Please reload the page in another browser. We'd recommend trying Mozilla Firefox ( [www.mozilla.org/en-US]("http://www.mozilla.org/en-US") )[/FONT]

---

### Post by kansasnoob on 2015-11-29
> use HAL with insecure, unsupported and outdated Flash on Firefox

There is nothing "unsupported" or "outdated" about flash in Ubuntu ATM if installed properly:

```
lance@lance-desktop:~$ apt-cache policy flashplugin-installer
flashplugin-installer:
  Installed: 11.2.202.548ubuntu0.14.04.1
  Candidate: 11.2.202.548ubuntu0.14.04.1
  Version table:
 *** 11.2.202.548ubuntu0.14.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse i386 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse i386 Packages
        100 /var/lib/dpkg/status
     11.2.202.350ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse i386 Packages

```

BTW 'hal' is also required to view Amazon content. It's not all that hard to Use Chrome or Chromium to view content from one source while using Firefox w/hal to view content from another. The sky is not falling ;)

---

### Post by kansasnoob on 2015-11-29
Just thought to add - Crackle now refuses to play content with the Linux version of flash, but it plays OK in Chrome.

---

### Post by bathynomusBLUE on 2015-11-29
> **kansasnoob said:**
> There is nothing "unsupported" or "outdated" about flash in Ubuntu ATM if installed properly:

Perhaps, I am misinformed. My current Google searches show that Flash on Linux is not supported by Adobe. Anyone? Clarification?

---

### Post by kansasnoob on 2015-11-29
We get security updates until some time in 2017:

[http://www.dedoimedo.com/computers/flash-linux-future.html](http://www.dedoimedo.com/computers/flash-linux-future.html)

After that we'll see what happens. In the meanwhile there are at least three alternatives:

[http://ubuntuforums.org/showthread.php?t=2290589](http://ubuntuforums.org/showthread.php?t=2290589)

---

### Post by bathynomusBLUE on 2015-11-30
> **kansasnoob said:**
> I guess there are actually three workarounds; (1) [the "hal hack"]("http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045"), (2) [pipelight]("http://ubuntuforums.org/showthread.php?t=2290589&page=4&p=13345702#post13345702"), and (3) [wine]("http://community.linuxmint.com/tutorial/view/2028"). Since #1 worked well enough for me I'm happy but I can certainly see how this would tick off Chrome users.

Does anyone notice any performance difference between the 1) [the "hal hack"]("http://ubuntuforums.org/showthread.php?t=2290589&p=13339045#post13339045") Vs (2) [pipelight]("http://ubuntuforums.org/showthread.php?t=2290589&page=4&p=13345702#post13345702")? I did both and the hal method seems to have smoother playback. With pipelight, the video didn't seem as smooth at certain times. Xubuntu 15.04

I also have a Debian Jessie 8.2 box. Could I use the same hal ppa settings or would I need to do something different so that it doesn't break my stuff?

---

### Post by kansasnoob on 2015-11-30
> I also have a Debian Jessie 8.2 box. Could I use the same hal ppa settings or would I need to do something different so that it doesn't break my stuff? 

No idea. Personally if I wanted to try those packages in Debian I'd download the needed dot-debs and use dpkg to install them rather than use the whole PPA. Or maybe ask at Debian forums? They may have found an even smarter way to get it working.

---

### Post by T.J. on 2015-12-02
IMHO It is best to compile [https://github.com/cshorler/hal-flash](https://github.com/cshorler/hal-flash) for yourself.  I would also advise that you download a copy of Flash for Linux while you can.  Once Firefox no longer supports Netscape plugins, you can be sure the plugin is going to disappear.   Hulu does not support EME, so that means that after Firefox depreciates Flash, you will no longer be able to watch Hulu at all without using Windows or a hack like Pipelight.

---

### Post by deadflowr on 2016-04-21
Bumping this to say hulu now seems works on Chrome again.

it seems to now use html5 for the video streaming 
and flash for the ads.

Or at least that is how it seems.

Perhaps other will try it and see.

[s]My only problem has been full screen is not full screen, but the quick workaround is to press f11 when in fullscreen to get actual full screen.
Esc or f11 to exit fullscreen[/s]
Seems an update fixed my fullscreen issues

[Thanks to oldos2er]("http://ubuntuforums.org/showthread.php?t=2320725&page=2&p=13472809#post13472809") for giving me the idea revisit this issue.

fwiw

---

