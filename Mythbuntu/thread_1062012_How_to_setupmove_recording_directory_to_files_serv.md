---
title: "How to setup/move recording directory to files server"
date: 2009-02-06
forum: Mythbuntu
---

### Post by rodercot on 2009-02-06
Hey All,

 I have been searching for a couple days on this. 

 I have a machine setup with as the Mst B/E with an XBMC front end currently. It has a 280gb partition set to /var/lib/myth or the default. 

 I want to change the default recording directory to use my media server which is //TOWER/disk1 through disk 11/

 I will make a directory on the server for recordings. I am unsure of the process and actual paths req'd in the myth setup to do this properly. 

 Thanks,

 Dave

---

### Post by crez79 on 2009-02-06
Mount the share on the master backend. 

Open the mythtv backend setup program. (mythtv-setup in terminal)

Add the folder to the storage editor.

There is a [good pdf]("www.mythtv.org/docs/mythtv-HOWTO.pdf") that shows how in a little more detail.

You can move the existing recordings to the new directory and remove the default location, or just add the second location and myth will evenly load up the directories. I would leave at least one place locally on the master backend in case the server goes down it wont miss any recordings.

---

### Post by rodercot on 2009-02-07
Hey all,
 
 Well I am still pulling my hair out with this. I have tried what I can think of on my test machine and it sees the shares but will not mount them. 

 This is what I would like to achieve and I am getting nowhere fast. 

 The main machine is already up and running as the master and I set it to allow remote connections it is currently at localhost so I will have to change that I know. 

 The front end is XMBC and that is working fine. I have not setup any recording YET. The default recording directory is what I have used right now. 

 This main machine has a pvr-150 hooked to a Bell Express VU 6141 rcvr and that is fine, channel changine via lirc and the mce remote/dongle is fine.

 NOW, the second machine I want to use is in the bedroom, it only has XBMC on it currently (Live) But that machine has an pvr-150 in it as well and there is a Express VU 6000 rcvr in that room that I would like to use. That machine only has a 20Gb Hard drive in it so I would like the recording directory to use my media server.

 I have read wiki's manuals, etc and cannot find a solid model to bas my setup on. 

 I would like to have both machines to run Myth and both to use there own rcvr to watch live tv, I will use Mythweb for scheduling etc recording and finally I would like both machines to use my media server as the default recording directories/storage groups.

 I have two media servers both Unraid which share automagically windows SMB shares. They are on 24-7 and with a Batt Backup in use. I can use either machine It makes no difference to me. 

 one is //TOWER/disk1/movies1
        //TOWER/disk2/movies2 etc to disk11

 two is //tower2/disk1
        //tower/disk2 etc..

 I can add a drive to this server dedicated to only myth 

 IS there a decent how to on configuring something like the above. 
 I am assuming I need a primary backend (master) slave (secondary backend) all cards setup on the master backend and sources setup on their respective machines. recording, storage groups etc setup on the master. 

  I cannot understand why I cannot figure this out. I have searched pretty much all I can think of on Google and the wiki and have read the manual and the mythguide numerous times.

 Thanks very much,

 Dave

---

### Post by Mythgruntled on 2009-02-07
How about adding the server to fstab on the frontend boxes, eg. I have:
```
//_insert_server_IP_here_/recordings /myth/tv smbfs username=defaults,password=defaults,
uid=mythtv,gid=mythtv,lfs,rw 0 0
```to get my recordings to go into the file server's 'recordings' share.

---

### Post by rodercot on 2009-02-08
> **Mythgruntled said:**
> How about adding the server to fstab on the frontend boxes, eg. I have:
```
//_insert_server_IP_here_/recordings /myth/tv smbfs username=defaults,password=defaults,
uid=mythtv,gid=mythtv,lfs,rw 0 0
```to get my recordings to go into the file server's 'recordings' share.


 OK that worked I can now browse the shared folder from /var/lib/mythtv/recordings/twr2live

 but now when I shutdown I get a cannot find the cifs server error twice and hangs for a few minutes and then the same on bootup it hangs for about a minute looking for the share before finding it. 

 I was expecting to see the share added to the desktop as well but that did not happen. 

 Dave

