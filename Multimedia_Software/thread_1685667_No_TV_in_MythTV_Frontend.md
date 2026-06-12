---
title: "No TV in MythTV Frontend"
date: 2011-02-11
forum: Multimedia Software
---

### Post by alex341 on 2011-02-11
After overcomming a lot of difficulties, my MythTV (Via Epia 10000EG with Hauppauge PVR 500 card) worked with Mythbuntu 9.04. Last year it crashed and I had no time to spare to rebuild it. 
 
Last couple of weeks I had more time and downloaded and tried to install Mythbuntu 10.10. Everything seems to be installed ok, but I get no picture in MythTV when I select "Watch TV" and no picture when I try to record something. When watching TV, the message "Please wait" appears for appr. 5 secs and then the system returns to the menu.
 
I installed Mythbuntu 10.10 and am using the provided IVTV drivers.
 
Dmesg and lspci give no errors, every seems to be in order, IVTV drivers are loaded, initialized and errorfree.
Cat /dev/video0 gives me static in MPLAYER.
The MythTV backendlog doesn't even give a message, the frontend log just says there is no picture...
 
There seems to be an error between the back and frontend. I checked the settings in capturecards, TV sources, channel edits, etc,etc, but I can't find it. Who can help me?

---

### Post by x53x6ex69x67x67x65x72 on 2011-02-11
Hi
I had same problem and it was because destination folders was not writable by mythtv

---

### Post by alex341 on 2011-02-12
Mythtv is owner of the directories. Made the directory available for everybody (chmod 777 directory), but no change, no live tv...
 
Anyone else a sugestion?

---

### Post by x53x6ex69x67x67x65x72 on 2011-02-12
check mythtv-setup for livetv directory when I changed it I had same problem but when I reseted it to default dir it fixed.

---

### Post by alex341 on 2011-02-13
No change...

---

### Post by screwbunt2 on 2011-02-14
@X53 - 

Could you be more specific about which menu and sub menus you are talking about to set the recording folder? Are you talking Frontend settings or Backend settings.

I've used Mythbuntu for a couple years with my PVR-350 & PVR-500 tuners with no trouble. Now since I've upgraded to 10.10 it's been nothing but headaches. I also get a black screen when trying to watch Live TV and after several seconds an error about excessive buffering retries (sorry don't have the message now).

BUT...  sometimes when I try to go back into Live TV I will get a picture and can watch TV, unless I try and change channels, then I have the same problem.

I didn't change any drivers or any folders, and since it sorta works, it seems more like some setting. I'm willing to look and try the directory suggestion if you can tell me where to find it.  My setup is a combined FE/BE.

Thanks!


UPDATE:

It looks like I might have solved my own problem. It's really strange that everything worked before the upgrade and I was still able to get lucky and watch a channel sometimes. So I went into Synaptic package manager and searched for IVTV and NONE of the drivers or support packages were installed. I installed ivtv-utils, libvideo-ivtv-perl, and xserver-xorg-video-ivtv. I rebooted and now I'm back where I was before the upgrade.

---

### Post by screwbunt2 on 2011-02-14
ALEX341 - 

I remember almost pulling my hair out trying to get my tuners working and seeing the same problems you are having. I'm trying to remember what I found. I think the PVR tuner cards have several input/outputs and I had picked the wrong one. It was a backend setting, where you add the tuners there is/was a drop down menu you could pick a different input from the card. Sorry it's been awhile, see if you can try finding that and if you find the input that works for you. I'll poke around and see if I can find it and update this post.

UPDATE: Ok, on the BACKEND setup, check out 4) INPUT CONNECTIONS. You should notice /dev/video0 has several different choices, like TUNER, S-Video, and Composite. Also, if you're seeing static, did you make sure your antenna/cable connection is good?  Do you have a digital converter box for over the air, or do you have cable?

---

### Post by alex341 on 2011-02-15
God, I feel stupid... In the frontend, in the setup, you can set your tv settings and CPU usage. I have changed everything in the backend, but nothing worked. 
 
Afster I changed a couple of settings in the front end (CPU usage to minimum, killed all processes in the backend), it worked... I got a picture!!! (Still don't have sound, can't find the first channels, don't have EPG, but the basis is there).

---

