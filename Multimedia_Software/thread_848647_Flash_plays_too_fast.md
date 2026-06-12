---
title: "Flash plays too fast"
date: 2008-07-03
forum: Multimedia Software
---

### Post by monkman on 2008-07-03
ubuntu 8.04 32bit
flash-plugin-nonfree 9.0.124
firefox 3.0
opera 9.51
c2d e6400
2gb ram


when playing flashvideos it's like smurf is singing, because it plays too fast. i don't know where to change it. is there even a chance to change it?

thx!

---

### Post by |{urse on 2008-07-03
try this.

sudo killall powernowd

---

### Post by monkman on 2008-07-03
powernowd: no process killed

i guess i don't have this service running, so no change in smurf singing here...

---

### Post by cpetercarter on 2008-07-03
Is it all videos that have this problem, or just some? There is a well-known problem with Flash that, unless the audio is recorded at a sampling rate which is an even multiple of 11.025kHz, it sounds like Alvin and the Chipmunks.

---

### Post by monkman on 2008-07-03
all videos on sites like youtube.com, myvideo.de etc...

---

### Post by |{urse on 2008-07-03
only solutions i have seen are to remove your current flash plugin

sudo apt-get purge flashplugin-nonfree

and install the latest beta

on this page

[http://labs.adobe.com/downloads/](http://labs.adobe.com/downloads/)

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz)

> Linux (.tar.gz)

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.


---

### Post by monkman on 2008-07-03
thx, i'll try that out tomorrow, on my notebook it runs fine. strange...

maybee because i had to decrease the frontside bus on my system? with the original it's quite unstable... from 250 to 245MHZ (asrock 775i65G)

---

### Post by monkman on 2008-07-04
the installation of flash 10 didn't solve it. i tried flash on the win2k which runs in dual boot here. there it's okay, so no hardware issue with timing, as i thought earlier. what can i do now?

thx!

---

### Post by monkman on 2008-07-10
solved by reinstallation of system...

---

