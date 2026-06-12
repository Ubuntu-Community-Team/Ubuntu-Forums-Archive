---
title: "MythTV frontend crashes on watching TV"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by middlewordie on 2007-09-02
Hi

I've just installed Myth TV to a new built PC

Sempron 2800
Asus K8V Upgrade
1GB Ram
160GB Maxtor HD
ATI Radeon 7000
Hauppage Nova-T DVB card

The card works ok as I've been watching Football Focus in Mplayer.
The backend seems ok - recognises the card, finds loads of channels etc.

However, the frontend crashes when I try to watch TV. The screen goes blank and the keyboard and mouse are inoperable. I have to reset the machine using the case button.

Why might this be and what can i do to solve it? Do I need a different Graphics card for mythtv?

I'm very new to linux so i've no idea how to interrogate it using terminal, but if someone would be kind enough to tell me how to, i'll happily follow your instructions!

Thanks

Nick

---

### Post by drifting on 2007-09-02
Too be honest I am a noob too, but I gave up using an ATI card, had so many crashes, and weird slow motion playbacks, that in the end I bought a cheap Nvidia 5200, no problems since!

Paul.

---

### Post by middlewordie on 2007-09-03
Paul

Thanks for that - I've read Garry Parker's [how to]("http://www.parker1.co.uk/mythtv_ubuntu.php") and he used a fx5200 and had no problems. did you have to install proprietary drivers though? Apparently I may have to do that too!

I'm so close, but yet so far!

Cheers

Nick

---

### Post by drifting on 2007-09-03
Yes I did use restricted drivers, at the time the easiest way was to use Envy. (Do a search in the forums for Envy)

Other than that you can use the restricted drivers options. I have used both methods on my now fully Ubuntu'd machines.

Paul.

---

### Post by middlewordie on 2007-09-23
I've now bought and installed the F5200 and used Envy. I've now got TwinView working with the same display on my TV and my monitor, but with out any success in getting Myth TV to work.

I still get a blank screen when I start watching TV in mythtv, but it closes the watching TV section down and puts me back into the main menu.

I've found another post [ here]("http://ubuntuforums.org/showthread.php?t=533499&highlight=mythtv+blank+screen") which seems to describe the same thing occurring in MythBuntu but with no replies!

Could it by the timeout is set too short and it can't find channels straight away, so closes down? I've only got one DVB card, would this affect how MythTv works?

---

### Post by middlewordie on 2007-09-25
Bump

I'm a bit confused by this, because I can watch TV using DVB stream, but not using MythTV.
When I run mythfrontend from terminal I get the following:

nick@sempron2800:~$ mythfrontend
> X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-09-25 18:09:22.466 Using runtime prefix = /usr
2007-09-25 18:09:22.480 Gnome-Screensaver support enabled
2007-09-25 18:09:22.480 DPMS is active.
2007-09-25 18:09:22.505 New DB connection, total: 1
2007-09-25 18:09:22.511 Connected to database 'mythconverg' at host: localhost
2007-09-25 18:09:22.512 Total desktop dim: 1024x768, with 2 screen[s].
2007-09-25 18:09:22.516 Running in a window
2007-09-25 18:09:22.516 Using screen 0, 1024x768 at 0,0
2007-09-25 18:09:22.535 Current Schema Version: 1160
2007-09-25 18:09:22.535 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-09-25 18:09:22.535 Enabled verbose msgs:  important general
2007-09-25 18:09:22.910 Total desktop dim: 1024x768, with 2 screen[s].
2007-09-25 18:09:22.912 Running in a window
2007-09-25 18:09:22.912 Using screen 0, 1024x768 at 0,0
2007-09-25 18:09:22.913 Switching to square mode (MythCenter)
2007-09-25 18:09:22.933 Using the Qt painter
mythtv: could not open config file /home/nick/.mythtv/lircrc
mythtv: No such file or directory
Failed to read lirc config /home/nick/.mythtv/lircrc for mythtv
2007-09-25 18:09:23.447 Joystick disabled.
2007-09-25 18:09:24.185 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-09-25 18:09:24.214 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-09-25 18:09:24.279 Registering Internal as a media playback plugin.
2007-09-25 18:09:41.251 New DB connection, total: 2
2007-09-25 18:09:41.252 Connected to database 'mythconverg' at host: localhost
2007-09-25 18:09:41.325 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2007-09-25 18:09:41.326 Using protocol version 31
2007-09-25 18:09:41.347 TV: Attempting to change from None to WatchingLiveTV
2007-09-25 18:09:41.348 Using protocol version 31
2007-09-25 18:09:43.853 GetEntryAt(-1) failed.
2007-09-25 18:09:43.855 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo
2007-09-25 18:09:43.855 TV Error: LiveTV not successfully started
2007-09-25 18:09:43.856 TV Error: LiveTV not successfully started
2007-09-25 18:09:43.865 TV: Deleting TV Chain in destructor
2007-09-25 18:09:43.870 DPMS Deactivated 
2007-09-25 18:09:43.871 DPMS Reactivated.
2007-09-25 18:09:45.507 TV: Attempting to change from None to WatchingLiveTV
2007-09-25 18:09:45.508 Using protocol version 31
2007-09-25 18:09:47.685 GetEntryAt(-1) failed.
2007-09-25 18:09:47.687 EntryToProgram(0@Thu Jan 1 01:00:00 1970) failed to get pginfo
2007-09-25 18:09:47.687 TV Error: LiveTV not successfully started
2007-09-25 18:09:47.687 TV Error: LiveTV not successfully started
2007-09-25 18:09:47.697 TV: Deleting TV Chain in destructor
2007-09-25 18:09:47.701 DPMS Deactivated 
2007-09-25 18:09:47.702 DPMS Reactivated.


