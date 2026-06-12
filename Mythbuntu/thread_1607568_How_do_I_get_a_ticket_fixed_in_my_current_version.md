---
title: "How do I get a ticket fixed in my current version"
date: 2010-10-27
forum: Mythbuntu
---

### Post by bcg30506 on 2010-10-27
This issue has been bugging me for some time:
[Ticket 6771]("http://svn.mythtv.org/trac/ticket/6771")
However, it seems it was marked for release in 0.24 even though the change has been made.  I'm on 0.23.1-fixes and have no interest in moving to 0.24 especially this early in its cycle.

What is the best way to fix this in my version without anything else changing?  Do I have to change/build from source myself?  If so, how?  How do I know the configure options used for what I'm running since it came from a repository and I did not compile it?

---

### Post by tgm4883 on 2010-10-28
You would need to download the source for 0.23/0.23.1 and see if the patch applies cleanly. Then compile the code if it does.

---

### Post by bcg30506 on 2010-10-28
How do I ensure everything is configured EXACTLY how I've got it now?  I did not build this myself but am running the version from mythbuntu's auto-builds.  Instead of downloading the source from mythtv's site, can I just install the mythtv-dev packages from the repository and that will give me the source and current config?

I have everything else working great and really don't want anything at all to change except for this broken feature to be fixed.

Any chance this ticket will be backported to 0.23.1-fixes?

---

### Post by azmyth on 2010-10-28
You won't lose your config settings on an upgrade. You'll have to either upgrade to 0.24 or add the patch to the source code of 0.23 fixes and then compile yourself.

---

### Post by bcg30506 on 2010-10-28
I guess this is my confusion:  What config settings?  I did not compile what I have now.  I installed it with apt-get.  I don't even have the source at the moment.

So, can I get the source via apt-get?
Will it have the config setup to match what is installed now?
Do I have to build every piece or just the frontend with the patch?

Thanks.

---

### Post by rhpot1991 on 2010-10-28
If you have a src line for the autobuilds then all you need to do is apt-get source and you will be able to build with the same configuration that the autobuilds uses.

---

### Post by bcg30506 on 2010-10-28
> **rhpot1991 said:**
> If you have a src line for the autobuilds then all you need to do is apt-get source and you will be able to build with the same configuration that the autobuilds uses.

Thank you!  This what I was trying to figure out.  Never having done this before, would this command be correct:

```
sudo apt-get --compile source mythtv
```

to get the version I have installed and rebuild a .deb file from the source?  I understand I'll need to put the patched source changes in and compile manually, but am trying to get a big picture handle on the process.

---

### Post by bcg30506 on 2010-10-28
Got it working!!!  There were quite a few steps as I did not have a devel environment and it was trial & error plus Googling, but it built, I made the source changes manually from the TracLog, rebuilt and copied the new .so file to the plugins directory and restarted the frontend.  Voila!  I now have exif display in 0.23.1-fixes.

Here were the steps from a clean directory:
```

apt-get source mythgallery
cd mythplugins-0.23.1+fixes26863/
sudo apt-get install libqt4-dev
sudo apt-get install libmyth-dev
sudo apt-get install libexif-dev ccache libfreetype6-dev libmp3lame-dev libasound-dev libjack-dev libraw1394-dev libiec61883-dev libavc1394-dev libXv-dev libXvMC-dev
./configure --prefix=/usr --disable-mytharchive --disable-mythbrowser --disable-mythgame --disable-mythmusic --disable-mythnews --disable-mythvideo --disable-mythweather --disable-mythzoneminder --disable-mythmovies --disable-mythnetvision --enable-exif --enable-new-exif --enable-opengl
make
cd mythgallery/mythgallery/
vi singleview.cpp  #make changes and save
cd ../..
make
cd mythgallery/mythgallery/
cp /usr/lib/mythtv/plugins/libmythgallery.so libmythgallery.so.OLD
sudo cp libmythgallery.so /usr/lib/mythtv/plugins/

```
I've attached the updated singleview.cpp file for any interested.  I've also attached a screenshot showing it working.

---

