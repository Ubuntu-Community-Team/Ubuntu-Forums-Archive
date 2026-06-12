---
title: "kworld 115 doesn't record"
date: 2008-10-13
forum: Mythbuntu
---

### Post by 4dognight on 2008-10-13
Im going nuts trying to figure this out! I have the kworld 115 tuner in a slave backend. It is the only tuner installed in this backend. I can watch live tv on both the SD tuner and the ATSC tuner on it. The problem is whenever I schedule a recording on the ATSC tuner it nevers records. 
When I look in the recordings directory the file doesn't exist. If I watch live tv and , then press R to record, it records fine. The problem is only on a scheduled recording. I have turned on debugging  in mythbackend to -v all,nodatabase. I can confirm I see it fails to find the file.

2008-10-13 19:33:21.193 read  <- 12 664     FILL_PROGRAM_INFO[]:[]mythtv-backend[]:[]How I Met Your Mother[]:...
2008-10-13 19:33:21.199 SG(Default): FindRecordingFile: Searching for '4050_20081013193000.mpg'
2008-10-13 19:33:21.200 SG(Default): FindRecordingDir: Checking '/var/lib/mythtv/recordings'
2008-10-13 19:33:21.201 SG(): FindRecordingDir: Checking '/var/lib/mythtv/recordings'
2008-10-13 19:33:21.203 SG(Default) Error: FindRecordingFile: Unable to find '4050_20081013193000.mpg'!
2008-10-13 19:33:21.204 ProgramInfo, Error: GetPlaybackURL: '4050_20081013193000.mpg' should be local, but it can not be found.


There is other msgs in the log, but most dont give any indication that there is a problem. I can paste some more of the log if someone is interested.

I am running the latest version of mythbuntu from a fresh install. I have plenty of disk space available. Someone help!

---

### Post by novellahub on 2008-10-14
Do you have your default storage group for the slave backend set up to '/var/lib/mythtv/recordings'?

---

### Post by 4dognight on 2008-10-14
> **novellahub said:**
> Do you have your default storage group for the slave backend set up to '/var/lib/mythtv/recordings'?

Yes, its the default. I never touched it. Im thinking I will install the card into the Master BE, and see what happens.

---

### Post by novellahub on 2008-10-14
Could you check on another thing?  Does both your machines have different host names?

---

### Post by 4dognight on 2008-10-14
> **novellahub said:**
> Could you check on another thing?  Does both your machines have different host names?

Yes, I have assigned IP addresses and given them names. Which I have also created in /etc/hosts on each box.

---

### Post by newlinux on 2008-10-14
I've seen this before as a channel lock problem. LiveTV would work if I waited, but scheduled recordings would not get a lock in time and then the recording would fail. This used to only happen to me on some channels though, not all of them, and for some reason deleting all my cards and re-adding them and rescanning fixed it.

Just a thought...

other than that, maybe run repair on your DB.

---

### Post by 4dognight on 2008-10-14
Well, I went and did a complete reinstall of myth on the server with this tuner.
It did the exact same thing. I then also removed the analog tuner for the kworld115 from the list of tuners, thinking it may be getting confused. It still behaves the same. I even checked the tables in the database. I can see the entry for it in the record and recorded tables. 

I will try installing it in the master BE tomorrow and see if it still wont record scheduled recordings.

Gettin tired of this. Perhaps I should get a different tuner ? 
:mad::mad::mad::mad:

Newlinux, do you have this same card working in your myth server? Is it in the master backend or slave backend?

---

