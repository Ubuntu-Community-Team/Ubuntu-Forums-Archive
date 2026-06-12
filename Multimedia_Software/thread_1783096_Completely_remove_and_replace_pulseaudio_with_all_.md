---
title: "Completely remove and replace pulseaudio with all issues around"
date: 2011-06-15
forum: Multimedia Software
---

### Post by kovo1533 on 2011-06-15
[B]OK, there are many threads about removing problematic pulseaudio but there is more things to do, so I decided to make one big step-by-step thread that will cover all issues connected with pulseaudio removal as a volume control icon in notification area (system tray), notifications, keyboard shortcuts and etc...  
[/B]

**At first say goodbye to pulseaudio:**
**1. Open console or terminal or what it is named and run this:**
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio  pulseaudio-utils

```

2. Now reboot the computer to let changes take effect and after reboot we can continue with game.
ALSA should take control over the soundsystem after this reboot, my experiences are that sound works also 9 of 10 users reports that no problems are here. If no, search other threads how to install ALSA.

Few things will happen after you remove pulseaudio: you lost volume control icon from system tray (or notification area you know what I mean :D). To fix this we must recompile some packages connected with gnome panels because sicne pulseaudio is used in ubuntus volume applet is missing in pre-compiled distribution packages. Let's strat:
  
**3. Now again open terminal and satisfy depencies to be able to compile source:**
```
sudo apt-get install devscripts build-essential fakeroot
```
```
sudo apt-get build-dep gnome-applets
```

**4. CD to your home directory:** ("cd" is command to "go into" folder)
```
cd ~
```

**5. Make directory** called for example "build":[/B]
```
mkdir build
```

**6. go to this directory:**
```
cd build
```

**7. get source code**
```
apt-get source gnome-applets
```

8. Then when this is done, **don't close terminal** and **open your home directory with file browser** (nautilus) and there should be directory called "build" (because of point number 5) and go into that diretory. There should be some files and a one directory with sources:

[IMG]http://kovo.webovka.eu/linux/ubuntuforum_pulseaudio/1.png[/IMG]

Important for us is name of higlighted folder it can be different in ubuntu versions. In my case directory is called "gnome-applets-2.30.0" I will use that in next steps.

---

### Post by kovo1533 on 2011-06-15
**9. Back to the terminal: go to folder disscused in previous point**
```
cd gnome-applets-2.30.0
```

**10. Then you're going to specify the configure options to enable the mixer applet for compilation. To do that:**
```
gedit debian/rules
```
Look for line that starts with (I think its line 12 but in other versions it could be different so copy this and use find option of gedit CTRL + F) 
```
DEB_CONFIGURE_EXTRA_FLAGS +=
```
I saw two lines here, use the first and add this at the end of line:
```
--enable-mixer-applet
```
Save the file and close.

**11. Now second source fix: **
Little explanation:

[IMG]http://kovo.webovka.eu/linux/ubuntuforum_pulseaudio/2.png[/IMG]

This is how it will look when all will be done. But when you click the button "Volume control" nothing will happen because this button want to run "gnome-volume-control" which is installed only with pulseaudio. We want to open some window with volume bars for PCM, microphone, line in and more. There are lot of programs to do it you can choose one. I am using gnome-alsamixer so install it:
```
sudo apt-get install gnome-alsamixer
```

**12. ...but Back to the "volume control" button fix **  
```
gedit mixer/applet.c
```
search for line containing:
```
gnome-volume-control
```
and replace this expression with name or command to run your program in my case
```
gnome-alsamixer
```
save the file and exit

**13. Now we are going to compile source and build .deb packages**
First install this (i got some error first time, something about gstreamer inproper version i dont remember)
```
sudo apt-get install libgstreamer-plugins-base0.10-dev
```
when done
```
dpkg-buildpackage -b -j4 -D
```
... well this takes some time so sit and do somethnig i'm going to look for beer

**14.** When done, check the directory from step number 8 and **there should appear .deb files**

**15. Back to terminal if .deb(s) are there. Go directory up.**
```
cd ..
``` 
16. Now install all debs with this command:
```
sudo dpkg -i *.deb
```

**17.** We are at the last round of this part. **Now logout/login back to changes take effect.** After doing this right click on panel choose "add to panel" and search for volume control. and "add" it :)

[IMG]http://kovo.webovka.eu/linux/ubuntuforum_pulseaudio/3.png[/IMG]

**18. Yupiiii WE ARE DONE** (at this main part) can to get drunk :D **... only ine important thnig:**
System updates will destroy our long work to protect us against updates open synaptic package manager (in system >> administration ?? >> synaptic) and copy search for this packages:

[B]gnome-applets
gnome-applets-data
gnome-applets-dbg [/B]

... we must tell our system to NOT UPGRADE this packages to do this find the package and from synaptic menu choose "lock version". The packages should be red colored after this.

[IMG]http://kovo.webovka.eu/linux/ubuntuforum_pulseaudio/4.png[/IMG]

---

### Post by handy on 2011-06-15
Thanks for your *first* post, it is the valuable one. :)

---

### Post by handy on 2011-06-15
Now that you have added to your 2nd post I take back what I said about your 1st post. :)

---

### Post by MadhaviPrem on 2011-06-15
Hi Thanks for your post. I am removing Pulseaudio from 11.04. But after pulse audio removal following applications do not play sound
1. Totem Movie player
2. Decibel
3. Bluemindo

Do you have a solution for this . Aso I cannot delete the .pulse folder and .pulse-cookie from the home folder after deleting they appear again after next reboot it means somewhere the Pulse Audio is not uninstalled totally . Thanks

---

### Post by handy on 2011-06-15
The following may give you the info' that you need to get ALSA working as a replacement to pulseaudio:

[http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/](http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/)

---

### Post by beew on 2011-06-15
Why is pulseaudio problematic? I think most threads that advises its removal were based on info when it first came out and it was probably buggy then (I wouldn't know because I wasn't around) but it has been great since 10.04 as far as I can tell.

---

### Post by handy on 2011-06-16
Personally I don't know what the problem(s) are, I use Arch & I chose to use ALSA/OSS. So I have had no experience with pulseaudio.

---

### Post by kovo1533 on 2011-06-19
> **MadhaviPrem said:**
> Hi Thanks for your post. I am removing Pulseaudio from 11.04. But after pulse audio removal following applications do not play sound
1. Totem Movie player
2. Decibel
3. Bluemindo

Do you have a solution for this . Aso I cannot delete the .pulse folder and .pulse-cookie from the home folder after deleting they appear again after next reboot it means somewhere the Pulse Audio is not uninstalled totally . Thanks

try set sound output plugin from pulseaudio to alsa in your players options somewhere, maybe will help ... i had exact problem only with QMMP and this was solution ..

---

### Post by Yellow Pasque on 2011-06-19
No need to reinvent the wheel: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

You will also need to configure apps to use ALSA. Here's the quick way to do gstreamer apps:
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink alsasink
```

