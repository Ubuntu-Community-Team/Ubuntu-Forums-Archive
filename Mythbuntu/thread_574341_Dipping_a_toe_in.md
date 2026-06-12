---
title: "Dipping a toe in ?"
date: 2007-10-12
forum: Mythbuntu
---

### Post by thesciphishow on 2007-10-12
Greetings all, 

I really like the look of MythBuntu for getting MythTv running on a computer I currently have plugged into the TV. I tried to get MythTV running a while ago now but ran into all sorts of problems, most of which I suspect are now solved. Mainly due to drivers and channel config for the DVB tuner etc. 

So it would seem like a good time to switch from the windows box that is currently setup to do the job.

However the only problem is that although I think my wife would prefer MythTV to the current setup, she would not prefer not being able to use the digital tuner at all.

So is there anyway (and forgive me if this turns out to be a dumb question) to do a live CD boot or something of MythBuntu to see if all the hardware is supported and works before I take the plunge and actually overwrite chunks of the harddisk ? 

I don't need the whole thing running, I just need  to see that the USB wireless adapter comes up (apparently it is supported) and that the TV tuner starts up ok and I can watch some channels. Provided they come up ok all will be well and I can go ahead and trash the windows install, but hopefully you can see the dilemma I have. I don't want to break a functional (if ugly) installation only to discover that the new thing doens't work.

Thanks. 

Jason

---

### Post by 7bigjohn on 2007-10-12
Just install it on another HDD.  I was in the same situation as you were.  Mythbuntu is by far the best Distro yet!

---

### Post by stevetv on 2007-10-12
you can run mythbuntu as a live cd .. but i believe only as a frondend.  which means you need another mythtv computer running on your network.   someone will tell me im wrong if im wrong.

many (most?.. lots of anyway) dvb tuners are supported.  And so long as your other hardware bits arent bleeding edge, they're quite possibly supported too.

the common things things that cause trouble are : motherboard chipsets, and tuners, and configuring sound and lan.  theoretically any hardware that will work with linux will work with mythubuntu.  if youre looking for tv out.. hope you have a nvidia video card or life will be harder.

7bigjohn is right.. you wont know till you try.  you can try to install onto a new partition on your current drive??? ....just put the cd in, and when it loads it will ask you if you want to blank the drive or create another partition.  i havent done this so i don;t know if it works well.

but ubuntu is quite friendly to work with compared to many distros...and ive found quite a good GAF. 

 list your hardware...

---

### Post by superm1 on 2007-10-12
Be mindful which drive the bootloader gets installed on however during install.

Also, You can test the wifi during the live boot mode.  Testing the tv tuner may be possible if you install xawtv or tvtime, or use VLC.  No guarantees there though.  All depends on what kind of tuner you have and how well supported it is in any of those applications. 

VLC is preinstalled on the disk, tvtime and xawtv can be installed via synaptic or apt-get while the disk is booted temporarily.

---

### Post by thesciphishow on 2007-10-12
It would require have a spare HDD to install too that is the concern. 

As for hardware, the hardware of concern is a DVICO fusion DVB-T tuner (which I did get running long ago but it required patched drivers, has that changed ?). The main problem I had there was finding the channel settings for Sydney Australia. 

The network card is a DWL-G132 USB Wireless card from D-Link. Although that could actually be replaced if needed as it doesn't work quite right with the current windows setup anyway (although would be nice to get it fixed). 

It has an ATI Radeon video card at the moment, but I did run the GeeXBox live cd and there was no problem there. The display ran fine. 

Is it possible to do a regular ubuntu live cd run and see if the TV card works and I can get the channels set up ? I'm pretty sure everything else can can made to work ok, but getting the TV part to work is where everything fell apart last time I tried, and that was pretty much the point of the exercise.

---

### Post by thesciphishow on 2007-10-12
> **superm1 said:**
> Be mindful which drive the bootloader gets installed on however during install.

Also, You can test the wifi during the live boot mode.  Testing the tv tuner may be possible if you install xawtv or tvtime, or use VLC.  No guarantees there though.  All depends on what kind of tuner you have and how well supported it is in any of those applications. 

VLC is preinstalled on the disk, tvtime and xawtv can be installed via synaptic or apt-get while the disk is booted temporarily.

Thanks. Is this an ubuntu or a mythbuntu live cd ?

I'll toss the windows install completely if I can just check that those few things actually work correctly. 

Thanks again

Jason

---

