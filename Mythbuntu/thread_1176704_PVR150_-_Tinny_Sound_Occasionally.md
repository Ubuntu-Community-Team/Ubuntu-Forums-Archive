---
title: "PVR150 - Tinny Sound Occasionally"
date: 2009-06-02
forum: Mythbuntu
---

### Post by wizgnome on 2009-06-02
I have been running mythbuntu for about 6 months and mostly everything works fine. But I have a problem where occasionally the recorded sound is tinny or distorted. I am using the PVR150 capture card and a google search revealed that this sometimes happens. Has it ever been solved.

If I select Live TV and it happens to be distorted, exiting to the menu and selecting it again fixes the problem. However with recordings I don't know about the problem until I go to watch them some time later. If I make several recordings on the same channel then one might be distorted and the others will be ok.

This only happens on around 1 in 20 or more recordings.

---

### Post by LowSky on 2009-06-02
this seems to be a defect in the card if its only occuring randomly.

FYI in about 10 days the US is going totaly digital, so your [PVR-150]("http://www.mythtv.org/wiki/Hauppauge_PVR-150") will no longer work without using a digital converter box or cable TV

---

### Post by wizgnome on 2009-06-02
> **LowSky said:**
> this seems to be a defect in the card if its only occuring randomly.

FYI in about 10 days the US is going totaly digital, so your [PVR-150]("http://www.mythtv.org/wiki/Hauppauge_PVR-150") will no longer work without using a digital converter box or cable TV

I am not in the US, and I use it with a digital Satellite receiver (I could also use it with a digital set top box) so your comment is totally irrelevant also the problem often occurs with this card. I was looking to see if anyone had solved the problem

---

### Post by LorenzoS on 2009-06-03
I have the PVR-500 and get the same problem sporadically.  I never found any insight into the cause.

---

### Post by LowSky on 2009-06-04
> **LorenzoS said:**
>  I never found any insight into the cause.

Well if it is effecting other people, then I going to assume its a bad chipset or your power supply/motherboard isn't supplying the correct voltage going to the card. Try using another PCI slot

---

### Post by Furry_Fighter_20x66 on 2009-06-05
This problem I have at times too. Fortunately for me I have found the problem has gradually gone away to the point it occurs for me maybe once every 40 recordings.

I have found that the likelihood of the problem is increased with back to back recordings. I can only speculate since no error messages occur but I think the card resets after a recording and then before it can finish properly resetting it is recording again.

It's not really a big issue for me anyway since the machine is only taping maybe one or two shows a day and no one watches live TV on it. If you can schedule things around so they don't record back to back it will likely solve many of your tinny recordings.

---

### Post by foxbuntu on 2009-06-06
The issue is a known problem with some of the analog ivtv based tuners. It basically boils down to myth not clearing the audio channel when the channel switches on an external source. (i.e. a set-top-box)

The good news: I have been working on packaging a small wrapper script that will tune channels and keep this audio issue from happening. I will be posting the package in a ppa on launchpad and announce when it completed.

---

### Post by Billsputters on 2009-06-08
I've just finished building my box and got it mostly working, just a few frills to finish.

Anyway, I've recorded a few programs and set up a schedule for tonight and programmed the sat decoder to change channel as well. First programme was on BBC Entertainment, so I manually changed to that channel. Low and behold, tinny sound. This was not present on the recording I made on the same channel some 10 hours earlier. Strangely enough, if I manually change the sat decoder channel to the channel either side, both are perfect sound.

So, it's something to do with the channel and how the audio is sent.

Later . . 

I've just rebooted and the problem has gone. But I am puzzled as to why just changing channel externally on the same mythtv input gives clear sound on other channels but buzzy tinny sound on one particular on. And why that should go on a reboot.

---

### Post by tgm4883 on 2009-06-08
> **Billsputters said:**
> I've just finished building my box and got it mostly working, just a few frills to finish.

Anyway, I've recorded a few programs and set up a schedule for tonight and programmed the sat decoder to change channel as well. First programme was on BBC Entertainment, so I manually changed to that channel. Low and behold, tinny sound. This was not present on the recording I made on the same channel some 10 hours earlier. Strangely enough, if I manually change the sat decoder channel to the channel either side, both are perfect sound.

So, it's something to do with the channel and how the audio is sent.

Later . . 

I've just rebooted and the problem has gone. But I am puzzled as to why just changing channel externally on the same mythtv input gives clear sound on other channels but buzzy tinny sound on one particular on. And why that should go on a reboot.

I don't have the commands in front of me until I get home, but if you are getting tinny sound you can change the audio channel to something else and back again and if it works you can wait for foxbuntu's fix

