---
title: "MythTV help"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by newman on 2007-09-03
I've set up MythTV with my ATI HDTV card using the guide here : [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O)

It seems to work but the video is extremely choppy.  However, the main issue is that once I reboot the system, I try to run watch TV and I get a message "mythtv is already using all available inputs for the channel you selected, if you want to watch an in-progress recording select one from the playback menu. If you want to watch livetv cancel one of the in-progress recordings from the delete menu."

I have to run the backend setup again and MythTV will work until the next system reboot.  I have searched for an answer but can't find one.

Please help...

This TV card is the only hardware keeping me tied I have to windows...

---

### Post by studiodaz on 2007-09-03
I am getting this same problem, after trying to get my screen res correctly setup.:confused:

---

### Post by bowmanr@mailcity.com on 2007-09-04
There's some info in this <<http://ubuntuforums.org/showthread.php?p=3306935>> thread that /may/ help.

---

### Post by newman on 2007-09-04
Thanks for the reply. As I've said, I got it to work, but after a system reboot myth no longer works. I have to "modprobe" the tv card and re-run the mythbackend and set everything up again. Somehow it won't keep the settings or something. It's very frustrating, and makes me want to return to windows...  :(

---

### Post by dodongo on 2007-09-04
Hi newman -- Out of curiosity, have you checked your system status to verify what the frontend thinks the hardware is doing?  If you go to the Information Center screen in the frontend, it should tell you about the jobs the backend is working on.  That might provide some clues.

Also, this is just a shot in the dark, but are you only running MythTV off that one machine?  If so, are the backend server settings listed as 'localhost' or a numeric IP address (other than 127.0.0.1)?

---

### Post by newman on 2007-09-04
thanks dodongo
I just started the pc and I went to "system status" in myth.  Under "Tuner Status" it says "Tuner 2 is Unavaible"
Job Que is empty.
Yes I'm running MythTV on this single PC.

---

### Post by dodongo on 2007-09-05
hm.  Does it give you any information about Tuner 1?

---

### Post by newman on 2007-09-06
No
all it says it "Tuner 2 is Unavaible"

---

### Post by newman on 2007-09-06
Now when try to run Myth, it kicks me back to the ubuntu login screen! wtf?  POS

---

### Post by Scorpuk on 2007-09-06
What command do you type in when you modprobe?


You can get your computer to do this automatically for you when it boots each time by adding them to the /etc/modules file.

ie if you did modprobe this_module

you could add it like so:

```
# /etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

lp 
sbp2 
this_module
```

Maybe not a complete answer but something that may, hopefully, help.

---

### Post by dodongo on 2007-09-06
Great advice above with respect to /etc/modules

Also, the fact that you don't have Tuner 1 really raises some red flags for me.  Try the above and see if your situation improves.  If something is still wonky, re-run mythtv-setup completely (i.e., go through all the steps again) and make sure you've set up Tuner 1 (and Tuner 2 as well if you have a dual-tuner card).

It's an aggravating beast to set up, but I promise the results are worth it :)

---

### Post by newlinux on 2007-09-06
> **dodongo said:**
> Great advice above with respect to /etc/modules

Also, the fact that you don't have Tuner 1 really raises some red flags for me.  Try the above and see if your situation improves.  If something is still wonky, re-run mythtv-setup completely (i.e., go through all the steps again) and make sure you've set up Tuner 1 (and Tuner 2 as well if you have a dual-tuner card).

It's an aggravating beast to set up, but I promise the results are worth it :)


The tuner card numbering may be due to the fact Myth doesn't reset the Tuner numbering usually unless you delete *all* the tuners. So each time you add another tuner, it will start as Tuner #1 plus the number of the last tuner that was added. I once had to resetup a couple of tuners so many times I was at Tuner 28. I had tuner 1, 2, 25, 26, 27, and 28 - because the last four I had to resetup so many times while I was still figuring things out. I had to delete them all to get the numbering normal again. So if you reran mythtv-setup and set the tuner up again before deleting the first one and then deleted the first one, you'd only have tuner 2. Otherwise something else is wrong.

Yes, you definitely need to add the module to your /etc/modules or your system won't know to reload that module to control the card after each boot.

