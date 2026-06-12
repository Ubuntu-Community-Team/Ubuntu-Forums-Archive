---
title: "i915 ivybridge HDMI goes blank after power saving"
date: 2014-02-17
forum: Multimedia Software
---

### Post by Lei_Jiang on 2014-02-17
Hi,

I have an HTPC/server with an i5 3570 CPU on a z77 mobo. The OS is Ubuntu server 12.04 and I installed xfce and xbmc on top of it. The video output goes out of the onboard HDMI port, through an AV Receiver and finally into my Panasonic TV. And I have 2 issues currently.

First one is when starting the OS, I have to turn on the TV. Otherwise X.org won't be able to figure out the display and the screen will never be right. But this is something I can live with because I rarely turn off the box.

The second one is, once I leave the box untouched for a while, the video goes into power saving, there will be a very good chance the screen will be blank when I turn the TV back on. Since I am running xbmc, I set it to the standalone mode and it is the default DE with timed login. I have found that killing xbmc actually will fixes it. Gdm will spawn xbmc automatically in a few seconds so that is my current solution. But it is much too inconvenient to do so every time I start watching a movie. 

Also there are a few things worth noting.

#1, This only happens to ivybridge(or onward maybe). I had an i530(Ubuntu 11.10) box earlier but did not have this problem
#2, This seems to have a lot to do with the i915 driver. If I do not turn on TV when system boots, the display is screwed no matter how I kill xbmc, gdm or X itself.
#3, The audio part is still working after power saving. When the blank screen happens, I still can hear xbmc audio from my AVR.

I googled quite a bit and it seems for some people, setting the EDID fixes their display detection problem. So I tried using a windows program to grab the TV EDID and then set it using KMS but with no success. Some said manually setting TV mode lines in X config works but the examples given are all in Xorg.conf form and the X config in Ubuntu now uses conf.d and I'm not sure what to put in there. Also someone said turning of power saving fixes this but that's does not sound good to me.

Could someone please give me a point in direction as how to troubleshoot this? Which log files to check and what to look for?

Thanks a lot!

---

### Post by squakie on 2014-02-18
I don't know about everything you've mentioned, but with XBMC you did go into settings and turn off the screen saver, right?  I also had trouble with screen blanking after the XBMC screen saver time out.  Just setting it to none fixed it for me.  OF course, you'll probably want to check the ubuntu screen saver as well - think there is a setting under power options to not blank the screen or go to the screen saver.

---

### Post by Lei_Jiang on 2014-02-19
Thanks for the advice!

I tried yesterday and it did not work. The xbmc power saving was disabled by me already. And it does not seem to have anything to do with the screen anyway. The options are, sleep/hibernate/shutdown the OS after how many minutes of inactivity. And the xbmc screen saver was just dimming the screen to 20% brightness. I disabled it as well but then the screen still went blank after some 10 minutes.

Through google I find people are also having trouble with xscreensaver. The default screen saver is blank screen and default time is 10 minutes. Very suspicious, so I tried disabling it. But it did not fix the issue, either. When the screen is blank I tried ssh into the box and xscreensaver-command -deactivate for display 0 to 10. Most said 'no display' while 0 and 10 said xscreensaver is not running. So this is a dead end, too.

The monitor power saving, at least from the gnome screensaver configuration dialog, seems to be off. And I tried both methods in [this post]("http://forum.odroid.com/viewtopic.php?f=52&t=2410") to disable the xscreensaver and dpms with no success. Curiously I can see the DPMS is on in Xorg.0.log. I will try to turn it off completely today and see if it works.

Another thought from me now is that this may not have anything to do with screensaver or power saving at all. Since it actually only happens when I turn on the TV after it has been off for a while. And the TV seems to have a 'wait' period before it really goes off(if I turn it back on in 1 or 2 minutes it starts up really quickly and never has the blank screen). I am starting to think this is due to the hand shake failure between X.org and the TV. I will try to configure display manually and see if it works.

---

### Post by Lei_Jiang on 2014-02-20
Hi,

I tried using an explicit x.org.conf yesterday. The x.org part went well. I used most of the sample config file from [OpenELEC ]("http://wiki.openelec.tv/index.php/Configuring_a_Custom_xorg.conf#tab=Intel")and it worked. But it solved neither of the problem I had.

However, I found something that might be useful.

#1 When I turn on the TV, in syslog there are quite a few lines complaining the EDID received is invalid. And there will be one line complaining something like intel graphics gen6 power saving error. I googled about the gen6 error and it seems to be a bug either in kernel (likely) or in the intel driver.
#2 After that, the screen is blank. I can connect a keyboard and try to switch to one of the text consoles using Ctrl-Alt-Fn. And viola, I have the display. And then when I switch to X, everything's back. And simultaneously, I can see an 'HDMI hotplug event' in the syslog. This is very interesting. Because by my understanding, this is to say that the kernel only thinks the HDMI connection is back when I switch the console! Now it looks rather like a kernel bug.

I am running the official 3.2.0 kernel and I am considering to get one of the experimental versions to see if the blank screen is fixed.

---

### Post by Lei_Jiang on 2014-02-23
Hi,

For the record.

I upgraded kernel to 3.5.x as well as the quantal xorg. There is little improvement or even a bit worse. Now switching to text console no longer triggers HDMI hotplug and I get a blank screen all the time. But indeed the EDID errors in the syslog is gone. If anyone wants to try these simply install [FONT=Ubuntu Mono]linux-image-generic-lts-quantal[/FONT] and [FONT=Ubuntu Mono]xserver-xorg-lts-quantal[/FONT].

---

