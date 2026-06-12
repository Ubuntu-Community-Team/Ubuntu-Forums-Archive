---
title: "Is enabling Beats Audio EQ on the horizon?"
date: 2015-04-04
forum: Multimedia Software
---

### Post by Krillo on 2015-04-04
Is enabling Beats Audio EQ on the horizon?

My laptop HP Spectre X2 has Beats Audio and the built in speakers have a horrible peak at around 1-2kHz, sound pretty much like a telephone. So EQ is pretty much needed to make the speakers usable. I'm wondering if there is any chance of getting the EQ to work within the foreseeable future?

Also it seems the audio starts distorting earlier than on "that other OS". I've fiddled with audio settings, but there isn't a lot of difference, the audio does get louder, but distorts easily.

PS I'm an audio engineer. ;-)

---

### Post by mcduck on 2015-04-04
Knowing that the Beats Audio stuff on computers is nothing more than a EQ preset anyway, you should be fine using any EQ to tweak the sound to your liking. 

(And also since it really is just EQ preset in the Windows driver, there is nothing to enable. Of course they could provide you with a modified Linux driver that does the same EQ tweak by default, or a EQ application with their logo thrown in, but that wouldn't really make any difference to just tweaking the EQ settings yourself wit some other tool)

Anyway, take a look at this for a system-Wide Pulse Audio EQ: [http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html]("http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html")

edit: Or being an audio engineer, you might want to try this one instead. Bit more complicated to set up, but also gives you more defined control so smoothing out the peak without loosing anything else would be easier: [http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html]("http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html")

---

### Post by Krillo on 2015-04-04
kewl, will try that :)

---

### Post by Krillo on 2015-04-04
hm doing

```
sudo apt-repository
```

I get command not found. Did

```
sudo apt-get install software-properties-common
```

but it says it's installed :-k

---

### Post by mc4man on 2015-04-04
> **Krillo said:**
> hm doing

```
sudo apt-repository
```

I get command not found. Did

```
sudo apt-get install software-properties-common
```