And when I run myth backend I get:
nick@sempron2800:~$ mythbackend
> 
2007-09-25 18:10:09.613 Using runtime prefix = /usr
2007-09-25 18:10:09.630 New DB connection, total: 1
2007-09-25 18:10:09.636 Connected to database 'mythconverg' at host: localhost
2007-09-25 18:10:09.639 Current Schema Version: 1160
Starting up as the master server.
2007-09-25 18:10:09.661 New DB connection, total: 2
2007-09-25 18:10:09.662 Connected to database 'mythconverg' at host: localhost
2007-09-25 18:10:09.664 EITHelper: localtime offset 1:00:00 
2007-09-25 18:10:09.670 TVRec(2) Error: Start channel from DB is empty, setting to '1' instead.
2007-09-25 18:10:09.700 New DB connection, total: 3
2007-09-25 18:10:09.700 Connected to database 'mythconverg' at host: localhost
2007-09-25 18:10:11.754 New DB scheduler connection
2007-09-25 18:10:11.754 Connected to database 'mythconverg' at host: localhost
2007-09-25 18:10:11.757 Main::Starting HttpServer
QServerSocket: failed to bind or listen to the socket
2007-09-25 18:10:11.768 Main::HttpServer Create Error
2007-09-25 18:10:11.768 Main::Registering HttpStatus Extension
2007-09-25 18:10:11.796 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-09-25 18:10:11.796 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/var/lib/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.

---

### Post by superm1 on 2007-09-27
> **middlewordie said:**
> Bump

I'm a bit confused by this, because I can watch TV using DVB stream, but not using MythTV.
When I run mythfrontend from terminal I get the following:

nick@sempron2800:~$ mythfrontend



And when I run myth backend I get:
nick@sempron2800:~$ mythbackend

Don't start the backend like this.  There are init scripts for this exact purpose that handle starting as the appropriate user and permissions

```
sudo /etc/init.d/mythtv-backend restart
```

---

### Post by Wd2048 on 2007-09-28
I had the same problem with the front-end hosing up on me.

Here's what I did, and it worked for me.
From within the frontend:
Utilities/Setup > Setup > TV Settings > Playback
Unselect "Enable Realtime priority threads"

I haven't had any problems with my mythbox since.

Hope this helps
-b

---

### Post by Nightwalker07 on 2007-10-02
> **Wd2048 said:**
> I had the same problem with the front-end hosing up on me.

Here's what I did, and it worked for me.
From within the frontend:
Utilities/Setup > Setup > TV Settings > Playback
Unselect "Enable Realtime priority threads"

I haven't had any problems with my mythbox since.

Hope this helps
-bYep, I've got the same problem! :( I've worked for a whole day to get this bad-boy working and bought a Nova-T 500 so it would be compatible and I would have a good guide. I tried your ''Enable Realtime priority threads' unselected that in the options then about 10seconds latter I was just navigating through the menus and the system locked up completely. So far I've had like 8 freeze's and me just cutting the power, im now trying to run the software updates but the overall system stability seems to be degrading and that downward-slope has started since I got MythTV "working".

