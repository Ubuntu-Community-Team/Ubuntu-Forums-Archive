---
title: "Flash on Opera in Ubuntu"
date: 2016-09-14
forum: Multimedia Software
---

### Post by vinayshrinivas on 2016-09-14
There is a lot of contradictory and outdated information on how to get flash working on Opera browser in Ubuntu.  I just went through the process, so thought I should explain the steps for other users who may be in the same position.  I assume you have Opera installed.

1. Download flash player from Adobe [https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/)

2. Go to download location, and run the following command from the command prompt:  tar xvf flash_player_ppapi_linux.i386.tar.gz
This will give you two files: libpepflashplayer.so and manifest.json

3. Now, you need to move these files to a location. This is where things are not clear on the web. The location used is the one that google Chrome would have used.  That is where Opera looks for this plugin.  So do the following:
    3a. Create folder using: sudo mkdir -p /opt/google/chrome/PepperFlash
    3b. Copy both the files libpepflashplayer.so and manifest.json to the above folder

4. Now restart Opera

You should now have flash.

---

### Post by howefield on 2016-09-14
It is easier than that when I install Opera in Xenial 16.04.x

Install the downloaded Opera .deb file with apt and it pulls flash as a dependency.

---

### Post by deadflowr on 2016-09-14
Should just only need to add the canonical partners repository in Software and Updates.
Then install the adobe-flashplugin package, which will pull in the pepperflash plugin automagically,
and then Opera will use that.

It's also the better option as it'll auto-update when regular Ubuntu security updates come.
Security updates you would have to fix manually every time an update came otherwise.

My 2 cents on it, anyway.

---

### Post by dirimemat on 2016-11-27
I'd like to thank you for this post, you saved me :)
I've been trying to install various packages through apt but they didn't work .

---