---

### Post by nickrout on 2009-06-08
v4l2-ctl -a 1 should get rid of the tinny audio.

Set up a cron job that does nothing but this, every minute, viz

for loop in 1 2 3 4 5 6 
do
   v4l2-ctl -a 1
   sleep 10
done

(or something like that).

That script will run through the loop 6 times at 10 sec per loop. If cron runs the script every minute you'll only ever get 10 secs of tinny audio. You can adjust the script to run a tighter loop, say 20 loops of 3 seconds if 10s too much.

---

### Post by LorenzoS on 2009-06-09
> **nickrout said:**
> v4l2-ctl -a 1 should get rid of the tinny audio.I've never known the tinny audio to start in the middle of a recording.  So would it make sense to put this command in my channel changing script that is executed before each recording?

---

### Post by tgm4883 on 2009-06-09
> **nickrout said:**
> v4l2-ctl -a 1 should get rid of the tinny audio.

Set up a cron job that does nothing but this, every minute, viz

for loop in 1 2 3 4 5 6 
do
   v4l2-ctl -a 1
   sleep 10
done

(or something like that).

That script will run through the loop 6 times at 10 sec per loop. If cron runs the script every minute you'll only ever get 10 secs of tinny audio. You can adjust the script to run a tighter loop, say 20 loops of 3 seconds if 10s too much.

I've never seen the tinny audio start in the middle of a recording either.  I have a script that changes the audio to 0, then back to 1 when it changes channels.  Haven't had issues with tinny audio since

---

### Post by LorenzoS on 2009-06-09
> **tgm4883 said:**
> I have a script that changes the audio to 0, then back to 1 when it changes channels.If you don't mind, what are the command lines you use?

---

### Post by bcg30506 on 2009-06-09
This script seems to work for me:

#!/bin/bash

# General Instruments DCT2244abcdef digital cable box (0_93)
REMOTE_NAME=blaster
for digit in $(echo $1 | sed -e 's/./& /g'); do
  irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
  sleep 0.3  # note, you may have to tweak the interdigit delay up a bit
done
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME SELECT
sleep 0.3
irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME EXIT

# Try to prevent audio static
sleep 0.1
v4l2-ctl -d 1 --set-audio-input=1

This is the change channel script I use with my external cable box.  It goes into my 2nd tuner which is why I have the -d 1 parameter and it uses the Line In input (1).  My first tuner would be -d 0 and it uses audio input 0 (Tuner).

You can see a list of your audio inputs with:

v4l2-ctl -d 0 --list-audio-inputs
v4l2-ctl -d 1 --list-audio-inputs
(one for each tuner card in my case)

---

### Post by LorenzoS on 2009-06-12
Success!  I added v4l2-ctl -d 1 --set-audio-input=1 into my channel changing script for the 2nd tuner on my PVR-500 and I have not encountered the problem after several back-to-back recordings.  Thanks very much bcg, tgm and nick for the help!

---

### Post by Billsputters on 2009-07-15
On some channels I get really quiet sound. It sounds like it's gating, ie. if it's below a certain level, then we get silence. This coupled with the lower level from some channels makes difficult viewing! I can't ascertain if it is the channels from the decoder giving low levels on particular channels with any degree of accuracy, but I suspect that that is part of the problem.

So, how do I add the above v4l2-ctl -d 1 --set-audio-input=1 into my channel changing script. I don't have a /usr/local/bin/chan_changer.sh, do I just add it?

---

### Post by ds_pablo on 2009-07-16
> **Billsputters said:**
> On some channels I get really quiet sound. It sounds like it's gating, ie. if it's below a certain level, then we get silence. This coupled with the lower level from some channels makes difficult viewing! I can't ascertain if it is the channels from the decoder giving low levels on particular channels with any degree of accuracy, but I suspect that that is part of the problem.

So, how do I add the above v4l2-ctl -d 1 --set-audio-input=1 into my channel changing script. I don't have a /usr/local/bin/chan_changer.sh, do I just add it?

I too get tinny sound at times from my PVR-150 but am using the card to do tuning--i.e. no external tuner.  How can this be rectified?

---

### Post by Bentley8 on 2011-01-12
Anything more regarding a fix for those of us that don't use external tuners?

Can a script be written that only resets the audio and ignores any other activity?  Would MythTV accept the audio reset, but then use the built-in channel changing, or would it then stop changing channels altogether?

I suppose I could fiddle about with it, but I've been beaten up by MythTV a lot lately and want to avoid more bruising.

---

