---
title: "Screen tearing"
date: 2008-07-01
forum: Multimedia Software
---

### Post by Bosconian on 2008-07-01
I have tried playing various videos in Ubuntu 8.04 but every single one suffers from really bad horizontal screen tearing. If I reboot into XP, the same video plays perfectly.

The same happens with BBC iPlayer.

Does anyone have a solution for this?

---

### Post by xc3RnbFO8P on 2008-07-01
Maybe this:
[http://ubuntuforums.org/showthread.php?t=705781]("http://ubuntuforums.org/showthread.php?t=705781")

---

### Post by Bosconian on 2008-07-01
Thanks but that doesn't make any difference.

---

### Post by xc3RnbFO8P on 2008-07-01
Here is another one:
[http://xbmc.org/forum/showthread.php?t=34045&page=2]("http://xbmc.org/forum/showthread.php?t=34045&page=2")

---

### Post by feenicks on 2008-07-01
I had screen tearing on my old video card until I turned off all desktop effects.  Now I am using an Nvidia 7600 GS and can run the basic effects without notable tearing.  If it distracts me I turn it off when watching video.  Just try turning off the effects and see if it clears up.  I'm pretty sure you just don't have the graphics processing power to run that and a video.

---

### Post by Bosconian on 2008-07-02
> **feenicks said:**
> I had screen tearing on my old video card until I turned off all desktop effects.  Now I am using an Nvidia 7600 GS and can run the basic effects without notable tearing.  If it distracts me I turn it off when watching video.  Just try turning off the effects and see if it clears up.  I'm pretty sure you just don't have the graphics processing power to run that and a video.


Turned off all effects and BBC iPlayer is no different at all. Terrible screen tearing. In XP, iPlayer plays flawlessly and looks a lot better. Ubuntu with no desktop effects looks primitive in comparison.

---

### Post by markbuntu on 2008-07-02
First of all, what video card are you using? 

There are fixes but most of them are card manufacturer specific.

---

### Post by Melcar on 2008-07-02
What card/drivers are you using?  I know there is screen tearing with fglrx.  Don't know if it's the same with the nvidia driver.

---

### Post by markbuntu on 2008-07-02
No, it is not. Screen tearing in nvidia is completely different than screen tearing in fglrx. This is why more information is needed.

---

### Post by Bosconian on 2008-07-02
I have a nVidia 7300 graphics card in my laptop.

It's an Acer Aspire 5633WLMi
Intel Core 2 Duo T5500 1.66Ghz
2gb ram
120Gb HDD

XP runs perfect on it. Ubuntu runs like a nightmare.

---

### Post by Bosconian on 2008-07-04
Anyone?

If I can't fix this then I'm going to have to reformat and use Windows XP. Ubuntu feels like an OS from the 1980s.

---

### Post by medic2000 on 2008-07-04
Wish you happy days with your XP...

---

### Post by Bosconian on 2008-07-05
> **medic2000 said:**
> Wish you happy days with your XP...

LOL, I said I would be forced to go back to XP not that I wanted to ;)

Can anyone help because this is making me tear my hair out and there is less and less to tear out these days.

I like lots of things about Ubuntu but not just not the way that something that would take me 30 minutes to fix in XP is taking me 3 days+ to fix in Linux.

Please, if anyone can help it would be greatly appreciated. Weirdly, if I start XP from a Virtualbox within Ubuntu, then iPlayer also plays without tearing which encourages me that there must be a solution to this. As soon as I use iPlayer within Ubuntu though directly there is tearing all over the place and also the playback is not as smooth.

---

### Post by Tomatz on 2008-07-05
Try this:

```
sudo apt-get install vlc
```

Then open **vlc** (in sound and video)

Click **settings** then **preferences**

**Check advanced options** (bottom rh)

Then drop down **video** (lh pane)

Then **select output modules**

Switch it from **default** (xv) to [B]X11
[/B]
**Save** the configuration (bottom lh)


Now try to play a video in vlc ;)

---

