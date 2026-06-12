---
title: "Can't scan channels thru STB...frustrated!!"
date: 2010-03-29
forum: Mythbuntu
---

### Post by sbradley07 on 2010-03-29
I cannot get the channel scanning function to find channels thru my Comcast STB.  I have scoured the usual forums and wikis for a resolution to my problem, but nothing has helped.  I'm hoping someone here can help me out.  

When attempting to scan for channels, nothing happens.  I see "Scanning us-cable 2...No Lock" and nothing else.  It just sits there...0% signal strength, 0% scan progress.

My system is set up as follows:

- Mythbuntu 9.10 installed as combined frontend/backend
- Hauppauge WinTV-HVR-1600 ATSC/ClearQAM/NTSC  (with remote, USB IR receiver, IR transmitter)
- nVidia GE Force 9500 GT
- Comcast Digital Cable - Set Top Box is a DCT-5100

My connections are:
- Coax from wall to "Ant In" on back of STB
- Coax from "To TV" on STB to "Analog Cable TV In" port on the Hauppauge 1600
- DVI and RCA audio cables from nVidia to back of Sony TV

Backend config:
- General:  TV Format=NTSC; Channel Freq Table=us-cable
- Capture Card:  Card Type=IVTV MPEG-2; Device=/dev/video0; Input=Tuner1
- Video Source:  Listing Grabber=Schedules Direct; Lineup=Digital Channels
- Input Connections:  MPEG:/dev/video0 maps to SD source on Tuner1; Preset Tuner Channel=3; External Channel Change=blank
- Scan Config:  Vid Source=my digital source; Input=MPEG:/dev/video0 (Tuner1); Services=TV; Scan Type=Full Scan; Channel Table=us-cable

I've read about defining a channel changer script in the External Channel Changer field, but not having one defined now should not keep the scan from working, should it?  I was under the impression that once I have completed a successful scan, I would then need a script to change the STB channels with my Myth remote.  Also, do I really need to define a script, or can I just change channels with my cable remote?  

Do I have all this set up right?  Any ideas why I am not getting channels?

---

### Post by azmyth on 2010-03-29
It's been awhile since I had to do this but if memory serves me correctly. You setup your video sources with Schedules direct and then you tie this with the card in input connections. You'll see the fetch channels for listing source. Select this and wait as it takes awhile then you should be good to go after you exit mythtv-setup and do filldatabase.

Also, do I really need to define a script, or can I just change channels with my cable remote? 

I use to do this when I had a box that needed RF to change the channel.

---

### Post by tgm4883 on 2010-03-29
How is MythTV suppose to scan for channels if it can't change the channel on the STB? It would only get a single channel.


That being said, I think analog channel scanning was broken in 0.22

---

### Post by klc5555 on 2010-03-29
You can't scan because your list of possible channels for the 1600 in this configuration consists of precisely one: ch. 3.

The STB is doing all the tuning, and piping everything into ch. 3. 

You can use your STB remote to change channels in livetv, of course, but you'll need to get lirc, an ir blaster, and a channel-changing script enabled so that Mythtv will be able to change channels on the STB by itself without your intervention. Otherwise doing scheduled recordings becomes problematical.

---

### Post by sbradley07 on 2010-03-29
> **tgm4883 said:**
> How is MythTV suppose to scan for channels if it can't change the channel on the STB? It would only get a single channel.


That being said, I think analog channel scanning was broken in 0.22

I guess I misunderstood this part.  So what you are saying is, MythTV scans for channels thru the STB by sending channel change commands for every channel?  

If so, what do I use for the "External Channel Change Command"?  I see a number of scripts under /usr/share/doc/mythtv-backend/contrib/channel_changers.  Is that where I should be looking?  Given the remote, IR blaster and STB that I have, do I need to create a script or can I use one already there?

---

### Post by sbradley07 on 2010-03-30
With the responses to my post above, I did some more digging into a external channel change script.  

My assumption is (please correct me if I am wrong) that, in order for the channel scan to work, a script must execute to change the channels on the STB for each channel it has to scan.

I have a script that works from the command line...I can power on/off and change channels on the STB (I see the red LED flashing on the IR Blaster).  However, when I put the script into the Input Connections screen and try to rescan, nothing happens...I am not seeing any red light activity and no channels are ever found.  I assume Mythtv is having a problem running the script.

script is /usr/local/bin/change_ch.sh
```
#!/bin/sh
REMOTE_NAME=DCT2000
cmd="$1"

case $cmd in
[0-9]*)
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend SEND_ONCE $REMOTE_NAME $digit
sleep 1
# If things work OK with sleep 1, try this for faster channel changes:
# sleep 0.3
done
;;

*)
irsend SEND_ONCE $REMOTE_NAME $cmd
;;
esac
```

