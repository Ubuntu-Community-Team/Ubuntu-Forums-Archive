---
title: "Getting Mythbuntu up and running"
date: 2011-11-04
forum: Mythbuntu
---

### Post by rmjohnson144 on 2011-11-04
Hello, I found this while looking for a TV program for linux.  I looked it over and it sounded like a plug and play setup instead of installing Ubuntu and configuring it myself.  But, after install I can't get any TV at all.  The docs say it supports my TV card (Hauppauge HVR-2250).

I go to the terminal and run mythtv-setup like the program told me as it said it couldn't find a capture device.

when I get there it lists:

Card Type: Analog V4L capture card
Video device: (blank)
Probed info: Failed to open
VBI device: (blank)
Audio device: ALSA:deault
Forced audio sampling rate: (None)
Default input: (blank)

I can't select any of the blank fields drop down box.  nothing happens when I click on them.

Here's my current rig:
Motherboard:GigaByte Z68MA-D2H-B3
CPU: i3-2100T
RAM: 8GB G.Skill 1600MHz
Video: ATI HD 5670
TV Card: Hauppauge HVR-2250
HDD: WD 2TB Caviar Black SATA III - all for this install.


let me know if you need any more info
-=Mark=-
I run update and installed all the latest updates.  still no love.  Should I install the restricted drivers for my video card?

---

### Post by LowSky on 2011-11-05
did you install the firmware for the 2250? Linux only includes the driver, but not the firmware. See this link to get the TV card working.
[http://ubuntuforums.org/showpost.php?p=11205874&postcount=425](http://ubuntuforums.org/showpost.php?p=11205874&postcount=425)

then go to this link (start at step 4)
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)


**_READ EVERYTHING CAREFULLY_** and it will work.

---

### Post by vidtek on 2011-11-05
> **rmjohnson144 said:**
> Hello, I found this while looking for a TV program for linux.  I looked it over and it sounded like a plug and play setup instead of installing Ubuntu and configuring it myself.  But, after install I can't get any TV at all.  The docs say it supports my TV card (Hauppauge HVR-2250).

I go to the terminal and run mythtv-setup like the program told me as it said it couldn't find a capture device.

when I get there it lists:

Card Type: Analog V4L capture card
Video device: (blank)
Probed info: Failed to open
VBI device: (blank)
Audio device: ALSA:deault
Forced audio sampling rate: (None)
Default input: (blank)

I can't select any of the blank fields drop down box.  nothing happens when I click on them.

Here's my current rig:
Motherboard:GigaByte Z68MA-D2H-B3
CPU: i3-2100T
RAM: 8GB G.Skill 1600MHz
Video: ATI HD 5670
TV Card: Hauppauge HVR-2250
HDD: WD 2TB Caviar Black SATA III - all for this install.


let me know if you need any more info
-=Mark=-
I run update and installed all the latest updates.  still no love.  Should I install the restricted drivers for my video card?

  Hello Mark-  I'm in the same boat as you, with HVR2200 tuner card.    Thought I'd upgrade to oneric I use a 250gb for my o/s drive as I have three or four lying round the workbench so took a backup of my o/s drive and promptly dropped the backup hdd off the bench halfway through the oneric install.
     
  It's a nice brick now, so I am stuck with the oneric install. I managed to get sound working through SPDIF coaxial after much drama, and have most of the stuff I use, printers etc., but have been struggling with my hvr2200 and getting nowhere fast.   

   My dmesg | grep saa7164 is identical to yours.    The tv card and swimming pool controller is all  that remains to get going.  I control my pool chlorine and ph through a bluetooth connection to the modbus system of the pool controller box.  Unfortunately my programming skills don't extend to rewriting the controller programme for linux from windows xp so I use virtualbox.   
If you manage to get the Hauppauge going or find someone who has succeeded, please post it here.      Best of luck, Tony  

edit-  I tried Lowsky's instructions, but still no go for me.
 Tony

---

### Post by vidtek on 2011-11-05
Mark- 

I didn't answer your question with regard to restricted drivers for your ATI card.  Yes, you should, otherwise you won't get the best results.  The ATI drivers are not as mature as the Nvidia ones though, they are still a bit buggy from what I've read here and elsewhere.

