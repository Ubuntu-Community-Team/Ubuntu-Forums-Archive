---
title: "Should I upgrade my TV card?"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by yanewby on 2007-02-20
I currently use a Pinnacle PCTV Pro TV card.  This is an analogue TV card that has a BT878 chip on it.  I use the S-Video connector to record video from the output of my cable TV box whilst audio is recorded via my sound card.  

Sometimes the video is choppy, if I have been doing too much on my PC when I am recording TV.

My question is would it be beneficial to upgrade the TV Card to something like a Hauppauge PVR-150?

---

### Post by crispy_420 on 2007-02-21
You might be limited by your CPU. With a bttv based card and recording, the CPU is doing all the work. 

So a PVR-150 will help you. As the encoding is being done by the card and not your CPU. This should help your problem. But keep in mind that set up will not be simple. You'll have to manually install the drivers. There is plenty of help on these forums so if you make the jump, be patient with the transition. You'll also have the option of MythTV too.

Hope that gives an idea...

---

### Post by pico2215 on 2007-02-21
I would recommend the Hauppauge PVR-150 as well. I use it with MythTV, and it's wonderful. I'm able to record scheduled programs in the background without any noticeable slowdown at all. And it's a pretty decently priced card too.

Like crispy_420 mentioned, myth setup is pretty complicated, but there's plenty of places to find help on these forums.

The only area I really had issues with was the remote. Even though there were how-tos out there on how to get it to work, it still took a little messing around with it on my own to get working the way I wanted. But once you get it, you're set.

---

### Post by yanewby on 2007-02-27
Thanks for the replies and apologies for my slow response!

I have decided to go for the PVR-150.  I have looked into MythTV before and it is far to much for what I require.  With my old TV card I used to use a simple mencoder/crontab command to record the programs I required.

Will I still be able to use these commands?  I have tried searching the net but it is difficult to find anything specific to the PVR-*50 cards due to the generic nature of the "PVR" term.

This is what I currently use:

mencoder -tv driver=v4l2:buffersize=32:norm=PAL:input=1:forceaudio:immediatemode=0:adevice=/dev/dsp:amode=1:fps=25:quality=60:width=640:height=480:device=/dev/video0:chanlist=europe-west:channel=50 tv:// -o /home/xyz/Desktop/"$TITLE".avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1000:keyint=25 $PROCESSVIDEO -af volume=-20 -oac mp3lame -lameopts cbr:vol=0:br=96:mode=1 -endpos $RECORDLENGTH -noskip

where $TITLE, $PROCESSVIDEO and $RECORDLENGTH are variables relating to the title, aspect ratio and length of the programme.

How will I need to alter this to record from my PVR-150?

Thanks again!

---