if you continue to have problems, take a look at your mythbackend logs, and the output from running mythfrontend from the terminal when you have problems. Post them back and we can probably help you more.

---

### Post by newman on 2007-09-06
> **Scorpuk said:**
> What command do you type in when you modprobe?


You can get your computer to do this automatically for you when it boots each time by adding them to the /etc/modules file.

ie if you did modprobe this_module

you could add it like so:

```
# /etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

lp 
sbp2 
this_module
```

Maybe not a complete answer but something that may, hopefully, help.



THANK YOU!

"sudo modprobe cx88-dvb"

I added cx88-dvb to my modules list and it worked.

I am still getting slow or pausing video, and if I try to run myth in compiz/xgl session, it kicks me to ubuntu login screen.  Myth works in gnome session, but again the video is really slow. 
I tried different settings for the video decoder in myth, but nothing.
I just built this PC with a Gigabyte AMD 690G M/B, AMD 64 x2 CPU, and 2GB RAM. I believe the PC is up to the task. I don't play games so I'm just using the built in ATI Radeon Xpress 1250 video.  I'm using the ubuntu restricted ati driver. I notice I get lots of screen tearing in compiz and in DVD movies or videos, so it must a driver issue or something. I was thinking of getting a Nvidia 8500GT (?) card perhaps, if I can't get decent results with the integrated ATI video. Any suggestions?

Thanks again everyone for your kind help - I'm frustrated but hopeful! :)

---

### Post by newman on 2007-09-06
> **dodongo said:**
> Great advice above with respect to /etc/modules

Also, the fact that you don't have Tuner 1 really raises some red flags for me.  Try the above and see if your situation improves.  If something is still wonky, re-run mythtv-setup completely (i.e., go through all the steps again) and make sure you've set up Tuner 1 (and Tuner 2 as well if you have a dual-tuner card).

It's an aggravating beast to set up, but I promise the results are worth it :)



I'm using an ATI HDTV Wonder card - I wonder if the "tuner1 and tuner2" issue has something to do with the fact that the analog tuner in this particular card is not usable in ubuntu???

thanks again for all your help.

Now just need some help with my video performance / tearing issues! :confused:


BTW - the main reason I wanted to use the integrated video was that my system is so quiet! My last few video cards added a lot of noise to my PC. So I have to get a video card, I'd like a suggestion for a fanless one. I've always had ATI cards, but the driver issues are making me think twice...

---

### Post by Scorpuk on 2007-09-07
I set up my mythtv frontend+backend HTPC using this graphics card and it works a treat:

[http://www.dabs.com/productview.aspx?Quicklinx=4LNB&SearchType=1&CategorySelectedId=11021&SearchTerms=xfx&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=11021](http://www.dabs.com/productview.aspx?Quicklinx=4LNB&SearchType=1&CategorySelectedId=11021&SearchTerms=xfx&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=11021)


Or you could go with something with a little bit more power for not much extra cost:

[http://www.dabs.com/productview.aspx?Quicklinx=4LZH&SearchType=1&CategorySelectedId=11021&SearchTerms=gigabyte&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=50509,11021](http://www.dabs.com/productview.aspx?Quicklinx=4LZH&SearchType=1&CategorySelectedId=11021&SearchTerms=gigabyte&PageMode=3&SearchKey=All&SearchMode=All&NavigationKey=50509,11021)


Of course pricing may differ depending in which country you are in. :)

---

### Post by newman on 2007-09-12
I gave up. Installed Vista. HDTV card works in Media Center without messing around with anything. ATI drivers work - no more screen-tearing or $hitty playback of DVD's in linux. Overall a much smoother experience than ubuntu...:guitar:

---

### Post by dodongo on 2007-09-12
One of the unofficial tenets of the Linux community is that there is no one solution that's right for everyone.  So while your preferred solution may be different than mine, I'm glad you at least got it up and running.

For what it's worth, ATI has been on a long run of having totally crappy support for anything Linux.  You've seen firsthand the frustration that can be induced by a hardware company refusing (or very begrudgingly at least) to support their own hardware.  You couldn't get your hardware to cooperate with the OS; in my case, they decided to completely stop supporting my not-quite 3-year-old graphics card in Linux.  Sorry you got into the middle of that-- it's ugly :)

