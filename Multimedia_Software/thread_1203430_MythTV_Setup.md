---
title: "MythTV Setup"
date: 2009-07-03
forum: Multimedia Software
---

### Post by DCGStudios on 2009-07-03
I'm currently trying to get my MythTV on Ubuntu 9.04 working and iv ran into some problems. 
My PC Specs: Nvidia 9800 GTX, Hauppauge WinTV PVR-150, Intel Core 2 Quad 2.3ghz hooking into a LG 720p TV. Im using comcast cable and the wiring seems to be correct. I have worked with MySQL servers before and understand tverhe mechanics but cannot seem to get MythTV to recieve the program list or anything. When i press "Watch TV" it blinks and does nothing. Any ideas or suggustions would be greatly appreciated. Thaks in advance, DCG Studios.  ](*,)

---

### Post by DCGStudios on 2009-07-03
Bump - 

Im now able to login through terminal into mysql, but when I try to configure the frontend I cant login. Any ideas?

---

### Post by Hobgoblin on 2009-07-03
I found [this guide](http://www.parker1.co.uk/mythtv_ubuntu.php) invaluable.

---

### Post by jasonsjunk on 2009-07-03
Make sure you setup the user permissions for the user mythtv and the database that mythtv uses properly.  I am assuming both the backend and the frontend are on the same box.  

As for the program listing did you setup schedules direct?  To the best of my knowledge that is the only way you can get program listings for Comcast.  Mine works fine with Dish network and I have a very similar setup to the one you are using.  

On another note...when you setup the backend did you have it scan for channels.  MythTv needs to see that channel 3 or 4 is a good frequency otherwise you will have problems.  I had issues just trying to go through SVID w/RCA audio, I have both a coax and the SVID connected although all of my recordings are done over SVID.  Myth and the PVR-150 are a bit quirky that way esp if you have a WinMCE PVR-150 like I do.

---

### Post by wellyno1 on 2009-08-24
Hi - I am trying to configure Mythbuntu... I am running into problems because I can't set user permissions for the user "mythtv". Additionally I can't " su mythtv" as I get an authentication error. 

Can anyone help me initially login as "mythtv" from the terminal so I am able to set permissions on files for this user?

Apologies if this is a really dumb question - still getting m head around "other" OS.

Cheers.

---

