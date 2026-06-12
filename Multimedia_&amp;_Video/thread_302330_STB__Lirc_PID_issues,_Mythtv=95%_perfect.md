---
title: "STB / Lirc PID issues, Mythtv=95% perfect"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by wgaprotest on 2006-11-18
See my last explanation and buy the 150 model if you need a digital setop box.

:-k MythTv is 95% working and gorgeous. I'm very pleased with Edgy (so easy for sun-java, flash, ivtv, and so many other things) superm1's great work on the howto's, and, if I do say it myself, this noob.

I am able to change channels, watch live tv with audio and video, record tv, use lirc with mplayer, and almost everything else. The last issues to resolve are:

1. The change-channel-lirc is not running in daemon mode, and I believe it should be from a previous faulty installation. There is no change-channel-lirc.pid file anywhere on the system. When I wake the mythbackend as a user I do get the line: "External Tuning program exited with no error" and while I intend to stop doing that (start it as a user), it's giving me these useful logging outputs.

2. This next problem is probably a result of #1: I generally have to tune the channel to 3 with the "ivtv-tune -c 3" terminal command prior to starting mythfrontend. Then, when I try to change channels while I'm watching live tv (with the hauppague remote) what I get is the numbers on the tv screen, but that's it. If I use "26-ok" the playback shows the channel number on the screen, pauses, and that's it. The recordings menu show different tv programs that would correspoond with the channels I pressed, but watching those recordings reveals that the channel had remained at ch 3.

I must use the original remote that came with the universal cable STB (Explorer 1840) before the channels will actually change. Similarly, when recording something I've planned from the EPG guide, I must make sure I've changed the channel to the correct one with the STB's remote.

3. This may be a clue: when I type in "irw" in terminal, and press remote buttons, the result is the correct channel number, but with Hauppauge_350, and I have a Hauppauge 250. I believe it should be returning the Hauppauge _pvr, or Hauppauge 250. Not a big deal, but...For the lircrc file I used the one that was posted, being applicable for all Hauppauge remotes, mythtv, mplayer, and xine. I did uncomment the correct section corresponding to my card, leaving the 350's brand name (and another corresponding line) commented. 

4. Once I can get the STB working properly with the remote, then perhaps I can move on to fix a couple of other things. I used to get a cdrecord error relating to scanbus, but that seems to be gone now that I added the lirc to the rc.local file as per another forum howto. Now I'm getting something brand new, although it's probably of minor significance due to what I think is a counter issue:

2006-11-18 11:34:48.086 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(1983)
2006-11-18 11:34:48.088 TFW, Error: Write() -- IOBOUND end
2006-11-18 11:34:48.099 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(1983)
2006-11-18 11:34:48.101 TFW, Error: Write() -- IOBOUND end 

If someone can help me with these, especially the STB issue, I may be finally ready to tackle how to get the mythbackend daemon running all the time.

Thanks in advance for any help you can give me.

---

### Post by superm1 on 2006-11-19
> **wgaprotest said:**
> 
1. The change-channel-lirc is not running in daemon mode, and I believe it should be from a previous faulty installation. There is no change-channel-lirc.pid file anywhere on the system. When I wake the mythbackend as a user I do get the line: "External Tuning program exited with no error" and while I intend to stop doing that (start it as a user), it's giving me these useful logging outputs.

The first thing to check here is if you have more then one of these change-channel-lirc's sitting around.  Look around /usr/local/bin/ and /usr/bin.  Make sure that only one is there.  Next thing is the permissions on /dev/lirc*.  When running the backend in daemon mode, the 'mythtv' user will need to have write/read permissions on /dev/lirc*.  A quick experiment would be to change the ownership of the /dev/lirc0 or /dev/lirc1 that you are using to mythtv:mythtv, and then start the backend as a daemon.  If this works, you have identified your problem and need to set the permissions via a udev rule or rc.local.

> **wgaprotest said:**
> 
2. This next problem is probably a result of #1: I generally have to tune the channel to 3 with the "ivtv-tune -c 3" terminal command prior to starting mythfrontend. Then, when I try to change channels while I'm watching live tv (with the hauppague remote) what I get is the numbers on the tv screen, but that's it. If I use "26-ok" the playback shows the channel number on the screen, pauses, and that's it. The recordings menu show different tv programs that would correspoond with the channels I pressed, but watching those recordings reveals that the channel had remained at ch 3.