---

### Post by kovo1533 on 2011-06-19
**Continue to second part - shortucts and screen notifications**

I will use most of ideas from here: [http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/]("http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/")
This is simillar what we have done in first part - make volume icon with bar available, i used this solution in the past but wasn't pretty specially if you have transparent panel and wanted vertical volume bar and bar will not close or move when manipulating volume with hotkeys and some other details, i like things when they work and are pretty both together.


**1. Install some depencies: open terminal and paste:**
```
sudo apt-get install python python-notify python-gtk2 python-alsaaudio python-eggtrayicon
```

**2. Downolad this:** (is from upper described site)

[http://howto.blbosti.com/files/alsa/alsa_mixer_applet_1.1.tar.gz]("http://howto.blbosti.com/files/alsa/alsa_mixer_applet_1.1.tar.gz")

**3. Extract files (Right click - extract)**

**4. press "Alt + F2" the "run application" should apperar and run:**
```
gksudo nautilus
```
... it is better sometimes to store files somewhere "far away from yourself" to folder where you usually don't go.

**5.** Now when we have root rights **copy files (except file  volbar.py we don't need this one here) to for example /usr/local/bin**

**6. Check if all copied files are executable: **

You can do it by right click and choose "properties" for every file and mark "executable" field (if not) or run this commands:
```
cd /usr/local/bin
sudo chmod +x alsa*

```

**7. go to system >> preferences >> startup applications**
...and add new. Name should be whatever and command:
```
python /usr/local/bin/alsavol.py
``` 

**8. Now add keyboard shortuts. System >> preferences >> keyboard shortcuts** 
**a)** At first you will probably need free your hotkeys from non-working old settings. In "sound" section of shortuts list set another key combination (that you will never use) for actions "volume up" "volume down" and "mute". You must do this because in this section we are not able to edit commands that runs when key combination is pressed. 
**b)** click "add shortut". Name it whatever you want and in command field paste:

for mute:
```
/usr/local/bin/alsa_master_mute
```

for adding volume:
```
 /usr/local/bin/alsa_master_up
```

for vol down:
```
/usr/local/bin/alsa_master_down
```

**9. you should see three newly created items at the end of list** in the column for key combinations you will see "disabled". Click on this word and after that you are asked to push key combination. This worked for me also for "FN + something" keys and special volume keys on my desktop and lenovo S12 ion notebook.

**we are done**

---

### Post by akavir on 2011-08-14
I removed pulseaudio to correct issues with playing some windows games in Wine(Fallout:NV, Call of Duty:MW2)after removal it solved all the problems I had with those applications.  But as stated above, I lost sound from Totem Movie Player, Banshee, and a few other apps.  Not a huge deal because XBMC worked great out of the box.  But I would like to re-enable sound to these apps.  I've tried the above terminal commands and using the gstreamer gui settings to no avail.  Anyone have ideas?

---

### Post by over_my_head on 2012-02-02
Thanks for posting this!
i followed through most of it but i ran into a couple of problems:

> **kovo1533 said:**
> 
**10. Then you're going to specify the configure options to enable the mixer applet for compilation. To do that:**
```
gedit debian/rules
```
Look for line that starts with (I think its line 12 but in other versions it could be different so copy this and use find option of gedit CTRL + F) 
```
DEB_CONFIGURE_EXTRA_FLAGS +=
```
I saw two lines here, use the first and add this at the end of line:
```
--enable-mixer-applet
```
Save the file and close.



when i open this file i find a line that says 
```
DEB_CONFIGURE_EXTRA_FLAGS += --disable-scrollkeeper
```

do i delete the '--disable-scrollkeeper' part and paste in the '--enable-mixer-applet' or do i just paste '--enable-mixer-applet' AFTER the 'scrollkeeper' part?

second issue i ran into was that

when i got to this part:

> 
```
gedit mixer/applet.c
```
search for line containing:
```
gnome-volume-control
```
and replace this expression with name or command to run your program in my case
```
gnome-alsamixer
```
save the file and exit


i couldn't find a line that said 'gnome-volume-control'. i found a couple of comments in the file that said "gnome-volume-applet-name" but no 'gnome-volume-control'.

I'm running ubuntu 11.10. 

thanks in advance!

---