Something else that may assist you along the way, install Kaffeine, it's an excellent all-round media player which uses DVB and Analogue tuners. It's a lot easier to test and see if the tuners are working in Kaffeine rather than Mythtv.

If the tuners don't show up in Kaffeine, you stand Buckley's chance with Mythtv. 

Best regards, Tony

---

### Post by rmjohnson144 on 2011-11-05
> **LowSky said:**
> did you install the firmware for the 2250? Linux only includes the driver, but not the firmware. See this link to get the TV card working.
[http://ubuntuforums.org/showpost.php?p=11205874&postcount=425](http://ubuntuforums.org/showpost.php?p=11205874&postcount=425)

then go to this link (start at step 4)
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)


**_READ EVERYTHING CAREFULLY_** and it will work.

I did everything in the first post, but I couldn't find the capture device in backend.  I went to settings and it only had add a device.

but everything seem to go smoothly.  I didn't get any errors at all.

Thanks for your help and if you think I may have missed something let me know.

-=Mark=-

---

### Post by rmjohnson144 on 2011-11-05
I found the device by adding a new capture device.  However, I connot change the Card Type field.  It still reports the V4L type.

I tried adding another new device and it still says for device 1.  do I just manually change all the ) to 1 and save it?  I thought it would do this automatically and I don't want to alter anything and mess things up.

I reran the dmesg command and now I get this:

```
mark@mark-Z68MA-D2H-B3:~$ dmesg | grep saa7164
[    9.828438] saa7164 driver loaded
[    9.828492] saa7164 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.877888] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,insmod option]
[    9.877895] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfb800000
[    9.877903] saa7164 0000:02:00.0: setting latency timer to 64
[   10.042545] saa7164_downloadfirmware() no first image
[   10.042553] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   10.121594] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   10.121597] saa7164_downloadfirmware() firmware loaded.
[   10.121606] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   10.121611] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   10.121613] saa7164_downloadfirmware() BSLSize = 0x0
[   10.121615] saa7164_downloadfirmware() Reserved = 0x0
[   10.121617] saa7164_downloadfirmware() Version = 0x1661c00
[   16.965525] saa7164_downloadimage() Image downloaded, booting...
[   17.069390] saa7164_downloadimage() Image booted successfully.
[   19.110730] saa7164_downloadimage() Image downloaded, booting...
[   20.980299] saa7164_downloadimage() Image booted successfully.
[   21.024661] saa7164[0]: Hauppauge eeprom: model=88061
[   21.640555] DVB: registering new adapter (saa7164)
[   24.985102] DVB: registering new adapter (saa7164)
[   24.985412] saa7164[0]: registered device video0 [mpeg]
[   25.215027] saa7164[0]: registered device video1 [mpeg]
[   25.425782] saa7164[0]: registered device vbi0 [vbi]
[   25.425817] saa7164[0]: registered device vbi1 [vbi]
```

This reports devices for both 0 and 1.

Maybe I'll try the Kaffeine program Tony suggests and see what happens.

Thanks for the help fellas
-=Mark=-

---

### Post by vidtek on 2011-11-05
Lowsky and Mark-  

Just had a thought-I'm running the 64-bit version and I see from his stats that Mark is too.  
Oneric has truncated the 64-bit libary folder to virtually nothing.  I wonder if this has anything to do with it.  

Tony.

---

### Post by nickrout on 2011-11-05
> **rmjohnson144 said:**
> I found the device by adding a new capture device.  However, I connot change the Card Type field.  It still reports the V4L type.
It is not reporting anything, it is offering you a choice, v4L happens to be the first in the list. Try the left and right arrow buttons.

Are you trying to use the analogue or the digital side of this card?

---

### Post by vidtek on 2011-11-06
> **vidtek said:**
> Lowsky and Mark-  

Just had a thought-I'm running the 64-bit version and I see from his stats that Mark is too.  
Oneric has truncated the 64-bit libary folder to virtually nothing.  I wonder if this has anything to do with it.  

Tony.

