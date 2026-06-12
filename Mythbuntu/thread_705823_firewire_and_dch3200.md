---
title: "firewire and dch3200"
date: 2008-02-23
forum: Mythbuntu
---

### Post by 4dognight on 2008-02-23
trying to get firewire working with a dch3200 stb. plugreport works and so does firewire tester. I configure the backend script to prime it. I have added the firewire port in the config. 

When i start the frontend and cycle thru my tuners with the 'Y' key, It never even switches to the firewire .

Am I missing something here? How do I switch to the firewire  input in the frontend?

---

### Post by newlinux on 2008-02-23
You are doing the right thing to get to it, which implies something isn't right in the setup.

Do you have it set to start on a channel that is not 5c protected and have you associated a video source with it? On your status screen does the tuner show up as connected? What do your logs say?

---

### Post by 4dognight on 2008-02-24
yes i have it on a non 5c channel. i used the diagnostic on the stb to verify. no CCI flag setting either
the status screen shows it as unavailable. odd thing there is it has my pvr500 tuners in there twice.first 2 shows as good. then as unavailable. then tuner5 as the firewire as unavailable.

 2008-02-23 23:21:24.375 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 5

that is in the backendlog i see this. not sure if its related.


also as a side question. I have to start the frontend manually. how do i get it to start automatically on a boot. Or at least have it in the dropdown menu? I am starting it manually in a terminal window.

---

### Post by newlinux on 2008-02-24
So the tuner is failing to start up. Do you have multiple backends? Are all your backends running? 

Have you modified the init script to give mythtv ownership of the firewire? Otherwise setting up the firewire tuner will fail each boot.

As far as autostarting goes, I don't do that, but I think there are a number of ways to do it. I don't know if mythbuntu control center has a setting for it or not. Are you running Gnome? You can put startup programs in System->Preferences->Sessions. Or you can create a file: ~/.config/autostart/mythtv.desktop. You'd put something like:
```

[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=MythTV
Comment=
Exec=/usr/bin/mythfrontend -l /var/log/mythtv/mythfrontend.log
StartupNotify=false
Terminal=false
Hidden=false

``` 
in there...

---

### Post by 4dognight on 2008-02-24
ok, i got some partial success.
I had chosen 'other' for my stb as it wasnt in the drop down list. I tried choosing it as a dct6214 , and i got it to work , or at least temporarily.

One problem i think i have, is with the node keeps changing on me. Is there some sure fire way to make it stay put?

I then compiled the latest version of 6200ch, since it supported the dch3200, or at least partially. I had to add my specific vendor id, which are all hard coded(hmmm :shock:) in the pgm. I tested it manually which worked great. then entered it into the myth config throught the gui. Now once in a while when i change channels it fails and i get the following in the log.


2008-02-24 14:16:50.189 NVP: Prebuffer wait timed out 10 times.
2008-02-24 14:16:51.916 NVP: Prebuffer wait timed out 10 times.
2008-02-24 14:16:53.644 NVP: Prebuffer wait timed out 10 times.
2008-02-24 14:16:55.008 RingBuf(/storage/1059_20080224141648.mpg): Invalid file (fd -1) when opening '/storage/1059_20080224141648.mpg'.
2008-02-24 14:16:55.008 NVP, Error: JumpToProgram's OpenFile failed.
2008-02-24 14:16:55.008 NVP, Error: Unknown error, exiting decoder
2008-02-24 14:16:55.012 TV: Attempting to change from WatchingLiveTV to None
QObject::disconnect: Unexpected null parameter


Is this a problem with the ring buffer size? should it be made larger?

btw. I seem to be getting quite a few of my channels available through firewire, which is nice to see.

---

### Post by newlinux on 2008-02-24
Does this happen when changing to the same channels all the time (i.e. are you sure these aren't 5c protected channels/programs)? I doubt it is a problem with the ring buffer size.

When does the node change? After reboots or poweroff of the DCH? The node can change anytime after a reboot, disconnection or poweroff of either the box or the computer... I don't know anything you can do about it

---

### Post by 4dognight on 2008-02-24
slowly but surely I am getting there! My problem was due to a bad coax cable. my stb had trouble tuning into some channels. this caused it to dislay a msg that it was unavailable. got a new cable and now changing to channels works... almost :-)  