Btw I have had MythTV working with my card, I have watched/recorded TV etc. but it just started locking up at random intervals into watching TV, it could have been 5mins then I'll be alright for 25mins, but it'd lock-up, full system freeze and I'd have to cut the power! Not what you wana be doing when there's something you wana watch :mad:

---

### Post by Nightwalker07 on 2007-10-02
I have a dedicated machine I am trying to setup for MythTV:

- 1.8ghz AMD
- Asus A7V8X-X Mobo
- 640mb RAM
- 300GB IDE HDD
- Hauppauge WinTV Nova-T 500 PCI > **[MythTV Guide for this card]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI")**

ooop, dosent matter now :( my ubuntu installation has properly fallen over, too many lockups/powerdowns. ](*,)

---

### Post by superm1 on 2007-10-02
> **Nightwalker07 said:**
> Yep, I've got the same problem! :( I've worked for a whole day to get this bad-boy working and bought a Nova-T 500 so it would be compatible and I would have a good guide. I tried your ''Enable Realtime priority threads' unselected that in the options then about 10seconds latter I was just navigating through the menus and the system locked up completely. So far I've had like 8 freeze's and me just cutting the power, im now trying to run the software updates but the overall system stability seems to be degrading and that downward-slope has started since I got MythTV "working".

Btw I have had MythTV working with my card, I have watched/recorded TV etc. but it just started locking up at random intervals into watching TV, it could have been 5mins then I'll be alright for 25mins, but it'd lock-up, full system freeze and I'd have to cut the power! Not what you wana be doing when there's something you wana watch :mad:
Sounds to me like you need to do some hardware diagnostics.  Memory checks, hard drive checks, etc.  MythTV itself doesn't make hardware go bad, but it can push your hardware a little harder than a few other packages.

---

### Post by Nightwalker07 on 2007-10-02
I've ran spinrite on the 300GB HDD for 10+hrs, all fine there. I'll do a memory test tomorrow. I think it might be down to the GFX card, its very old and budget probably, Im in work tomorrow and I'll try a new GFX card there. Im trying hard to get this ubuntu/MythTV setup running nicely for my partner & I, I would just love to isolate the problem at the mo so I new what knew what kit I need to get :confused: I'll post back tomorrow.

---

### Post by Nightwalker07 on 2007-10-03
Right, im at work, new GFX-Card (WinFast Geforce) brand new ubuntu 7.04 installation, no errors or problems. I thought this time I would do 'other' things to keep the system ticking oand check its general hardware-stability, instead of going straight into MythTV installation, plugins, codecs and all the rest.

So... I set it doing the 120 updates that it wanted to do, it dl'd and finished installing them fine. Installed UNIX & Samba share/services and setup a couple of shares, used Disk Usuage Anaylser & GIMP, all working fine no problems. Then I thought I'd set a GPU-intensive screensaver going to leave it under some stress, I previewed/fullscreened 'Atunnel' **then when I clicked the button in the top right to leave fullscreen the screen would go black for a second or two and then it would revert to the login screen.** I proceeded to login and it would basically reload me user-enviroment, so essentially clicking that leave-fullscreen button from the screensaver logged me out!? This same experience happened to me a couple of times last night when troubleshooting my MythTV installation, the same thing happened, since then I have a brand new ubuntu-installation and GFX card.

I have now got the system running MemTest86+, I would love to diagnose the problem so if anyone has ever seen this sort of behavior before, please any advise would be greatly appreciated!

---

### Post by Nightwalker07 on 2007-10-03
Update: There was 2 sticks of RAM in this system, a 512mb stick & a 128mb.

- **MemTest86+ found 6 errors on the 512MB stick, that was happily snapped and thrown away.**
- 128mb stick cleared OK.

I've got two new sticks of 256mb installed, so thats 512mb of RAM installed & checked OK.

- My colleague recommended selecting 'Desktop Effects' from the menu to have it install the NVIDIA drivers for the new GFX card, which it did fine. Reboot, and tried the whole screensaver 'Leave Fullscreen' issue I'd been having and **there was no longer an issue!**

So thats two issues we've just fixed; now I've got a more up to date GFX-card with drivers installed and functioning properly, secondly some faulty RAM was identified & removed. I think I'll save it till tomorrow to install MythTV, Mplayer, Codecs, Plugins etc. but hopefully things are looking up.

---

