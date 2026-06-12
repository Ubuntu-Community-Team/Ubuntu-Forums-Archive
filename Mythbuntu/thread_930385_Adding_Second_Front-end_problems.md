---
title: "Adding Second Front-end problems"
date: 2008-09-26
forum: Mythbuntu
---

### Post by Boppy3125 on 2008-09-26
Short version:  Installed Mythbuntu 8.04.1 on second machine as secondary back-end/front-end.  I configured the mysql to point to the primary, it looks like recorded TV comes up.  Live TV just kills Myth.  Video Manager is asking to remove videos from the database.

Help please.:confused:

Not sure where to go with the Live TV.  I thought since I was pointing to that database it would properly leverage the master back-end.  I have configured the ip addresses of both back-ends on this machine in the back-end setup, and that is it for now.  I am not ready to dive into the cable box setup right now.  What am I missing on using this front-end to watch TV from the other back-end?

Video Manager seems to see the list of videos that the master has, and is looking at this machine's paths for the files.  I don't want to loose anything, so I didn't let it delete them.  I actually want to get at those videos here.  Should I be looking at sharing and mounting that across the network into the same path?  I guess that is do-able.  I am surprised that it doesn't differentiate between the two machine's videos.

Any help would be appreciated.:confused:

---

### Post by volkswagner on 2008-09-26
You set it up as a slave backend?  Are there any tuners installed?  The problem can be related to playback settings on the new machine.  Try different playback profiles.

Videos and music are handled differently than tv/recordings directory.  Yes you will need to setup shares and mount them, for vids to be seen on remote machines.

Any information in the logs?  
/var/log/mythtv/mythfrontend.log
/var/log/mythtv/mythbacktend.log

---

### Post by Boppy3125 on 2008-09-26
Thanks volkswagner, I didn't know about the Playback Profiles.  I little searching now I see that if I don't have the hardware acceleration I should choose the "Slim" profile.  I don't think I knew what that setting really meant before.  I will try that and report back.:)

On the videos front, my concern is that if this front-end doesn't see some movie of the other front-end, this one's video manager wants to remove it from the database.  But then when I go back to watch it downstairs it will be gone.  I am fine with having to setup the network part and manage the videos a second time.  It just looks to me like Video Manager is not concerned with which machine I am on.  It seems to me like I should be able to have "Bug's Life" on two different front-ends at two different paths, but video manager will constantly want to delete these references.  Am I misunderstanding what video manager is wanting to do?:confused:

Forgot about the logs part, I will collect those and post back after I play with the profile part.

---

### Post by Archmage on 2008-09-26
Is your frontend allow to listen to conection outside him? You don't have set it on listen only to 127.0.0.1?

---

### Post by Boppy3125 on 2008-09-26
> **Archmage said:**
> Is your frontend allow to listen to conection outside him? You don't have set it on listen only to 127.0.0.1?

Huh?  Not sure what you are asking, maybe refer to a specific part of the front-end setup and I will look tonight.

---

### Post by Boppy3125 on 2008-09-26
OK, maybe this will clear up what I am trying to do.  I started with machine1 as a frontend/backend.  Life was good, decided to expand.

