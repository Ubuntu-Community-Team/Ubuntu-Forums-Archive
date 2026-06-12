---
title: "Problems with Firefox &amp; Flash"
date: 2015-07-21
forum: Multimedia Software
---

### Post by Rebecca_D on 2015-07-21
Using the *Software Updater*, I recently updated **Firefox to v39** and **Adobe Flash to v18.0.0.209**. I am running on **64bit Ubuntu 14.04LTS**.

Since upgrading I am continually having Firefox crash and displaying the automated crash report form. Must have sent about 50 of these in the past two weeks! When working, Firefox operates normally apart from in respect of its connection with Flash on a couple of streaming TV channels (UK Channel 4OD and Demand 5), with which I had no problems before upgrade. C4OD will not stream at all and 5OD displays the message **"*To view this page ensure that Adobe Flash Player version 15.0.0 or greater is installed. *" !!** Other channels such as You Tube, BBC and ITV stream normally.

I have tried re-installing Firefox with no improvement. I also find that the two channels mentioned have the same problem when using the Google Chrome browser. I have read about Pepper Flash but am a bit confused about whether one needs to uninstall Adobe Flash if you install it.

Any help would be greatly appreciated. Thank you.

---

### Post by sudodus on 2015-07-21
The current version of flashplayer for firefox is 11.2

> flashplugin-nonfree (11.2.202.491ubuntu0.12.04.1) precise-security; urgency=medium

  * New upstream release 11.2.202.491
    - debian/flashplugin-installer.{config,postinst},
      debian/post-download-hook: Updated version and sha256sum

 -- Chris Coulson <chris.coulson@canonical.com>  Wed, 15 Jul 2015 19:33:32 +0100

This version is actually old, there are only security updates, because the owner of Flash does not provide any new version for linux (except the one that comes with Chrome if I understand it correctly). So if you need a newer version of flash, we cannot provide it for firefox.

---

### Post by Bucky Ball on 2015-07-21
Install pepperflashplugin-nonfree. You then need to check in Chrome or Chromium that it is using the right one. There's a heap of info online about how to do this. I don't use Chrome or pepperflash, so can't help there, but help is not far away. :)

---

### Post by SeijiSensei on 2015-07-21
> **Rebecca_D said:**
> I have read about Pepper Flash but am a bit confused about whether one needs to uninstall Adobe Flash if you install it.

No, you can have both installed, as long as you choose "Never Activate" for one of them in Tools >Add-Ons so they don't conflict.