D/loaded the 32-bit Oneric and installed on a spare drive.
Same result, so it's not a 64-bit problem.

Tony.

---

### Post by rmjohnson144 on 2011-11-08
I finally got it to work with Kaffeine under Ubuntu 10.04.3 LTS 64-bit.  It took some doing, but got running although the video blurs on quick motions.  I had to edit the xine-config file.  

```
# number of audio buffers
# numeric, default: 230
engine.buffers.audio_num_buffers:1500

# number of video buffers
# numeric, default: 500
engine.buffers.video_num_buffers:2500

# default number of video frames
# numeric, default: 15
engine.buffers.video_num_frames:50

```

the xine-config is a hidden file and can be found at .kde/share/apps/kaffeine  you will need su permissions.  I just used:
```
sudo su
```

I had to change the audio buffers at first as I was getting intermittent sound, and that didn't work, then I changed the video buffers and I got sound, but blur was bad.  I then changed video frames and that helped, but still a little blur.

I also had to install libxine1-ffmpeg that has some other xine utils with it:
```
sudo apt-get install libxine1-ffmpeg
```

I then tried it on Mythbuntu 11.04 64-bit, and installed Kaffeine and I got it to scan channels, but no video or audio at all.  not even the control button at the bottom Kaffeine worked.  they were all greyed out except the play button which didn't work.

still working for a solution for Mythbuntu 11.04, but Mythbuntu 11.10 gets me nothing at all.  not even channel scans yet.

hopefully someone reports success of sorts.

---

### Post by nickrout on 2011-11-09
> **rmjohnson144 said:**
> I finally got it to work with Kaffeine under Ubuntu 10.04.3 LTS 64-bit.  It took some doing, but got running although the video blurs on quick motions.  I had to edit the xine-config file.  

```
# number of audio buffers
# numeric, default: 230
engine.buffers.audio_num_buffers:1500

# number of video buffers
# numeric, default: 500
engine.buffers.video_num_buffers:2500

# default number of video frames
# numeric, default: 15
engine.buffers.video_num_frames:50

```

the xine-config is a hidden file and can be found at .kde/share/apps/kaffeine  you will need su permissions.  I just used:
```
sudo su
```

I had to change the audio buffers at first as I was getting intermittent sound, and that didn't work, then I changed the video buffers and I got sound, but blur was bad.  I then changed video frames and that helped, but still a little blur.

I also had to install libxine1-ffmpeg that has some other xine utils with it:
```
sudo apt-get install libxine1-ffmpeg
```

I then tried it on Mythbuntu 11.04 64-bit, and installed Kaffeine and I got it to scan channels, but no video or audio at all.  not even the control button at the bottom Kaffeine worked.  they were all greyed out except the play button which didn't work.

still working for a solution for Mythbuntu 11.04, but Mythbuntu 11.10 gets me nothing at all.  not even channel scans yet.

hopefully someone reports success of sorts.

So did you get the analogue or the digital side working?

---

### Post by leeper69 on 2011-11-09
I know this may help you get your TV working in Ubuntu. I don't use your capture card I use a PC 5500 but your card should work with kaffeine I chose to use this program over Meth TV because it is easy to set up and it works in KDE Gnome and XFCE desktops.

---

### Post by rmjohnson144 on 2011-11-09
> **nickrout said:**
> So did you get the analogue or the digital side working?

I only get the digital channels with dvb.  I haven't tried any of the others to see what I get.

I have just been trying to get any TV at all.  So far only the 10.04 worked.  11.04 scans and finds channels, but nothing displays at all.  11.10 gets nothing at all.

do I maybe need to compile something for 11.10?  not sure why it gets nothing unless the driver needs updating.  but the driver/firmware seem to load just fine.

In 10.04.3 I do get firmware issues saying the first firmware fails and second loads.  It says it every boot.  Maybe I'll try configuring MythTV in 10.04.3 to see if maybe it will help me to get it working in 10.11, since I know the card is working fine in 10.04.3

---

### Post by nickrout on 2011-11-09
> **rmjohnson144 said:**
> I only get the digital channels with dvb.  I haven't tried any of the others to see what I get.

