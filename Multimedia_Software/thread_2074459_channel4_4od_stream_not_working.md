---
title: "channel4 4od stream not working"
date: 2012-10-21
forum: Multimedia Software
---

### Post by mf205 on 2012-10-21
I recently installed ubuntu 12.04 alongside W7 on my wife's old Dell laptop.  This sits next to our TV, and we primarily use it for catching up TV programmes.  Flash seems to be installed correctly, since BBC iPlayer and ITV player are both working fine.  But I can't get channel 4 4od to work - when I choose a programme and hit play, I just get the buffering animation (pictured) ad infinitum.  This is on Firefox, but I've also tried it with chromium and have the same problem.

I have adblock plus enabled; if I disable this, then the ads play quite happily, but when it comes to the actual programme, I have the same problem.

Any ideas?

---

### Post by cheesah on 2012-10-27
Hi,
I've just installed Mythbuntu and am having the same issue with 4oD. I've installed Firefox and Opera, to see if it was just Chromium but they're all the same. itv, bbc etc. are all ok. 
Also tried the flash settings manager, adding channel4 to the allow list and upping the local storage.

---

### Post by devnull12 on 2012-10-27
Following advice I found on [this]("http://m.jguk.org/2012/10/resolved-channel4-4od-working-with.html") page, I fixed this by installing the "hal" package:

sudo apt-get install hal

I have no idea that that package is for. Maybe it would be a good idea for it to be part of the standard distro.

---

### Post by cheesah on 2012-10-28
Fantastic! This worked, thank you.

---

### Post by Greg K Nicholson on 2013-01-18
Yes! Thank you.

Remarkably, it seems that HAL is required to play 4oD programmes on Ubuntu (and presumably Linux in general).

This is remarkable because [HAL is a fairly low-level piece of software]("https://en.wikipedia.org/wiki/HAL_%28software%29") used to detect hardware properly. It's also been obsolete for several years, and the most recent version dates from 2011.

HAL *should* be completely unrelated to video. I can only suspect that 4oD is using some sort of [DRM]("https://en.wikipedia.org/wiki/DRM"), and that my netbook's hardware (which came with Linux) somehow passes 4oD's inquisition.

Once again, the fix (that worked for me) is to [install the “hal” package]("https://apps.ubuntu.com/cat/applications/hal/") (and disable AdBlock).

---

### Post by Herby Pepper on 2013-02-06
thanks [devnull12]("http://ubuntuforums.org/member.php?u=1748679") !
sudo apt-get install hal
works for me (Mint 14.1)

---

### Post by Purple Penguin on 2013-02-25
Hi, Hal worked for me too, thank you! :D
(Ubuntu 12.10)

---

### Post by Yettie on 2013-03-29
Whatever the reason, this solution worked for me too.

---

### Post by shof2k on 2013-04-14
I've tried reinstalling HAL, but this isn't helping anymore. I suspect it has something to do with the recent update to Flash.

