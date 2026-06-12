---
title: "Three problems I've had, could you please help?"
date: 2007-10-05
forum: Mythbuntu
---

### Post by DucoNihilum on 2007-10-05
In order of my priority.

1. I got my PVR 150 with the remote. I want to set up the remote properly. I picked the hap remote in the setup, but it didn't work well (most of the buttons didn't really work correctly, most notably channel up / down), I tried another hap remote setting (which didn't work at all) and then moved it back to my old one. Now not only do the keys not work properly, but it inputs my command 2-3 times, so if I wanted channel 05, it would go on the screen 00 55 or even 000 555..... How can I fix this? 

2. My channel listings from listing direct aren't entirely accurate, the channel name (like CSPAN) show up as "Adding Channel [Channel number]". I contacted schedules direct about it, and they told me to follow the instructions on this page. [http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295](http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295)
I tried, I got to this part

Schedules Direct registration required in advance.
Sign up at [http://www.schedulesdirect.org](http://www.schedulesdirect.org)
(don't forget to add a lineup!)

It said zap2it not schedules direct. So... won't work.

I found out that I was using XMLTV module version is 0.5.45 when schedules direct requires me to use  XMLTV 0.5.48 as a minimum.  How can I update this?

3. I have an extra 40GB hard drive I want to use for space, I have it plugged in, and it's a slave. It has data on it, i'd like to format it. How can I do this (and let mythbuntu use it?) I'm a noob to linux and haven't been able to figure it out.

---

### Post by superm1 on 2007-10-06
> **DucoNihilum said:**
> In order of my priority.

1. I got my PVR 150 with the remote. I want to set up the remote properly. I picked the hap remote in the setup, but it didn't work well (most of the buttons didn't really work correctly, most notably channel up / down), I tried another hap remote setting (which didn't work at all) and then moved it back to my old one. Now not only do the keys not work properly, but it inputs my command 2-3 times, so if I wanted channel 05, it would go on the screen 00 55 or even 000 555..... How can I fix this? 


This has been a bit of a complaint for a few people.  We're going to try to have it generate better results for these remotes by RC.  Hopefully :)

> 
2. My channel listings from listing direct aren't entirely accurate, the channel name (like CSPAN) show up as "Adding Channel [Channel number]". I contacted schedules direct about it, and they told me to follow the instructions on this page. [http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295](http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295)
I tried, I got to this part

Schedules Direct registration required in advance.
Sign up at [http://www.schedulesdirect.org](http://www.schedulesdirect.org)
(don't forget to add a lineup!)

It said zap2it not schedules direct. So... won't work.

You need to update xmltv as described below.

> 
I found out that I was using XMLTV module version is 0.5.45 when schedules direct requires me to use  XMLTV 0.5.48 as a minimum.  How can I update this?

Open up the update notifier item and let it check for new things.  There is a new xmltv that was uploaded to repositories two nights ago.  It will be included in the RC as well.

> 
3. I have an extra 40GB hard drive I want to use for space, I have it plugged in, and it's a slave. It has data on it, i'd like to format it. How can I do this (and let mythbuntu use it?) I'm a noob to linux and haven't been able to figure it out.

Install gparted from synaptic.  It's pretty straightforward to use for formatting and such.

---

### Post by DucoNihilum on 2007-10-06
> **superm1 said:**
> This has been a bit of a complaint for a few people.  We're going to try to have it generate better results for these remotes by RC.  Hopefully :)


You need to update xmltv as described below.


Open up the update notifier item and let it check for new things.  There is a new xmltv that was uploaded to repositories two nights ago.  It will be included in the RC as well.



Install gparted from synaptic.  It's pretty straightforward to use for formatting and such.

I don't know how to open up the update notifier item or install gparted from synamptic. I only have mythbuntu and I'm not very good at working in a CLI.

---

### Post by superm1 on 2007-10-06
> **DucoNihilum said:**
> I don't know how to open up the update notifier item or install gparted from synamptic. I only have mythbuntu and I'm not very good at working in a CLI.
No prob, don't need to touch command line.

Quit Mythtv, and you will brought to a desktop.  Click the applications menu.  Choose system.  Synaptic is listed there and so is Update Manager.

---

### Post by DucoNihilum on 2007-10-06
> **superm1 said:**
> No prob, don't need to touch command line.

Quit Mythtv, and you will brought to a desktop.  Click the applications menu.  Choose system.  Synaptic is listed there and so is Update Manager.

I'm brought to a logon screen that automatically logs me onto mythTV. There's no area for 'applications'

---

### Post by superm1 on 2007-10-06
> **DucoNihilum said:**
> I'm brought to a logon screen that automatically logs me onto mythTV. There's no area for 'applications'
You need to be on the beta release for this area to work.

Considering your uncomfort with the command line, i would recommend a fresh install from the beta disk.

If you change your mind and want to upgrade by hand, follow this thread: [http://ubuntuforums.org/showthread.php?t=567329](http://ubuntuforums.org/showthread.php?t=567329)

---

### Post by DucoNihilum on 2007-10-06
Alright, I now have the latest version for schedules direct, and schedules direct does show the listings correctly when I follow the steps..... but they don't show up correctly in my actual channel guide. It still shows "Adding Channel X"

ALSO- I partitioned the other drive as expanded 3 or some sort, but it's not showing up as space I can use with mythbuntu.

---

### Post by dannyboy79 on 2007-10-08
are you using the Scan For Channels? If so, that's wrong. You need to setup a Source first, pull down the lineup, then exit that, go to inputs, then create an input, then chose hte source you just created from the list, then tell it to "retrieve listings from source". It should pull down all your channels. when you exit mythtv-setup, then it'll run mythfilldatabase which is what you want. that should be it. ALSO, a note of caution. Sometimes it helps if you "delete all cards", then recreate your tuner card, then associate your source with that card within inputs, and that's it.

---

### Post by DucoNihilum on 2007-10-10
> **dannyboy79 said:**
> are you using the Scan For Channels? If so, that's wrong. You need to setup a Source first, pull down the lineup, then exit that, go to inputs, then create an input, then chose hte source you just created from the list, then tell it to "retrieve listings from source". It should pull down all your channels. when you exit mythtv-setup, then it'll run mythfilldatabase which is what you want. that should be it. ALSO, a note of caution. Sometimes it helps if you "delete all cards", then recreate your tuner card, then associate your source with that card within inputs, and that's it.

Alright, thanks. That worked. 

Now I still have two problems.


1. Remote doesn't work- does anyone know when / if this will be fixed, or if there is a workaround?

2. I can't figure out how to properly extend that drive over. 

3. I have an external hard drive I'd like to transfer some of my recording over to, but I can't drag and drop anything- something to do with mounting....

---

### Post by dannyboy79 on 2007-10-11
Issue 1:
use irw to check what the buttons are called when you push one. FOr example, I downloaded a lircrc for mtthtv that says it was compatible with mythtv but my channel up and channel down didn't do anything either. So I just started irw, then pushed the channel up button and it shows, ch+ and ch-. When I went back into the /home/username/.mythtv/lircrc to see what the files contained, it actually had Channel Up, obviously this isn't correct, so I changed it to match what irw was showsing, restart my machine and sure enough, now the buttons that weren't working work correctly.
Issue 2:
I have no idea what this means?
Issue 3:
plug in your external drive, then issue the mount command, look toward the bottom of the output and read whether it's getting mounted with read/write permissions or not. Do you have read/write on the folder it's getting mounted to?

---

