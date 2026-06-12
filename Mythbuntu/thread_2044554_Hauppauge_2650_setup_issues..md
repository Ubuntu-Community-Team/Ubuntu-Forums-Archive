---
title: "Hauppauge 2650 setup issues."
date: 2012-08-19
forum: Mythbuntu
---

### Post by soggypretzels on 2012-08-19
I am trying to watch and record US digital cable with Mythbuntu 12.04. I have my backend and frontend on one box with no other MythTV clients on the network. When I tried to set up capture cards, the Hauppauge 2650 will only be recognized as a HDhomerun device. I have tried scanning for channels using Backend-Setup and that seemed to work. however, when I open the frontend and select "Watch TV" the screen flashes to "Please Wait..." then instantly kicks me back to the main frontend menu.

I know the tuner is getting video, because if I open the "HDHomeRun Config GUI" application and scan for channels, if I hit "view" I get video from that channel.

This is driving me nuts. There seems to be very little documentation on the Hauppauge 2650 with regards to it working in Linux.

P.s. I'm a noob.

---

### Post by tgm4883 on 2012-08-19
The most common reason for that is that you didn't go though all of the steps in mythtv-setup (specifically, 2, 3 and 4). We'd need to look at /var/log/mythtv/mythbackend.log to pinpoint the exact reason for it though

---

### Post by soggypretzels on 2012-08-19
The whole file is too large to post (<2mb) so only posted events after August 17. If that messes something up tell me if there is a way to post just the info you need.

The log can be found here:
[http://pastebin.com/DW0faC2n](http://pastebin.com/DW0faC2n)

Thanks for you help!

---

### Post by tgm4883 on 2012-08-20
```
Aug 19 00:29:45 berson-media mythbackend[4283]: E TVRecEvent dtvmultiplex.cpp:325 (ParseTuningParams) DTVMux: ParseTuningParams -- Unknown tuner type = 0x2000
Aug 19 00:29:45 berson-media mythbackend[4283]: E TVRecEvent dtvchannel.cpp:308 (SetChannelByString) DTVChan(20118B03-0): SetChannelByString(8-1): Failed to initialize multiplex options
Aug 19 00:29:45 berson-media mythbackend[4283]: E TVRecEvent tv_rec.cpp:3681 (TuningFrequency) TVRec(1): Failed to set channel to 8-1. Reverting to kState_None
```

Did you try setting that up as a network tuner rather then an HDHomerun?

Also, do you have multiplex enabled on either of the tuners?

---

### Post by soggypretzels on 2012-08-20
I have not tried setting it up as a network tuner. Should I?

I'm not sure I even know what multiplex is. Enlighten me?

---

### Post by tgm4883 on 2012-08-20
> **soggypretzels said:**
> I have not tried setting it up as a network tuner. Should I?

I'm not sure I even know what multiplex is. Enlighten me?

Lets try disabling Multirec first, since the hardware can't do it.

From [http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex](http://www.mythtv.org/wiki/Record_multiple_channels_from_one_multiplex)
> Setup Tuners / Capture Cards

Tuner priorities aside, when selecting a tuner for a recording, the backend will choose the first tuner defined sequentially by the MythTV setup program. As such, it is often preferred to delete all capture cards and recreate them from scratch, than to delete cards individually.
For proper setup with multi-channel-recording, or multirec, tuners should be configured in order, and the number of simultaneous recordings set all at once.** This is set with the number of recordings setting in the advanced options in card configuration. Default is two, and maximum is five.** When the recorder selects a tuner, it will cycle through sequentially until it finds a virtual tuner capable of receiving that channel. Proper configuration in this manner means it will properly use an in use tuner on the multiplex, before falling back to an unused tuner.
The consequence of this is that live TV can use any channel, and thus will pick the first available virtual tuner, even if locked to a multiplex. The only way to leave this multiplex is to manually switch to a different card or different source. The alternative is to go back through after adding tuners, and add one more virtual tuner for each physical one. Then set the frontend to avoid conflicts in playback settings. This will have the frontend select inputs from the back of the list, so if no recordings are currently active, each live tv session will get its own physical tuner. Be aware of the implications to scheduling conflicts this may cause.

So you'll need to go back into MythTV setup. Go to the setup for each card (under step 2), go into Advanced settings, and ensure that set the max number of recordings to 1.

---

### Post by soggypretzels on 2012-08-20
I've set the "max recording" for both tuners to 1 in mythbackend setup.
Still nothing.

---

### Post by tgm4883 on 2012-08-20
> **soggypretzels said:**
> I've set the "max recording" for both tuners to 1 in mythbackend setup.
Still nothing.

Did you try setting it up as a network recorder?

---

### Post by soggypretzels on 2012-08-20
It gives me a "all tuners are busy" error. There didn't seem to be a way to scan for channels with the tuners set up as network.

---

### Post by tgm4883 on 2012-08-21
Looks like it's literally a Prime with some reduced functionality, so probably best to go back to telling MythTV it's a Prime.

Did you follow this when adding it?
[http://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime](http://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime)

---

### Post by soggypretzels on 2012-08-21
Is it possible to use EIT instead Schedules Direct?

---

### Post by tgm4883 on 2012-08-22
Possibly. In the US, EIT is completely terrible to the point it is unusable, so I've never used it.

---

### Post by soggypretzels on 2012-08-23
Ok, set it up as HDhr-p used schedules direct. Used the guide you linked me to. When doing DB-fill there were some non-fatal errors, but it did say it completed successfully. Sadly after reopening the frontend and selecting "Watch TV" the issue persists (flashes to "Please wait" then dumps me back to the main menu).

I'm running out of hair to tear out.

Thanks again for the help.

---

### Post by tgm4883 on 2012-08-23
> **soggypretzels said:**
> Ok, set it up as HDhr-p used schedules direct. Used the guide you linked me to. When doing DB-fill there were some non-fatal errors, but it did say it completed successfully. Sadly after reopening the frontend and selecting "Watch TV" the issue persists (flashes to "Please wait" then dumps me back to the main menu).

I'm running out of hair to tear out.

Thanks again for the help.

We'd need to see fresh backend logs to assist.

---

### Post by soggypretzels on 2012-08-24
Turns out the backend had still had the analog channels that were scanned earlier (from previous attempts to fix) and those were somehow conflicting with the digital channels that you helped me get. I deleted all the channels and re-downloaded the schedules. Great success!

Thanks so much for your help. couldn't have done it without you.

[Solved]

---

