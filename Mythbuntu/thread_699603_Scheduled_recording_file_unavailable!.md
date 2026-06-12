---
title: "Scheduled recording: file unavailable!"
date: 2008-02-17
forum: Mythbuntu
---

### Post by Isostar on 2008-02-17
When I try to watch a scheduled recording i frequently get the error message: "recording unavailable, the file for this recording cannot be found" and sometimes the recordings work just fine. Can someone tell me how to debug this?

Live TV always work, and it also records as I watch.

The file is missing in my recordings directory (/var/lib/mythtv/recordings). I watched that folder as the recording started but it doesn't appear. Is the file recorded to another folder and then moved to it's correct location on completion?
 
I see no errors in the mythbackend.log:
TVRec(1): Changing from None to RecordingOnly 
TVRec(1): HW Tuner: 1->1 
Started recording: ...
...
TVRec(1): Changing from RecordingOnly to None 
Finished recording

I checked the database record for the recording the filesize field is 0.
Is it possible that some autoexpire function wipes the file directly after it has been recorded?

My tuner card is Hauppauge NOVA T-500 (two channels).

---

### Post by volkswagner on 2008-02-17
Do they show up in the recordings list?  If so when you try to play does it say file is unavailable?  Try restarting the backend and recheck.  Easy way is exit frontend, go to sytem and select mythbackend setup, then exit, no need to run mythfill database, and then open mythfrontend see if the recordings appear.

Wondering if you have the same problem as me.

[http://ubuntuforums.org/showthread.php?t=697445]("http://ubuntuforums.org/showthread.php?t=697445")

Do you have just one machine running backend and frontend or multi machine setup?

---

### Post by Isostar on 2008-02-17
Yes they show up in the recordings list on the frontend, but when I try to play I get the error message file unavailable. File is missing on disc. 
So the question is where does the recorded files go?
According to the log the recording started and ended without errors.

It is a single machine.

(And there should be enough disc space left.)

---

### Post by volkswagner on 2008-02-17
Any luck with restarting mythbackend?

Have you evaluated your folders on the system to see if you can find the large file by right clicking and checking file sizes?

---

### Post by Isostar on 2008-02-18
No restarting the backend doesn't help.

---

### Post by Isostar on 2008-02-25
Reinstalled from scratch, it works now.
It was a good thing that 8.04 alpha 2 forced me to reformat!:)

---

### Post by tobycatlin on 2008-08-13
I get the same problem as described. Some programs record and other say they have but then when you try to play the file it says it cannot be found. I havn't looked to see if the db matches the mpg files in recordings but something is going wrong with recording. also it seems to happen more with wife swap than top gear, which gets me in trouble.

I have a single machine setup running ubuntu hardy which is fully updated. The tv card is haupague nova-t 500 dual tuner card. it's basically two tuners and a usb hub so it looks to ubuntu as two usb devices.

If i restart the backend it starts working again for a while but then after a few days it starts missing recording. I am not sure but it seems to happen more when both tuners are recording. I'd rather not re-install if possible as i have made many changes. 

if anyone has any ideas i'd love to hear them. 
thanks for any help

toby

---

### Post by tobycatlin on 2008-08-13
i found the file name of a failed recording and the mpg file was indeed missing from the disk. I also grepped the logs (var/logs/mythtv) for the file name and it showed up nothing except play back errors

mythbackend.log:2008-08-13 23:34:45.492 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/media-box/1004_20080813175800.mpg): Could not open /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/media-box/1004_20080813175800.mpg.
mythbackend.log:2008-08-13 23:34:45.495 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/media-box/1004_20080813175800.mpg) Error: Invalid file descriptor in 'safe_read()'

any other places i should be looking for errors?

ta

---

### Post by flecki on 2008-08-14
Hi All,

i think it´s a bug and tried to report it - no reply yet:

