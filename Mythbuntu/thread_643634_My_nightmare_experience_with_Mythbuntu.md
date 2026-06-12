---
title: "My nightmare experience with Mythbuntu"
date: 2007-12-18
forum: Mythbuntu
---

### Post by Solv on 2007-12-18
I just thought I'd post a bit of a review on my experience with mythbuntu and why I'm now looking to other options.  Please bear in mind I'm not a n00b, I actually deleted my current gentoo mythtv installation to give mythbuntu a go.  I thought rather than whining and bitching about my problems on irc, I should post this here and hope the developers can improve on mythbuntu in the future.

Firstly, my specs:
CPU: Pentium Celeron D 330
Motherboard: Foxconn 661FX
RAM: 756 MEG
Display Adapter: Nvidia Ti4200 128 Meg
Tuner Card: Technisat AirStar 2 (b2c2-flexcop-pci kernel module)

Installation:  Seemed to go well, the first time I installed it I opted to keep my existing home partition, and reformat the others as /boot and / and of course swap

The one problem I encountered while rebooting was when it finishes by launching mythtv-setup it was unable to access my tuner card, so I couldn't do a channel scan and properly configure my card...well I exited and rebooted.

First Run:
Okay I got into xfce and it seemed good...except as mythfrontend launched it complained about not being able to connect to the backend...okay, fair enough I haven't set the backend up properly.  So I ran mythbuntu control centre, ran mythtv-setup and this time it could access the card, and it scanned for my channels correctly and it all seemed okay.

While I was in the control centre I thought I'd check out the other options.  I tried the xorg configure module and it was okay..but I wanted TV out.  No problem, I'll just get nvidia-settings and make some changes, as well as nvtv to get that working easily.....ummm...no sorry ubuntu's nvidia-setting removes the nvidia-glx-legacy driver and tries to install nvidia-glx....which doesn't work on my card!  Funny, because I ran nvidia-settings just fine on gentoo.  Oh well how about nvtv...nope that segfaults...geez.

Okay I'll do it myself (already this is starting to get beyond the new linux user), so I add the appropriate lines to xorg.conf including a TVOverScan option which I would have been able to set if I was able to use nvidia-settings.  Okay restart X...that's nice everything looks better.

Somewhat distracted I continued to look through the control centre options...I decided to enable the non-free codecs....the control centre flashed a progress dialog for a second then quit??  Tried again...nope...okay I'll do it myself in synaptic...eventually I figured out that it was trying to get the packages from the CD...which I had to remove to restart the install!  Maybe a dialog to ask to reinsert the CD would be better??

Okay now onto my remote.  I have a serial IR receiver that came with my card, and a generic 4 in 1 remote I have programmed with irrecord.  Low and behold there was no option to select a generic serial port ir receiver.  In the manual it gave me instructions to change a heap of config files to free up the com port and I had to download the setserial and configure it manually...why??  Surely there are many people with serial port ir receivers? I imported my backed up lircd.con file...restarted the lirc daemon......but no action.  Ran cat /dev/lirc0 and it was getting input...so the port was working...but irw gave me no output....i gave up as i still needed to figure out the frontend/backend issue.

Going back to the frontend, I decided to change the appearance to my favourite one retro...however it looked much more squashed and unattractive than when i was running it on gentoo.......oh well...I can live with that.  So I thought I'd run the backend setup again, and then restart the service manually.  Okay this should work...no sorry...try again!! Now I've set mythtv up a number of times and I KNEW my setup options were correct.  I looked to the mythbuntu forums for help and saw people with the same problem...it was suggested to be a mysql problem.  I'm not familiar with mysql so I followed the examples and tried to reconfigure it deleting other existing mysq.txt file runnin dpkg-reconfigure, and running mysql command to reset the passwords...instead I screwed it up completely and decided that I would just try and do another fresh install, and this time use the whole disk.  