I must use the original remote that came with the universal cable STB (Explorer 1840) before the channels will actually change. Similarly, when recording something I've planned from the EPG guide, I must make sure I've changed the channel to the correct one with the STB's remote.

See if #1 is fixed and then try this again :)

> **wgaprotest said:**
> 
4. Once I can get the STB working properly with the remote, then perhaps I can move on to fix a couple of other things. I used to get a cdrecord error relating to scanbus, but that seems to be gone now that I added the lirc to the rc.local file as per another forum howto. Now I'm getting something brand new, although it's probably of minor significance due to what I think is a counter issue:

2006-11-18 11:34:48.086 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(1983)
2006-11-18 11:34:48.088 TFW, Error: Write() -- IOBOUND end
2006-11-18 11:34:48.099 TFW, Error: Write() -- IOBOUND begin cnt(2048) free(1983)
2006-11-18 11:34:48.101 TFW, Error: Write() -- IOBOUND end 

This is a very nasty problem to debug usually.  When is this happening?  If it's happening when you have multiple recordings going at the same time or lots of things accessing the drives (eg frontends, other backends comm flagging), then your drives can't handle the load. 

If it's happening when say a frontend is watching and the backend is just recording one show, then you have probably got some hardware related problems.  I had a LVM2 setup spanned across 5 drives, and ran into this once.  It took me going through and running DFT on each of the drives, checking smart logs, and running performance tests on the drives to identify which one it is.  This can also be a bad IDE/SATA cable or possibly even a bad controller.

---

### Post by wgaprotest on 2006-11-20
Thank you so much for your time and kind reply, superm1. You may very well be the only person who can help me sort this out, as I've already tried in so many places, including the #myth-users irc channel.

A bit of an update before I delineate how I've attempted to follow your suggestions. I must admit that I've been at this for hours, so I'm exhausted. My latest log will follow at the bottom.
[INDENT]Just before I read your reply, I'd read somewhere about the numbering of the tuners being crucial, and so deleted the tuner, sources, inputs, etc. from mythtv-setup, to almost start from scratch, and looking for more cleanliness to avoid getting mixed up. Then I ran into other issues and with perms to the recordings directory, and assorted other things, and it's taken me hours to get back to being able to watch and listen to a live tv feed. LOL, I thought I'd finally mastered chown/chmod and permissions...[/INDENT]

> The first thing to check here is if you have more then one of these change-channel-lirc's sitting around. 
There were a couple in the trash, so I emptied those.
> Next thing is the permissions on /dev/lirc*. When running the backend in daemon mode, the 'mythtv' user will need to have write/read permissions on /dev/lirc*. A quick experiment would be to change the ownership of the /dev/lirc0 or /dev/lirc1 that you are using to mythtv:mythtv, and then start the backend as a daemon.
I really thought this was the source of the problem, as the ownership of lirc was root:root and the permisions had no executables for anyone. I've now changed it to mythtv:users, with full rwx for all--at least until I have this box set up properly for myself and mythtv...then I'll worry about my son and reducing the write permissions. I really didn't want the ownership of the lirc to be restricted to mythtv only, as I plan to be using the remote for other programs, too, and I want to be able to watch/listen to tv/music while I'm doing other things, here on my own desktop, and not just on the mythtv's desktop. That should be ok, right?

But no, changing the ownership and permissions of the /dev/lirc didn't help me change channels with the remote: perhaps because: <get this> after the reboots the ownership, permissions, and lack of executables is back to the way it was originally when I discovered them. All I'm getting is the same old, same old. And quite frankly, I don't think I know how to set permissions through:
> need to set the permissions via a udev rule or rc.local

