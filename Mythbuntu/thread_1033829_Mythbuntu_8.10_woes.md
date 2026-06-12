---
title: "Mythbuntu 8.10 woes"
date: 2009-01-07
forum: Mythbuntu
---

### Post by GCFreak on 2009-01-07
Hi there,

I'm new to Mythbuntu but I'm not new to Linux. Experiences with Mythbuntu has mostly been good, but I have a few problems:

1. NetworkManager doesn't remember my network card's settings and I have to reconfigure it every time I reboot the computer.

2. The Hauppauge Nova-T 500 remote. Not all the buttons work, unfortunately, and I have no idea how to get them to work properly.

3. Configuring the TV. I have ABSOLUTELY NO IDEA where to configure it. If I was supposed to configure it when I installed Mythbuntu, I missed it... but I don't know where to go to configure it now, I've been through most of the settings (I think) and I can't find it.

This is kinda urgent so any help is appreciated. Thanks. =)

EDIT: I found the MythTV Backend options (no idea why I didn't see it there before =P) but I forgot the password for the database so I can't log in to it. Can I retrieve the password somehow?

EDIT2: I rebooted the machine, and *ahem* now the Frontend is asking for the database password, so yeah, now I got myself in a bind...

*sigh* EDIT3: Well, nevermind that database problem...I reset the password and got back into it... I've been looking through the Backend options and it looks like that my Nova-T 500 isn't supported by MythTV? I thought it was? Is there any tutorial I need to follow to get it to work...?

---

### Post by crez79 on 2009-01-07
Network manager doesn't work for me either. I use a static IP, so I just uninstalled it configured the network manually.

If you look in ~/.mythtv/mysql.txt the password will be in there.

Type:
```
nano ~/.mythtv/mysql.txt
```
into terminal to view it easily.

Check in the [mythbuntu install manual]("http://www.mythbuntu.org/installation_manual") and it has instructions to at least get you started on how to get things working.

From a new Linux user to another, nothing happens quickly...for me at least. It is very different from windows and takes a lot of getting used to. On the plus side, there are a lot of new users thanks to Ubuntu so there are a lot of very useful resources and very helpful people.

EDIT: Well it looks like you solved your password problem. A google search turned up [this]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI"). It might help answer some of your questions about your remote.

---

### Post by GCFreak on 2009-01-07
Linux has been no picnic so far for me, but it's still not as bad as Windows...=P

Anyway, yeah I've managed to get past the database problem, but yeah, everything else in the first post is still there...

EDIT: Also, this concern I have just sprang to mind. My media centre is running in NTSC, while the TV I'm running on is PAL. Even though the TV can run NTSC, it does some strange warping of the image so I don't see all of the screen, and would like to switch it to PAL, and in the NVIDIA Control Panel I don't know how to change it...

---

### Post by GCFreak on 2009-01-08
Well, after following lots of other threads, I managed to get rid of the NetworkManager problem... now that just leaves the remote (which by the way is still not working properly despite that link earlier in the thread), TV and PAL. Thanks for your help so far, guys. =)

---

### Post by uncle hammy on 2009-01-08
For your remote, you'll likely need to edit your lircrc file in /home/<your user>/.mythtv

Here's a sample you can use as a guide [http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt](http://wilsonet.com/mythtv/lircrc-haupgrey-g3.txt)

if you go to a terminal screen, type irw you can press the keys on your remote to see how lirc recognizes them, which will help you creating your lircrc file.

Hope that helps

---

### Post by fatmonk on 2009-01-08
> **GCFreak said:**
> Hi there,

2. The Hauppauge Nova-T 500 remote. Not all the buttons work, unfortunately, and I have no idea how to get them to work properly.

3. Configuring the TV. I have ABSOLUTELY NO IDEA where to configure it. If I was supposed to configure it when I installed Mythbuntu, I missed it... but I don't know where to go to configure it now, I've been through most of the settings (I think) and I can't find it.

[snip]

*sigh* EDIT3: Well, nevermind that database problem...I reset the password and got back into it... I've been looking through the Backend options and it looks like that my Nova-T 500 isn't supported by MythTV? I thought it was? Is there any tutorial I need to follow to get it to work...?

You didn't mention which video card you are using, but if it's nVidia based then the [How To]("http://ubuntuforums.org/showthread.php?t=665704") in this forum will help you out getting TV out to work. You can't do it all through the the nVidia settings pages (you have installed the proprietary drivers haven't you?)

As for the Nova-T 500 - it does work I have one working like a charm (except for the very occassional hang up now) in my box. Just follow the instructions [here]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI") making sure you do the things such as enabling the LNA etc. If its just the remote that you're having problems with then you could be set for a marathon job. The Nova-T 500 seems to ship with a few different remotes. People have got them working but its a big job - I haven't got mine working yet (only curor keys, numbers and power buttons). There seems to potentially be a problem with HAL grabbing the input from some IR receivers rather than letting LIRC deal with it - that's my next avenue of investogation.

-FM

---

### Post by fatmonk on 2009-01-08
> **GCFreak said:**
> Hi there,

2. The Hauppauge Nova-T 500 remote. Not all the buttons work, unfortunately, and I have no idea how to get them to work properly.

3. Configuring the TV. I have ABSOLUTELY NO IDEA where to configure it. If I was supposed to configure it when I installed Mythbuntu, I missed it... but I don't know where to go to configure it now, I've been through most of the settings (I think) and I can't find it.

[snip]

