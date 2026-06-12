---
title: "Mythtv - tuner in use"
date: 2009-07-12
forum: Multimedia Software
---

### Post by ketom2000 on 2009-07-12
When I go to Watch TV the screen flashes black and I am returned to the main menu.

When I go to the Information Center and check System Status, under Tuner Status I see Tuner 1 is unavailable.

When I check the backend server for Capture Card Setup I see that the card type as IVTV MPEG-2 encoder card, Video device is /dev/vidoe0 the probed info is a Hauppauge WinTV PVR-150 (which is correct) and the the default input is Tuner 1.

I can use the capture card using a command line interface, so the card is working.

I just can't watch tv through MythTV.

I can see the schedule fine.

Any suggestions on what to try next?

---

### Post by HappyFeet on 2009-07-12
During setup, did you select the correct modules? By default, it will load the v4l modules. If you do not remember selecting PVRx50 from a pull down menu during setup, i would just run setup again (not reinstall) and carefully look for that. 

Did you add mythTV to ubuntu? I could never get it working right doing it that way. I just installed Mythbuntu and all was right in the world. Btw, I have the same TV tuner card as you.

---

### Post by ketom2000 on 2009-07-12
I took your advice and started from scratch with a Mythbuntu install.  It worked right away.

---

### Post by HappyFeet on 2009-07-12
Great to hear. Are you going to install the ubuntu-desktop on top of it?

---

### Post by ketom2000 on 2009-07-12
Yes.

---