I also confirmed for myself a suspicion that (after reading another thread to which you'd contributed) that I have to be the mythtv user before the /etc/init.d/mythtv-backend will work as advertised. I can now start/stop/restart from kcontrol--system services, and from konsole, too.

I do, however, always have to, after the initial login, use "ivtv-tune -c 3" to get any livetv feed. That should be fairly easy to setup as automatic, but I can't remember how (I tried setting it up as a post-BE startup command in the global mythtv-settings, but nada). After the initial login and tuning with ivtv-tune, then mythtv will remember the last channel I was in for subsequent starts of mythfrontend.

At least I'm not getting any more IOBOUND errors, but it took some doing to get rid of them. And the cdrecord--scanbus error is back, although I thought I'd taken care of that for good, too.

And the picture isn't as good as it was...I've tried some other codecs, deinterlacing, opengl settings, etc, but these things result in either a total system crash or inability to see any livetv feed.

How to make the ownnership, permissions, and executable ability of the lirc stick? I must admit, however, that I have little hope that changing these things permanently will solve the channel-changing issue, as I'm sure it didn't help before a reboot while they were still ok. I really don't know what to do about the NV and buffer issues (buffering pauses only occur when I'm trying unsuccessfully to change the channel with the Hauppauge remote; they don't occur at all when I do successfully change the channel with the STB remote.

Any ideas/suggestions would be appreciated.

Regards...](*,) ](*,) ](*,)

P.s. don't worry about the sdb (usb printer/scanner/mfc) or the SIP stuff that's for mythphone...I couldn't be bothered about gallery or phone for now. It's the channels.... <grrrrrr>

-----------------------------------------------------------------------
 $ mythbackend & mythfrontend
