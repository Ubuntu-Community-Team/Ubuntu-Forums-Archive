---
title: "Mythtv-for-windows Is this functional yet?"
date: 2010-09-12
forum: Mythbuntu
---

### Post by williammanda on 2010-09-12
I came across the google code for mythtv for windows. Is this functional yet? If so, does anyone have any feedback? If not, any ideas when it will be available? Here's the link:

[http://code.google.com/p/mythtv-for-windows/]("http://code.google.com/p/mythtv-for-windows/")

---

### Post by ian dobson on 2010-09-12
Hi,

I've seen quite afew posts on the MythTV devs mailing list about compiling MythTV under windows. Up until now, no dev actually used the windows port, but there seems to be a new programmer that seems to be spending quite abit of time working on windows.

The link you posted is just a repositry for the dependancies for the mythtv build system rather than a working system.

Regards
Ian Dobson

---

### Post by brianafischer on 2010-09-13
I can say that the frontend is functional.


I just setup a Windows 7 VirtualBox to compile MythTV on Windows 7.  Windows 7 support was added in Qt 4.6 and a compile from source created a working frontend using 0.23.1 fixes for me.


The builds from [http://members.iinet.net.au/~davco/](http://members.iinet.net.au/~davco/) are a bit old and for Windows XP from what I can tell.  I was only able to get them working once a long time ago.


I have only tested Live TV and Watch Recordings which seem to work ok for my limited testing.  However, hardware accelerated decoding (DXVA2) is not yet supported.  It seems that MythTV uses FFMPEG on Windows for playback which does support DXVA2.  There have been some commits on the mailing list for adding this support to 0.24.


I can upload my Windows 7 build to a file sharing site if you would like.  Let me know.

---

### Post by aug2000 on 2010-09-16
Hi,
 
I just recently installed mythbuntu on a server and now I am trying to get a mythtv frontend on an xp computer.  I downloaded the build that brianafischer mentioned in the last post and installed it.  Unfortunately, I have tried communicating to the backend and I get an error about the mythtv protocol being mismatched (which closes the frontend).  I know I need to update, but I can't seem to get it to work.  Does anyone, by any chance, have an updated mythtv for windows?
 
Thanks

---

### Post by brianafischer on 2010-09-16
> **aug2000 said:**
> Hi,
 
I just recently installed mythbuntu on a server and now I am trying to get a mythtv frontend on an xp computer.  I downloaded the build that brianafischer mentioned in the last post and installed it.  Unfortunately, I have tried communicating to the backend and I get an error about the mythtv protocol being mismatched (which closes the frontend).  I know I need to update, but I can't seem to get it to work.  Does anyone, by any chance, have an updated mythtv for windows?
 
Thanks
What version of mythbackend are you running?

Run mythbackend --version on a server terminal for your backend then post here. 
Run mythfrontend --version from the command line on windows and post here also.

Also, what version did you download from the build site?

---

### Post by aug2000 on 2010-09-17
Hi Briana
 
Thanks for the quick reply. This is the version of my mythbackend
 
[COLOR=#000000][FONT=Arial]mythserver@mythserver:~$ mythbackend --version[/FONT][/COLOR]
[FONT=Arial][COLOR=#000000]Please include all output in bug reports.[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]MythTV Version : 24158[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]MythTV Branch : branches/release-0-23-fixes[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]Network Protocol : 56[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]Library API : 0.23.20100314-1[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]QT Version : 4.6.2[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]Options compiled in:[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libudev using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg[/COLOR][/FONT]
 
[COLOR=#000000][FONT=Arial]The mythtv windows front end I'm using is from the link you had listed previously. I think its version 0.23, and I'm guessing it isn't the latest version (0.23-fixes). I have tried compiling it myself but it crashes while the perl script tries to install the componants needed for compiling. [/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]Thanks in advance for any help you can give this windows spoiled noob ;)[/FONT][/COLOR]
[FONT=Arial][/FONT] 
[FONT=Arial]** oh sorry, forgot to check the windows version.  I'll post when I get home[/FONT]

---

### Post by superm1 on 2010-09-17
> **aug2000 said:**
> Hi Briana
 
Thanks for the quick reply. This is the version of my mythbackend
 
[COLOR=#000000][FONT=Arial]mythserver@mythserver:~$ mythbackend --version[/FONT][/COLOR]
[FONT=Arial][COLOR=#000000]Please include all output in bug reports.[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]MythTV Version : 24158[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]MythTV Branch : branches/release-0-23-fixes[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]Network Protocol : 56[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]Library API : 0.23.20100314-1[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]QT Version : 4.6.2[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]Options compiled in:[/COLOR][/FONT]
[FONT=Arial][COLOR=#000000]linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libudev using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg[/COLOR][/FONT]
 
[COLOR=#000000][FONT=Arial]The mythtv windows front end I'm using is from the link you had listed previously. I think its version 0.23, and I'm guessing it isn't the latest version (0.23-fixes). I have tried compiling it myself but it crashes while the perl script tries to install the componants needed for compiling. [/FONT][/COLOR]
 
[COLOR=#000000][FONT=Arial]Thanks in advance for any help you can give this windows spoiled noob ;)[/FONT][/COLOR]
[FONT=Arial][/FONT] 
[FONT=Arial]** oh sorry, forgot to check the windows version.  I'll post when I get home[/FONT]
What you'll need to do is update the backend to the latest autobuilds build for 0.23.1.

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

It looks like according to the site you posted they have 25457 there which is newer than your 24158.

---

### Post by aug2000 on 2010-09-17
oh, so its the other way around.  That sounds a lot easier to fix then recompiling a windows version.  Thanks, will try that tonight.:p

---

### Post by brianafischer on 2010-09-17
I could not get the 0.23.1-fixes branch working but 0.23-fixes worked fine on Windows.  I would double-check the Windows frontend is running protocol 23056 before updating your backend.

Also, the update instructions to 0.23.1 are below:
[http://ubuntuforums.org/showthread.php?t=1555173](http://ubuntuforums.org/showthread.php?t=1555173)

---

### Post by tgm4883 on 2010-09-17
> **brianafischer said:**
> I could not get the 0.23.1-fixes branch working but 0.23-fixes worked fine on Windows.  I would double-check the Windows frontend is running protocol 23056 before updating your backend.

Also, the update instructions to 0.23.1 are below:
[http://ubuntuforums.org/showthread.php?t=1555173](http://ubuntuforums.org/showthread.php?t=1555173)

Um, thats not even close to the instructions for enabling the 0.23.1 builds. Look here instead [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by brianafischer on 2010-09-17
[See post #7]("http://ubuntuforums.org/showpost.php?p=9741976&postcount=7")

:-)

---

### Post by tgm4883 on 2010-09-17
> **brianafischer said:**
> [See post #7]("http://ubuntuforums.org/showpost.php?p=9741976&postcount=7")

:-)

Great, how do you get the repositories section to show up in MCC? It's not showing up on a default Mythbuntu 10.04 install

---

### Post by brianafischer on 2010-09-17
> **tgm4883 said:**
> Great, how do you get the repositories section to show up in MCC? It's not showing up on a default Mythbuntu 10.04 install
[See post #7]("http://ubuntuforums.org/showpost.php?p=9741976&postcount=7")


[http://www.mythbuntu.org/auto-builds]("http://www.mythbuntu.org/auto-builds") is the official guide though as you stated previously

;-)

---

### Post by tgm4883 on 2010-09-17
> **brianafischer said:**
> Last edited by brianafischer; 15 Minutes Ago at 05:56 PM..

Nice fix ;)

:EDIT:

Also, the reason I push people to the web page is it has a lot of info about what the auto-builds are and what will get updated if people activate them. There is a lot of confusion without that information.

---