*sigh* EDIT3: Well, nevermind that database problem...I reset the password and got back into it... I've been looking through the Backend options and it looks like that my Nova-T 500 isn't supported by MythTV? I thought it was? Is there any tutorial I need to follow to get it to work...?

You didn't mention which video card you are using, but if it's nVidia based then the [How To]("http://ubuntuforums.org/showthread.php?t=665704") in this forum will help you out getting TV out to work. You can't do it all through the the nVidia settings pages (you have installed the proprietary drivers haven't you?)

As for the Nova-T 500 - it does work I have one working like a charm (except for the very occassional hang up now) in my box. Just follow the instructions [here]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI") making sure you do the things such as enabling the LNA etc. If its just the remote that you're having problems with then you could be set for a marathon job. The Nova-T 500 seems to ship with a few different remotes. People have got them working but its a big job - I haven't got mine working yet (only curor keys, numbers and power buttons). There seems to potentially be a problem with HAL grabbing the input from some IR receivers rather than letting LIRC deal with it - that's my next avenue of investogation.

-FM

---

### Post by GCFreak on 2009-01-08
ATM I have an 8500GT in here, and the NTSC problem is just a concern, I can live with it like that.

I followed the tutorial at the MythTV wiki, and it can't find the firmware file when it tries to use it, even though it's in /lib/firmware so the card still isn't working. I appreciate any help with regard to this.

---

### Post by GCFreak on 2009-01-08
Ok, scratch that, I managed to get the firmware to load, and MythTV picks it up. But, when I try to scan channels, the button for it is blanked out, and I don't know the specifications for our channels...

---

### Post by GCFreak on 2009-01-10
(damnit triple post...)

Anyway, I was playing around with it, and I managed to get the TV to work, at last! TV ONE and TV2 (both 720p) stutters a little with fast moving motion (signs I got to upgrade the CPU for HD in general) and TV3 (1080i) is unwatchable, with it stuttering to no end and the frontend crashing and just terminating itself, with no error message. SD channels work fine.

Oh well, at least it's ALMOST working now. =) Still got problems with the remote though...

EDIT: Well, I enabled 5.1 on Mythbuntu and MythTV (found the options for them finally...) but now nothing on MythTV plays any sound. Just my luck. =/

Thanks for any help with this.

---

### Post by GCFreak on 2009-01-10
(seriously, I hate doing quadruple posts =P)

Anyways, I've got the sound card to work properly in 5.1 =P But now, MythTV doesn't play any sound =/ lol, help...

---

### Post by GCFreak on 2009-01-11
Well, I decided to just junk the installation I had on there and installed Mythbuntu again, and I've had absolutely no problems setting it up until now. I've set up everything except the capture card in the MythTV backend settings. Whenever I try to enter the section to add a capture card, it just sits there doing nothing. This was my terminal window when I killed it:

```
2009-01-12 14:09:40.459 Using runtime prefix = /usr
2009-01-12 14:09:40.473 XScreenSaver support enabled
2009-01-12 14:09:40.473 DPMS is active.
2009-01-12 14:09:40.474 Empty LocalHostName.
2009-01-12 14:09:40.474 Using localhost value of mediacentre
2009-01-12 14:09:40.484 New DB connection, total: 1
2009-01-12 14:09:40.488 Connected to database 'mythconverg' at host: localhost
2009-01-12 14:09:40.489 Closing DB connection named 'DBManager0'
2009-01-12 14:09:40.491 Primary screen 0.
2009-01-12 14:09:40.492 Connected to database 'mythconverg' at host: localhost
2009-01-12 14:09:40.493 Using screen 0, 1024x768 at 0,0
2009-01-12 14:09:40.501 New DB connection, total: 2
2009-01-12 14:09:40.501 Connected to database 'mythconverg' at host: localhost
2009-01-12 14:09:40.502 Current Schema Version: 1214
2009-01-12 14:09:40.524 Primary screen 0.
2009-01-12 14:09:40.524 Using screen 0, 1024x768 at 0,0
2009-01-12 14:09:40.526 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-01-12 14:09:40.527 Switching to square mode (Mythbuntu-8.04)
2009-01-12 14:09:40.549 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
2009-01-12 14:09:40.550 lirc_init failed for mythtv, see preceding messages
2009-01-12 14:09:40.551 JoystickMenuClient Error: Joystick disabled - Failed to 
read /home/media/.mythtv/joystickmenurc
2009-01-12 14:09:41.543 Specified base font 'medium' does not exist for font clo
ck
2009-01-12 14:09:41.543 Specified base font 'medium' does not exist for font sma
ll
2009-01-12 14:09:41.543 Specified base font 'medium' does not exist for font med
ium
2009-01-12 14:09:41.543 Specified base font 'medium' does not exist for font lar
ge
2009-01-12 14:09:41.545 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/ba
se.xml
2009-01-12 14:09:41.684 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-12 14:09:41.709 No theme dir: /home/media/.mythtv/themes/Mythbuntu-8.04
2009-01-12 14:09:53.072 Running tv_find_grabbers.
2009-01-12 14:11:05.912 Couldn't get handle
                        eno: No such file or directory (2)
2009-01-12 14:11:05.913 GetSTBListPrivate -- begin
2009-01-12 14:11:05.913 GetSTBListPrivate -- got lock
2009-01-12 14:11:05.913 GetSTBListPrivate -- end
2009-01-12 14:11:05.919 Can't open DVB frontend ().
```

Thanks.

---

