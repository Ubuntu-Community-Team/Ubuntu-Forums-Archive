---
title: "Front end crash"
date: 2010-02-25
forum: Mythbuntu
---

### Post by benlyboy on 2010-02-25
Help 

Came home from work today to find that the front end on my mythbox had closed. I tried to restart. but nothing happens when I click in it. I also can not open the backend setup, again nothing happens if I try to open it.

I know that the backend is still working, as I can still use it through mythweb.

The only thing I can think of is that I did an update ether last night or the night before and there was an error at the end of that. But all seemed fine after that.

Any ideas where I should start...?

I tryed opening the front end from terminal by typing "mythfrontend" but received this notice"bash: /usr/bin/mythfrontend: permission denied.

this is from the front end log

2010-02-24 22:00:02.219 [mpeg2video @ 0x7f1b4b0db300]warning: first frame is no keyframe
2010-02-24 22:00:02.397 [mpeg2video @ 0x7f1b4b0db300]warning: first frame is no keyframe
2010-02-24 22:01:17.927 NVP(0): prebuffering pause
2010-02-24 22:01:23.940 TV: Attempting to change from Watching WatchingLiveTV to None
2010-02-24 22:01:23.947 [mp2 @ 0x7f1b4b0db300]incomplete frame
2010-02-24 22:01:23.948 AFD Error: Unknown audio decoding error
2010-02-24 22:01:24.504 TV: Changing from Watching WatchingLiveTV to None
2010-02-24 22:01:24.838 SendReceiveStringList(MESSAGE,SYSTEM_EVENT PLAY_STOPPED SENDER mythbox) called from UI thread
QMutex::lock: mutex lock failure:
QMutex::lock: mutex unlock failure:

---

### Post by benlyboy on 2010-02-26
please any ideas? 

I Have no idea where to start. I don't want to have to start over with a reinstall, as I have just got my box to the point where everything was working great.

---

### Post by nickrout on 2010-02-26
have you rebooted?

---

### Post by benlyboy on 2010-02-26
Thanks for the reply

Yes I did try rebooting



It boots up to the decktop but no front end

---

### Post by benlyboy on 2010-02-26
Ok an update 

Had a look in /usr/bin and found a executable file called mythfrontend.real.
So I ran this in Terminal and my frontend appeared. and it seems to work fine.

The backend setup still doesn't work through. 

Does this give anyone any ideas as to what is going on...?

---

### Post by jimmyoo0 on 2010-02-26
I have exactly the same problem, and as you say "/usr/bin/mythfrontend.real" works and so does "/usr/bin/mythtv-setup.real" but not "mythfrontend", "/usr/bin/mythfrontend", "mythtv-setup" or "/usr/bin/mythtv-setup"

I am running mythbuntu repos 0.23  trunk [23612]

I first noticed this yesterday just after i updated, i then updated again this morning hoping that would fix it but it hasen't.

I also tried un-installing and then reinstalling but that didn't make any difference.

So really just confirming, and that it affects me too but i wouldn't have a clue where to start to fix it.

---

### Post by benlyboy on 2010-02-26
I am running the same trunk as you.

I guess it was the update...thanks for letting me know

---

### Post by benlyboy on 2010-02-27
ok fixed it .

Both the frontend and the setup file showed up as "links to a shell script"

First up I made copies of both the "mythfrontend" and the "mythtv-setup"
calling them "mythfrontendtemp" and "mythtv-setuptemp".

Then copied my temp files back to the frontend and setup file.
this seemed to change it from a link to a script into a script file

like this 

sudo cp /usr/bin/mythfrontend /usr/bin/mythfrontendtemp 
sudo cp /usr/bin/mythfrontendtemp /usr/bin/mythfrontend 

Do the same for setup


After this my frontend worked right off, however my mythtv-setup still didn't work.

I then took a look at the permissions for the file and saw that it was not set to be executable 
so changed this and it now works.

sudo chmod ugo+x /usr/bin/mythtv-setup

There maybe a better way to do this but this is what worked for me...
Hope this helps others

---