but it says it's installed :-k
Maybe try c&p from the web page you're using, then sudo apt-repository ... would become
sudo add-apt-repository ppa:nilarimogard/webupd8
or
sudo add-apt-repository ppa:webupd8team/pulseaudio-eq
(depending on which way you are going

---

### Post by tgalati4 on 2015-04-04
Understand that Beats Audio is probably a lot more than simple EQ.  To get small, crappy speakers to sound less crappy, a lot of DSP work is done to "synthesize" bass (similar to Sony's Mega Bass), crystalize the higher vocal frequencies, widen the stereo field from 15" to a few feet, and compress the sound field so you can play louder without hitting distortion limits of either the amplifier or speaker.  All of this is wrapped up in a proprietary, binary driver, that is difficult to reverse engineer in an open source driver.

Linux does have the tools to do most of the above, but it would require an audio engineer and a lot of testing to come up with the DSP transform that Windows uses.

A simple test:  Make a 1-minute pink noise track using *audacity*.  Play it using an RTA visualizer and take a screen shot.  The frequency bars should be straight across.  Play the same track in Windows using Windows Media Player using the EQ visualizer and take a screen shot.  Compare the two.  That may get you to 80% of the performance.  That may be good enough.  To get the other 20% requires a lot more work.

---

### Post by mcduck on 2015-04-04
nah, it really is just 90'% EQ, plus a bit of compression (just like with their headphones). Add stereo expander if you want, I'm sure there's a LADSPA expander you can use with pulse audio, and those aren''t difficult at all to tweak.

---

### Post by Krillo on 2015-04-08
What's wrong here:

```
sudo apt-get pulseaudio-utils
```

:-k

---

### Post by tgalati4 on 2015-04-08
You need *install*.

```
sudo apt-get install pulseaudio-utils
```

To see if it is loaded already:

```
apt-cache policy pulseaudio-utils
```

---

### Post by Krillo on 2015-04-09
Seems it was already installed :oops:
Now the problem is I get no GUI.
Background: First installed xfce, then fluxbox. Upon installing fluxbox som stuff seems to have disappeared from GUI. Some panel which name I don't recall vanished.

---

### Post by tgalati4 on 2015-04-09
Unfortunately you can't change desktop enviromnments without breaking stuff.  Perhaps backing up your data and perform a clean install of the operating system and desktop environment that you would like to use.  If you want to experiment, use a virtual machine or find another computer to try different distros.

---

### Post by Krillo on 2015-04-09
Yep, I guessed so :'(

---

### Post by mcduck on 2015-04-09
> **tgalati4 said:**
> Unfortunately you can't change desktop enviromnments without breaking stuff.  Perhaps backing up your data and perform a clean install of the operating system and desktop environment that you would like to use.  If you want to experiment, use a virtual machine or find another computer to try different distros.
Most of the time you can, without any problems. I'm happily running Unity, Gnome Shell, XFCE and Openbox sessions my laptop, plus a custom one for Steam. I used to have LXDE as well but I left it out recently since I already have my own Openbox setup.

Usually installing another desktop environment shouldn't cause any trouble or uninstall things other DE's/Window managers need. In some cases you might end with some overlap in config files, though, or cluttered menus because you end installing multiple apps and tools for the same tasks, but even if things go bad it definitely won't require a reinstall of the OS. Just reinstall the desktop environment you prefer (and if that doesn't solve the problem it's some conflicting config file in your home directory so removing those will fix everything).

The whole reason why most desktop managers (like KDM, GDM and LightDM) have the options for selecting your session at login time. You are supposed to be able to have multiple environments installed at the same time so every user can choose which ever they prefer to use.

Anyway, the generic rule is to pay attention to what thr package manager tells you when you install something. If it tells it's going to uninstall something, you'll definitely want to make sure you know what you are doing before proceeding...

---

### Post by Krillo on 2015-04-12
So I re-installed my laptop and got Ubuntu Mate. Tried this EQ again. Seems to install OK as far as I can see, and it showes up in Sound Preferences "FFT based equalizer on Built-in Audio Analog Stereo", choosing this makes Rythmbox say "Couldn't start playback (null)" when attempting to play a mp3. Now I'm thinking that may have to do with no mp3 codec installed? Can't remember my choice during install :-k

```
user@laptop:~$ wget http://cgit.freedesktop.org/pulseaudio/pulseaudio/plain/src/utils/qpaeq -O /tmp/qpaeq
--2015-04-12 19:33:09--  http://cgit.freedesktop.org/pulseaudio/pulseaudio/plain/src/utils/qpaeq
Resolving cgit.freedesktop.org (cgit.freedesktop.org)... 131.252.210.161
Connecting to cgit.freedesktop.org (cgit.freedesktop.org)|131.252.210.161|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24612 (24K) [text/plain]
Saving to: &#8216;/tmp/qpaeq&#8217;

100%[======================================>] 24 612       117KB/s   in 0,2s   

2015-04-12 19:33:10 (117 KB/s) - &#8216;/tmp/qpaeq&#8217; saved [24612/24612]

user@laptop:~$ sudo install /tmp/qpaeq /usr/local/bin/
[sudo] password for user: 
user@laptop:~$ sudo apt-get install python-dbus python-qt4 python-qt4-dbus pulseaudio-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio-utils is already the newest version.
python-dbus is already the newest version.
python-dbus set to manually installed.
The following extra packages will be installed:
  libqt4-designer libqt4-help libqt4-opengl libqt4-scripttools libqt4-svg
  libqt4-test libqtassistantclient4 libqtwebkit4 python-sip
Suggested packages:
  python-qt4-dbg
The following NEW packages will be installed:
  libqt4-designer libqt4-help libqt4-opengl libqt4-scripttools libqt4-svg
  libqt4-test libqtassistantclient4 libqtwebkit4 python-qt4 python-qt4-dbus
  python-sip
0 upgraded, 11 newly installed, 0 to remove and 215 not upgraded.
Need to get 15,5 MB of archives.
After this operation, 63,6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main libqt4-designer amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1 [3 621 kB]
Get:2 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main libqt4-help amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1 [203 kB]
Get:3 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main libqt4-opengl amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1 [300 kB]
Get:4 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main libqt4-scripttools amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1 [219 kB]
Get:5 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main libqt4-svg amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1 [137 kB]
Get:6 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main libqt4-test amd64 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1 [61,3 kB]
Get:7 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main libqtassistantclient4 amd64 4.6.3-6 [14,4 kB]
Get:8 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main libqtwebkit4 amd64 2.3.2-0ubuntu7 [8 561 kB]
Get:9 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main python-sip amd64 4.16.3+dfsg-1 [68,9 kB]
Get:10 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main python-qt4 amd64 4.11.2+dfsg-1 [2 297 kB]
Get:11 http://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu/ utopic/main python-qt4-dbus amd64 4.11.2+dfsg-1 [13,1 kB]
Fetched 15,5 MB in 22s (693 kB/s)                                              
Selecting previously unselected package libqt4-designer:amd64.
(Reading database ... 156125 files and directories currently installed.)
Preparing to unpack .../libqt4-designer_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1_amd64.deb ...
Unpacking libqt4-designer:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Selecting previously unselected package libqt4-help:amd64.
Preparing to unpack .../libqt4-help_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1_amd64.deb ...
Unpacking libqt4-help:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Selecting previously unselected package libqt4-opengl:amd64.
Preparing to unpack .../libqt4-opengl_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1_amd64.deb ...
Unpacking libqt4-opengl:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Selecting previously unselected package libqt4-scripttools:amd64.
Preparing to unpack .../libqt4-scripttools_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1_amd64.deb ...
Unpacking libqt4-scripttools:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Selecting previously unselected package libqt4-svg:amd64.
Preparing to unpack .../libqt4-svg_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1_amd64.deb ...
Unpacking libqt4-svg:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Selecting previously unselected package libqt4-test:amd64.
Preparing to unpack .../libqt4-test_4%3a4.8.6+git49-gbc62005+dfsg-1ubuntu1_amd64.deb ...
Unpacking libqt4-test:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Selecting previously unselected package libqtassistantclient4:amd64.
Preparing to unpack .../libqtassistantclient4_4.6.3-6_amd64.deb ...
Unpacking libqtassistantclient4:amd64 (4.6.3-6) ...
Selecting previously unselected package libqtwebkit4:amd64.
Preparing to unpack .../libqtwebkit4_2.3.2-0ubuntu7_amd64.deb ...
Unpacking libqtwebkit4:amd64 (2.3.2-0ubuntu7) ...
Selecting previously unselected package python-sip.
Preparing to unpack .../python-sip_4.16.3+dfsg-1_amd64.deb ...
Unpacking python-sip (4.16.3+dfsg-1) ...
Selecting previously unselected package python-qt4.
Preparing to unpack .../python-qt4_4.11.2+dfsg-1_amd64.deb ...
Unpacking python-qt4 (4.11.2+dfsg-1) ...
Selecting previously unselected package python-qt4-dbus.
Preparing to unpack .../python-qt4-dbus_4.11.2+dfsg-1_amd64.deb ...
Unpacking python-qt4-dbus (4.11.2+dfsg-1) ...
Setting up libqt4-designer:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Setting up libqt4-help:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Setting up libqt4-opengl:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Setting up libqt4-scripttools:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Setting up libqt4-svg:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Setting up libqt4-test:amd64 (4:4.8.6+git49-gbc62005+dfsg-1ubuntu1) ...
Setting up libqtassistantclient4:amd64 (4.6.3-6) ...
Setting up libqtwebkit4:amd64 (2.3.2-0ubuntu7) ...
Setting up python-sip (4.16.3+dfsg-1) ...
Setting up python-qt4 (4.11.2+dfsg-1) ...
Setting up python-qt4-dbus (4.11.2+dfsg-1) ...
Processing triggers for libc-bin (2.19-10ubuntu2) ...
user@laptop:~$ pulseaudio -k
user@laptop:~$ pulseaudio &
[1] 5304
user@laptop:~$ E: [pulseaudio] pid.c: Daemon already running.
**E: [pulseaudio] main.c: pa_pid_file_create() failed.**
^C
[1]+  Exit 1                  pulseaudio
user@laptop:~$ pactl load-module module-equalizer-sink
18
user@laptop:~$ pactl load-module module-dbus-protocol
19
user@laptop:~$ qpaeq
Got bus address:  "unix:abstract=/tmp/dbus-oGzVmSzUiY,guid=3bf3089c56cdc17166c59961552a8957" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-oGzVmSzUiY,guid=3bf3089c56cdc17166c59961552a8957" 
Registered DEC:  true 
Registered event listener change listener:  true 
^[[A^X^C
user@laptop:~$ qpaeq
Got bus address:  "unix:abstract=/tmp/dbus-oGzVmSzUiY,guid=3bf3089c56cdc17166c59961552a8957" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-oGzVmSzUiY,guid=3bf3089c56cdc17166c59961552a8957" 
Registered DEC:  true 
Registered event listener change listener:  true 


```

---

### Post by Krillo on 2015-04-14
No GUI opens when I do ```
qpaeq
```

This is the response:
```
user@laptop:~$ qpaeq 
Got bus address:  "unix:abstract=/tmp/dbus-4ocxka54tu,guid=35ddadd521d7679eb62b69f9552d4c96" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-4ocxka54tu,guid=35ddadd521d7679eb62b69f9552d4c96" 
Registered DEC:  true 
Registered event listener change listener:  true 


```

It shows up under Sound Preferences, but there's no settings like there is here

[IMG]http://4.bp.blogspot.com/-r3IabLvI3cM/UUBsE6PguEI/AAAAAAAAOjM/joUZhqyId0c/s1600/sound-settings.png[/IMG]

Just balance but that slider is there for all devices.

Any ideas?

---