I have just been trying to get any TV at all.  So far only the 10.04 worked.  11.04 scans and finds channels, but nothing displays at all.  11.10 gets nothing at all.

do I maybe need to compile something for 11.10?  not sure why it gets nothing unless the driver needs updating.  but the driver/firmware seem to load just fine.

In 10.04.3 I do get firmware issues saying the first firmware fails and second loads.  It says it every boot.  Maybe I'll try configuring MythTV in 10.04.3 to see if maybe it will help me to get it working in 10.11, since I know the card is working fine in 10.04.3

Well use 10.04 then! Why be hung up on a later release? You get the same version of mythtv once you install and use mythbuntu-repos.

If 10.04 works, use it.

---

### Post by rmjohnson144 on 2011-11-10
> **nickrout said:**
> Well use 10.04 then! Why be hung up on a later release? You get the same version of mythtv once you install and use mythbuntu-repos.

If 10.04 works, use it.

lol - you must be reading my mind.

I decided to run install Mythbuntu on my Ubuntu 10.04.3 but it is a nightmare.  I can't even get mythtv-setup to run at all.  It takes me to a config screen and ask me to choose a language then advamces to the database config menu and I can advance past it.  I thought it was lack of mysql, but I found it installed.  I even ran MySQL 5.1 reconfigure program and it still won't work.

I finally decided to just try Mythbuntu 10.04 and see what happens from there.  I figure since it's preconfigured I can get a little further than manually installing worrying if I'm missing some modules or something.

well, it's at 93% installed, so wish me luck.  lol
-=Mark=-

---

### Post by rmjohnson144 on 2011-11-12
well, I have partial success.  I got MythTV setup and watching video, but now I have no sound:P

I searched through Mythbuntu with no luck on finding any audio settings, and the one's I did find outside of mythbuntu interface reported there was no audio devices present.  But lsmod showed my ATIHDMI and an Intel HD audio.  I seen no Realtek audio, which my speakers are connected to.

Anyone know how I find or install sound for Mythbuntu 10.04?

I even update to latest everything (almost 300 updates) including kernel.  still no sound.

any tips?
-=Mark=-

---

### Post by rmjohnson144 on 2011-11-12
Well, I rebooted my pc and now when I go to watch V I get an error:

Mythtv is using all inputs, but there are no active recordings.

Search has revealed nothing.  It usually states a wrong IP in frontend and backend, but I double  checked and frontend has 127.0.0.1 and backend has 127.0.0.1 on both fields.

I then decided to install Kaffeine and it works great after installing libxine1-ffmpeg.  Sound is working as well.

not sure what else to try?

---

### Post by vidtek on 2011-11-13
> **rmjohnson144 said:**
> well, I have partial success.  I got MythTV setup and watching video, but now I have no sound:P

I searched through Mythbuntu with no luck on finding any audio settings, and the one's I did find outside of mythbuntu interface reported there was no audio devices present.  But lsmod showed my ATIHDMI and an Intel HD audio.  I seen no Realtek audio, which my speakers are connected to.

Anyone know how I find or install sound for Mythbuntu 10.04?

I even update to latest everything (almost 300 updates) including kernel.  still no sound.

any tips?
-=Mark=-

Mark-

You're nearly there-keep at it and you'll have sound.

It'll be easier to describe the steps you now need to take if you can use the "Terra" skin so I can tell you exactly what you need to do.  Start Mythtv and go to Themes.  Switch to Terra theme.
Now use the arrow keys to select the next step which is the setup icon.

Press enter until you get to the general setup.  Then enter 3 times which should get you to the audio setup.  Hit the down key 3 times which will highlight the "scan for audio devices" field.  Press enter and wait a few seconds.  Then down arrow key to the next field.

Then press the right arrow key to select the correct audio configuration for your setup.  There will be multiple choices, if you don't know which one, go through each in turn using the above steps until you get sound.  This will take a while, but it's the best way.

I'll respond to your next query in another post.

Bet regards, Tony.

---

### Post by vidtek on 2011-11-13
> **rmjohnson144 said:**
> Well, I rebooted my pc and now when I go to watch V I get an error:

