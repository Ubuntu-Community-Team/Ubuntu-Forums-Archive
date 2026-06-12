---
title: "Resolution stuck at 640x480"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by anndruu12 on 2007-06-12
Hello everyone. I am a brand new linux user. Just downloaded and installed Ubuntu 7.04 yesterday so I know absolutely nothing about the OS. The whole reason I downloaded it was to play around in it and learn more about it to try and diversify myself. I work as a computer tech but only ever deal with Windows machines. I know my way around Windows no problem but Linux is a whole new beast for me. 

Already within my first day I have run into my first problem. I installed Ubuntu with no problems. However once it was fully installed, my resolution never changed from 640x480. When I go into Screen Resolution Preferences, and click the box to change it but no other options come up besides 640x480. From what I read, this seems to be a commom problem but I was unable to find a solution that worked for me. I am running Ubuntu on a old Dell Inspiron 1100 laptop and am using the onboard video of course. 

With Windows, when you install an OS, you can go into device manager, see what drivers are missing and install them. In Linux, do you have to install sound, network, video, chipset, etc. drivers when you install the OS? If so, that may be why it doesn't work and how would I remedy that?

As you can tell, I am completely ignorant of Linux altogether so any help, put as dumb downed as possible is greatly appreciated. Thank you guys very much. I look forward to getting past this issue and learning all about Linux.

---

### Post by ubu-for on 2007-06-12
1. Open the "Terminal"

2. Enter (for backup)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

3. Enter
```
sudo gedit /etc/X11/xorg.conf
```

4. Go to this line ...
```
SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
```

... and add your native monitor resolution. Do the same for every line till "Depth 24".

5. Save the changes

6. Log off

7. Press "Ctrl + Alt + Backspace"


If Ubuntu starts only in recovery mode, log on and enter
```
sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

or ...
```
sudo nano /etc/X11/xorg.conf
```

... and undo all the former changes

or create a completely new xorg.conf with
```
sudo dpkg -reconfigure xserver-xorg
```

---

