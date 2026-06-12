---
title: "New mythbuntu install"
date: 2008-07-26
forum: Mythbuntu
---

### Post by chronographer on 2008-07-26
Hi all.

I have a new via 12000 mobo with a hauppuage 500 (i think, its a philips chipset) anyway, I have installed firmware for the tuner, and it workd ok in me-tv, and I have set up channels in mythtv-setup, all channels were found and its great BUT...

I have a problem where when in myth frontend I select watch TV and the screen flicks, as if to go to tv and then flicks back to the menu... I asked in IRC, and they were unhelpful so I ask here if anyone can help me get this box up and running!

As a side note, I was thinking of trying out xbmc on this box, is this easy to do and can I do it from the same install as the mythbuntu, so is it as easy as apt-get install xbmc ??

last thing, although I can watch tv with me-tv (a great program) it has some issues with image reproduction, it looks like its interlaced badly or something. I will try to take a screenshot later and post it.

Thanks for your help, please post, even if you have only encouragement! I don't want to have to install XP and use media portal!

---

### Post by superm1 on 2008-07-26
Sounds like you didn't associate your channel line up with the correct input of the card in mythtv-setup.

---

### Post by nickrout on 2008-07-26
take a look at your mythfrontend.log file in /var/log/mythtv

You can't expect us to help unless we have more information.

---

### Post by chronographer on 2008-07-26
Hi thanks for your response, I have attached my myth logs. This is the important bit > 2008-07-26 09:12:10.293 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-07-26 09:12:10.322 Using protocol version 40
2008-07-26 09:12:10.412 TV: Attempting to change from None to WatchingLiveTV
2008-07-26 09:12:10.428 Using protocol version 40
2008-07-26 09:12:12.555 GetEntryAt(-1) failed.
2008-07-26 09:12:12.561 EntryToProgram(0@Thu Jan 1 11:00:00 1970) failed to get pginfo
2008-07-26 09:12:12.562 TV Error: LiveTV not successfully started
2008-07-26 09:12:12.563 TV Error: LiveTV not successfully started
2008-07-26 09:12:12.620 TV: Deleting TV Chain in destructor
2008-07-26 09:12:12.688 DPMS Deactivated 

I don't know what this indicates, hopefully you can help! I have another issue, where in playing a avi file it plays fine for a minute or so, then the system locks up, can't ctrl alt backspace, nor ctrl alt F1... not ctrl alt del.  Any ideas how to trace this problem? I r3ead something about nehemiah boards and kernel problems, is that the case here?

So I now have 2 big things to solve, and green lines around TV in me-tv, seems to be interlacing problem...

Thanks, agl

ooh. backend logs have more info: > 2008-07-25 23:03:06.573 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2008-07-25 23:03:06.915 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?

just following that up now... (p.s. the logs are too big to attach, may attach later.)

---

### Post by chronographer on 2008-07-26
oops, looks like its something else actually: > 2008-07-27 11:48:47.962 adding: mythbox as a client (events: 0)
2008-07-27 11:48:47.988 TVRec(1): Changing from None to WatchingLiveTV
2008-07-27 11:48:48.064 TVRec(1): HW Tuner: 1->1
2008-07-27 11:48:49.597 TFW, Error: Opening file '/home/alex/music/1003_20080727114848.mpg'.
			eno: Permission denied (13)
2008-07-27 11:48:49.604 TVRec(1) Error: RingBuffer '/home/alex/music/1003_20080727114848.mpg' not open...
2008-07-27 11:48:49.606 TVRec(1) Error: CreateLiveTVRingBuffer() failed
2008-07-27 11:48:49.608 TVRec(1) Error: Failed to create RingBuffer 1
2008-07-27 11:48:49.609 TVRec(1): Changing from WatchingLiveTV to None

so permissions are wrong somewhere... what have I done? how do I fix it?

---

### Post by chronographer on 2008-07-26
Hey it seems to be fixed, I set the tv directory to music, which was silly, and the permissions were bad there, it was set as my users directory obviously. so the solution was to creat a new directory '/home/alex/TV' and chmod 777 for it so ican read and write and mythtv can read and write! Thanks for getting me to read the logs folks!

Now ... I have no great problems, as mythtv seems to play everything correctly without freezing. I just need to set up my remote control now... lets see how that goes. Thanks again.

agl

---

### Post by chronographer on 2008-07-27
Ok new system is go, but I get random system freezes, everything is unresponsive, seems like serious kernel stuff going down...

anyone help me fix it?

---

### Post by AJ1000 on 2008-07-27
Have you activated your lna?

To do this:

In /etc/modprobe.d/options add:

options dvb_usb_dib0700 force_lna_activation=1

Without activating the lna you are getting a signal strength of 0%. Could that be the issue?

Which version of Mythbuntu are you using?

---

### Post by chronographer on 2008-07-27
Hi. This is not my problem. I use a hauppuage nova t card, with a philips chipset. I have firmware for it, and now that I corrected my silly problem (see above, to do with permissions) I can watch live tv, record tv and watch movies.

I get a hard lock up now though, the computer will freeze. Sometimes it works for a long time before freezing, sometimes it freezes soon after turning it on. It has only frozen whilst playing videos, playing with VLC and mythtv will cause freeze, in mythtv playing videos or tv has caused lock up.

So I have swapped to a RT (real time) kernel and I will see if this changes any thing. agl

---