Mythtv is using all inputs, but there are no active recordings.

Search has revealed nothing.  It usually states a wrong IP in frontend and backend, but I double  checked and frontend has 127.0.0.1 and backend has 127.0.0.1 on both fields.

I then decided to install Kaffeine and it works great after installing libxine1-ffmpeg.  Sound is working as well.

not sure what else to try?

Mark-

This is a common Mythtv error.

I presume you are using a single box, looking at your signature stats.

Firstly, cold boot.  Power down for a couple of minutes at least, not just reboot.

It's a good idea to use a static I.P. address, if you don't know how to do that, look in your modem/router manual and change it's DHCP settings so your network MAC address is set to always issue a particular I.P. address to your machine.  Ascertain your machine's MAC address by using the command ->  ifconfig  in a terminal.  It will return a whole lot of stuff, but the bit you are interested in will look like this:


tony@workshopubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr _***1c:6f:65:c7:33:fe***_  
          inet addr:192.168.0.42  Bcast:192.168.0.255  Mask:255.255.255.0

I have bolded, italicised and underlined my machine's MAC address.

When the system comes back up, start mythtv, and go to setup -> general.

Put your ip. address in both the master and slave fields and you should then be able to see live tv.

One more thing- ATI video cards have flaky linux drivers, so you may need to go to the TV icon (in mythtv) then -> tv settings -> playback -> enter twice then down arrow key 3 times to highlight the "current video playback profile" field.  Change this to normal with the right arrow key before trying to watch tv .  You can then experiment to see which setting works best for you.

This is the beauty and pain of Mythtv, it is ultra-configurable which is a two-edged sword sometimes.

Best of luck Tony.

---

### Post by vidtek on 2011-11-13
> **vidtek said:**
> D/loaded the 32-bit Oneric and installed on a spare drive.
Same result, so it's not a 64-bit problem.

Tony.

Failed miserably to get my HVR2200 working on Oneric so I reverted back to

11.04

If anyone has succeeded to get this card going with Oneric can they please post a how-to?

Tony.

---

### Post by rmjohnson144 on 2011-11-13
I finally got sound last night.  While reading one of the many, many threads on the subject I hit one that said to scan for devices, which I don't have, and a few posts down some said they were using an outdated mythtv and suggested to upgrade to a newer version.  I followed the link they provided and upgraded to 0.24.1 as post advised, and voila! I had sound.  There was also a version 0.25, but wasn't sure how stable it was, so I just stayed with 24.1.

ah, so I should use my IP from router then.  I tried using that first, but could never get it to work, so I tried localhost and it worked.  I'll give that a try later.

Thanks for the tip on the ATI card setup.  I know they aren't very Linux friendly. I have a spare nvidia 210 in the closet if things look too bad.  I have a 5670 on here now as I game on it a lot on my win 7 boot drive.  I'll probably upgrade to a 440 or something later on.  Probably after x-mas.

---

### Post by rmjohnson144 on 2011-11-13
well, I changed my IP addresses to my local 192.168.1.142, but now when it starts it says:

Could not connect to master backend server.  Is it running?  Is the IP address set for it in mythtv-setup correct?

It still lets me watch tv though.  I only get the message when first starting up.

a wierd side effect, is now Kaffeine doesn't work.  It says no available device found.  it seems mythtv is blocking it somehow?

also, I'm trying to make the tv video a small windows so I can watch it while doing other things.  but, so far I can't seem to get it working right.

---

### Post by RideMan on 2011-11-13
If it is letting you watch TV, then it is successfully connecting to the backend. As an experiment, try this: quit MythTV front end, then run it again from the applications|multimedia menu. If you don't get the "could not connect" error, then your trouble is that frontend is starting up before backend is ready. So you can safely ignore the message.

I have the same problem, so when I figure out how to fix it, I'll let you know here.

--Dave Althoff, Jr.

---

### Post by rmjohnson144 on 2011-11-14
> **RideMan said:**
> If it is letting you watch TV, then it is successfully connecting to the backend. As an experiment, try this: quit MythTV front end, then run it again from the applications|multimedia menu. If you don't get the "could not connect" error, then your trouble is that frontend is starting up before backend is ready. So you can safely ignore the message.