[http://svn.mythtv.org/trac/ticket/5507]("http://svn.mythtv.org/trac/ticket/5507")

Happens to me very often unfortunately - i could not correlate it to a specific event and i even got logs with DVB and file options enabled....

I use a workaround by restarting the mythtv-backend process at specific times (early morning and before the evening shows start) twice a day - that saves me usually.

I also reported the bug with the mythbuntu bugtracker but also got no reply on it...

By browsing forums i found similar entries back till 2004 with this problem...

Please add your findings to the bug report so we might get more attention on it from the developers !!

---

### Post by maff on 2008-08-28
Anyone get any further with this? mine does it randomly, i.e. 5 shows to record it'll get the 1st 2d, 4th and miss the 3rd and 5th. Really annoying. Nothing in the backend log except from when you try to play it it fails.

---

### Post by tobycatlin on 2008-08-28
this problem is still affecting me and i would love to help.

If anyone can tell me where to start i'd be happy to do some work around this area.

I am getting to the point where i am gonna have to do a full reinstall. which i don't fancy much

---

### Post by JugeHuge on 2008-09-08
This has happened me about 3 times on 50 recordings.. Not much yet but still.. :( Solution would be nice.

---

### Post by JugeHuge on 2008-09-10
Okey.. Found out that when mythtv get partial lock on channel it will make recording entry. But because it's partial lock it won't get anything to write on file.

---

### Post by JugeHuge on 2008-09-15
Got again this situation.. Found out that NOVA-T 500 get itself some of state that i cannot be initialized. 

I closed mythtv frontend and backed and tried to scan channels for channel.conf file. I couldn't because scan informed that resource was busy!!

---

### Post by tobycatlin on 2008-09-15
So it looks like a problem with the nova-t 500?
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

The bottom of this page says:
'2008-06-16 - Today, using an up-to-date Ubuntu 8.04 x64, a recent V4L-DVB tree, the MythTV tuning and EIT settings and the provided remote receiver, this card is absolutely rock solid with no USB disconnects, no tuner lost or any other trouble. The few MythTV tweaks are an slight annoyance, but they are worth it. This card is a great DVB-T solution!'

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)

I am not sure what firmware i am running, but i am pretty sure it's older than 16-06-08. I am gonna try updating the firmware tonight and see if it helps

---

### Post by JugeHuge on 2008-09-15
Thanks for links..

How do i see what firmware get's loaded?? 
dmesg | grep -i dvb gives
```
[   35.459536] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   35.459567] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   35.459731] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   35.573262] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[   36.188307] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   36.188514] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   36.194163] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[   36.752817] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:03:06.2/usb3/3-1/input/input6
[   36.795324] dvb-usb: schedule remote query interval to 150 msecs.
[   36.795331] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   36.795510] usbcore: registered new interface driver dvb_usb_dib0700

```

There is no mention about firmware and it's version.

i have checked under /lib/firmware and dvb-usb-dib0700-1.10.fw can be found under /lib/firmware/2.6.24-21-generic and /lib/firmware/2.6.24-16-generic

but how i get dvb-usb-dib0700-1.20.fw in use???

---

### Post by tobycatlin on 2008-09-16
good question. Does anyone know how to tell what firmware is being used?

I have three versions of the firmware file. It seems that different versions of the dvb-usb-dib0700 drivers use different firmware but i don't know how to find out which one is being used.

I did notice that on the linuxtv wiki that there are reports of one of the tuners not waking up from a suspend. It could be that the missing recordings are because the second tuner hasn't awoken. I have noticed that it is often my second tuner that misses recordings.

To turn usb suspend off
sudo gedit /etc/modprobe.d/options
add:
options usbcore autosuspend=-1

---

### Post by JugeHuge on 2008-09-16
Have to try if that autosuspend would correct situation.

---

### Post by tobiz on 2008-09-16
I think I'm getting recording dropouts too, I'm using a Nova-T-500 card as well.  I'll run the usb fix and see if there's any improvement.

Asus M3N78-EMH HDMI
AMD 64x2 4800
2GB Memory
500GB HDD
Myhtbuntu 8.04.1

---

### Post by JugeHuge on 2008-09-17
Do'h.. No go with that USB autosuspend trick.. :( both tuners are out of this world..

Update: found /var/log/messages flooding with following lines
Sep 17 06:52:19 juge-desktop kernel: [14330.383532] mt2060 I2C read failed
Sep 17 06:52:19 juge-desktop kernel: [14330.391511] mt2060 I2C read failed
Sep 17 06:52:20 juge-desktop kernel: [14330.399500] mt2060 I2C read failed
Sep 17 06:52:20 juge-desktop kernel: [14330.873939] mt2060 I2C write failed (len=2)
Sep 17 06:52:20 juge-desktop kernel: [14330.873946] mt2060 I2C write failed (len=6)

I hit google and found out that this I2C write problem is been quite common.

---

### Post by JugeHuge on 2008-09-19
Here is some solutions which might help.

1 .[Add time]("http://ubuntuforums.org/showpost.php?p=4887362&postcount=14") between changing channels in mythtv

2. If you don't use hauppage remote. Take the cord of and add
options dvb_usb disable_rc_polling=1 to /etc/modprobe.d/options
[Disabling the remote control sensor]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Disabling_the_remote_control_sensor")

3. Disable active EIT scan from both tuners in mythtv backend setup. [ Disable active EIT scan ]("http://www.mythtv.org/pipermail/mythtv-commits/2008-February/037352.html")

---

### Post by tobycatlin on 2008-10-07
i have installed the latest dvb drivers with the latest firmware for the nova-t 500 but i still get missing recordings.

I have just noticed JugeHuge hint to disable eit active scanning, i hope this is the missing solution. i'll post if it works.

anyone else had success in fixing this?

ta

toby

---

### Post by 4dognight on 2008-10-07
> **JugeHuge said:**
> Okey.. Found out that when mythtv get partial lock on channel it will make recording entry. But because it's partial lock it won't get anything to write on file.

Yep, I noticed the same with mine too. Mine happens usually on a firewire connected cable box. If I ever get the partial lock. I have to reboot to get it to straighten out. Else I will keep getting file not found , bad file descripter error. restarting myth only doesnt fix it. It has to be a reboot.

---

### Post by JugeHuge on 2008-10-08
Forgot this thread..

When i send those three tips that might help. I all ready had bigger time set in my backend setup and i'm using hauppage remote so that wasn't option. So i applied myself that Active EIT scan and it solved this problem. Haven't got any missed recording in two weeks.

Downside is that now i get caps in EPG programs on some channels. Not much but some.

---

### Post by fatmonk on 2008-11-19
Possibly some more info on this, possibly not directly related.

I'm getting missed scheduled recording just as described here. Database entry is there but when I try to play it says there is no file found.

Seems to record when I'm watching the programme and recording at the same time, but not unattended reoding when Myth is left at a menu.

I just got my LCD working this week, and this is where the possibly new info comes in.

The LCD remains on the 'RECORDING' screen, including the name of the programme that it recorded, long after the recording ends. In fact until I press a button/key and move through menus which updates the LCD.

The progress bar on the LCD is full (and fills up through the recording as expected) showing that the programme got to the end.

This is when the file is not created (ie the recording fails).

If I am watching the channel while its recording (ie when it works and the file IS created OK), the LCD shows the same as above until the end of the recording when it switches back to the date and time.

So, it would seem, even if this is a Nova-T 500 issue, that there is also some MythTV interaction that isn't happening when it should.

There's plenty of disk space (its a new 500GB drive on a new install with the OS on a seperate disk. The recoridng directories are sym linked, and as I say the recordings are fine when watching the programme thats been recording so its not a permissions issue).

Hope this gives someone cleverer than me a clue as to what this might be.

(Will try the EIT scanning settings as well, and will report back)

-FM

---

### Post by briggella on 2008-12-27
I had this problem with my Mythbuntu setup when my avermedia tuner card died and I replaced it with a Hauppaage Nova T dual tuner. The tuning timeout was set to 500ms by default in the tuner setup screen. I adjusted it to about 30secs as apparently the hauppage cards can be very slow to tune. Since then I have not missed any programs.

---

### Post by captain_dan on 2009-02-20
I also have this problem. I have recently moved house and the signal strength was much lower. I enabled the onboard amplifier (options dvb_usb_dib0700 force_lna_activation=1) and this helped my Live TV and all signals are watchable. I can record live TV no worries. Since doing this I have problems recording TV when scheduled by the frontend. Most fail, the only channel that has worked is channel seven and the signal has been terribly distorted. Could it be that the onboard amplifier is not working for the scheduled recordings? I have tried all of the fixes mentioned above to no avail. Does anyone have a solution to this problem? I am running 8.10. with the 1.20 firmware. Does going back to 7.10 fix the problem?
Thanks for any help!

---

### Post by captain_dan on 2009-02-23
Updating the problem above: There does not appear to be any errors in the logs. I have done a clean install of 8.10 and changed the card to a Dvico Dualdigital 4 tuner. I am still encountering the random Scheduled recording: file unavailable message. Live TV records fine. I am going to try an install of 8.04 to see if that fixes the problem. I will report back....

---

### Post by lofgren on 2009-03-02
Any luck Captain_dan?

I have a similar issue - one particular channel will not lock, therefore, does not record.

Only happened after upgrading from 8.04 to 8.10 (which I did to install a nova-td-500). 
When I gave up and decided to ditch the nova-td, I put my old single-tuner cards back in and they had the same issue with the same channel.

---

### Post by adamclinch on 2010-11-05
I just had this problem and was able to resolve it by: 

-creating new directories for the recordings
-making sure the permissions and ownership allowed mythtv to write to them
-configure these directories to be the default destination in mythtv-setup storage.

---

### Post by itlarson on 2010-11-05
Forgive me if this is off-base, as I didn't have time to read the entire post.  

Are you still using XFS?

I am, and occasionally get a similar issue.  Xfs-check, and xfs-repair seem to fix it.

---

### Post by Epiphyte on 2010-11-29
I am getting the same problem. I cannot record** *any ***programs !

I have newly installed Mythbuntu V10.04.

I have done the following:

1. added a delay to change channels for my tuner card;
2. Disabled active EIT scanning from my tuner (I'm not running a nova-t 500);
3. Checked the ownership and permissions of the relevant storage directories.

Can anyone else help out there? :confused:

---

### Post by lnoland on 2010-12-01
> **Epiphyte said:**
> I am getting the same problem. I cannot record** *any ***programs !

I have newly installed Mythbuntu V10.04.

I have done the following:

1. added a delay to change channels for my tuner card;
2. Disabled active EIT scanning from my tuner (I'm not running a nova-t 500);
3. Checked the ownership and permissions of the relevant storage directories.

Can anyone else help out there? :confused:

If you aren't getting any recordings and your permissions are correct then you likely have something going on I haven't seen before.  In case it helps,  however, I used to have frequent problems with myth not finding the file for a given recording.  I discovered from experimentation that the channels most frequently to  encounter the problem often had a difficult time locking onto the signal.  I fixed it by changing all of my digital tuners to use the Quick tuning option.  The only time I see the problem these days is if there is a problem during recording such as a station where the reception is so bad that virtually everything pixelates.

- Les

---

### Post by Epiphyte on 2010-12-02
Les,

THANKS - that worked !  \\:D/

I had to search for the options a bit, but found it and managed to record a couple of programs.

Seems like lots of other folk have the same problem
[http://www.gossamer-threads.com/lists/mythtv/users/454454]("http://www.gossamer-threads.com/lists/mythtv/users/454454")

Now for some real testing ;)

Cheers

---

### Post by dmizer on 2010-12-02
Glad to hear that you've resolved your problem. If you'd like to mark this thread as solved, please use the "Mark this thread as solved" function in the "Thread Tools" menu at the top of the thread. :)

---

### Post by lnoland on 2010-12-06
> **Epiphyte said:**
> Les,

THANKS - that worked !  \\:D/

I had to search for the options a bit, but found it and managed to record a couple of programs.

Seems like lots of other folk have the same problem
[http://www.gossamer-threads.com/lists/mythtv/users/454454]("http://www.gossamer-threads.com/lists/mythtv/users/454454")

Now for some real testing ;)

Cheers

I'm glad that worked for you.  I wish that other thread had existed back when I was having the problem. I did a lot of searching and found very little on the subject (and no solutions).  The cases I found where people were reporting trouble generally included symptoms or issues I didn't have.  I got the idea for the quick tuning option from advice given to someone who was having trouble locking signals on live tv.  Since I was already suspecting a link between my symptoms and channel locking I decided to try it -- and it worked like a champ.  I'd passed over that option a million times in the setup and had no idea what it was for.

I hope your setup is working well now.

- Les

---

### Post by Epiphyte on 2011-01-04
> **dmizer said:**
> Glad to hear that you've resolved your problem. If you'd like to mark this thread as solved, please use the "Mark this thread as solved" function in the "Thread Tools" menu at the top of the thread. :)
Dear dmizer,

Sorry, I cannot mark this thread as solved, since I was not the person who started it.

Regards

---