### Post by stevetv on 2007-10-12
> **thesciphishow said:**
> It would require have a spare HDD to install too that is the concern. 

As for hardware, the hardware of concern is a DVICO fusion DVB-T tuner (which I did get running long ago but it required patched drivers, has that changed ?). The main problem I had there was finding the channel settings for Sydney Australia. 

The network card is a DWL-G132 USB Wireless card from D-Link. Although that could actually be replaced if needed as it doesn't work quite right with the current windows setup anyway (although would be nice to get it fixed). 

It has an ATI Radeon video card at the moment, but I did run the GeeXBox live cd and there was no problem there. The display ran fine. 

Is it possible to do a regular ubuntu live cd run and see if the TV card works and I can get the channels set up ? I'm pretty sure everything else can can made to work ok, but getting the TV part to work is where everything fell apart last time I tried, and that was pretty much the point of the exercise.

its a mythbuntu live cd.


there are quite a few varieties of DVICO fusion tuners.  almost all of which work fine to my knowledge. you shouldnt have any problems.

im frightened of ati cards as at least until recently their tv out wasnt supported under linux.. but then what do i know.

 you live in australia hey?  to get a working epg you'll need to install xmltv via apt (unless it's been fixed in the latest release), and then create tv_grab_au_reg (just google to find it).  then setup your epg.  let me know if you need help with this.. 

should make a wiki page for setting up mythbuntu in australia?  in the current situation, i think many people will have questions regarding setting up a working epg.

---

### Post by thesciphishow on 2007-10-12
Is "epg" short for episode guide ? 

Actually that is one of the things that doesn't really matter. It would be nice but it actually not essential. 

But thanks for the advice. Seems like this might all be a go. WooHoo

Jason

---

### Post by stevetv on 2007-10-12
epg = electronic program guide.  trust me... after you have it you'll never enjoy life without it.

it also insures you can use all of mythtv's functionality.

for example.. with the epg working, you can tell mythtv what tv shows you like it to record.. for example, the simpsons.. and it will just record all the eps of the simpsons that are shown.  you can tell it to commercial flag some programs but not other.. you can search for programs that will be shown that week... etc etc. 

without an epg, your recordings wont have a name.. you'll have to name them manually.  you dont want to do this.

---

### Post by stevetv on 2007-10-12
epg = electronic program guide.  trust me... after you have it you'll never enjoy life without it.

it also insures you can use all of mythtv's functionality.

for example.. with the epg working, you can tell mythtv what tv shows you like it to record.. for example, the simpsons.. and it will just record all the eps of the simpsons that are shown.  you can tell it to commercial flag some programs but not other.. you can search for programs that will be shown that week... etc etc. 

without an epg, your recordings wont have a name.. you'll have to name them manually.  you dont want to do this. 

if all else fails.. you can use over the air program guide.  your digital tuner will collect broadcast information provided by the broadcasters.  but its only for a few hours to a few days ahead... anyway...

---

### Post by superm1 on 2007-10-12
> **stevetv said:**
> its a mythbuntu live cd.


there are quite a few varieties of DVICO fusion tuners.  almost all of which work fine to my knowledge. you shouldnt have any problems.

im frightened of ati cards as at least until recently their tv out wasnt supported under linux.. but then what do i know.

 you live in australia hey?  to get a working epg you'll need to install xmltv via apt (unless it's been fixed in the latest release), and then create tv_grab_au_reg (just google to find it).  then setup your epg.  let me know if you need help with this.. 

should make a wiki page for setting up mythbuntu in australia?  in the current situation, i think many people will have questions regarding setting up a working epg.
This is one of those items that with all the devs being in other parts of the world gets overlooked.  

If xmltv doesn't install off the RC still, we'll try to get that fixed by release time.

Does that tv grabber need to be setup *before* mythtv-setup is launched for the first time?

Do i understand this correctly?

I also have heard that you need a terminal window to properly configure the grabber during mythtv-setup's run.  We have switched it over so that mythtv-setup launches a terminal window behind it (that you can alt-tab to) for this purpose.

---

### Post by stevetv on 2007-10-12
> **superm1 said:**
> This is one of those items that with all the devs being in other parts of the world gets overlooked.  

If xmltv doesn't install off the RC still, we'll try to get that fixed by release time.

Does that tv grabber need to be setup *before* mythtv-setup is launched for the first time?

Do i understand this correctly?

