---
title: "newbie mythbuntu 8.04 questions:  sound and existing library"
date: 2008-08-04
forum: Mythbuntu
---

### Post by chene on 2008-08-04
greetings,

I've just installed mythbuntu to a spare PC of mine.  The intent was to use it as a HTPC:  the PC is connected to my TV, it will be used mainly to play divx/xvid files and FTA, so it acts both as the front/back-end.

My question (for now) is:  how to I integrate my existing video library into mythbuntu?  I tried to copy some video files into /var/lib/video but inside mythbuntu it still says no video found.  How do I initiate mythbuntu to scan my existing video library?

any help is very much appreciated,

---

### Post by SniperKIng on 2008-08-04
Hey

In order for mythtv to see your videos you must first make sure they are in the right location which you have already done (They can be placed in any location as long as you tell mythtv to look for them there.) Then on the main menu you go on Videos and click Video Manager, this should then find them for you. Hope this helped

SniperKIng

---

### Post by chene on 2008-08-04
Thank you.  At first I placed my video files to /var/lib/video but mythbuntu didn't find them.  But after a reboot it re-appeared.

My second question:  The volume played from mythbuntu is EXTREMELY low compared to my other sourced on the same TV.  I've played with the audio settings but doesn't seem to be able to find the right combination to get the volume up to the right level.  I'm using an Asus AMD motherboard (a7v) with onboard sound.

My question question, which is just minor annoyance.... I have a 42" plasma (720p) with a screen resolution of 1024x768.  when I watch a show in 16:9 aspect ration from my xbox XBMC it occupies the entire screen.  However, the same video, when viewed using mythbuntu, will have black-bands above/below the video.  Mythbuntu detects my screen resolution correctly and is set up to 16:9 aspect ratio.  Is there a way to adjust it so that the video occupy the entire tv screen?

thanks in advance,

> **SniperKIng said:**
> Hey

In order for mythtv to see your videos you must first make sure they are in the right location which you have already done (They can be placed in any location as long as you tell mythtv to look for them there.) Then on the main menu you go on Videos and click Video Manager, this should then find them for you. Hope this helped

SniperKIng

---

### Post by SniperKIng on 2008-08-04
Right its me again lol. I had all your problems on saturday when i did a fresh install so hope fully i can help.

Sound - I messed with the setting in myth to no avail before diciding to check the volume of mythbuntu itself which was set to just under full by default. Go to your destop and on the toolbar right click and i think u choose customize or the add buttong if there is one, from there add the speaker symbol to the taskbar. left click it from the bar and u should see the volume controlls just make sure they are all up. That fixed it for me.

Video - Erm my tv is 4:3 but mythtv i think is 16:9 in default so just try changing this to 4:3 it worked for me.

If that doesnt work go in setup click apperance im not sure what page but i think on one of them there is an option to use the same size for tv and menus just tick that and see if it works.

SniperKIng

---

### Post by SniperKIng on 2008-08-04
P.S if you press W during playback it will cycle through play modes but that is just untill you escape the video

---

### Post by chene on 2008-08-05
hi all, 

just an update on how I fixed my sound volume problem.  I don't think it was elegant but it works and will suffice for the moment.  Since mythbuntu uses alsa, I ran "sudo alsamixer" to play with the internal volume control, adjusting each option (pcm and via (my onboard sound)) until the volume reached an acceptable level.  After exiting alsamixer, I used "alsactl store" to save these values so that when the machine reboots the volume will remain the same.

hopefully these will help others,

---