The good news is that ATI has announced they'll be opening a lot of the relevant docs regarding their hardware to developers, with the obvious intent of improving the support of ATI hardware in Linux.  Enough people are frustrated by the way things are now that massive improvements are just around the corner.

I hope, given some time, you get the urge to experiment again.  It's great fun, and can lead one into to a truly superior platform.   Keep an ear to the ground about support for your card.  We'll all still be here, and in my experience, issues like yours only get better given time.

---

### Post by Hotkey on 2007-11-21
Hi everyone!

I just slipped into this board and this discussion as i'm searching for some informatione for myth tv and ubuntu.
I've just ordered my new HTPC (ASUS P2-M2A690G), and since i don't want to by an additional windows licence i thought this would be the perfect time to use linux. The reason i'm using windows so far is mainly because of the games. so my linux knowledge is very basic.

Unfortunately i never thought about getting a problem with an ATI Gfx Card. In this case the ASUS Barebone has the Integrated ATI RadeonTM 1250 onboard with HDMI out.

After doing some research about Linux, Mythtv and ATI it seems that i will have a problem to get this thing working properly.

Is there someone out there who can give me an info wether this problem with Linux/Ati/Mythtv is still there? Maybe there's someone who actually managed to get this combination working properly? (*crossing fingers*)

Thanks in advance and with best regards

Hotkey

---

### Post by newlinux on 2007-11-21
The drivers are still problematic for ATI, but some have gotten Mythtv to work with ATI cards.  It's hit or miss depending on your system configuration (and specific ATI card) and mythtv needs.

---

### Post by Hotkey on 2007-11-21
> **newlinux said:**
> The drivers are still problematic for ATI, but some have gotten Mythtv to work with ATI cards.  It's hit or miss depending on your system configuration (and specific ATI card) and mythtv needs.

Thanks for the info, are there any do's or don'ts i should know about? As i said, i'm new to linux and i read about differen drivers for ati like "propriet" or "fglrx".
What's the clue about these different drivers?

Thanks again

Hotkey

---

### Post by Cuppa-Chino on 2007-11-23
this would be interesting to follow up, 
a couple of issues you might have with the ATI hardware are that currently there still seems to be a problem with suspend using fglrx drivers - this is due to an issue with the newer kernels and the not-quite up to date drivers, hopefully this will be fixed in the next driver release when it becomes avail for ubuntu.

why am I so interested in this? nvidia has been the linux favourite for awhile but amd has been quite proactive, they released a whole range of gpu specs and an open source driver is being rapidly developed. I am holding fire to see a review of the amd 770g motherboard chipset as I am hoping (bit delusional I know hoping for a new chipset and then wanting to run linux on it).

one thing you can be assured off though with the amd/ati chipset are at least less power hungry than the competition, let us know of your progress

---

### Post by eggert on 2007-11-23
Hi.

I'm trying to run mythtv frontend on a Mitac 8207 laptop.  It has got Ati Radion X1600 video card.

On Feisty I had it running very nice after installing .deb package compiled with fix for Xv error resulting in wrong colors.
After upgrade to Gutsy it took a big negative turn.  As expected the colors were wrong again so I got the sources for mythlib, installed a bunch of dependencies, messed around a bit and managed to compile it with the fix enabled.  Colors are allright now, but the playback is very jerky on video (was too before recompile), with very little motion it is acceptable but as soon as things start moving it is unusable.

Disabling the fglrx driver the video is ok although dropping a few frames and using all the cpu power (accompanied with annoying noise from the fan).  With the fglrx running, mplayer plays the video fine with acceptable cpu usage (40%).

I've been searching for a solution now for 5 hours and am about to give up, but if anyone can point me in a useful direction I'd be very happy.

cheers
Eggert

---

### Post by vkangin on 2008-06-22
Hotkey,

I would gladly appreciate for your comments about ASUS P2-M2A690G & kubuntu. I wanna buy it but not sure that will work well with 1080P under linux. Please advice.

> **Hotkey said:**
> Thanks for the info, are there any do's or don'ts i should know about? As i said, i'm new to linux and i read about differen drivers for ati like "propriet" or "fglrx".
What's the clue about these different drivers?

Thanks again

Hotkey

---