Following adobe support instructions at [http://forums.adobe.com/message/4797322](http://forums.adobe.com/message/4797322) (message 21), the adobe console at [http://drmtest2.adobe.com/AccessPlayer/player.html](http://drmtest2.adobe.com/AccessPlayer/player.html) comes up with the following error message.

```

Status event received on  Sun Apr 14 19:11:00 GMT+0100 2013 code =  DRM.UpdateNeededButIncompatible level =  error 
Start to download DRM Module Sun Apr 14 19:10:59 GMT+0100 2013

```

Any adobe wizards know how to sort this out?

Peace

---

### Post by Fynn on 2013-04-14
Worked for me, thanks.

---

### Post by shof2k on 2013-04-15
which version of flash do you have. Did you try my instructions? If so, what was the result?

---

### Post by shantiq on 2013-04-18
Thank you Hal thanx for talking to me and for stopping that wheel and playing the docum:oentary, thank you Hal

---

### Post by funkeymonkey on 2013-05-29
ohhh hal, why dont you work? :( after crying in to my coffee cup and hunting over the whole wide interweb and trying all the bits one by one and all at once ive found i can now watch the ads! yippie,,,,, for some reason i really wanna buy some nike trainers and a useless windows 8 laptop...... erm yeah, back to it, i'm running ubuntu 13.4 and updated all codecs and everything i can think of, flash, restet flash, tried other sites.... also... you know those sites where the people are leing down but look like they are fighting? why do they always work flawlessley? so after 10 mins break (actually 2 mins:p) of watching people kinda fighting but without punching,,,, i got back to finding the fault and cant..... dont make me boot windows! ohh i hate windows! and p.s this is my first post so thought i'd ramble on, sorry for my spelling i'm lazy and dumb! :) love you! boo 4od! and nope i havent installed add blocker...... well.... the two ladies wrestling is back on,,,,, whats that long black thing.....?  O_o ohhh.... this may not be wrestling....... x_x

---

### Post by jpules on 2013-07-18
This worked for me, too! Very strange!

---

### Post by jim_deadlock on 2013-10-26
This has previously worked for me, but now there is no hal in the saucy repository. I've tried manually installing hal but the installation package insists that I don't have expat installed (I have). So my 4od is currently not working. Any suggestions?

---

### Post by jim_deadlock on 2013-10-26
As luck would have it, OMG! Ubuntu have covered this very thing [here]("http://www.omgubuntu.co.uk/2013/10/fixing-amazon-prime-streaming-drm-protected-flash-13-10").

---

### Post by samwillc on 2013-11-07
> **devnull12 said:**
> Following advice I found on [this]("http://m.jguk.org/2012/10/resolved-channel4-4od-working-with.html") page, I fixed this by installing the "hal" package:

sudo apt-get install hal


Good find, thanks!

> **jim_deadlock said:**
> As luck would have it, OMG! Ubuntu have covered this very thing [here]("http://www.omgubuntu.co.uk/2013/10/fixing-amazon-prime-streaming-drm-protected-flash-13-10").

I only tried 4OD this morning and wondered why the little circle just kept spinning. Thanks for the link.

---

### Post by submarine1980 on 2013-12-10
sudo apt-get install hal

worked for me (channel 5 - Monty Halls series!!!)

thanks

D

---

### Post by nicolasdiogo on 2014-07-30
in my case i had to install HAL

and also enable javascript (as i have a pluggin that blocks it - NoScript)
for adobe.com and macromedia.com

just test your installation on the macromedia website and if it works you should be good to go!

thanks for the comments above!

now i can watch my video on the way home?

LOL

---

### Post by joll-nicholas on 2014-11-17
This - or rather the following - works for me on Firefox (on Linux Mint 17 Cinnamon x64) but not on Chromium or Opera.

rm ~/.adobe -rf
sudo apt-get -y install hal hal-info
sudo apt-get -y install flashplugin-installer --reinstall
sudo rm -r /etc/hal
sudo ln -sn /usr/share/hal /etc/hal
cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

I managed to get Chromium (haven't tried Opera) to use PepperFlash, but that didn't help.

---

### Post by your_name3 on 2015-03-19
> **joll-nicholas said:**
> This - or rather the following - works for me on Firefox (on Linux Mint 17 Cinnamon x64) but not on Chromium or Opera.

rm ~/.adobe -rf
sudo apt-get -y install hal hal-info
sudo apt-get -y install flashplugin-installer --reinstall
sudo rm -r /etc/hal
sudo ln -sn /usr/share/hal /etc/hal
cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2


Confirmed with Ubuntu 14.14/Firefox. :)

---

### Post by MrSteve on 2015-03-19
just giving some info that i picked up about HAL ...

flash player in firefox is a plug in so HAL will work
but in chromium and chrome (also the new opera) flash is built into the browser and is not a plug in so HAL will not work 

here is a link to a HAL ppa for ubuntu ...
[https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal)

---

### Post by theonewhoshallnotbenamed on 2015-11-17
oh man, I have tried literally everything suggested on this thread and still having problems. 

My 4od has been working fine on Ubuntu 14.04 for the last three months.  All of a sudden, it stops.  It never worked on Chrome anyway which I use for Netflix now as no other browser lets that play and I've been using FFox for 4od.  Friday I was watching it, by Monday, I was getting a black box, not even an image or spinning circle.  Nothing.  

Have tried installing hal, reckons its the most recent version now.  Installed the pepper flash thing. disabled adblockers.  I'm at a total loss now. I wouldnt have minded if I'd done something to have caused a sudden change but I was using it fine on Friday and havent used it over the weekend and then bam, gone.  Its spinning circle on Chrome and black box on Chromium. 

HELP!?

---

### Post by jim_deadlock on 2015-11-17
I'm glad you said that because I suddenly have exactly the same as what you said. They must have changed something on their end to break it. Bah!

---

### Post by theonewhoshallnotbenamed on 2015-11-22
argh so frustrating and I have googled and tried stuff for hours and hours now and I'm so frustrated.  I havent seen whether it's stopped working on my mint pc yet but it does work via the app on my phone.  this isn't the best option, but, if I do want to watch anything from channel 4 at least I have that. I used to like just watching reruns of Gogglebox when there was nothing else on TV... now I cant :-(  I am relieved however also that it's not just me! although that doesnt really help either of us haha!

---