### Post by newlinux on 2008-10-15
I have 3 Kworld 110s (pretty much the same as the 115) and an Avermedia A180 (which has the same digital chip but no analog capabilities. 2 of them are in slave backends on my main mythtv system, and 2 in a master backend on a secondary mythtv system that I operate. My guess would be since the tuners actually work, it's not the cards, it something else in the setup. I've helped many people get the Kworld 115 working... Yours is working... but I'm not sure about why it won't record...

Chances are it wasn't anything with your slave backend, probably something more myth configuration related - maybe the DB in the master backend. reinstalling the slave and having the same issue is an indicator this may be true...

---

### Post by newlinux on 2008-10-15
found another person with your problem (not sure if it was the same tuner card, but doesn't appear they got a solution)... Maybe try changing your storage groups just to see what happens...

---

### Post by novellahub on 2008-10-15
The storage groups might be set up right but the recording directory permissions might be set up wrong. I run a non standard disk setup and had to make the recording direcory to have the permissions set to 775 and make the owner mythtv:mythtv

---

### Post by novellahub on 2008-10-15
> **newlinux said:**
> I have 3 Kworld 110s (pretty much the same as the 115) and an Avermedia A180 (which has the same digital chip but no analog capabilities. 2 of them are in slave backends on my main mythtv system, and 2 in a master backend on a secondary mythtv system that I operate. My guess would be since the tuners actually work, it's not the cards, it something else in the setup. I've helped many people get the Kworld 115 working... Yours is working... but I'm not sure about why it won't record...

Chances are it wasn't anything with your slave backend, probably something more myth configuration related - maybe the DB in the master backend. reinstalling the slave and having the same issue is an indicator this may be true...

I have 3 Kworld 115 cards as well.  I have used them with ATSC and QAM with success.  My guess is setup related as well.

---

### Post by newlinux on 2008-10-15
> **newlinux said:**
> found another person with your problem (not sure if it was the same tuner card, but doesn't appear they got a solution)... Maybe try changing your storage groups just to see what happens...

[http://www.gossamer-threads.com/lists/mythtv/users/337787](http://www.gossamer-threads.com/lists/mythtv/users/337787)

sorry, forgot the URL

---

### Post by 4dognight on 2008-10-15
I will take a look at the recordings director, but I doubt it is the problem. As it does record if I am watching live TV and press 'R' to record it. I have verified it does create the file in my recordings directory, in this situation. 
I agree it must be something in the configuration, in the DB. I started looking into the data in some of the tables . I will look at little closer. Maybe I can post the contents, and you can compare it to what you have.

---

### Post by newlinux on 2008-10-15
I'd be happy to do comparisons with your DB where I can help. Good luck. I am very curious about this problem...

---

### Post by 4dognight on 2008-10-15
Here are the permissions on the directories.
rick@mythtv1:/var/lib/mythtv$ ls -la
total 24
drwxr-xr-x  6 root   root   4096 2008-07-04 23:20 .
drwxr-xr-x 49 root   root   4096 2008-10-14 18:52 ..
drwxrwsr-x  2 mythtv mythtv 4096 2008-06-03 05:59 music
drwxrwxr-x  2 mythtv mythtv 4096 2008-06-03 05:59 pictures
drwxrwsr-x  2 mythtv mythtv 4096 2008-10-14 21:35 recordings
drwxrwxr-x  2 mythtv mythtv 4096 2008-06-03 05:59 videos

Here is the rows for the cardinput and capturecard tables.

mysql> select * from capturecard where cardid=9
    -> \G
*************************** 1. row ***************************
               cardid: 9
          videodevice: 0
          audiodevice: 
            vbidevice: 
             cardtype: DVB
         defaultinput: DVBInput
       audioratelimit: NULL
             hostname: mythtv1
         dvb_swfilter: 0
         dvb_sat_type: 0
dvb_wait_for_seqstart: 1
          skipbtaudio: 0
        dvb_on_demand: 1
      dvb_diseqc_type: NULL
        firewire_port: 0
        firewire_node: 2
       firewire_speed: 0
       firewire_model: NULL
  firewire_connection: 0
           dbox2_port: 31338
       dbox2_httpport: 80
           dbox2_host: NULL
       signal_timeout: 14500
      channel_timeout: 16500
     dvb_tuning_delay: 25
             contrast: 0
           brightness: 0
               colour: 0
                  hue: 0
             diseqcid: 0
          dvb_eitscan: 0
1 row in set (0.00 sec)

mysql> select * from cardinput where cardinputid=9
    -> \G
*************************** 1. row ***************************
    cardinputid: 9
         cardid: 9
       sourceid: 3
      inputname: DVBInput
externalcommand: NULL
     preference: 0
      shareable: N
       tunechan: NULL
      startchan: 42#1
  freetoaironly: 1
    diseqc_port: NULL
     diseqc_pos: NULL
 lnb_lof_switch: 11700000
     lnb_lof_hi: 10600000
     lnb_lof_lo: 9750000
    displayname: ATSC
  radioservices: 0
    dishnet_eit: 0
    recpriority: 3
      quicktune: 1
1 row in set (0.01 sec)

---

### Post by newlinux on 2008-10-16
I have much smaller signal (3000) and channel timeouts (5500) and no tuning delay, but I don't know if this is causing your problem. Also, I have a different quicktune setting (I don't use quicktuning, mine is set to 0). Other than that everything is pretty much the same.

---

### Post by 4dognight on 2008-10-16
I increased the tuning timeout as I noticed it seems to take about 8-10 seconds to get a picture up when I watch live tv. Once its up and running, changing channels is quicker though. Im not sure about the quicktune setting. I will try changing it tonight.

---

### Post by 4dognight on 2008-10-17
I tried changing the quick tune setting, but it didnt help.

I then deleted all of my capture cards and recreated them. Still nothing.
I then put the tuner card in my Master BE, deleted all tuners and recreated them, and still nothing!! 
I dont think there is anything else to try. I think its fleabay for this tuner card and try a different brand.:(

---

### Post by novellahub on 2008-10-17
This is a longshot now.  Do you have the firmware for the card?

The instructions on how to get the firmware is the same as the ATI Card here:

[https://help.ubuntu.com/community/MythTV_Edgy_hardware#ATI%20HDTV%20Wonder](https://help.ubuntu.com/community/MythTV_Edgy_hardware#ATI%20HDTV%20Wonder)

Also, are you using the card for QAM or ATSC brodcasts?  I want to make sure you are using the right connection on the back of the card (One is for antenna/ATSC and one for cable/QAM).

---

### Post by 4dognight on 2008-10-17
Thats the same driver. I can see it getting loaded in dmesg. I am incorrectly labeling the card as ATSC in the configuration, but it is using QAM to tune. I have coax going to both inputs. I pick up analog on one and the digital on the other. The card works fine, I can watch live TV on both the Digital an analog inputs. I also have removed the analog input, thinking it is conflicting somehow, but it didnt  help.  The problem is I never get a file for scheduled recordings. In Mythweb the filesize shows up a 'B'. Which I think means 'Bad' or no file exists. File permissions are ok, as there are other recordings in the directory from the other tuners.
One thing I noticed, is I am seeing msgs in the log about unable to find files in the directory(prob because it didnt create them in the first place).
But it references them with out full path. I can post actual examples later, but they are something like 192.168.2.6/1050_123456789.mpg. Not sure if its a problem, but I would expect it to have the path, like, 192.168.2.6/var/lib/mythtv/recordings/1050_123456789.mpg

---

### Post by newlinux on 2008-10-17
So you have other digital tuners that don't have this problem on the same system? And this happens for both your digital and analog recordings for the 115? That is just weird and clearly beyond my understanding. So you have a card using this same input source that works for scheduled recordings? Perhaps run mythbackend with the database verbosity - maybe this will show a problem with the DB when trying to schedule a recording.

---

### Post by 4dognight on 2008-10-17
The other tuners are a pvr350 and pvr500. I have not tried scheduling recordings with the analog tuner on this 115. The Pvr350 and 500 are much better and I have higher priorities set for them. I have used the analog and digital tuner on the 115 for watching live tv. 

I have tried using -v all on mythbackend. I will post the output from it tonight.

---

### Post by newlinux on 2008-10-17
The reason I ask is that I guess it is possible to have corruption with the video source. I did some searching and it people have had this problem (where livetv would work and scheduled recordings wouldn't) and it was related to video source problems in the DB. I would try a scheduled recording with the analog side of the 115 as well and see if that works.

For what it's worth, I have a PVR-150 and after playing with the recording profiles a bit for the Kworld 110 I was able to get the analog quality to be pretty much indistinguishable from the PVR-150 recordings. Now some of this of course is subjective and based on how well your display monitor cleans up things, so YMMV.

---

### Post by 4dognight on 2008-10-18
Well I had given up , and decided as a last resort to start from scratch. I wiped the database clean and started over. I am now able to record on this tuner. I have no idea what the problem was or how it got messed up. I guess when all else fails, its best to start from scratch.

---