So I reran the install...had the same problem with accessing my tuner card from the livecd mythtv-seup, and rebooted.  Okay back into a fresh install...and guess what.  Cannot connect to backend!?!?!  I'm starting to lose it now...eventually I tracked down the problem...the init file was not loading mythbackend EVEN THOUGH IT SAID IT WAS!!
Running mythbackend manually started it up and after running mythfrontend I had TV...yeeha....MYTHBUNTU devs please take note this is a SERIOUS bug to have on a final release!!!  Well I thought that solved everything but....

I didn't want TV on my monitor I wanted it on my TV (Svideo output to CRT TV).  So I just disconnected my monitor..set up my TV as the primary monitor like I had with gentoo, and restarted X.  Everything looked fine, started the backend...started the frontend...and nope, instead of TV I just got a blue screen....and to make matters worse, now the retro theme wasn't displaying any pictures...just the background, and if I pressed escape the option to exit appeared...

That was it, I wasn't going to waste anymore time...so I thought I'd try linuxmce...well that couldn't even get past a reboot after install....I think ubuntu based media centres are obviously not for me.

Thanks for taking the time to read this...I hope you guys get things working better in the future, as for me I'm gonna try knoppmyth and see what happens

---

### Post by stevetv on 2007-12-18
dude..i have that card and i had the same problem until i updated vlc.  theres a note on the wiki saying so.

that would have fixed your "unable to connect to backend" problem.

i didnt read the rest of your post, so likely there were other issues not related to the card...  

(why would people "bitch and moan" on irc... mythbuntu is open source and free.)"

---