Now, for my next problem. I can only change to channels below 70 from within mythtv, If I change using the stb box to a channell > 70 it works, and even displays using myth. I just cant change channels > 70 in myth cause there is no schedules. Do i need to somehow specify in schedules direct that i want > channel 70?

Also, my other problem. I have no sound! does firewire provide sound? I am trying to use just my stereo output from the sound card for now. My MB does have optical out, but for now stereo out for now will do.

---

### Post by newlinux on 2008-02-24
You can specify in schedules direct a lineup that has all the channels you want, and then you can fetch those channels from schedules direct into your mythtv video source and then you should be set.

Hmm, yes, firewire provides sound. It is a digital transmission of the entire stream (audio and video). Do you get any messages from mythfrontend about audio when you playback something from firewire?

---

### Post by 4dognight on 2008-02-25
2008-02-24 23:41:08.079 Opening ALSA audio device 'default'.
2008-02-24 23:41:08.143 Mixer unable to find control Master
2008-02-24 23:41:08.143 Mixer unable to find control Master
2008-02-24 23:41:08.143 Mixer unable to find control Master

Ok, I still have no sound. This is from my frontend log. Looks like its having problems finding control master? I have no sound on both of the pvr500 tuners and this firewire tuner.

Is there something in ubuntu i can use to trouble shoot my sound problem, instead of trying to get it working by going into mythtv?

btw i got the schedules direct straightened out. i created one for the pvr500 and one for firewire with all the channels. channel changing works now. I will have to edit my entire lineup, because if i switch to a channel that doesnt exist, it will mess up my firewire connection, to the point of having to go into the config and move it off that bad channel, as it always restarts at that last channel i was on.

---

### Post by newlinux on 2008-02-25
That sound problem is probably a myth configuration issue, not an overall ubuntu one, and if so, will need to be troubleshot in myth. Can you play any of your recordings with sound using mplayer? What do you have you sound device set to?

---

### Post by 4dognight on 2008-02-25
I tried playing a dvd in mplayer, but no sound. My device is set to ALSA/default in the config. I tried to other settings but did nothing to help. This is why I think its a fundamental problem in the OS/hardware. It is on board sound on a ABIT AN-M2 MB. Bios is set to AC-97(has option for HD audio). It has an optional optical SPDIF. maybe I should try that?

---

### Post by newlinux on 2008-02-25
> **4dognight said:**
> I tried playing a dvd in mplayer, but no sound. My device is set to ALSA/default in the config. I tried to other settings but did nothing to help. This is why I think its a fundamental problem in the OS/hardware. It is on board sound on a ABIT AN-M2 MB. Bios is set to AC-97(has option for HD audio). It has an optional optical SPDIF. maybe I should try that?

So you don't get sound for anything on your system?
I see, you are probably right about it being an overall ubuntu issue. I have always found it better to get regular sound working then spdif (Because spdif can have some additional complications) but it can't hurt to try. I would definitely work on getting it to work outside of myth first, and then mess with myth settings.

There is a thread somewhere on this forum that is called comprehensive guide to sound. It has a lot of trouble shooting tips. search for that and try it out...

---

### Post by 4dognight on 2008-02-26
I googled around and found there is a bug in ubuntu and the version of ALSA for the ALC883/888 sound driver. I updated to the latest version of ALSA 1.0.16 and I got sound coming out now. Except I have something strange, where it seems like the builtin speakers on the TV are incompatible. If I hook up a pair of PC speakers to my PC they work fine, but when connected to the TV speakers, there is no sound. I know the TV speakers work, cause I have them hooked up to the STB, and when I switch to just the STB input, the sound comes thru the TV speakers. Maybe my PC sound is too little power to drive my TV speakers?

My next step is to try the SPDIF through my Audio amp.

Except for the few quirks with firewire I mentioned earlier, I will have to call this a success in getting firewire to work. I have pretty much all my stations available through firewire, including my HD channels. Cool!

Any new problems/questions. I will make a new post.
thanks for you help Newlinux.

---