I have the same problem, so when I figure out how to fix it, I'll let you know here.

--Dave Althoff, Jr.

Cool, I figured it had to be fine as it was working OK.  Only on first boot does it say anything.

I just finished configuring Mythbuntu 11.04 and after updating to MythTV 0.24.1 it worked first try, no hiccups at all.

Maybe I'll give 11.10 a try tomorrow now that I nkow how to set things up.

too bad Kaffeine still doesn't startup.  I really liked the ability to watch TV in a little screen so I can watch foorball while working on my computer.

Maybe I'll figure out how to get MythV to have different size windows.

---

### Post by Tasmac on 2011-11-14
hey mark, I found the thread and read all all the added threads.

Oh ya, finally got MythTV installed on a Kernel sever(ubuntu 10.04) yaa :)
the server does not have a desktop, but i can log on another pc and activate a desktop for it. the frontend played live tv just fine. the problem is on the network side.
   I have XMBC on my laptop (ubuntu) and under video I have mythtv I click on that I can see recorded movies(just folders, nothing in them) and on live tv I can see the channels , but when i click on them .. nothing if I click on the 2 more times I get a 2013:connect to MySQL failed error

On mythbox under XBMC it fails to connect. but it gets the packets because if I change the settings I get packet failure
according to the Mythbox log it is also 2013:connect to MySQL failed error. highlighted in red
       _______________________________________________

                         The log from my laptop: mythbox under XBMC