This week I installed on machine2.  I intend to some day configure the cable STB over firewire on this one, but that is after basics are stable.  So, I installed this as a secondary backend/frontend.  In the mythtv-setup (for this ones backend) I configured the "IP address for mythtv" setting to this guy's ip address.  Then set the "Master Server IP address" setting to machine1's ip.  {I am 80% sure that I have public address and not the loop back on machine1's settings of the same.  I will confirm that also.}

Selecting to watch live TV kills the frontend process, as does watch recordings.  I will look at the profile and confirm the master backend configuration.  If that doesn't solve it for me I will get the logs and post.

Manage Videos in machine2's frontend looks like it is going to remove machine1's videos.  Surely someone else is running multiple frontends with one myth database and different videos on the different machines.  I don't know what I should do here.  Maybe I let it remove all the entries next time then run down to machine1 and see for sure what happened.  I haven't really seen anything in wikis or forums that talks about difficulties with MythVideo on multiple fronends, so I assume I am doing something wrong.  Does anytone have experience with this type of setup?

---

### Post by volkswagner on 2008-09-26
> **Boppy3125 said:**
> .........Manage Videos in machine2's frontend looks like it is going to remove machine1's videos.  Surely someone else is running multiple frontends with one myth database and different videos on the different machines.  I don't know what I should do here.  Maybe I let it remove all the entries next time then run down to machine1 and see for sure what happened.  I haven't really seen anything in wikis or forums that talks about difficulties with MythVideo on multiple fronends, so I assume I am doing something wrong.  Does anytone have experience with this type of setup?

You will need to enter both video directories, in each setup.  I can't remember if it is comma separated list or just spaces.  You will still need to set up shares for both directions and both machines.  

The only issue should be when the secondary backend is off, the vids should show as unavailable on the master machine.

---

### Post by mark467 on 2008-09-27
I had a similar experience. You may have 2 problems. First to get the videos and music you need to share and mount them on 2nd pc. This is from another post from SiHa and it worked perfect:

 Re: remote frontend mount problem
It's not obvious, but the Frontend looks in it's local filesystem for Mythvideo etc, so you need to map these onto the backend directories.

There's an excellent guide to mouting nfs shares here:

[http://czarism.com/easy-peasy-ubuntu...s-file-sharing](http://czarism.com/easy-peasy-ubuntu...s-file-sharing)

and here:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I can't remember where I got this last bit, but my frontend /etc/fstab entries are (from memory):

192.backend.ip.address:/var/lib/mythtv/videos /var/lib/mythtv/videos nfs rsize=8192,wsize=8192,timeo=14,intr
192.backend.ip.address:/var/lib/mythtv/pictures /var/lib/mythtv/pictures nfs rsize=8192,wsize=8192,timeo=14,intr

I think the syntax is correct, but try
Code:

$sudo mount -a

before rebooting to check all is well.

To see the posters you will also need to do this to your folder containing the jpgs. Mine is located in /home/(username)/.mythtv/MythVideo
replace (username) with yours like this:

192.168.1.25:/home/mark467/.mythtv/MythVideo /home/mark467/.mythtv/MythVideo nfs rsize=8192,wsize=8192,timeo=14,intr

The destination folders you are mapping to must already exist, but don't neccesarily need to be the same as on the backend.

Once these are mounted, Mythvideo should be able to see stuff.

The other problem might be like my other post. See this post...

[http://ubuntuforums.org/showthread.php?t=930840](http://ubuntuforums.org/showthread.php?t=930840)

Hope this helps

---

### Post by Boppy3125 on 2008-09-28
Thanks Volkswagner and Mark467, I now have my mounts setup and sort of working.  I can browse the videos now.  I tried to watch a video and the same thing happened with TV, the Myth client seemed to crash.  Of course that was when the rest of the family came down and wanted to watch TV, so my troubleshooting was cut short again.

I am currently wondering if it this is related to the video drivers.  I have an on-board radeon Xpress 200 from ATI.  I had real problems getting my custom resolution to take.  Maybe I have messed up something there.

On the mounting side, I had shared with samba on my first computer so that my windows machine could push out the ripped DVDs and such.  I mounted the videos with SMB instead of NFS.  My thought is that it works so why start another service, or are there advantages that NFS will give me on this?

---

### Post by Boppy3125 on 2008-09-28
Not really anything in the backend log worth sharing.  Since I haven't setup any devices there is a message about that.  On the backend hosting the files there aren't any messages that really look like problems.  But when I tried watching recorded programs and Live TV this morning I got some interesting message.  Then the last thing in the morning was an attempt to watch a video after getting the mounting problems worked out.  The more I think about it, since the videos don't related to a backend, it has to be something going on with this machine.  I wonder now if I have something off on the video drivers.  So I then tried to start MPlayer, that flashed things and knocked me back to the welcome screen.  VLC seemed to play my video fine, but then the sound continued after the app was closed.  xine seemed to work.  Enough for tonight.

---

### Post by volkswagner on 2008-09-29
What sound card are you using?  How is your sound connected, direct to powered speakers, via an amp/receiver, spdif, etc.?  Post output of the following.

```
lspci
```

```
aplay -L
```


Can you play a dvd located in the DVD drive with mythtv internal player?  I am not sure if you have a drive installed.

---

### Post by Boppy3125 on 2008-09-29
I will have to check on the specifics tonight.  It is an on-board sound card, currently just using the headphone jack into my amp.  I think it is part of the ATI radeon Xpress 200, but I could be wrong about that.  Sound was working fine when I tested the video with VLC last night, though.  Thanks for the follow-up, I will get that output.

---

### Post by Boppy3125 on 2008-09-29
lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:08.0 Communication controller: Agere Systems Unknown device 0620
02:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```

aplay -L
```
default:CARD=IXP
    ATI IXP, ATI IXP AC97
    Default Audio Device
front:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    Front speakers
surround40:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    4.0 Surround output to Front and Rear speakers
surround41:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Bt878
    Brooktree Bt878, Bt87x Digital
    Default Audio Device
```

---

### Post by Boppy3125 on 2008-09-29
I went into the Audio settings and change the Mixer Device to ALSA:default and that seems to gotten rid of the message about /device/mixer.  It now just segfaults for no apparent reason.


Arg.  bed time.

---

