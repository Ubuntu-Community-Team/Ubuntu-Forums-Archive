---
title: "Flash at warp speed and no sound! Help please Scottie."
date: 2014-08-23
forum: Multimedia Software
---

### Post by Rebecca_D on 2014-08-23
Help needed quickly if possible please.

Using Ubuntu 14.04LTS with a 64bit ASUS P6T SE motherboard having built in digital audio stereo (IEC958).

Had computer on this morning, everything working fine. Did some auto-updates. Turned it off. When I re-booted this afternoon I found that if I used Flash player the video was turning overultra-fast and I could elicit no sound, either related to the video or just playing an audio file. I have tried re-booting with no effect.

Had a search and found this post [(No Sound And Flash Videos Play Super Fast After Daily Update)]("http://askubuntu.com/questions/118459/no-sound-and-flash-videos-play-super-fast-after-daily-update") in the forum. The preferred answer suggested the installation of **pulseaudio** then starting it. I already have this installed, use *Pulse* as my sound server and it 'appeared' to be working, however I tried to install it, then start it from *terminal* and got the following output:

> :~$ sudo apt-get install pavucontrol
[sudo] password for ****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pavucontrol is already the newest version.
pavucontrol set to manually installed.
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.

:~$ pavucontrol

(pavucontrol:3940): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2:16: Theming engine 'adwaita' not found

(pavucontrol:3940): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1443:2: Missing name of pseudo-class
sudo apt-get install libasound2-plugins &#8220;pulseaudio-*&#8221; paman padevchooser paprefs pavucontrol pavumeter



At the end of the last line terminal appeared to crash? No further output or return to the prompt. Assuming naively that the last line was a suggestion as to what I needed to do I ran the command and got this output

> :~$ sudo apt-get install libasound2-plugins &#8220;pulseaudio-*&#8221; paman padevchooser paprefs pavucontrol pavumeter
[sudo] password for ****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package &#8220;pulseaudio-*&#8221;
E: Couldn't find any package by regex '&#8220;pulseaudio-*&#8221;'
:~$


At this point I'm stuck. If it is any help at all and taking the lead from the author of the post above, this is the putput of my */var/log/apt/history log*, giving the updates that I have done today. Don't know if it will help.

> Start-Date: 2014-08-23  05:51:39
Commandline: aptdaemon role='role-commit-packages' sender=':1.52'
Install: libkdecorations4abi1:amd64 (4.11.10-0ubuntu0.1, automatic), libkwineffects1abi4:amd64 (4.11.10-0ubuntu0.1, automatic), libkwinglesutils1:amd64 (4.11.10-0ubuntu0.1, automatic), python3-pyqt4:amd64 (4.10.4+dfsg-1ubuntu1, automatic), python3-dbus.mainloop.qt:amd64 (4.10.4+dfsg-1ubuntu1, automatic), libkwinglutils1abi3:amd64 (4.11.10-0ubuntu0.1, automatic), kde-window-manager:amd64 (4.11.10-0ubuntu0.1, automatic), libxcb-xtest0:amd64 (1.10-2ubuntu1, automatic), kde-window-manager-common:amd64 (4.11.10-0ubuntu0.1, automatic), ubiquity-frontend-kde:amd64 (2.18.8.1, automatic), libxcb-damage0:amd64 (1.10-2ubuntu1, automatic), libkworkspace4abi2:amd64 (4.11.10-0ubuntu0.1, automatic), kde-style-oxygen:amd64 (4.11.10-0ubuntu0.1, automatic), python3-sip:amd64 (4.15.5-1build1, automatic)
Upgrade: libebook-contacts-1.2-0:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), evolution-data-server-common:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), libgirepository-1.0-1:amd64 (1.40.0-1ubuntu0.1, 1.40.0-1ubuntu0.2), libebackend-1.2-7:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), ubiquity:amd64 (2.18.8, 2.18.8.1), unity-gtk2-module:amd64 (0.0.0+14.04.20140403-0ubuntu1, 0.0.0+14.04.20140403-0ubuntu2), gir1.2-edataserver-1.2:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), evolution-data-server-online-accounts:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), unity-gtk-module-common:amd64 (0.0.0+14.04.20140403-0ubuntu1, 0.0.0+14.04.20140403-0ubuntu2), gir1.2-ebook-1.2:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), python-secretstorage:amd64 (2.0.0-1ubuntu1, 2.0.0-1ubuntu1.1), ubiquity-ubuntu-artwork:amd64 (2.18.8, 2.18.8.1), libedata-book-1.2-20:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), libunity-gtk2-parser0:amd64 (0.0.0+14.04.20140403-0ubuntu1, 0.0.0+14.04.20140403-0ubuntu2), gir1.2-freedesktop:amd64 (1.40.0-1ubuntu0.1, 1.40.0-1ubuntu0.2), libcamel-1.2-45:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), gir1.2-glib-2.0:amd64 (1.40.0-1ubuntu0.1, 1.40.0-1ubuntu0.2), ubiquity-frontend-debconf:amd64 (2.18.8, 2.18.8.1), gir1.2-ebookcontacts-1.2:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), unity-gtk3-module:amd64 (0.0.0+14.04.20140403-0ubuntu1, 0.0.0+14.04.20140403-0ubuntu2), libecal-1.2-16:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), libebook-1.2-14:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), evolution-data-server:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), libedataserver-1.2-18:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), libedata-cal-1.2-23:amd64 (3.10.4-0ubuntu1.1, 3.10.4-0ubuntu1.2), libunity-gtk3-parser0:amd64 (0.0.0+14.04.20140403-0ubuntu1, 0.0.0+14.04.20140403-0ubuntu2)
End-Date: 2014-08-23  05:53:39

Start-Date: 2014-08-23  08:15:16
Commandline: aptdaemon role='role-commit-packages' sender=':1.71'
Upgrade: ubuntu-release-upgrader-gtk:amd64 (0.220.2, 0.220.4), python3-distupgrade:amd64 (0.220.2, 0.220.4), ubuntu-release-upgrader-core:amd64 (0.220.2, 0.220.4)
End-Date: 2014-08-23  08:15:21

I am not a linux expert although I try my best, so if you need any further information please give me clear instructions suitable for a bear of little brain. Any help would be greatly appreciated.

Many thanks in advance.

Rebecca

---

### Post by Rebecca_D on 2014-08-23
I have solved the problem. Should have looked around a bit more before baying for the moon. Tried suggestions in the **Sound Troubleshooting** sticky. Killed *pulseaudio* and restarted. All fine. Flash now calmed down. Only remaining problem is that I think I have lost my plug-in speakers. Sound is fine through headphones. Will investigate.

---