Another alternative is to use [Pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") to run the Windows version of FlashPlayer.

---

### Post by ajgreeny on 2015-07-21
Channel 5 has recently "upgraded?" its system player 
[https://help.channel5.com/hc/en-gb/articles/203580542-New-video-player-released-for-www-channel5-com-Monday-6-July-2015](https://help.channel5.com/hc/en-gb/articles/203580542-New-video-player-released-for-www-channel5-com-Monday-6-July-2015)
and as far as I'm aware it means it is no longer available to Linux users, or at least I can't get it to play on Firefox even using the freshplayerplugin, or chromium using pepperfplashplugin-nonfree.

Channel 4 is the same, unfortunately, and I think this is something that we are not likely to solve very easily.  It used to play with no major problem apart from the need to install hal from the ppa [http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu](http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu)

As you say ITVplayer and BBCiPlayer both work fine as streaming apps

Thank goodness I can still get all these catch-up services via a Now-TV box which I have been using for a while now, and to which I have side-loaded a RARflix app to use with the plex-mediaserver that I have running on this desktop machine.

---

### Post by monkeybrain20122 on 2015-07-24
> **ajgreeny said:**
> Channel 5 has recently "upgraded?" its system player 
[https://help.channel5.com/hc/en-gb/articles/203580542-New-video-player-released-for-www-channel5-com-Monday-6-July-2015](https://help.channel5.com/hc/en-gb/articles/203580542-New-video-player-released-for-www-channel5-com-Monday-6-July-2015)
and as far as I'm aware it means it is no longer available to Linux users, or at least I can't get it to play on Firefox even using the freshplayerplugin, or chromium using pepperfplashplugin-nonfree.

Channel 4 is the same, unfortunately, and I think this is something that we are not likely to solve very easily.  It used to play with no major problem apart from the need to install hal from the ppa [http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu](http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu)
.

If you use freshplayerplugin hal will not work, it works only on system flash (11.2)

If hal + flash 11.2 doesn't work you have two options 
1) (Easy) use pipelight flash, the tricky part is how to switch between freshplayerplugin and pipelight-flash (it is not as smooth as freshplayer) You may want to checkout update-alternatives

2) use freshplayerplugin but instead of the pepper-flash non free package from Ubuntu or Chrome, extract libpepperflash.so  from Chrome OS iso. [https://github.com/i-rinat/freshplayerplugin/blob/master/doc/known-issues.md](https://github.com/i-rinat/freshplayerplugin/blob/master/doc/known-issues.md) (see DRM doesn't work)


But these are only workarounds which you shouldn't have to do. As a U.K taxpayer you and other British Linux users should write to the BBC and raise hell about it. You may get a sympathetic ears from MPs who recently supported ditching MS's format for ODF.

---

### Post by monkeybrain20122 on 2015-07-24
> **SeijiSensei said:**
> No, you can have both installed, as long as you choose "Never Activate" for one of them in Tools >Add-Ons so they don't conflict.
.

It won't work, if more than one version of flashs are present the same setting (Ask to activate, always activate or never activate) applies to all. Firefox would automatically choose the highest version available. So a tricky situation would arise if one has both pepper flash via freshplayerpluin and pipelight flash since they have the same version. It is easy to disable pipelight flash but there is no built-in mechanism to disable freshplayerplugin, some kind of install/updtae alternatives tricks will be needed.

---

### Post by Julind on 2015-07-24
Imo the freshplayer plugin is really unstable using chrome's libpepperflash.so. I gave it a go and literally everytime I **closed** firefox a crash window would appear + the countless amount of times it would crash out of nowhere. Going back to adobes fixed it all.

Regarding the problem, im not sure why websites like that are throwing you erorrs about flash player's version. Have you tried completely removing/purging flash then reinstalling? I had this problem and this did it. If not - fresh player is the solution, but it will be unstable, and you will have to uninstall adobes one since they will conflict

---

### Post by monkeybrain20122 on 2015-07-25
> **Julind said:**
> Imo the freshplayer plugin is really unstable using chrome's libpepperflash.so. I gave it a go and literally everytime I **closed** firefox a crash window would appear + the countless amount of times it would crash out of nowhere. Going back to adobes fixed it all.



Try disabling vaapi/vdpau/hwdec in  freshplayerplugin's .config file. See my post #17 on this thread [http://ubuntuforums.org/showthread.php?t=2285910&page=2](http://ubuntuforums.org/showthread.php?t=2285910&page=2)

---

### Post by ajgreeny on 2015-07-25
> **monkeybrain20122 said:**
> Try disabling vaapi/vdpau/hwdec in  freshplayerplugin's .config file. See my post #17 on this thread [http://ubuntuforums.org/showthread.php?t=2285910&page=2](http://ubuntuforums.org/showthread.php?t=2285910&page=2)
I agree with monkeybrain20122 about the need to disable vaapi and vdpau but I haven't disabled hwdec in my system and freshplayer works very smoothly.  With vaapi and vdpau enabled it would make FF crash every time I used it.

You need to add a freshwrapper.conf file to your ~/.config folder.  Here's mine which works fine on my hardware, Intel i5-3570K using HD4000 igp.
```
#Configuration options for FreshPlayerPlugin
#
# This configuration file is optional. Wrapper will search for it first
# in ~/.config/freshwrapper.conf, then in /etc/freshwrapper.conf.
# If wrapper fails to find configuration, it will use default values,
# which you can find below

# Audio buffer is used to continuously provide sound adapter with data.
# Values too low may lead to buffer underruns and stuttering.  Values
# too high will lead to noticeable latency. Usually plugin selects size
# on its own, but you may override bounds here

# lower bound for audio buffer size, in milliseconds
audio_buffer_min_ms = 20

# higher bound of audio buffer size, in milliseconds
audio_buffer_max_ms = 500

# output sound through JACK. If enabled, only JACK will be tried, and if
# your machine doesn't have it, there would be no sound, and no sync
audio_use_jack = 0

# Path to the Pepper Flash plugin.
# If the option is absent, freshwrapper will search for Pepper Flash in
# a number of location where it could be. Usually that's enough, but if
# not, you should manually enter the right path. Multiple paths could
# be specified, separated by colon.
#pepperflash_path = "/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so"

# "Command-line" arguments for Flash
flash_command_line = "enable_hw_video_decode=1,enable_stagevideo_auto=1"

# enable 3d and stage 3d
enable_3d = 1

#enable_3d_transparent = 0

# enable hardware-accelerated video decoding. Requires 3d to really work
enable_hwdec = 1

# when set to 1, limits output to warnings and errors only
quiet = 0

# When multiple monitors with different resolutions are used, size
# of fullscreen window can vary. But some Flash movies request these
# parameters once at startup and rely on them to be correct. By default,
# if zeros are used here, freshwrapper will select minimal width and
# height across all monitors.
fullscreen_width = 0
fullscreen_height = 0

# Enables DNS query case randomization to partially protect against DNS
# poisoning attacks. It was reported that some Mikrotik routers do not
# support this trick. Set parameter to 0 if you have an affected model
randomize_dns_case = 0

# scaling factor (floating point value) used to convert screen pixels
# to device independent pixels. You may need it for displays with
# high DPI
device_scale = 1

# method org.freedesktop.ScreenSaver.SimulateUserActivity() in KDE 5 seems
# to have no effect unless GetSessionIdleTime() called afterwards. Set
# parameter to 1 to call latter
quirk_plasma5_screensaver = 0

# whenever to use windowed plugin mode
enable_windowed_mode = 0

# whenever XEmbed used in windowed mode (if browser advertises its support)
enable_xembed = 1

# if set to 1, fullscreen window will be kept always above browser, and hidden
# from taskbar and pager
tie_fullscreen_window_to_browser = 1

# enable using of VA-API for hardware accelerated video decoding
enable_vaapi = 0

# enable using of VDPAU for hardware accelerated video decoding
enable_vdpau = 0
```

---

### Post by Julind on 2015-07-25
Thanks for the fix. Will surely give it a go. ;)

---

### Post by nargaroth_reg on 2015-09-03
I can't seem to get freshflashplayer to work. I installed it with the weupd8 ppa and pepper flash with the pepperflashplugin-nonfree package. It works fine in chromium and firefox seems to detect it (libfreshwrapper-pepperflash.so is the file of the active plugin) but whenever I try to watch a flash video an empty black box appears and it doesn't start. Any suggestions? I already tried changing permissions and making libpepflashplayer.so executable but nothing changed. I'm using firefox 40.0.3 on ubuntu trusty amd64.

---

### Post by monkeybrain20122 on 2015-09-03
> **nargaroth_reg said:**
> I can't seem to get freshflashplayer to work. I installed it with the weupd8 ppa and pepper flash with the pepperflashplugin-nonfree package. It works fine in chromium and firefox seems to detect it (libfreshwrapper-pepperflash.so is the file of the active plugin) but whenever I try to watch a flash video an empty black box appears and it doesn't start. Any suggestions? I already tried changing permissions and making libpepflashplayer.so executable but nothing changed. I'm using firefox 40.0.3 on ubuntu trusty amd64.

See post #10. just copy ajgreeny's config file to ~/.config/freshwrapper.conf and restart Firefox, if it still doesn't work try setting hwdec=0 as well, restart FF again.

---

### Post by nargaroth_reg on 2015-09-03
Thanks for the suggestion but that only made the black square a white one.

---

### Post by monkeybrain20122 on 2015-09-03
I think you will have better luck here [https://github.com/i-rinat/freshplayerplugin/issues](https://github.com/i-rinat/freshplayerplugin/issues)

---

### Post by d-cosner on 2015-09-03
The current version of Firefox uses html5 when possible and has caused me lots of crashed I have never had before using flash! I finally installed the YouTube Flash Video Player extension and set Youtube to use the flash player again. I have not had a single crash since!

---

### Post by nargaroth_reg on 2015-09-03
> **monkeybrain20122 said:**
> I think you will have better luck here [https://github.com/i-rinat/freshplayerplugin/issues](https://github.com/i-rinat/freshplayerplugin/issues)
Another person that uses nvidia 304 reported a similar problem there, maybe it is related to the driver. I tried turning on and off the rest of the options of the config file but nothing worked.

---

### Post by monkeybrain20122 on 2015-09-03
Not sure what parameters webupd8 used to compile freshplayerplugin. But you can try compiling it yourself, which is quite easy. First remove freshplayerplugin
```
sudo apt-get remove freshplayerplugin
sudo apt-get autoremove

```
Install dependencies
```
sudo apt-get install cmake gcc g++ pkg-config ragel libasound2-dev \
           libssl-dev libglib2.0-dev libpango1.0-dev libgl1-mesa-dev     \
           libevent-dev libgtk2.0-dev libxrandr-dev libxrender-dev       \
           libxcursor-dev libv4l-dev libgles2-mesa-dev libavcodec-dev    \
           libva-dev libvdpau-dev libdrm-dev rtmpdump librtmp-dev
```
Then download the zip file from [https://github.com/i-rinat/freshplayerplugin](https://github.com/i-rinat/freshplayerplugin), extract then cd into it. So let's say the extracted folder is in the Downloads directory
```
cd Downloads/freshplayerplugin-master
mkdir build && cd build
cmake DCMAKE_BUILD_TYPE=RelWithDebInfo -DWITH_HWDEC=1 -DWITH_GLES2=0 .. 
make
```

Then copy libfreshwrapper-pepperflash.so to .mozilla/plugins
```
cp libfreshwrapper-pepperflash.so ~/.mozilla/plugins
```
Retstart Firefox.

The GLES2=0 option may fix your problem.

A sample config file is in freshplayerplugin-master/data you may want to take a look at that (there may be some newer options than the one you copied), change whatever parameters you want and replace your .config/freshwrapper.conf with it (rename it to remove '.example') if needed (or you can just keep the one you made earlier, shouldn't matter)

---

### Post by ajgreeny on 2015-09-03
In spite of my recent comments in post #10 of this thread, I have just had to remove the new version of freshplayerplugin that was updated only yesterday on my system as it was impossible to start FF with that version installed.  Previous versions were running well, only this most recent update has caused this problem, and it was not even necessary to try to run a flash video for the crash to happen; it just would not allow FF to start.

It took a while to figure out what was going on and even starting FF with a new profile or in safe-mode did not stop the crashes, and I was getting pretty desperate, as I could not start FF to disable anything.  Why safe mode or a new profile did not let it run I have no idea, and it was only looking through my update history that I found freshplayerplugin had been updated just before the crashes started.

I am now back to the official flashplugin-installer which works fine and plays flash videos without a problem, but it was good to have an updated flash for the times that flash was needed.

---

### Post by jawilljr2 on 2015-09-03
> **ajgreeny said:**
> In spite of my recent comments in post #10 of this thread, I have just had to remove the new version of freshplayerplugin that was updated only yesterday on my system as it was impossible to start FF with that version installed.  Previous versions were running well, only this most recent update has caused this problem, and it was not even necessary to try to run a flash video for the crash to happen; it just would not allow FF to start.

It took a while to figure out what was going on and even starting FF with a new profile or in safe-mode did not stop the crashes, and I was getting pretty desperate, as I could not start FF to disable anything.  Why safe mode or a new profile did not let it run I have no idea, and it was only looking through my update history that I found freshplayerplugin had been updated just before the crashes started.

I am now back to the official flashplugin-installer which works fine and plays flash videos without a problem, but it was good to have an updated flash for the times that flash was needed.

[Severe FireFox crash with freshplayer](https://github.com/i-rinat/freshplayerplugin/issues/261)

> BTW, crash could be worked around by removing "flash_command_line" parameter from configuration file. That parameter have no visible effect anyway.

I commented out that line and the crash went away.

---

### Post by ajgreeny on 2015-09-03
Thanks for that. As you will have perhaps seen in the other thread where I posted, [http://ubuntuforums.org/showthread.php?t=2293256&p=13349644#post13349644](http://ubuntuforums.org/showthread.php?t=2293256&p=13349644#post13349644), that has solved the problem.

---

### Post by nargaroth_reg on 2015-09-04
> **monkeybrain20122 said:**
> Not sure what parameters webupd8 used to compile freshplayerplugin. But you can try compiling it yourself, which is quite easy. First remove freshplayerplugin
```
sudo apt-get remove freshplayerplugin
sudo apt-get autoremove

```
Install dependencies
```
sudo apt-get install cmake gcc g++ pkg-config ragel libasound2-dev \
           libssl-dev libglib2.0-dev libpango1.0-dev libgl1-mesa-dev     \
           libevent-dev libgtk2.0-dev libxrandr-dev libxrender-dev       \
           libxcursor-dev libv4l-dev libgles2-mesa-dev libavcodec-dev    \
           libva-dev libvdpau-dev libdrm-dev rtmpdump librtmp-dev
```
Then download the zip file from [https://github.com/i-rinat/freshplayerplugin](https://github.com/i-rinat/freshplayerplugin), extract then cd into it. So let's say the extracted folder is in the Downloads directory
```
cd Downloads/freshplayerplugin-master
mkdir build && cd build
cmake DCMAKE_BUILD_TYPE=RelWithDebInfo -DWITH_HWDEC=1 -DWITH_GLES2=0 .. 
make
```

Then copy libfreshwrapper-pepperflash.so to .mozilla/plugins
```
cp libfreshwrapper-pepperflash.so ~/.mozilla/plugins
```
Retstart Firefox.

The GLES2=0 option may fix your problem.

A sample config file is in freshplayerplugin-master/data you may want to take a look at that (there may be some newer options than the one you copied), change whatever parameters you want and replace your .config/freshwrapper.conf with it (rename it to remove '.example') if needed (or you can just keep the one you made earlier, shouldn't matter)
That didn't work either, but thanks for putting together all the steps to build it. I was going to try pipelight but it wanted to install 300 mb of dependencies and that is too much just for flash imo (I don't use the other plugins). I'll keep the old adobe version for now, although in my computer it makes watching windowed videos and doing anything else in ff impossible.

---