```
I | bootstrapper.py | MainThread | Line 88 | Mythbox Logger Initialized
D | platform.py | MainThread | Line 107 | syspath[0] = /home/tasmac/.xbmc/addons/script.mythbox
D | platform.py | MainThread | Line 107 | syspath[1] = /home/tasmac/.xbmc/addons/script.module.simplejson/lib
D | platform.py | MainThread | Line 107 | syspath[2] = /home/tasmac/.xbmc/addons/script.module.beautifulsoup/lib
D | platform.py | MainThread | Line 107 | syspath[3] = /usr/lib/xbmc/addons/script.module.pil/lib
D | platform.py | MainThread | Line 107 | syspath[4] = /home/tasmac/.xbmc/addons/script.module.elementtree/lib
D | platform.py | MainThread | Line 107 | syspath[5] = /usr/lib/xbmc/addons/script.module.pysqlite/lib
D | platform.py | MainThread | Line 107 | syspath[6] = /usr/lib/xbmc/system/python/python24.zip
D | platform.py | MainThread | Line 107 | syspath[7] = /usr/share/xbmc/system/python/lib/python24.zip
D | platform.py | MainThread | Line 107 | syspath[8] = /usr/share/xbmc/system/python/lib/python2.4/
D | platform.py | MainThread | Line 107 | syspath[9] = /usr/share/xbmc/system/python/lib/python2.4/plat-linux2
D | platform.py | MainThread | Line 107 | syspath[10] = /usr/share/xbmc/system/python/lib/python2.4/lib-tk
D | platform.py | MainThread | Line 107 | syspath[11] = /usr/share/xbmc/system/python/lib/python2.4/lib-dynload
D | platform.py | MainThread | Line 107 | syspath[12] = /home/tasmac/.xbmc/addons/script.mythbox/resources/src
D | platform.py | MainThread | Line 107 | syspath[13] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/decorator
D | platform.py | MainThread | Line 107 | syspath[14] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/odict
D | platform.py | MainThread | Line 107 | syspath[15] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/bidict
D | platform.py | MainThread | Line 107 | syspath[16] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/elementtree
D | platform.py | MainThread | Line 107 | syspath[17] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/tvdb_api
D | platform.py | MainThread | Line 107 | syspath[18] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/tvrage
D | platform.py | MainThread | Line 107 | syspath[19] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/themoviedb
D | platform.py | MainThread | Line 107 | syspath[20] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/IMDbPY
D | platform.py | MainThread | Line 107 | syspath[21] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/simplejson
D | platform.py | MainThread | Line 107 | syspath[22] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/mysql-connector-python
D | platform.py | MainThread | Line 107 | syspath[23] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/python-twitter
D | platform.py | MainThread | Line 107 | syspath[24] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/twisted
D | platform.py | MainThread | Line 107 | syspath[25] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/zope.interface
D | platform.py | MainThread | Line 107 | syspath[26] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/mockito
D | platform.py | MainThread | Line 107 | syspath[27] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/unittest2
D | platform.py | MainThread | Line 107 | syspath[28] = /home/tasmac/.xbmc/addons/script.mythbox/resources/lib/unittest
D | platform.py | MainThread | Line 107 | syspath[29] = /home/tasmac/.xbmc/addons/script.mythbox/resources/test
I | bootstrapper.py | MainThread | Line 100 | MythBox 1.0.4 Initialized
D | settings.py | MainThread | Line 152 | Loading settings from /home/tasmac/.xbmc/userdata/addon_data/script.mythbox/settings.xml
D | bootstrapper.py | MainThread | Line 215 | Punting on debug shell -- not packaged
D | home.py | MainThread | Line 61 | lastfocusid = 250
D | db.py | MainThread | Line 173 | Initializing myth database connection
[COLOR=Red]**D | toolkit.py | MainThread | Line 84 | showPopup: XBMC.Notification(Error,Connect to MySQL failed: 2013: Lost connection to MySQL server during query,7000)**[/COLOR]
D | advanced.py | MainThread | Line 79 | /home/tasmac/.xbmc/userdata/advancedsettings.xml does not exist. Starting fresh
D | uisettings.py | MainThread | Line 162 | Advanced settings:
 <advancedsettings />
D | uisettings.py | MainThread | Line 170 | onInit
D | uisettings.py | MainThread | Line 256 | Rendering mysql_user
D | uisettings.py | MainThread | Line 256 | Rendering video/timeseekbackward
D | uisettings.py | MainThread | Line 256 | Rendering fanart_tvrage
D | uisettings.py | MainThread | Line 256 | Rendering mysql_password
D | uisettings.py | MainThread | Line 256 | Rendering logging_enabled
D | uisettings.py | MainThread | Line 256 | Rendering mysql_host
D | uisettings.py | MainThread | Line 256 | Rendering mysql_port
D | uisettings.py | MainThread | Line 256 | Rendering paths_recordedprefix
D | uisettings.py | MainThread | Line 256 | Rendering streaming_enabled
D | uisettings.py | MainThread | Line 256 | Rendering mysql_database
D | uisettings.py | MainThread | Line 256 | Rendering fanart_tmdb
```all the settings are basic too make it easier, ill change them later

I only get this error log for mythbox, I have no idea where the error log for XMBC mythtv
If ya recognize anything, im all ears
--------------------------
**/etc/mysql/conf.d/mythtv.cnf**
[mysqld]
bind-address=0.0.0.0
------------------------------
**I adde this line in MySQL **
mysql> grant all on mythconverg.* to mythtv@"192.168.1.%" identified by "mythtv"
--------------------------------------------
**/home/anthony/.mythtv/mysql.txt **
DBHostName=192.168.1.128
DBHostPing=no
DBUserName=mythtv
DBPassword=mythtv
DBName=mythconverg
DBType=QMYSQL3
LocalHostName=Media-Server
-------------------------------------
**/etc/mysql/my.cnf **
#bind-address           = 127.0.0.1
--------------------------------------
 If i missed anything let me know thanx tasmac

---

### Post by Tasmac on 2011-11-16
figured i would put this in, after a lot of reading I'm a nube at MySQL :
---------------------------------------

$ mysql -u root -p

    ****To see user's Grant tables table****