---

### Post by rodercot on 2009-02-11
So I think I have most of this working. I have not setup the shared drives yet, I am going to add a new drive to the server for that first. 
 
 I setup my slave machine, I had the hardest time with the pvr-150 in the slave machine. I set it all up and then ran mythfill on the master but it would always say that tuner 4 is unavailable. 

 Now I set the recording directory to /var/lib/mythtv/recordings, which I assume is using the local drive which is 80Gb and then the master b/e has 280gb when I look at free space on the slave machine it is saying that I have 3?? GB opf space, so I take it myth is combining the space from the master and the space from the slave as one drive but priority for recordings is going to the master first. I hope this is proper.

 I had suspend/resume working fine on the initial install after I set up the slave backend it no longer comes out of sleep mode, it tries to I can hear the drives wake and the activity light on the odd flashes then nothing it just continues to flash the pwr light on the pc. Is Myth using pm-utils now in 8.10? Where are the suspend log files placed.

 Thanks,

 Dave

---

### Post by Mythgruntled on 2009-02-11
> **rodercot said:**
> Now I set the recording directory to /var/lib/mythtv/recordings, which I assume is using the local drive which is 80Gb and then the master b/e has 280gb when I look at free space on the slave machine it is saying that I have 3?? GB opf space, so I take it myth is combining the space from the master and the space from the slave as one drive but priority for recordings is going to the master first. I hope this is proper.I don't know for sure, but I think that this is *not* the case. I think if it can't connect to your shared 280GB drive on bootup, then it will use the 80GB local drive instead. Hopefully someone else can confirm or deny this.
Sorry I can't assist with any of the other issues.

---

### Post by rodercot on 2009-02-12
> **Mythgruntled said:**
> I don't know for sure, but I think that this is *not* the case. I think if it can't connect to your shared 280GB drive on bootup, then it will use the 80GB local drive instead. Hopefully someone else can confirm or deny this.
Sorry I can't assist with any of the other issues.

 It looks like it does combine the two from what I can see here from Mythweb disk space info.

 
Machine information
This machine's load average: 
1 Minute: 0.13 
5 Minutes: 0.11 
15 Minutes: 0.07 
Disk Usage:

MythTV Drive #1: 

Directory: xbmc:/var/lib/mythtv/recordings 
Total Space: 284,131 MB 
Space Used: 1,904 MB 
Space Free: 282,226 MB 
MythTV Drive #2: 

Directory: mythbed:/var/lib/mythtv/recordings 
Total Space: 76,498 MB 
Space Used: 129 MB 
Space Free: 76,369 MB 

Total Disk Space: 
Total Space: 360,630 MB 
Space Used: 2,034 MB 
Space Free: 358,596 MB 

Last mythfilldatabase run started on 2009-02-10 17:04 and ended on 2009-02-10 17:04. mythfilldatabase ran, but did not insert any new data into the Guide for 1 of 1 sources. This can indicate a potential grabber failure.
Suggested next mythfilldatabase run: 2009-02-11 13:17.
There's guide data until 2009-02-24 02:00 (12 days).
DataDirect Status: Your subscription expires on 11/06/09 06:16:17 PM 

 What does this mean and how do we troubleshoot it.

 Last mythfilldatabase run started on 2009-02-10 17:04 and ended on 2009-02-10 17:04. mythfilldatabase ran, but did not insert any new data into the Guide for 1 of 1 sources. This can indicate a potential grabber failure.

 Oh! and one other quick one, The second maching is also running XBMC as a front end, my question though is do I point the myth:// protocol ip address to the Master backend or point to the localhost (slave machine) LiveTv works either way but I cannot see any recordings in the list.


 Thanks,

 Dave

---

### Post by Mythgruntled on 2009-02-12
> **rodercot said:**
> It looks like it does combine the two from what I can see here from Mythweb disk space info. Wow I think you're right - can you please post your whole fstab here? as it might assist me with my own setup. thanks.

---