I also have heard that you need a terminal window to properly configure the grabber during mythtv-setup's run.  We have switched it over so that mythtv-setup launches a terminal window behind it (that you can alt-tab to) for this purpose.

yeah.  xmltv does need to be installed before you can select the relevant tv_grab_xx in mythtv-setup. ideally this would be done before mythtv-setup is run the first time so there is no need to rerun the backend setup.  but it does not NEED to be done before... without it you cannot select an appropriate grabber, but all that means is that the epg will not work right off the bat.  after xmltv is installed, you'd just need to rerun the backend setup and select an appropriate grabber.  after the backend setup is complete, you then need to configure xmltv.  

do you need to open a terminal window at this point?  yes and no.  that is how it has typically been done yes.  a terminal is opened so that one can configure xmltv at that point.  but no it doesnt need to be done at that time.  i've always found it difficult and annoying to configure the xmltv file so I do it later.

for australians it's not possible to configure xmltv right away because there is no tv_grab_au shipped with xmltv. it needs to be created from  the python script from 

[http://www.cse.unsw.edu.au/~willu/xmltv/tv_grab_au_reg](http://www.cse.unsw.edu.au/~willu/xmltv/tv_grab_au_reg) 

the instructions for use are [http://www.cse.unsw.edu.au/~willu/xmltv/tv_grab_au_reg.html](http://www.cse.unsw.edu.au/~willu/xmltv/tv_grab_au_reg.html)

note that there are other tv_grab_au files around.  if youre going to include a tv_grab_au, please include this one as it will work with the community guide.  FYI, the community guide is guide data created by just people like us.  as we only have 5 channels in australia, this is possible.  the community guide provide free guide data to whoever wants it.  you can see the concept here:
[http://www.tuhs.org/twiki/bin/view/TVGuide/WebHome](http://www.tuhs.org/twiki/bin/view/TVGuide/WebHome)

---

### Post by thesciphishow on 2007-10-13
Ok i'm trying the install at the moment and i've run into a problem. Hopefully a trivially resolved one. 

There was some concern expressed over an ATI Radeon card. 

Well i've gone through the boot process, when I just had the ATI card with the TV plugged into it, it wouldn't load. The X-Server just kept crashing. 

So I dragged out the old 15 inch LCD I used to have plugged into the machine and dual headed it. This time the boot has gone through and i've started the live CD frontend. 

However, obviously this is a pretty serious problem with the lack of TV out support. Is this a known problem and can it be resolved because it is basically a show stopper and replacing the video card is not really an option. 

What is weird is that GeeXBox loaded and displayed stuff on the TV through the Radeon card without any issues at all. So I am assuming a real solution does in fact exist to this problem.

---

### Post by stevetv on 2007-10-13
yeah im not certain what ati drivers are installed.  to my knowledge (which is minimal), the ati drivers won't support tv out without a patch.  ive got no real experience with ubuntu so i don't know if this patch is typically included.

heres a link to the patch

[http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html)

have a look if this patch is applicable to the drivers you have installed..  nvidia have quite good drivers for linux, so if you can pick up a cheap nvidia card you'll make your life much easier IMHO. 

having said that, i would think ati would be working hard to improve their driver situation regarding tv out... so things might improve soon.. and superm1 might be able to include the tv out patch in the next release if it's not already ...

---

### Post by thesciphishow on 2007-10-13
Any suggested fixes that don't involve patcihing the kernel ?

---

### Post by superm1 on 2007-10-13
> **thesciphishow said:**
> Any suggested fixes that don't involve patcihing the kernel ?

Use the proprietary fglrx driver.  It supports TV-Out.

---

### Post by thesciphishow on 2007-10-13
Thanks. Guess what my next question is. 

Is that the proprietary driver it wants me to set up with the restricted drivers option window ? It didn't seem to do anything. Is that the part I want or should I be going through [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) to get it to work. OBviously without the network this is going to be a problem. 

Also, I ran into trouble with the USB network dongle. According to dmesg it seemed to detect it and also notice when I plug and unplug, but how do I configure it for use ? There didn't seem to be wifi setup for anything in the menus at the install/live front end, page when I got to it. 

IT did seem to detect the TV card and put an option in for it, but when I tried to open the DVB card in vlc the log was full of timeout messages.

---

### Post by Wuffles on 2007-10-14
Just regarding a good epg for Australia, I highly recommend that you look at shepherd: [http://svn.whuffy.com/index.fcgi/wiki/Installation](http://svn.whuffy.com/index.fcgi/wiki/Installation)

---

