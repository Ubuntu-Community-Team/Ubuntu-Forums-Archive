---
title: "Scanning channels - no signal"
date: 2012-12-03
forum: Mythbuntu
---

### Post by Twobytoons on 2012-12-03
I installed Mythbuntu over the weekend. I have a Hauppauge HVR 2250 tv turner card that I followed the instructions on linuxtv to install. I believe that it is working correctly, but when I go to set up Mythtv and scan for channels everything comes back as "timed out - no signal." 

Any ideas on how to fix this issue? Let me know if you need any more information to help me problem solve.

Thank you for your help,

---

### Post by klc5555 on 2012-12-04
Not my card, but one that gets discussed here perennially. You may need to install the firmware for it if you haven't done so already.

One relevant thread is here: [http://ubuntuforums.org/showthread.php?t=942403](http://ubuntuforums.org/showthread.php?t=942403)

The meat of the matter is post #10, the part talking about firmware.

A more up-to-date discussion of the firmware installation process (for Ubuntu 12.10 specifically) is here: [http://askubuntu.com/questions/214166/how-to-set-up-hvr-2250-tv-card-in-ubuntu-12-10](http://askubuntu.com/questions/214166/how-to-set-up-hvr-2250-tv-card-in-ubuntu-12-10)

Hopefully these will get you going.

---

### Post by topcat5 on 2012-12-04
I started having this problem to after the last update as of today.   (I'm on 12.04 [v0.26.0-53-gb28041a]

Prior to this the card worked perfectly as a DVB device.   

It's odd however I an continue to watch already scanned channels without issue, but I can't scan.   I get the same error as that of the OP.

---

### Post by Twobytoons on 2012-12-07
Work just became overwhelming this week and I finally just now got around to checking out the firmware. That is the exact post I followed when setting up the firmware before trying to set up the back end of MythTV. 

Any other thoughts of what might be going on?

---

### Post by klc5555 on 2012-12-07
Sorry, again, not my card. But until someone running a 2250 weighs in with concrete knowledge, your description is lacking in necessary details.

First, are you sure you've got signals? Second, are you configuring and scanning digital (terrestrial, QAM from cable, or other) or trying to configure analog? 

If you are trying to set up digital, do you have the frequency table set for 8VSB if terrestrial and QAM (256 or 64) if cable? If cable, are you sure you have unencrypted QAM signals to scan for? If absolutely all digital on the cable is encrypted and you have to get everything through a cable box, then setup will be different.

But scanning can in fact be screwed up; it gets torched periodically in Mythtv. To this end, it's always a good idea to have a set of the command-line dvb-apps installed from the repository. Run "scan" using the 8VSB or QAM frequency tables to see whether anything's there. Full scan runs up to about 10 minutes. If "scan" finds signals, you can use it again to make a channels.conf which can be loaded in lieu of scanning for channels.

If you're trying to set up analog, I can't help you at all --I don't know anything about the peculiarities of this card's driver and its recently added analog support. Hopefully some of this card's users will weigh in.

---

### Post by Twobytoons on 2012-12-08
> **klc5555 said:**
> Sorry, again, not my card. But until someone running a 2250 weighs in with concrete knowledge, your description is lacking in necessary details. 

Sorry, I didn't know what details were needed. I'm new at all of this. 

> **klc5555 said:**
>  First, are you sure you've got signals? 

Nope - no idea. How would I check that?

> **klc5555 said:**
>  Second, are you configuring and scanning digital (terrestrial, QAM from cable, or other) or trying to configure analog? 

QAM256 from comcast

> **klc5555 said:**
>  If you are trying to set up digital, do you have the frequency table set for 8VSB if terrestrial and QAM (256 or 64) if cable? If cable, are you sure you have unencrypted QAM signals to scan for? If absolutely all digital on the cable is encrypted and you have to get everything through a cable box, then setup will be different. 

I'm not sure that the QAM signals are unencrypted. We don't have a cable box currently with our limited basic cable through comcast so I didn't expect we would need a cable box to set this up. 

> **klc5555 said:**
>  But scanning can in fact be screwed up; it gets torched periodically in Mythtv. To this end, it's always a good idea to have a set of the command-line dvb-apps installed from the repository. Run "scan" using the 8VSB or QAM frequency tables to see whether anything's there. Full scan runs up to about 10 minutes. If "scan" finds signals, you can use it again to make a channels.conf which can be loaded in lieu of scanning for channels. 

We were able to scan using w_scan and found 300+ channels that we saved and created a channels.conf file. I can figure out how to tell MythTV setup to import channels from that file and when select next it runs a scan and comes back with:

13 new non-conflicting atsc channels which we insert all of them manually
103 new non-conflicting scte channels  which we insert all of them manually
128 new non-conflict mpeg channels which we insert all of them manually
31 new conflict scte channels and we renamed all of them
86 new conflicting mpeg channels and we rename all of them
147 unused transports and we marked them as invisible


After which we went to exit the backend of MythTV to see if we could watch TV and it says "card one type dvb input is set to start on channel "please add" which does not exsist." It will not allow us to select a channel to start on.
  

> **klc5555 said:**
>  If you're trying to set up analog, I can't help you at all --I don't know anything about the peculiarities of this card's driver and its recently added analog support. Hopefully some of this card's users will weigh in.

---

### Post by klc5555 on 2012-12-08
> **Twobytoons said:**
> Sorry, I didn't know what details were needed. I'm new at all of this. 



...

We were able to scan using w_scan and found 300+ channels that we saved and created a channels.conf file. I can figure out how to tell MythTV setup to import channels from that file and when select next it runs a scan and comes back with:

13 new non-conflicting atsc channels which we insert all of them manually
103 new non-conflicting scte channels  which we insert all of them manually
128 new non-conflict mpeg channels which we insert all of them manually
31 new conflict scte channels and we renamed all of them
86 new conflicting mpeg channels and we rename all of them
147 unused transports and we marked them as invisible


After which we went to exit the backend of MythTV to see if we could watch TV and it says "card one type dvb input is set to start on channel "please add" which does not exsist." It will not allow us to select a channel to start on.

When you finished the "Input Connections" the imported channels should have all been added to the database and their pages and data should be visible and editable in "Channel Editor" in the backend setup. At this point you should be able to go back into "Input Connections" and back to the page for your tuner. The "startup channel" entry should have turned into a  dropdown menu, in which you can choose one of the actual channels (best a well-known ATSC one), finish the "Input Connections" stage again, and exit the backend setup. You should no longer get this error message, and should (in theory) be ready to try livetv from the frontend.

If the channels are visible in the Channel Editor, but do not appear in the dropdown menu for your tuner in Input Connections, exit the backend setup anyway. despite the error message ("No, I know what I am doing") and go ahead and let mythfilldatabase run. Then, go back into the backend setup, back into Input Connections and your tuner's page, and now the startup channel should be selectable from the dropdown menu.

w_scan probably could not tell the difference between unencrypted clearQAM and encrypted (unlike myth's scanner when it actually works) and so I believe that probably most of the channels you set up are in fact encrypted ones. As you come across these either livetv will not lock or the frontend will hang. Make a note of which ones they are as you come across them, so that their database pages may be deleted later from Channel Editor,

---

### Post by Twobytoons on 2012-12-09
> **klc5555 said:**
> When you finished the "Input Connections" the imported channels should have all been added to the database and their pages and data should be visible and editable in "Channel Editor" in the backend setup. 


It's not :( We even went through the channel editor and scan for channels that way. Any ideas of how to get the channel.conf file to populate in the channel editor?

We were able to locate the channel.conf file in the home folder and view it through a text editor. There is information in there about the channels that we can manually enter the channel information into the channel editor. But once we manually enter a channel we still cannot watch it through the "Watch Live TV" option in the frontend.

---

### Post by topcat5 on 2012-12-09
I'm seeing the same problem with ATSC from an OTA connected to the card.  As I mentioned previously scanning was working prior to a couple of updates ago.  When I try to do a channel scan with that particular tuner now, I get an error message from myth.   On the otherhand, I can watch, without issue, the channels that were previously scanned with this card.  

I also have two HDhomeruns configured in the system.  These continue to scan fine.   

This would suggest to me that some kind of bug has been introduced causing issues with DVB devices during channel scanning.  I haven't had a chance to do some log analysis, but I wanted to put this out there to help with the OP's problem.  In my case I can rule out equipment, setup and signal problems.

---

### Post by klc5555 on 2012-12-09
> **Twobytoons said:**
> It's not :( We even went through the channel editor and scan for channels that way. Any ideas of how to get the channel.conf file to populate in the channel editor?

We were able to locate the channel.conf file in the home folder and view it through a text editor. There is information in there about the channels that we can manually enter the channel information into the channel editor. But once we manually enter a channel we still cannot watch it through the "Watch Live TV" option in the frontend.

Normally when a channels.conf has been imported and scanned, the channels populate in the database. Channels populate in the database and are visible in Channel Editor under the Video Source that was bound to the tuner in Input Connections before the scan was performed. So ... it hadn't occurred to me to ask: did you set up a Video Source (in Video Sources) specifically for your cable digital, which Video Source you could call "QAM" (or whatever) and which you bound to your tuner in Input Connections prior to undergoing the scanning process? The Video Source does not need to have a listings "grabber" set --that can be set up later. The Video Source is like the holding container for all the channel information that is found through a scan or in a channels.conf, information that is later editable with the Channel Editor.

topcat5 indicates that dvb device scanning is broken on current revisions of Mythtv 0.26. However, since you are using a new install you are presumably running Mythbuntu 12.04(.1) with some revision of Mythtv 0.25. Of course, this does not mean that scanning may not also be broken for your pvr 2250 in Mythtv 0.25 --scanning appears to have been broken more often than not over the past few years. However, there are indications also that channels.conf importing may have been broken in some revisions of 0.25 

If all else has failed, you should be able to add a digital channel manually to your digital Video Source by using "add channel" in the Channel Editor. You say you've tried this. The add channel brings up a multi-page form: one p. 1, name, callsign, and channel number can be whatever you choose, click through p. 2, and on p. 3 you can add the scanned frequency from your channels.conf information to the line "frequency or channel" and finish. If you absolutely cannot import channels.conf data by the usual method, then you may wish to test a manual channel add with one of your 13 ATSC channels identified by w_scan in your channels.conf. If this channel can be added in Channel Editor to your digital Video Source, set as a startup channel in Input Connections, the mythtv-setup info saved, the mythbackend started, and finally mythfrontend started, you should be able to tune this channel in livetv.

---

### Post by Twobytoons on 2012-12-10
> **klc5555 said:**
> Normally when a channels.conf has been imported and scanned, the channels populate in the database. Channels populate in the database and are visible in Channel Editor under the Video Source that was bound to the tuner in Input Connections before the scan was performed. So ... it hadn't occurred to me to ask: did you set up a Video Source (in Video Sources) specifically for your cable digital, which Video Source you could call "QAM" (or whatever) and which you bound to your tuner in Input Connections prior to undergoing the scanning process? The Video Source does not need to have a listings "grabber" set --that can be set up later. The Video Source is like the holding container for all the channel information that is found through a scan or in a channels.conf, information that is later editable with the Channel Editor. 

We did set up the video source for our QAM 256 and then bound that to our input connections. But just to be sure, we deleted that and did it all over again...same issue 


> **klc5555 said:**
>  If all else has failed, you should be able to add a digital channel manually to your digital Video Source by using "add channel" in the Channel Editor. You say you've tried this. The add channel brings up a multi-page form: one p. 1, name, callsign, and channel number can be whatever you choose, click through p. 2, and on p. 3 you can add the scanned frequency from your channels.conf information to the line "frequency or channel" and finish. If you absolutely cannot import channels.conf data by the usual method, then you may wish to test a manual channel add with one of your 13 ATSC channels identified by w_scan in your channels.conf. If this channel can be added in Channel Editor to your digital Video Source, set as a startup channel in Input Connections, the mythtv-setup info saved, the mythbackend started, and finally mythfrontend started, you should be able to tune this channel in livetv.

We entered all 13 channels manually. But in doing so we only had 2 pages...there was never a 3rd page option to add in a line about "frequency or channel". But in hopes that it would work we set up a startup channel, saved the info, started the backend and then started the front end....we got an error "failed to connect to mythtv backend server" 

Thinking that maybe we forgot to start the backend we typed "/usr/bin/mythbackend" and a whole slew of errors followed...I think I found the problem :confused: 
The errors all started after: 
mythbackend: Problem with capture cards: Card 1failed init 
ERROR: no valid capture cards are defined in the database.  
mythbackend: No capture cards are defined: Please run the setup program.

But when I go into the backend and look under capture card everything is still there and I believe it is working. But then again, I have no idea how to check if it truly is. 

Thanks everyone for all your help. I must say this has been a very frustrating experience for my husband and I and we couldn't do it without your help.

---

### Post by klc5555 on 2012-12-10
> **Twobytoons said:**
> We did set up the video source for our QAM 256 and then bound that to our input connections. But just to be sure, we deleted that and did it all over again...same issue 




We entered all 13 channels manually. But in doing so we only had 2 pages...there was never a 3rd page option to add in a line about "frequency or channel". But in hopes that it would work we set up a startup channel, saved the info, started the backend and then started the front end....we got an error "failed to connect to mythtv backend server" 

Thinking that maybe we forgot to start the backend we typed "/usr/bin/mythbackend" and a whole slew of errors followed...I think I found the problem :confused: 
The errors all started after: 
mythbackend: Problem with capture cards: Card 1failed init 
ERROR: no valid capture cards are defined in the database.  
mythbackend: No capture cards are defined: Please run the setup program.

But when I go into the backend and look under capture card everything is still there and I believe it is working. But then again, I have no idea how to check if it truly is. 

Thanks everyone for all your help. I must say this has been a very frustrating experience for my husband and I and we couldn't do it without your help.

Mythbackend runs as root. Otherwise it can't initialize the hardware, which is owned by root. ("mythtv" owns the mythconverg database, and each normal user account on the machine owns mythfrontend). So if your backend is not running in Mythbuntu but you're trying to start it manually from a terminal, you need to do it sudo. First make sure it's not running:```
sudo killall mythbackend
```then try starting it:```
 sudo mythbackend
``` followed by your user password when prompted. Note that distinct from most distros, in Ubuntu "mythbackend" is a wrapper script, while the actual program has been renamed to mythbackend.real

And if error messages pop up when starting mythbackend sudo in a terminal, they'll be significant.

Also, at this point you should have mythbackend.log and mythfrontend.log under /var/log/ or /var/log/mythtv  The final sets of entries from both of these after a failed run may provide clues.

---