mysql> SHOW GRANTS FOR 'username'@'xxx.xxx.x.xxx';  (xxx.xxx.x.xxx is the user's ip address)

******To Create a user*****

mysql> connect mythconverg;
mysql> GRANT ALL PRIVILEGES ON mythconverg.* TO 'someuser'@'xxx.xxx.x.xxx' IDENTIFIED BY 'your_password';
mysql> flush privileges;
mysql> exit;


******To delete a user*****
mysql> connect mythconverg;
mysql> REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'someuser'@'xxx.xxx.x.xxx';    (you have to make sure they have no grants or privileges before you can remove the user)
mysql> DROP USER 'someuser'@'xxx.xxx.x.xxx';
mysql> flush privileges;
mysql> exit;
---------------------------------------------------------------------------------

#bind-address localhost 127.0.0.1  in /etc/mysql/my.cnf  


I put this in because I hate using default user's and passwords  that everyone on earth knows. and per ip address. 

so all 5 computer locations connect using different accounts

I havent figured out yet how to view who is actually in the DB by a single search :confused:
or how many user's they are

---

### Post by vidtek on 2011-11-17
> **rmjohnson144 said:**
> Cool, I figured it had to be fine as it was working OK.  Only on first boot does it say anything.

I just finished configuring Mythbuntu 11.04 and after updating to MythTV 0.24.1 it worked first try, no hiccups at all.

Maybe I'll give 11.10 a try tomorrow now that I nkow how to set things up.

too bad Kaffeine still doesn't startup.  I really liked the ability to watch TV in a little screen so I can watch foorball while working on my computer.

Maybe I'll figure out how to get MythV to have different size windows.

In the TV ->setup ->appearance there are options to size the Mythtv display. Aternatively, start mythfrontend -w  to put it into a normal window (so you can access the taskbar with the mouse)
Tony.

---

### Post by nickrout on 2011-11-17
> **Tasmac said:**
> figured i would put this in, after a lot of reading I'm a nube at MySQL :
---------------------------------------

$ mysql -u root -p

    ****To see user's Grant tables table****

mysql> SHOW GRANTS FOR 'username'@'xxx.xxx.x.xxx';  (xxx.xxx.x.xxx is the user's ip address)

******To Create a user*****

mysql> connect mythconverg;
mysql> GRANT ALL PRIVILEGES ON mythconverg.* TO 'someuser'@'xxx.xxx.x.xxx' IDENTIFIED BY 'your_password';
mysql> flush privileges;
mysql> exit;


******To delete a user*****
mysql> connect mythconverg;
mysql> REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'someuser'@'xxx.xxx.x.xxx';    (you have to make sure they have no grants or privileges before you can remove the user)
mysql> DROP USER 'someuser'@'xxx.xxx.x.xxx';
mysql> flush privileges;
mysql> exit;
---------------------------------------------------------------------------------

#bind-address localhost 127.0.0.1  in /etc/mysql/my.cnf  


I put this in because I hate using default user's and passwords  that everyone on earth knows. and per ip address. 

so all 5 computer locations connect using different accounts

I havent figured out yet how to view who is actually in the DB by a single search :confused:
or how many user's they are

mythtv is not designed to be secure. It is designed to be used on your LAN without external access. 

All of the necessary access and passwords is set up by default with the ubuntu packages. But you nedd to make sure you specify that other hosts on the network can connect (do not fall into the trap of thinking you only want a BE/FE combined machine alone forever).

sudo dpkg-reconfigure is your friend if you screw these things up.

---

### Post by rmjohnson144 on 2011-11-17
I just decided to install Mythbuntu 11.10 today and it went very smoothly.  although, in addition to the backend error, now I get a error when I hit watch TV the first time:

```
Error:  MythTV is using all inputs, but there are no active recordings?
```

I hit OK and it returns me to the frontend where I select Watch TV again, and then it works fine.

The setup was basically the the same as the others I did following the instructions from Lowsky in post #2.

@Tasmac

Sorry I can't be of more help as I'm not quite as far as you are.  I will be looking for help setting this up to work over the router soon to work on my iPad 2 and wireless desktop.  so, you may be hearing from me soon!  lol

Thanks for everyone's help getting this up and running.
-=Mark=-

---

### Post by Tasmac on 2011-11-18
> **nickrout said:**
>  (do not fall into the trap of thinking you only want a BE/FE combined machine alone forever).



Actually I don't have any FE/BE combined machines.
I have one Backend only server on one rig, and 3 frontend only clients

---