2006-11-20 03:01:22.639 Using runtime prefix = /usr
2006-11-20 03:01:22.724 New DB connection, total: 1
2006-11-20 03:01:22.770 Connected to database 'mythconverg' at host: localhost
2006-11-20 03:01:22.777 Current Schema Version: 1160
Starting up as the master server.
2006-11-20 03:01:22.790 New DB connection, total: 2
2006-11-20 03:01:22.791 Connected to database 'mythconverg' at host: localhost
2006-11-20 03:01:22.792 mythbackend: MythBackend started as master server
2006-11-20 03:01:22.801 EITHelper: localtime offset 0:00:00
2006-11-20 03:01:22.809 New DB connection, total: 3
2006-11-20 03:01:22.810 Connected to database 'mythconverg' at host: localhost
2006-11-20 03:01:23.000 Using runtime prefix = /usr
2006-11-20 03:01:23.020 DPMS is active.
2006-11-20 03:01:23.068 New DB connection, total: 1
2006-11-20 03:01:23.078 Connected to database 'mythconverg' at host: localhost
2006-11-20 03:01:23.082 Total desktop dim: 1024x768, with 1 screen[s].
2006-11-20 03:01:23.086 Running in a window
2006-11-20 03:01:23.087 Using screen 0, 1024x719 at 0,0
2006-11-20 03:01:23.365 Current Schema Version: 1160
2006-11-20 03:01:23.366 mythfrontend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2006-11-20 03:01:23.366 Enabled verbose msgs:  important general
2006-11-20 03:01:23.889 Total desktop dim: 1024x768, with 1 screen[s].
2006-11-20 03:01:23.890 Running in a window
2006-11-20 03:01:23.890 Using screen 0, 1024x719 at 0,0
2006-11-20 03:01:23.892 Switching to square mode (Titivillus)
2006-11-20 03:01:23.908 Using the Qt painter
2006-11-20 03:01:24.177 ret_pid(0) child(6517) status(0x0)
2006-11-20 03:01:24.262 Joystick disabled.
2006-11-20 03:01:24.481 Loading from: /usr/share/mythtv/themes/default/base.xml
2006-11-20 03:01:24.894 Registering Internal as a media playback plugin.
2006-11-20 03:01:24.931 Registering MythDVD DVD Media Handler as a media handler ext()
2006-11-20 03:01:24.932 Mediamonitor: Adding /dev/hdc
2006-11-20 03:01:24.950 Mediamonitor: Adding /dev/fd0
no record for '/block/hdc/device' in database
no record for '/block/hdc/holders' in database
no record for '/block/hdc/queue' in database
no record for '/block/hdc/slaves' in database
2006-11-20 03:01:24.976 Mediamonitor: AddDevice() -- Not adding '/dev/hdc', it appears to be a duplicate.
no record for '/block/sdb/device' in database
no record for '/block/sdb/holders' in database
no record for '/block/sdb/queue' in database
no record for '/block/sdb/slaves' in database
2006-11-20 03:01:25.003 Registering MythDVD VCD Media Handler as a media handler ext()
2006-11-20 03:01:25.026 Registering MythGallery Media Handler 1/2 as a media handler ext()
2006-11-20 03:01:25.026 Registering MythGallery Media Handler 2/2 as a media handler ext(gif,jpg,png)
2006-11-20 03:01:25.026 MonitorRegisterExtensions(0x100, gif,jpg,png)
2006-11-20 03:01:25.181 ret_pid(0) child(6517) status(0x0)
2006-11-20 03:01:26.185 ret_pid(0) child(6517) status(0x0)
Failed to run 'cdrecord --scanbus'
2006-11-20 03:01:27.189 ret_pid(6517) child(6517) status(0x0)
2006-11-20 03:01:27.189 External Tuning program exited with no error
2006-11-20 03:01:27.209 New DB scheduler connection
2006-11-20 03:01:27.210 Connected to database 'mythconverg' at host: localhost
2006-11-20 03:01:27.214 Main::Starting HttpServer
QServerSocket: failed to bind or listen to the socket
2006-11-20 03:01:27.222 Main::HttpServer Create Error
2006-11-20 03:01:27.223 Main::Registering HttpStatus Extension
2006-11-20 03:01:27.234 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2006-11-20 03:01:27.234 Enabled verbose msgs:  important general
2006-11-20 03:01:27.234 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2006-11-20 03:01:27.236 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2006-11-20 03:01:27.243 Failed to bind port 6543. Exiting.
Failed to run 'cdrecord --scanbus'
2006-11-20 03:01:28.178 Registering MythMusic Media Handler 1/2 as a media handler ext()
2006-11-20 03:01:28.179 Registering MythMusic Media Handler 2/2 as a media handler ext(ogg,mp3,aac,flac)
2006-11-20 03:01:28.179 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.101:5060 NAT address 192.168.0.101
SIP: Cannot register; proxy, username or password not set
2006-11-20 03:01:29.351 Starting media monitor.
2006-11-20 03:01:30.132 Executing '/usr/bin/pmount /dev/sdb'
mount: No medium found
mount: No medium found
2006-11-20 03:01:32.543 Failed to mount /dev/sdb.
2006-11-20 03:01:32.549 Media status changed...  New status is: MEDIASTAT_NOTMOUNTED old status was MEDIASTAT_UNPLUGGED
2006-11-20 03:01:36.633 New DB connection, total: 2
2006-11-20 03:01:36.634 Connected to database 'mythconverg' at host: localhost
2006-11-20 03:01:36.683 Connecting to backend server: 127.0.0.1:6543 (try 1 of 3)
2006-11-20 03:01:36.685 Using protocol version 31
2006-11-20 03:01:36.701 TV: Attempting to change from None to WatchingLiveTV
2006-11-20 03:01:36.702 Using protocol version 31
2006-11-20 03:01:41.707 DPMS Deactivated
2006-11-20 03:01:41.853 AFD: Opened codec 0x84f7ae0, id(MPEG2VIDEO) type(Video)
2006-11-20 03:01:41.888 AFD: Opened codec 0x84f7ee0, id(MP2) type(Audio)
2006-11-20 03:01:41.895 Opening OSS audio device '/dev/dsp'.
2006-11-20 03:01:41.945 VideoOutputXv: XvMCTex: Init failed
2006-11-20 03:01:41.947 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x209
2006-11-20 03:01:42.704 The realtime priority setting is not enabled.
2006-11-20 03:01:42.706 TV: Changing from None to WatchingLiveTV
2006-11-20 03:01:42.915 Video timing method: SGI OpenGL
2006-11-20 03:01:56.708 NVP: prebuffering pause
2006-11-20 03:01:58.831 NVP: Prebuffer wait timed out 10 times.
2006-11-20 03:02:00.463 New DB connection, total: 3
2006-11-20 03:02:00.480 Connected to database 'mythconverg' at host: localhost
2006-11-20 03:04:35.994 TV: Attempting to change from WatchingLiveTV to None
2006-11-20 03:04:36.478 TV: Changing from WatchingLiveTV to None
2006-11-20 03:04:36.486 DPMS Reactivated.
Destroying SipFsm object
[1] + Done(237)                  mythbackend
$