### Post by xc3RnbFO8P on 2008-07-05
Did you try Kaffeine?
Install Kaffeine-Gstreamer.
(if you haven't)

---

### Post by Bosconian on 2008-07-05
Sorry I forgot to mention, video playing is fixed but iPlayer isn't and I use iPlayer a lot.

It isn't an issue with my laptop being powerful enough because XP plays iPlayer prefectly.

---

### Post by Bosconian on 2008-07-05
A bit more info. This isn't just iPlayer but more a general problem with the flash player. I've just tried videos in full screen on gametrailers.com and get the same problem. Again, the same video in XP plays perfectly on the same laptop (I still have a small XP partition on the laptop which I had planned on deleting once I was happy with Ubuntu).

Has anyone else experienced this and solved it?

I am using Firefox 3 but have also tried Opera which has the same issues.

I am also finding that when I go full screen it starts dropping a lot of frames. Again no such problem in XP so I know my laptop is powerful enough to do it.

---

### Post by Tomatz on 2008-07-05
Ahh you are experiencing flash 9 for Linux which is seriously flawed :(

BBC iplayer uses flash.




Download and install The following .deb (double click on the file once downloaded):

[http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb](http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb)

Then in a terminal type:

```
sudo apt-get install libflashsupport
```

Now In the terminal type:
```

sudo apt-get remove --purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

**Reboot** to make sure no firefox processes are still running.


Hopefully you should get a good improvement :)

---

### Post by Bosconian on 2008-07-05
> **Tomatz said:**
> Ahh you are experiencing flash 9 for Linux which is seriously flawed :(

BBC iplayer uses flash.




Download and install The following .deb (double click on the file once downloaded):

[http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb](http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb)

Then in a terminal type:

```
sudo apt-get install libflashsupport
```

Now In the terminal type:
```

sudo apt-get remove --purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```

**Reboot** to make sure no firefox processes are still running.


Hopefully you should get a good improvement :)



This has made the problem 5 times as bad and now it plays at about 2 frame per second.

Could someone please tell me how to reverse these steps and put things back how they were?

Any other suggestions? Thanks.

---

### Post by Tomatz on 2008-07-05
> **Bosconian said:**
> This has made the problem 5 times as bad and now it plays at about 2 frame per second.

Could someone please tell me how to reverse these steps and put things back how they were?

Any other suggestions? Thanks.

```
sudo apt-get remove --purge nspluginwrapper libflashsupport flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```


**Reboot**

Don't know why it made things worse as it worked for me :confused:

After that you could try turning off **hardware acceleration** in flash settings. Just r-click on the flash video you are watching.

---

### Post by Bosconian on 2008-07-05
> **Tomatz said:**
> ```
sudo apt-get remove --purge nspluginwrapper libflashsupport flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
```


**Reboot**

Don't know why it made things worse as it worked for me :confused:

After that you could try turning off **hardware acceleration** in flash settings. Just r-click on the flash video you are watching.


No this hasn't put it back to how it was. FFS, I am going backwards here. Sorry just getting frustrated with this.

---

### Post by Tomatz on 2008-07-05
> **Bosconian said:**
> No this hasn't put it back to how it was. FFS, I am going backwards here. Sorry just getting frustrated with this.

Well you must have done something else because that _**reversed**_ what i told you to do in the first place.

Why should i bother trying to help you when google brings up dozens of results concerning this issue!

Instead of moaning and swearing at me when things go wrong why not try and fix the issue yourself :mad:

---

### Post by Bosconian on 2008-07-05
> **Tomatz said:**
> Well you must have done something else because that _**reversed**_ what i told you to do in the first place.

Why should i bother trying to help you when google brings up dozens of results concerning this issue!

Instead of moaning and swearing at me when things go wrong why not try and fix the issue yourself :mad:


Done nothing else in between at all. Thanks anyway.

---

### Post by Tomatz on 2008-07-05
You could try and install flash 10:

[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

---

### Post by madjr on 2008-07-06
> **Tomatz said:**
> You could try and install flash 10:

[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

+1

i just tried it and the performance is so much better even on and old pc with 256mb ram am typing this right now.

some instructions:

1- [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
. Click on &#8220;Download Plugin for Linux (**TAR.GZ**, 3.71 MB)&#8221; and save the file to your desktop.

2- Right click on the file and choose &#8220;**Extract Here**.&#8221; A new folder is created.


3- Double click **flashplayer-installer** inside. Choose option "**Run in terminal**"

4- close browser and install once

---

### Post by Bosconian on 2008-07-06
Thanks. I now have Flash 10 installed but no difference. Still screen tearing and frames being dropped.

---

### Post by madjr on 2008-07-06
> **Bosconian said:**
> Thanks. I now have Flash 10 installed but no difference. Still screen tearing and frames being dropped.

ok,

i was testing in my old PC with 256mb ram and it runs excellent (a lot better than flash 9)

but i just tested it on my Dell Dual-core laptop 1gb ram and **for some weird reaso**n, performance is still not as smooth...

so i had to downgrade to **v9,0,48** and things are running well again.

you can get that version here:

[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2)

or this link
[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

sadly adobe had the bright idea of placing all versions for all OS's in 1 big archive (100mb download)

once it finishes downloading look for **v9,0,48** and follow the same install steps as flash 10 in my other post.


Apart from the increased performance, the only difference is that fullscreen youtube opens in a separate browser window, but i seem to like it better that way.

i think that should temporarily fix your problem till they do so in flash 10.

if you would like to place some pressure on Adobe, just vote. See my signature.

**ps**: another function i use is the **compiz desktop quick zoom** effect is really useful: **super key** (the one with the windows logo) + mouse **wheel**

oh and can you specify **which websites** you have most issues?

---

### Post by Bosconian on 2008-07-07
> **madjr said:**
> ok,

i was testing in my old PC with 256mb ram and it runs excellent (a lot better than flash 9)

but i just tested it on my Dell Dual-core laptop 1gb ram and **for some weird reaso**n, performance is still not as smooth...

so i had to downgrade to **v9,0,48** and things are running well again.

you can get that version here:

[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266&sliceId=2)

or this link
[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

sadly adobe had the bright idea of placing all versions for all OS's in 1 big archive (100mb download)

once it finishes downloading look for **v9,0,48** and follow the same install steps as flash 10 in my other post.


Apart from the increased performance, the only difference is that fullscreen youtube opens in a separate browser window, but i seem to like it better that way.

i think that should temporarily fix your problem till they do so in flash 10.

if you would like to place some pressure on Adobe, just vote. See my signature.

**ps**: another function i use is the **compiz desktop quick zoom** effect is really useful: **super key** (the one with the windows logo) + mouse **wheel**

oh and can you specify **which websites** you have most issues?



Thanks for trying to help but this now leaves with a BBC iPlayer that will not go into fullscreen. So can't even test if it makes any difference.

Does anyone have any other suggestions?

I'm close to the end of the road with this now and will have to format and go back to XP. It's been 6 days now and I'm no closer to a solution. The only solution is starting to look like Windows. Can't be bothered with dual boot so it's one or the other.

---

### Post by Tomatz on 2008-07-07
There is a hack so you can download videos from BBCi in mp4 format (drm free).

Install this firefox addon:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Restart firefox then follow these instructions on setting up user agent switcher to act like an iphone:

[http://paininthetech.com/2007/10/03/fake-iphone-user-agent/](http://paininthetech.com/2007/10/03/fake-iphone-user-agent/)

Switch to the iphone entry in user agent switcher


Now just go to BBCi and you should see a previously hidden option to download programs.

;)

---

### Post by Bosconian on 2008-07-07
These are the only solutions I ever hear for Linux. Hacks, hacks and more hacks. Sorry, I am not being ungrateful for the help, but I am not interested in starting hacking things. An OS works or it doesn't.

Thanks for the help, genuinely appreciated but I'm going to reformat the drive and put user friendly Windows back on it. What with this, being told I need to "hack" my iPod Touch to work with Linux and "hack" my PDA, I've had enough.

Thanks anyway mate and everyone else who has contributed to this thread.

---

### Post by madjr on 2008-07-07
> **Bosconian said:**
> These are the only solutions I ever hear for Linux. Hacks, hacks and more hacks. Sorry, I am not being ungrateful for the help, but I am not interested in starting hacking things. An OS works or it doesn't.

Thanks for the help, genuinely appreciated but I'm going to reformat the drive and put user friendly Windows back on it. What with this, being told I need to "hack" my iPod Touch to work with Linux and "hack" my PDA, I've had enough.

Thanks anyway mate and everyone else who has contributed to this thread.

sorry to see you leave, but Ubuntu is not for everyone **at this point**. Specially if you have "specific" needs accumulated during your windows years..

Also many new users expect it to function and act exactly as windows does, like if it had been developed by Microsoft themselves...

if you're not afraid at tweaking you could get everything working, but if you want to live the vendor experience (the way they intended) then you should stick to how the vendor developed that stuff (with windows in mind)

I do **dual-boot** windows and Ubuntu, both have their pros and cons and both can be useful for different things.

Mac also has many issues, less games, less support, etc., It's not for everyone either. It has been competing with windows on the desktop long before linux and it's still on window's shadow.

The real dominant OS is windows. **It's a big monopoly**.

because of their bad practicies and monopoly they have been fined to pay **almost 1 billion euros** by the UE

[http://www.reuters.com/article/technologyNews/idUSL077129320080707?pageNumber=1&virtualBrandChannel=0](http://www.reuters.com/article/technologyNews/idUSL077129320080707?pageNumber=1&virtualBrandChannel=0)

You may want to check from time to time how things develop. I started a year ago and believe me things were not too good. But now things are a lot better and improving.

I just hope you at least have a bit of linux in mind when ever you make a future purchase.

Try to choose multi-platform compatibility over Vendor lock-in when ever possible.

for all the rants I've been seeing is ok, i had my share too when i started. Rants don't really help in any way, but i understand you.

anyway, even if you have windows issues feel free to ask for help in the forums. You may be leaving Linux for now, but that doesn't mean you can't participate in the community once in a while.

This is a community based effort so everyone is important not only the developers.

---

### Post by madjr on 2008-07-07
> **Bosconian said:**
> Thanks for trying to help but this now leaves with a BBC iPlayer that will not go into fullscreen. So can't even test if it makes any difference.

Does anyone have any other suggestions?

I'm close to the end of the road with this now and will have to format and go back to XP. It's been 6 days now and I'm no closer to a solution. The only solution is starting to look like Windows. Can't be bothered with dual boot so it's one or the other.

i use the **compiz zoom in function** for the BBC site

**windows key** (super) + **mouse wheel**

it will zoom in your entire desktop

here is a nice demo of how it's done:

[http://www.youtube.com/watch?v=yUsZ-DSzYNs](http://www.youtube.com/watch?v=yUsZ-DSzYNs)

like i said before this should be temporarily till adobe finishes improving flash 10 beta :)

gladly am the one who started the complaints at their site a few months ago, so am not going to rest till they fix every issue.
[http://ubuntuforums.org/showthread.php?t=769906](http://ubuntuforums.org/showthread.php?t=769906)

---

### Post by Bosconian on 2008-07-08
Thanks. I don't really like the zoom "solution" though. Just feels a bit clunky. The deed is already done though, I've reformatted and gone back to Windows. I'm so much happier already - everything just works as soon as you plug it in. Now I can get on with the important things in my life rather than spending a week trying to fix something so simple.

Each to their own of course. Don't get the wrong impression. There are things to like about Ubuntu but it is still years behind Windows in my humble opinion. Get Flash working, get the iPod Touch working by just plugging it in (no jailbreaking or any of that rubbish) and get PDAs syncing with ease and I may take another look. But I mean 100% working out of the box, no hacking whatsoever. Just plug in and start using.

Maybe a couple of previous posts have been mild ranting. My apologies. That is just based on serious frustration after being told how great Linux was and how much better than Windows it was. Quite the opposite in my experience.

Thanks for everyone's help, sorry it didn't work out and it has been in vain. I may run Ubuntu in a Virtualbox in Windows to see how it is progressing but in all honesty I can never see myself preferring it over Windows.

---

### Post by Tomatz on 2008-07-08
> **Bosconian said:**
> Thanks. I don't really like the zoom "solution" though. Just feels a bit clunky. The deed is already done though, I've reformatted and gone back to Windows. I'm so much happier already - everything just works as soon as you plug it in. Now I can get on with the important things in my life rather than spending a week trying to fix something so simple.

Each to their own of course. Don't get the wrong impression. There are things to like about Ubuntu but it is still years behind Windows in my humble opinion. Get Flash working, get the iPod Touch working by just plugging it in (no jailbreaking or any of that rubbish) and get PDAs syncing with ease and I may take another look. But I mean 100% working out of the box, no hacking whatsoever. Just plug in and start using.

Maybe a couple of previous posts have been mild ranting. My apologies. That is just based on serious frustration after being told how great Linux was and how much better than Windows it was. Quite the opposite in my experience.

Thanks for everyone's help, sorry it didn't work out and it has been in vain. I may run Ubuntu in a Virtualbox in Windows to see how it is progressing but in all honesty I can never see myself preferring it over Windows.

:rolleyes:

---

### Post by madjr on 2008-07-08
> **Bosconian said:**
> Thanks. I don't really like the zoom "solution" though. Just feels a bit clunky. The deed is already done though, I've reformatted and gone back to Windows. I'm so much happier already - everything just works as soon as you plug it in. Now I can get on with the important things in my life rather than spending a week trying to fix something so simple.

Each to their own of course. Don't get the wrong impression. There are things to like about Ubuntu but it is still years behind Windows in my humble opinion. Get Flash working, get the iPod Touch working by just plugging it in (no jailbreaking or any of that rubbish) and get PDAs syncing with ease and I may take another look. But I mean 100% working out of the box, no hacking whatsoever. Just plug in and start using.

Maybe a couple of previous posts have been mild ranting. My apologies. That is just based on serious frustration after being told how great Linux was and how much better than Windows it was. Quite the opposite in my experience.

Thanks for everyone's help, sorry it didn't work out and it has been in vain. I may run Ubuntu in a Virtualbox in Windows to see how it is progressing but in all honesty I can never see myself preferring it over Windows.

sounds good.

i've been running windows in virtualbox inside ubuntu. I've been using windows for 10 years and really got fed up with the viruses, spyware undetectable trojans and all the registry garbage.

so instead of re-formating windows every 3 or 4 months, i just use an virtual image and BAM windows is new again.

since linux is maintenance free and i reduced the windows maintenance by virtualizing i can get more work done and peace of mind.

also, using both OS's at the same time is kinda cool

[IMG]http://ubunturoot.files.wordpress.com/2007/12/virtual-cube.png?w=433&h=275[/IMG]

---

### Post by Bosconian on 2008-07-09
Well I've been back 100% with Windows for over 24 hours. I'm not using Ubuntu at all but I have come back here to this community to be fair to them

Fair? What I mean by that is that I thought it would only be fair to point out that I installed Vista Home Premium and Firefox 3 and Flash 9 and lo and behold I get the same screen tearing issues in BBC iPlayer.

I could easily of not mentioned this but I've criticised Ubuntu so I think it is only fair to paint the whole picture.

Only problem is I still can't use my iPod Touch in Ubuntu so I'm sticking with Windows.

---

### Post by Tomatz on 2008-07-09
> **Bosconian said:**
> Well I've been back 100% with Windows for over 24 hours. I'm not using Ubuntu at all but I have come back here to this community to be fair to them

Fair? What I mean by that is that I thought it would only be fair to point out that I installed Vista Home Premium and Firefox 3 and Flash 9 and lo and behold I get the same screen tearing issues in BBC iPlayer.

I could easily of not mentioned this but I've criticised Ubuntu so I think it is only fair to paint the whole picture.

Only problem is I still can't use my iPod Touch in Ubuntu so I'm sticking with Windows.

Why dont you dual boot?

Now you can install ubuntu in windows just like any other windows app. Wubi makes no changes to your drive/partition and the install (or uninstall) is as simple as one click.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Tomatz on 2008-07-09
> **madjr said:**
> sounds good.

i've been running windows in virtualbox inside ubuntu. I've been using windows for 10 years and really got fed up with the viruses, spyware undetectable trojans and all the registry garbage.

so instead of re-formating windows every 3 or 4 months, i just use an virtual image and BAM windows is new again.

since linux is maintenance free and i reduced the windows maintenance by virtualizing i can get more work done and peace of mind.

also, using both OS's at the same time is kinda cool

[IMG]http://ubunturoot.files.wordpress.com/2007/12/virtual-cube.png?w=433&h=275[/IMG]


You couldn't link me your skydome could you?

---

### Post by Bosconian on 2008-07-09
> **Tomatz said:**
> Why dont you dual boot?

Now you can install ubuntu in windows just like any other windows app. Wubi makes no changes to your drive/partition and the install (or uninstall) is as simple as one click.

[http://wubi-installer.org/](http://wubi-installer.org/)


No need mate, I'm typing this from Ubuntu. After spending a day with Vista, I thought long and hard and made the decision to make a permanent move to Ubuntu. Several reasons for this, first of all having the same issues with BBC iPlayer. Then having a problem with my mouse (which I did manage to fix) and a problem where my wireless connection kept being lost which I was unable to fix after several suggestions.

Now I could probably have persevered and solved that but it suddenly dawned on me how my previous beliefs about Windows were in fact incorrect. I've always seen it as the "plug and play OS". No tweaking required just install and use. Yet in 24 hours I was hacking my way through Vista looking for solutions to my problems.

So which would I prefer? Having to mess around with Windows to get it to work properly? Or mess around with Ubuntu getting it to work properly with this quite amazing community here? It was a simple choice to make ;)

---

### Post by Tomatz on 2008-07-09
> **Bosconian said:**
> No need mate, I'm typing this from Ubuntu. After spending a day with Vista, I thought long and hard and made the decision to make a permanent move to Ubuntu. Several reasons for this, first of all having the same issues with BBC iPlayer. Then having a problem with my mouse (which I did manage to fix) and a problem where my wireless connection kept being lost which I was unable to fix after several suggestions.

Now I could probably have persevered and solved that but it suddenly dawned on me how my previous beliefs about Windows were in fact incorrect. I've always seen it as the "plug and play OS". No tweaking required just install and use. Yet in 24 hours I was hacking my way through Vista looking for solutions to my problems.

So which would I prefer? Having to mess around with Windows to get it to work properly? Or mess around with Ubuntu getting it to work properly with this quite amazing community here? It was a simple choice to make ;)

:popcorn:

Great news Bosconian! It's all a myth really lmao. Windows is 10 times harder to install, all that hunting for drivers through dodgy sites and all. Ubuntu does most of it "out of the box"!

Do you think you could post a screenshot (press the print screen key) of this tearing along with the output of the following command:

```
lshw
```

Hopefully we can get to the bottom of this ;)


P.s

Sorry about the rant the other day :(

---

### Post by Bosconian on 2008-07-09
> **Tomatz said:**
> :popcorn:

Great news Bosconian! It's all a myth really lmao. Windows is 10 times harder to install, all that hunting for drivers through dodgy sites and all. Ubuntu does most of it "out of the box"!

Do you think you could post a screenshot (press the print screen key) of this tearing along with the output of the following command:

```
lshw
```

Hopefully we can get to the bottom of this ;)


P.s

Sorry about the rant the other day :(


Yeah I'm going to look into the tearing issue a bit more at some point. My first priority now I've decided to stick with Ubuntu, is decide on a replacement mp3 player for iPod Touch 16Gb. Yes, I'm that committed that I am going to replace my mp3 player.

---

### Post by Tomatz on 2008-07-09
Open a terminal and type:

```
sudo apt-get install amarok
```

That will install amarok which is a media player that supports syncing to ipods.

Then go to the link below for instructions on setting up your ipod (and ubuntu) to work with amarok.

[http://www.ipodtouchfans.com/wiki/index.php?title=Syncing_with_Ubuntu](http://www.ipodtouchfans.com/wiki/index.php?title=Syncing_with_Ubuntu)

;)

---

### Post by Bosconian on 2008-07-09
> **Tomatz said:**
> Open a terminal and type:

```
sudo apt-get install amarok
```

That will install amarok which is a media player that supports syncing to ipods.

Then go to the link below for instructions on setting up your ipod (and ubuntu) to work with amarok.

[http://www.ipodtouchfans.com/wiki/index.php?title=Syncing_with_Ubuntu](http://www.ipodtouchfans.com/wiki/index.php?title=Syncing_with_Ubuntu)

;)


No mate, that's the point. I don't want to jailbreak it. Too much "hacking" for me.

---

### Post by Tomatz on 2008-07-09
> **Bosconian said:**
> No mate, that's the point. I don't want to jailbreak it. Too much "hacking" for me.

I'm not sure you will be able to do it then :(

The only other way around the problem would be to install xp in a vm and install itunes on it. Virtualbox is a great vm, you can install it via synaptic.

Bloody apple! They should start supporting linux.

---

### Post by Bosconian on 2008-07-09
> **Tomatz said:**
> I'm not sure you will be able to do it then :(

The only other way around the problem would be to install xp in a vm and install itunes on it. Virtualbox is a great vm, you can install it via synaptic.

Bloody apple! They should start supporting linux.


Can't do that either. There is a bug in Virtualbox USB which doesn't detect the iPod Touch correctly. Plus you cannot update firmware via a virtual machine anyway even if it did work.

No I'm going to change mp3 player.

---

### Post by Tomatz on 2008-07-09
> **Bosconian said:**
> Can't do that either. There is a bug in Virtualbox USB which doesn't detect the iPod Touch correctly. Plus you cannot update firmware via a virtual machine anyway even if it did work.

No I'm going to change mp3 player.

Bummer :(

Just have a search around the forums before you buy one.

---

### Post by Bosconian on 2008-07-10
Turns out I cannot afford to sell my iPod Touch as I won't get as much as I thought I would for it. So I've reformatted back to XP (not Vista this time) and much happier with my iPod and iTunes.

Shame, Ubuntu has some nice touches but it isn't ready for the simple computer users like me who don't want to be hacking stuff to work all the time.

---

### Post by madjr on 2008-07-16
> **Bosconian said:**
> Turns out I cannot afford to sell my iPod Touch as I won't get as much as I thought I would for it. So I've reformatted back to XP (not Vista this time) and much happier with my iPod and iTunes.

Shame, Ubuntu has some nice touches **but it isn't ready for the simple computer users like me who don't want to be hacking stuff to work all the time.**

yea, sadly it would be ready for you if apple got itunes ported.

but who knows, i heard itunes will be working nicely in Wine pretty soon. So it will be just as straight forward as in XP.

anyway, see you soon, i know XP can be a bit "touch**é**" after a while

---

### Post by travelinman81 on 2008-07-16
I always hate to see people switch back to windows because of the "flaws of Linux" It isn't *nixes fault that vendors won't support it. The long standing myth of linux being hard to use and having to "hack" is rediculous it is the fault of software vendors for not making programs for linux. Adobe needs to get their act together along with many other company's. I use linux 100% of the time except on my daughters computer and my stupid computer at work. I have a linux server setup for file sharing & security of my data. My sons media computer is running Ubuntu and my desktop runs Ubuntu. It is really irritating that to sync my Ipod touch I have to use the tools built into linux to make it work because Apple refuses to release an Itunes for Linux. In the same sentence though those very things have freed me from the corporate mindset now it makes me feel good that there are ways to circumvent these companies. In you're face my Touch does sync with linux thats right how you like that Steve. Wait whats that Bill you say my school uses MS Office oh get some I have open office, whats up flashplayer you want to go sucky on me well I'll just get me some gnash then yeah how you like that. I thought it clunky at first when I started using Dapper but, now I can't see it any other way I love to be free from the bull and I love being able to dig into my OS and actually realize the potential of my computer. It's liberating and fantastic to know that no matter what there is a huge community of people who thrive on making things work. My computer and I are so much more intimate now than it ever was with windows, I actually understand what it is doing and it makes me dislike the vendors who don't get it and want to profiteer off of it all the more. There's my rant for the time. Oh and I ended up here checking up on a screen tearing issue for one of my buddies who just seen the light. The beautiful thing about linux is the community behind it. Peace out sorry bout the long winded rant but, I had to get that off my chest

---