permissions on the file:
-rwxr-xr-x 1 root root 265 <date> change_ch.sh

sysout log shows these two lines repeated 3 times:
lircd-0.8.6[894]: accepted new client on /var/run/lirc/lircd
lircd-0.8.6[894]: removed client

mythbackend log doesn't indicate any errors, though I see a couple of lines I don't understand and suspect they have something to do with channel scanning:
-ret_pid(2250 child(2250 status(0x0)
-External Tuning program exited with no error

Any ideas about what's going on, or other things I can try?

---

### Post by tgm4883 on 2010-03-30
> **sbradley07 said:**
> With the responses to my post above, I did some more digging into a external channel change script.  

My assumption is (please correct me if I am wrong) that, in order for the channel scan to work, a script must execute to change the channels on the STB for each channel it has to scan.

I have a script that works from the command line...I can power on/off and change channels on the STB (I see the red LED flashing on the IR Blaster).  However, when I put the script into the Input Connections screen and try to rescan, nothing happens...I am not seeing any red light activity and no channels are ever found.  I assume Mythtv is having a problem running the script.

script is /usr/local/bin/change_ch.sh
```
#!/bin/sh
REMOTE_NAME=DCT2000
cmd="$1"

case $cmd in
[0-9]*)
for digit in $(echo $1 | sed -e 's/./& /g'); do
irsend SEND_ONCE $REMOTE_NAME $digit
sleep 1
# If things work OK with sleep 1, try this for faster channel changes:
# sleep 0.3
done
;;

*)
irsend SEND_ONCE $REMOTE_NAME $cmd
;;
esac
```

permissions on the file:
-rwxr-xr-x 1 root root 265 <date> change_ch.sh

sysout log shows these two lines repeated 3 times:
lircd-0.8.6[894]: accepted new client on /var/run/lirc/lircd
lircd-0.8.6[894]: removed client

mythbackend log doesn't indicate any errors, though I see a couple of lines I don't understand and suspect they have something to do with channel scanning:
-ret_pid(2250 child(2250 status(0x0)
-External Tuning program exited with no error

Any ideas about what's going on, or other things I can try?

Yes

> **tgm4883 said:**
> That being said, I think analog channel scanning was broken in 0.22

---

### Post by Lepy on 2010-03-30
If you can change channels and power on/off the stb using your script, you've finished the hardest part! 

As klc5555 mentioned, your HVR-1600 will always be tuned to channel 3 and the stb will pipe any channel it changes to, using your script, to channel 3. Its kind of like watching a movie on an old VCR.

If the HVR were plugged directly into the wall through coax, you would be able to scan for channels using mythtv-setup (if its not broken as tgm4883 has suggested).

However, you would still not have any guide data. You must inject this data using either Schedules Direct (integrated and automatic) or with mc2xml (script and cronjob).

I think you should setup guide data and run mythfilldatabase, then, in mythtv-setup, option 4 (Input Connections) change external channel change command and preset tuner to channel but don't scan for channels!

---

### Post by sbradley07 on 2010-03-30
Thanks for all the input...I think I am getting closer.

First, "*I think analog channel scanning was broken in 0.22*":  can you post a link that describes this?  If I connect cable directly to my tv tuner card (not thru STB), I can scan for channels just fine.  Does your comment imply analog scanning is broken when coming thru a STB?

I figured out that the Input Connections field for setting the tuner channel=3 was not working.  I had to install ivtv-utils and set it manually before configuring the backend.  Once I did this, it seemed like channel scanning worked...or at least it found like the first 5 channels then it stopped.

Now when I load the frontend and select Watch TV, some strange things happen:  
1. I get a signal which I wasn't getting before, but the signal is all garbled...as if it's encrypted.  
2. Right when I start Watch TV, the IR blaster LED keeps lighting up in a pattern of 2 flashes/pause/2 flashes/pause... and it keeps repeating.  Also, the STB shows channel 5, and even using the channel up/down button on the STB won't change the channel.
3. When I try to change channels with my tv tuner remote, I don't see the LED on the blaster light up.

So, I suspect something is wrong with my script.  The signal is not reaching the IR blaster, so the remote is changing channels on the tuner card instead of the STB.  

Things I am trying next:  I found a new script that's a little different, and I will manually set the tuner channel to 3 before starting the frontend (maybe it keeps getting reset to something else.)

As always, if anyone has any further suggestions, I am all ears!  Thanks.

---

### Post by inovermyhead on 2010-03-31
FYI, if you look at the mythtv.org main page they've announced the first release candidate of 0.23 and if you look at the release notes they claim to have fixed the problem whereby analog scanning didn't work at all in 0.22.

---