---

### Post by wgaprotest on 2006-11-20
I'm now in the process of learning how to write/update udev and rc rules. that should take care of why the /dev/lirc files ownership and permissions revert to root after reboot. Not an easy task for a noob, although I have written them for my scanner/printer/mfc when other howtos gave me exactly what to paste into them :) Since the whole mythtv, java, flash, etc is so easy on edgy, perhaps the mythtv/lirc sections of your howto need these steps included? In terms of marketing a wonderful distro for more frustrated windoze ppl to come on board the ubuntu bandwagon...I may end up removing/flushing all the lirc stuff as per your howto as well, so that everything is clean.

FYI, I do have windoze xp/mce here on my other sata drive, and all the hardware. It was the only thing that worked with my other ATI Theatre 550 Pro tuner, with its PCIE x1 hardware interface. (I just bought the Hauppauge for Linux because I had no hope of getting the ATI tuner working under Linux...a quick search will tell you it's not supported by any distro.) However, I couldn't find any lirc.conf files for that remote, unlike with the Hauppauge, so I didn't bother setting up the lirc_mce module. I'd also prefer to have as little of microshaft's products on my linux machine as possible. Of course, I may have to finish installing the wine and some winblows products (word, so I can use endnote under linux) for work purposes. I'm now back in win, actually, temporarily, so I can do some powerpoint & video-editing work that I promised to do.

Take care, I'll be back in a day or two after having mastered this udev stuff.

---

### Post by wgaprotest on 2006-11-23
System has been totally cleaned, lirc and change-channel-lirc.pl file re-done, permissions of devices improved and udev rule written. Those permissions on the /dev/lirc now stays the way it should be after reboot.

However, the status of being able to change channels with the hauppauge remote is still the same as previously: I can do eveerything with the remote except actually change the channels on the SA digital cable box. For channel changing I must still use the universal STB remote, and have to be physically here to do that at the right time. 

The disconect is still between lirc and the STB for that type of event only. I think this is an important clue, and so the solution must be with the change-channel-lirc.pl file. However, I've already tried editing the file from 'sleep 1' to sleep 3' and this doesn't work: live tv doesn't start up at all if these edits have been made.

I've also really struggled, but got the OpenGL and xorg.conf file edited, and think this is an important part that's missing from the MythTvEdgyHardwarenVidia section: users must enable the OpenGL by typing into a terminal: nvidia-settings , using texturing, anti-aliasing, and almost all the settings there. and then making that change in vo in mplayer, too. 

The howto needs the udev rules section. In the stuff I downloaded from your repository, Mario, (I used your i2c and the change-channel file) there is no lirc.rules file to edit. Or at least I couldn't find it, and all the howtos I've seen for myth say it should be in /usr/src/contrib, or something like that. It isn't. So I simply copied other howtos' udev rules into a new file called 90-lirc.rules, and updated the rc scripts. I'm still not sure I've done it properly, although it seems to work. Could I have just added that content to 10-local.rules file I created when I got my scanner to work? Should there also be a udev rule for the change-channel-lirc.pl file? Also, this time around, when I run muthfrontend from terminal, I don't see any mention of the change-channel-lirc file being activated during startup, or 'exiting without error' like it did last time.

The "Failed to run 'cdrecord --scanbus'" line does still show up twice, as per usual.

This is just some feedback for you, as well as an attempt at collaborative trouble-shooting. Edgy for i386 is so easy compared to Dapper, in terms of sun-java, ivtv, flash...so many things that it could really bring hordes of new Unbuntu users onboard, but new Ubuntu users need complete howtos if they're not to get frustrated and give up. Me, I like to solve mysteries, hack, contribute, etc. :)

---

### Post by wjston on 2006-11-24
[COLOR="Red"]However, the status of being able to change channels with the hauppauge remote is still the same as previously: I can do eveerything with the remote except actually change the channels on the SA digital cable box. For channel changing I must still use the universal STB remote, and have to be physically here to do that at the right time. 
[/COLOR]
Have you considered using a MyBlaster. Forgive me if you have already mentioned this as I have just joined the forum and was searching for an answer on configuring ivtv-tune also when I came across your post.

I purchased the serial MyBlaster and downloaded the scripts on the MyBlaster/MythTV web page, and after a some hair pulling, managed to get it finally working yesterday. I had a few issues - added mythtv to uucp and to dialout in /etc/group. The channel-change script should be set to 755 so that it is accessible by all users, and if you are using a serial connector, your channel-change script will have to be accessing the correct serial port to work. My script for the Blaster was written to access ttyS1, but my default port was ttyS0. After pointing the script in the right direction, I was able to control my ExpressVu receiver.

Have you been able to resolve your problem with tuning your card? I also have to start a terminal and input ivtv-tune -c 3 -d /dev/video0 in order to get MythTV to output a signal. I would very much appreciate if you or anyone else with a suggestion please post it and I will give it a try. Putting it in /etc/rc.local did not work in Ubuntu although it did work in my previous setup MythDora.

Hopefully, someone can resolve this issue quickly.

---

### Post by wgaprotest on 2006-11-24
Thanks for the suggestion, and your time. I'll keep it in mind, but if you knew how many remotes and related equipment I already have, (for 2 pc tuners, plus the 3rd external cable tuner) perhaps you'll understand why I'm reluctant to throw more $ at this, as well as doubtful that it would actually help solve the problem(s). From what I've read, the MyBlaster is more for satellite receivers, and then there's the problem of availability. Yes, the sites say MyBlaster ships out of Toronto here, but there's not even in the phone book, and carefully don't give their locations on their site--probably for a reason. Did you buy yours online with a credit card? They're probably an American or other international company that will only accept credit cards or other high-tech wire transfers for payment, which is a showstopper for me. None of Bestbuy, Futureshop, or the source carry MyBlaster, and while my $3K system is all custom-made, heavily researched, etc., I like retail, and for accessories I tend to go for convenience and good terms.

No, I haven't found a solution to the need to use the ivtv-tune -c 3 command after first bootup. But then again, I think that would be solved if I could get the Hauppauge remote to change the channels, as it will remember the channels/signals it was on.

Last but certainly not lease: Welcome to the community!

---

### Post by wjston on 2006-11-24
Are you logging into your computer as mythtv or yourself when you fire up mythtv? I was unable to and am still unable to use my remote if I log in as myself and fire up mythtv from the applications applet. If I log in as mythtv user, my remote works. I am unsure why this is (some permission problem), but I'm not going to spend anymore time trying to fix this as I may end up hosing my system.

I purchased the MyBlaster online, and paid the difference between US/Canadian currency, but I never had to pay duty as they have a shipping address from Toronto. 

Another option for setting up a remote is using an infrared keyboard and IR learning remote. Apparently, this is relatively easy but I can't vouch for that. I hope you can resolve your remote issue soon and get your system working to your satisfaction.

Thanks for the welcome.

---

### Post by wgaprotest on 2006-11-24
Yeah, if you have to pay difference in CDN/USD then it's American company that just maintains a shipping office here to lower their shipping costs to mostly american customers, but aren't committed to us, and expect to treat us like a 52nd state. <argh...don't get me started on American arrogance> lol

I am logging in as the mythtv user, backend stays up all the time, not an issue. It's the lack of a proper udev rule probably, or a buggy change-channel-lirc.pl file, or the strong-enough-pulse not actually going through the irblaster to the actual setop box. Perhaps it's a defective sticky between the blaster and the setop...I haven't the foggiest clue.](*,) ](*,) ](*,)

---

### Post by wgaprotest on 2006-11-27
Mystery is solved:

the problem is a hardware limitation of the IR blaster that comes with the 250 card: it is only a receiver, and won't transmit channel changes to a digital cable STB. I've made a post to the hardware incompatibility list. Hauppauge is going to replace my 250 card with a model 150, which has a better IR blaster that receives and transmits.

---