### Post by hkazemi on 2007-12-18
I have an Air2PC (2nd rev) card and had initially had problems getting it working in Mythbuntu.  Eventually I found notes for loading firmware (copied and pasted below).  For my card, they depend on a small firmware file inside [http://www.bbti.us/download/windows/Technisat_DVB-PC_4_4_COMPACT.zip](http://www.bbti.us/download/windows/Technisat_DVB-PC_4_4_COMPACT.zip) ( Technisat_DVB-PC_4_4_COMPACT.zip ) .  It would be much more convenient and user-friendly if these necessary additional firmware files could just be included in the Mythbuntu or MythTV distribution from the get go.  They're not large, and they'd really make things easier for people getting stated with MythTV.

Notes page: [https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list)

Air2PC
HD5000 - supported out of the box 

Air2PC-ATSC-PCI (1st rev) - supporded but needs firmware The firmware can be obtained as follows: 

$ wget "http://www.linuxtv.org/downloads/firmware/dvb-fe-bcm3510-01.fw"
$ sudo cp dvb-fe-bcm3510-01.fw /lib/firmware
Air2PC-ATSC-PCI (2nd rev) - supported but needs firmware The firmware can be obtained as follows: 

Download this script: get_dvb_firmware 
[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?action=AttachFile&do=get&target=get_dvb_firmware](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?action=AttachFile&do=get&target=get_dvb_firmware)

$ chmod +x get_dvb_firmware
$ ./get_dvb_firmware nxt2002
$ sudo cp dvb-fe-nxt2002.fw /lib/firmware

---

### Post by superm1 on 2007-12-18
> **hkazemi said:**
> I have an Air2PC (2nd rev) card and had initially had problems getting it working in Mythbuntu.  Eventually I found notes for loading firmware (copied and pasted below).  For my card, they depend on a small firmware file inside [http://www.bbti.us/download/windows/Technisat_DVB-PC_4_4_COMPACT.zip](http://www.bbti.us/download/windows/Technisat_DVB-PC_4_4_COMPACT.zip) ( Technisat_DVB-PC_4_4_COMPACT.zip ) .  It would be much more convenient and user-friendly if these necessary additional firmware files could just be included in the Mythbuntu or MythTV distribution from the get go.  They're not large, and they'd really make things easier for people getting stated with MythTV.

Notes page: [https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list)

Air2PC
HD5000 - supported out of the box 

Air2PC-ATSC-PCI (1st rev) - supporded but needs firmware The firmware can be obtained as follows: 

$ wget "http://www.linuxtv.org/downloads/firmware/dvb-fe-bcm3510-01.fw"
$ sudo cp dvb-fe-bcm3510-01.fw /lib/firmware
Air2PC-ATSC-PCI (2nd rev) - supported but needs firmware The firmware can be obtained as follows: 

Download this script: get_dvb_firmware 
[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?action=AttachFile&do=get&target=get_dvb_firmware](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?action=AttachFile&do=get&target=get_dvb_firmware)

$ chmod +x get_dvb_firmware
$ ./get_dvb_firmware nxt2002
$ sudo cp dvb-fe-nxt2002.fw /lib/firmware
The problem is that there isn't any license listed on a lot of the firmware pieces like this for redistribution.

---

### Post by superm1 on 2007-12-18
Thanks for taking a look here.  Let me dissect a little bit of your post
> **Solv said:**
> 
<snip>

The one problem I encountered while rebooting was when it finishes by launching mythtv-setup it was unable to access my tuner card, so I couldn't do a channel scan and properly configure my card...well I exited and rebooted.

There have been exactly 2 other people who have mentioned this issue.  None of the developers have reproduced it though, so it's a bit hard to fix for that reason :)

> 
First Run:
<snip>

While I was in the control centre I thought I'd check out the other options.  I tried the xorg configure module and it was okay..but I wanted TV out.  No problem, I'll just get nvidia-settings and make some changes, as well as nvtv to get that working easily.....ummm...no sorry ubuntu's nvidia-setting removes the nvidia-glx-legacy driver and tries to install nvidia-glx....which doesn't work on my card!  Funny, because I ran nvidia-settings just fine on gentoo.  Oh well how about nvtv...nope that segfaults...geez.

The nvidia-settings package listed in apt really should be removed.  The binaries are included in the misc nvidia-glx packages now.  If you would be so inclined to file a bug on this on launchpad, it'd be appreciated.  Not many people still use legacy cards, so this doesn't crop up much.

> 
<snip>
Somewhat distracted I continued to look through the control centre options...I decided to enable the non-free codecs....the control centre flashed a progress dialog for a second then quit??  Tried again...nope...okay I'll do it myself in synaptic...eventually I figured out that it was trying to get the packages from the CD...which I had to remove to restart the install!  Maybe a dialog to ask to reinsert the CD would be better??

Fixed in development release.  This was something that cropped up the night of release when it was too late to fix.

> 
Okay now onto my remote.  I have a serial IR receiver that came with my card, and a generic 4 in 1 remote I have programmed with irrecord.  Low and behold there was no option to select a generic serial port ir receiver.  In the manual it gave me instructions to change a heap of config files to free up the com port and I had to download the setserial and configure it manually...why??  Surely there are many people with serial port ir receivers? I imported my backed up lircd.con file...restarted the lirc daemon......but no action.  Ran cat /dev/lirc0 and it was getting input...so the port was working...but irw gave me no output....i gave up as i still needed to figure out the frontend/backend issue.

From watching success reports, most people are not using serial remotes.  There is a more automated set of work underway for development release, but there is quite a bit to properly automating this.

> 
Going back to the frontend, I decided to change the appearance to my favourite one retro...however it looked much more squashed and unattractive than when i was running it on gentoo.......oh well...I can live with that.  

really bizarre.  never heard of such problems.

> 
So I thought I'd run the backend setup again, and then restart the service manually.

I certainly hope manually **does not **mean
```
mythbackend -d
```
Expect troubles if you aren't using an init script

> 
 Okay this should work...no sorry...try again!! Now I've set mythtv up a number of times and I KNEW my setup options were correct.  I looked to the mythbuntu forums for help and saw people with the same problem...it was suggested to be a mysql problem.  I'm not familiar with mysql so I followed the examples and tried to reconfigure it deleting other existing mysq.txt file runnin dpkg-reconfigure, and running mysql command to reset the passwords...

As seems to be the trend, multiple people run into issues with mysql, but no one can narrow down the step that they did to cause the trouble.  

> 
instead I screwed it up completely and decided that I would just try and do another fresh install, and this time use the whole disk.  

So I reran the install...had the same problem with accessing my tuner card from the livecd mythtv-seup, and rebooted.  Okay back into a fresh install...and guess what.  Cannot connect to backend!?!?!  

I bet your permissions on your recordings directory were wrong.  The backend was **starting**, but you didn't look at the logs to see why it was [I]exiting.
[/I]For future reference,
```
/var/log/mythtv/mythbackend.log
```

> 
I'm starting to lose it now...eventually I tracked down the problem...the init file was not loading mythbackend EVEN THOUGH IT SAID IT WAS!!
Running mythbackend manually started it up

Again, i suspect by manually you are talking about
```
mythbackend -d 
```
as your current user.  Bad idea.

> 
 and after running mythfrontend I had TV...yeeha....MYTHBUNTU devs please take note this is a SERIOUS bug to have on a final release!!!  Well I thought that solved everything but....

The bug here is the ability for someone other than the mythtv daemon user to be able to run mythbackend if my suspicion is correct.

>  
I didn't want TV on my monitor I wanted it on my TV (Svideo output to CRT TV).  So I just disconnected my monitor..set up my TV as the primary monitor like I had with gentoo, and restarted X.  Everything looked fine, started the backend...started the frontend...and nope, instead of TV I just got a blue screen....and to make matters worse, now the retro theme wasn't displaying any pictures...just the background, and if I pressed escape the option to exit appeared...

Sounds like you didn't set the video overlay properly.

> 
That was it, I wasn't going to waste anymore time...so I thought I'd try linuxmce...well that couldn't even get past a reboot after install....I think ubuntu based media centres are obviously not for me.

Thanks for taking the time to read this...I hope you guys get things working better in the future, as for me I'm gonna try knoppmyth and see what happens

Although you've already moved on to another product, being a little more patient would have likely solved most of your issues.  There are lots of other very bright people here on these forums who are actively trying to help everyone out with things that crop up.

---

### Post by Solv on 2007-12-18
Hey, thanks for your responses...it is good to see you know about a lot of the issues I raised, and thanks for the feedback on some of my problems.

When talking about running manually, you are correct...and the reason for doing this was because typing: sudo /etc/init.d/mythtv-backend restart, would return something of the sort: /usr/bin/mythbackend not running...then would go ahead an 'appear' to start it...ie there was no 'failed' feedback from the script.  The reason i ran mythbackend myself was to make sure that it would actually run, which I did....so the issue must be the init script?  I made no changes to it...like I said on first bootup after install it would not connect....which says to me there is something weird going on there that cannot be user error.

As for permissions, I changed the recordings folder to my home folder so i knew I had permissions.

I might give it another go...but I want to compare it to knoppmyth, and if I have similar issues...i will blame myself and come crawling back to you guys for help...it does appear that the community here is quite helpful and reasonable.

cheers,
Solv

---

### Post by hkazemi on 2007-12-18
> **superm1 said:**
> The problem is that there isn't any license listed on a lot of the firmware pieces like this for redistribution.

For what it's worth, BBTI (Broadband Technologies, Inc.) says "We support the development efforts of the Linux community and have incorporated native support for our products within the Linux-DVB framework. (www.linuxtv.org)." on [http://www.bbti.us/support.htm](http://www.bbti.us/support.htm) .

LinuxTV has a list of firmware here:
[http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)

Surely firmware from the LinuxTV site can be included, right?

What does BBTI need to say to  make people feel okay distributing the firmware?  Note that BBTI has ebay listings (e.g. [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=230204789761](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=230204789761) ) linked to from its homepage that say
"MYTH TV SUPPORT: This card is support by the Linux-DVB Open Source for those users wishing to use this card with MythTV. Please note that a kernel version of 2.6.13 or later must be used along with the card 's firmware which can all be downloaded from www.linuxtv.org."

In conclusion it appears BBTI is already interested in people using the card with MythTV and is directing people to the LinuxTV firmware section.

Even if there are remaining license concerns, the Mythbuntu installer could tell the user that firmware is needed and ask for permission from the user to automatically run the get dvb firmware script to get the needed firmware.

---

### Post by superm1 on 2007-12-18
> **Solv said:**
> Hey, thanks for your responses...it is good to see you know about a lot of the issues I raised, and thanks for the feedback on some of my problems.

When talking about running manually, you are correct...and the reason for doing this was because typing: sudo /etc/init.d/mythtv-backend restart, would return something of the sort: /usr/bin/mythbackend not running...then would go ahead an 'appear' to start it...ie there was no 'failed' feedback from the script.  The reason i ran mythbackend myself was to make sure that it would actually run, which I did....so the issue must be the init script?  I made no changes to it...like I said on first bootup after install it would not connect....which says to me there is something weird going on there that cannot be user error.

As for permissions, I changed the recordings folder to my home folder so i knew I had permissions.

I might give it another go...but I want to compare it to knoppmyth, and if I have similar issues...i will blame myself and come crawling back to you guys for help...it does appear that the community here is quite helpful and reasonable.

cheers,
Solv
Well setting the recordings folder to your home folder is the problem.  You may have permissions, but the mythtv daemon user does not.

---

### Post by superm1 on 2007-12-18
> **hkazemi said:**
> For what it's worth, BBTI (Broadband Technologies, Inc.) says "We support the development efforts of the Linux community and have incorporated native support for our products within the Linux-DVB framework. (www.linuxtv.org)." on [http://www.bbti.us/support.htm](http://www.bbti.us/support.htm) .

LinuxTV has a list of firmware here:
[http://www.linuxtv.org/downloads/firmware/](http://www.linuxtv.org/downloads/firmware/)

Surely firmware from the LinuxTV site can be included, right?

What does BBTI need to say to  make people feel okay distributing the firmware?  Note that BBTI has ebay listings (e.g. [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=230204789761](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=230204789761) ) linked to from its homepage that say
"MYTH TV SUPPORT: This card is support by the Linux-DVB Open Source for those users wishing to use this card with MythTV. Please note that a kernel version of 2.6.13 or later must be used along with the card 's firmware which can all be downloaded from www.linuxtv.org."

In conclusion it appears BBTI is already interested in people using the card with MythTV and is directing people to the LinuxTV firmware section.

Even if there are remaining license concerns, the Mythbuntu installer could tell the user that firmware is needed and ask for permission from the user to automatically run the get dvb firmware script to get the needed firmware.
What is particularly needed is a disclaimer saying explaining that it is OK to redistribute the firmware.  You are correct though that a grabber would be sufficient.  We actually have a specification planned for this, just need someone to uptake the effort:
[https://blueprints.edge.launchpad.net/mythbuntu/+spec/firmware-finder](https://blueprints.edge.launchpad.net/mythbuntu/+spec/firmware-finder)

---

### Post by twkisner on 2007-12-19
> **hkazemi said:**
> 
Air2PC-ATSC-PCI (1st rev) - supporded but needs firmware The firmware can be obtained as follows: 

$ wget "http://www.linuxtv.org/downloads/firmware/dvb-fe-bcm3510-01.fw"
$ sudo cp dvb-fe-bcm3510-01.fw /lib/firmware
Air2PC-ATSC-PCI (2nd rev) - supported but needs firmware The firmware can be obtained as follows: 

Download this script: get_dvb_firmware 
[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?action=AttachFile&do=get&target=get_dvb_firmware](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list?action=AttachFile&do=get&target=get_dvb_firmware)

$ chmod +x get_dvb_firmware
$ ./get_dvb_firmware nxt2002
$ sudo cp dvb-fe-nxt2002.fw /lib/firmware

That reminds me I need to edit this to add "apt-get install unzip".  No unzip in Mythbuntu...

---

