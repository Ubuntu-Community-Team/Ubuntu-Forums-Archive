---
title: "Issues with 8.04 64bit frontend"
date: 2008-08-07
forum: Mythbuntu
---

### Post by gsrcrxsi on 2008-08-07
well im having a few issues with my frontend that ive recently moved to 8.04 64bit. 

first. the screen settings will not stay put after a reboot. when it starts up it loads everything in 1024x768. on my SD tube TV, this makes text hard to read and a pain. everything looks great at 800x600, but it wont stay put. ive tried saving the settings to xorg.conf but it gives an error saying it cant create the backup. this was all done via the nvidia x server settings menu. i didnt have this problem under 7.10 32-bit.

second. the program guide is VERY laggy. it doesnt matter what the settings are put on it lags to all hell. it takes a good 20 seconds for it to respond. then it will stop responding all together. but if i ctrl+alt to another desktop, it responds. i dont have this issue on my backend w/frontend running the same OS, and i didnt have this issue with 7.10 32-bit.

---

### Post by Dark Hornet on 2008-08-07
The reason you are unable to save to your xorg.conf file from nvidia x server is because you are not running that program with the proper permissions.  Try running it with admin access.  I had this same issue when I was setting up my dual screen set up, and the nVidia gui would not let me save to my xorg.conf file.  The issue was the permissions.  Once I changed that, everything worked great!

Good luck!

---

### Post by gsrcrxsi on 2008-08-07
hmm that seemed to work (wont know til i reboot), thanks. 

what about the other issue?

---

### Post by Dark Hornet on 2008-08-08
I am not sure I know what you mean by "program guide"...are you referring to your TV program guide?

---

### Post by gsrcrxsi on 2008-08-08
yes. you know, when you press the "guide" button on the remote. where you scheduel recordings and see the TV show listings. its VERY slow.

---

### Post by Dark Hornet on 2008-08-08
Cool...I am assuming that you are running your TV through some sort of media program on your computer--let me know if this is not the case.  

If so, what is this program, and is it fully 64 bit compatible, is it still in beta, does it have any known bugs?  Is your GFX card powerful enough to run this size monitor?

Sorry for all of the questions, I am just trying to get a good base so I can more accurately help you.

---

### Post by gsrcrxsi on 2008-08-08
im sorry if this comes off as rude, but we are in the mythbuntu forum. im talking about mythtv. my OS is mythbuntu 8.04 64-bit. so yes its a media program, and yes, its 64-bit compatible.

graphics card is a non issue, the screen is only running at 800x600 res, its a 36" tube SDTV. plus it worked perfectly before, so hardware isnt the issue.

---

### Post by Dark Hornet on 2008-08-08
You will have to forgive me...I didn't realize that this was the Mythbuntu part of the forum...I monitor the various Ubuntu threads through Google Reader, and I saw this one...so all of the various threads get jumbled in with each other.

In response to this particular part of your issue, I am probably not the best person to help, as I have no experience with Mythbuntu.  Other than to say...make sure non of your dependencies are corrupt, etc...did the issue start after an update?

---

### Post by gsrcrxsi on 2008-08-08
this is a fresh install. so for the total of about 2 days that its been installed on the frontend the guide hasnt worked properly, verly slow response and occasionally will lock up there (the PIP still works fine in the guide).

everything else works perfectly

---

### Post by gsrcrxsi on 2008-08-09
up

---

### Post by gsrcrxsi on 2008-08-09
hmm i seem to have done the trick. it was already on Qt painter. but i changed the playback profile from CPU+ to normal and its worked fine. then after a reboot it was messed up again. all the settings were the same but it was laggy again. so then i changed it to Slim and its working again. im afraid to reboot in fear that ill have to switch it again after reboot. i mean it works but its annoying to have to do that after every reboot. thoughts?

also my color correction in nvidia settings doesnt load up after a reboot. i have to open nvidia settings for it to make the change. it saves the settings, just doesnt apply them until nvidia settings is opened back up.

---

