---
title: "newbie help"
date: 2008-07-06
forum: Mythbuntu
---

### Post by azmanam on 2008-07-06
Hi,

I've installed Mythbunutu with no major problems, but I can't Watch TV.  I'm almost positive it's because I don't have the 'Capture Cards', 'Video Sources', and/or 'Input Connections' configured correctly in MythTV setup.  I skipped over most of them during installation because I knew I was going to have trouble with my TV tuner card.  I bought the Hauppauge 1600, which the MythBuntu install guide (which I read after I bought the card) clearly says is not supported.

So after I installed the OS and partitioned the hard drives, etc.  I went back and followed the instructions in post #20 of this thread: [http://www.backports.ubuntuforums.org/showthread.php?t=813429&page=2](http://www.backports.ubuntuforums.org/showthread.php?t=813429&page=2).  I'm pretty sure the card should be recognized and working, because I received the conformation noted in the post ('dmesg | grep cx18' does indeed show 'Initialized card #0: Hauppauge HVR-1600' near the end of the output).  

Then I went back and tried to configure 'Capture Cards', 'Video Sources', and 'Input connections'.  But I don't really understand what the various input lines are asking me to do.

Can someone walk me through how to set up those menus to watch tv?  right now, when I select Watch TV from the MythTV menu, the screen flashes black for ~1 frame (very fast) then re-displays the MythTV menu.  

If I sounded like I know what I'm talking about, then I'm a good actor.  I can walk around a terminal, but not very fluently.  I'm probably going to need a bit more hand-holding than the average Linux user.  So I thank you, in advance, for the patience of whomever volunteers to help me with my setup.

---

### Post by nasha on 2008-07-07
If your research showed your tuner card is not supported, why on earth did you buy it and attempt an install!?!?!?

---

### Post by superm1 on 2008-07-07
So once you've got the card loading the driver like that.

a few things come to mind:

1) Are you on the latest 2.6.24-19 kernel?  
Have you done your updates yet?  If you haven't, please be sure to do those now.  You will hate to see breakage coming up because you didn't.  Once you do them, you may need to repeat some of those steps from #20.

2) Configuring your device.
If you are trying to use the digital side of this card, it needs to be configured as a DVB device in Capture cards.  If analog, then be sure to choose the right type PVR-XXX)

3) Video sources.
You need to make one of these.  Even if you dont have an account, you need a video source that says no account (or similar)

4) Input connections.
You need to connect the video device you made from the capture cards section to the video source you made in the video sources section here.  This is most commonly the reason for a black screen - not doing this step.

---

### Post by AndyCee on 2008-07-07
> If your research showed your tuner card is not supported, why on earth did you buy it and attempt an install!?!?!?

> which I read **after** I bought the card

-AndyCee

---

### Post by azmanam on 2008-07-07
> **nasha said:**
> If your research showed your tuner card is not supported, why on earth did you buy it and attempt an install!?!?!?

A fantastic question, indeed.  My order of research went as follows.  A co-worker has successfully gotten MythTV to work on a Gentoo system.  He recommended Hauppauge cards, as he's had previous success with them.  In researching the cards, it appeared most of them did not support digital TV input (if I was reading the specs correctly).  With the conversion to digital in Feb 09, I didn't want to have to purchase a new card right away, so I bought one that specifically indicated it would take digital input (the 1600).  I tried, very unsuccessfully, to install Gentoo by hand.  Then I found Mythbuntu and appreciated the all-in-one distro (my previous dabbles in Linux have been with Ubuntu Feisty).  Started reading through the manual and found the hardware incompatibility.  Browsed the forum for the aforementioned post on configuring the 1600 with Mythbuntu, and felt confident I could get my system to work.

@superm1
Thank you for your advice, I'll try those when I get home from work... *shrugs embarrassedly* I know how to 'uname -a' to check kernel version, but what's the command to request an upgrade?  

If I'm remembering correctly, when I go into the capture card menu (and others) and I select the proper setting, other fields appear which seem to need some input.  Do I change those at all, or leave as default?

Thanks again for all your help!  I really appreciate it.

---

### Post by superm1 on 2008-07-07
> **azmanam said:**
> 
snip

@superm1
Thank you for your advice, I'll try those when I get home from work... *shrugs embarrassedly* I know how to 'uname -a' to check kernel version, but what's the command to request an upgrade?  
[snip]

In your Applications menu, go find Update Manager.  Just run through all the updates in there and you will get the newer kernel.  If you've never run any updates, you will be on 2.6.24-16.

> 
If I'm remembering correctly, when I go into the capture card menu (and others) and I select the proper setting, other fields appear which seem to need some input.  Do I change those at all, or leave as default?

Leave them as default for now.  You can always go back if you realize you are missing something

> 
Thanks again for all your help!  I really appreciate it.
No prob.  Hopefully this all works out in the end :)

---

### Post by azmanam on 2008-07-07
1) upgraded kernel from 2.6.24-16 to 2.6.24-19

2) redid #20 from above.  Again received positive confirmation (noticed something about not installing a certain file (v4l-cx23418-apu.fw) and it asking if it was in a certain hotplug directory.  Searched for the file, the file is not on my computer.  Saw positive confirmation and stopped worrying :)

3) Capture Card: Card type = DVB DTV capture card (v3.x). DVB Device # = 0. Signal/Tuning Timeouts = 3000/5500 msec.

4) Video Sources: Used my trial account at SchedulesDirect.  Channel Frequency Table = Default.  I subscribe to standard cable (not "Digital Cable". that is, there is no hardware between the wall and the tv) (well, except for my computer :), do I need something different here?

5) Changed Video source to the setting from #4 above.  Use quick tuning = Live TV only.  Clicked Fetch Channels from Listings Source, starting channel = 1. (next screen) Input priority = 0, Input Group 1/2 = Generic/Generic.



Exited out, ran mythfilldatabase.  Selected Watch TV.  Screen goes black, says 'NVidia' (what I named one of the settings along the way), stays black...  Remembered cable was still plugged into back of TV... :)  Switched cable.  Screen stays black.  Rebooted 'just in case'.  Selected Watch TV.  Screen says NVidia again and stays black.  

Try arrow keys. Noticed channel changes, and I can see channel title with program information!!! but screen stays black...  Message appears: "You should have gotten a channel lock by now.  you can continue to wait for a signal, or you can change the channels with Up or Down, change video source (Y), inputs (C), etc."

y does nothing.  Shift+Y does nothing.  c redisplays 'NVidia' in corner, as does Shift+C.  I putz through the other keyboard keys and notice other options. I record my first show: "Sounds of Silence" :)  Program Guide works.

Went back in and created secondary settings for analogue input.  ran mythfilldatabase, selected Watch TV.  Same as above.  Y does nothing.  C re-displays NVidia.  Went back in and looked at settings.  It appears the analogue setup didn't take.  
Capture Card settings: video device is blank, with no drop-down options.  Manually typing in anything doesn't take, it reverts to blank if reopened.  Default input = Television.  
Input Connections settings: input = 'Could not open '' to probe its inputs'.  Video source = (None).  Changing that to my settings and selecting 'fetch channels...' doesn't take.  video source reverts to (none) on re-open.

Exit out, etc, Watch TV.  Problem persists...

So It looks like something more is working now that wasn't before, so at least I'm making progress!!!

New theory:  Reading through the rest of the posts at the thread mentioned above ([http://www.backports.ubuntuforums.org/showthread.php?t=813429](http://www.backports.ubuntuforums.org/showthread.php?t=813429)) it appears whatever I just installed doesn't play well with NVidia.  Does anyone else agree with my assessment?  The code starts to go over my head somewhat quickly.  It appears the OP says in post #35 he was using MPlayer (?) and was told to switch to me-tv.  How does me-tv compare to mythtv?  are they the same? drastically different? does the OPs problems with MPlayer mean I'll have the same problems with MythTV, and that they can be fixed by 'switching' to me-tv (if that's the right term)?

Post #20 at that thread (the one I used to get my 1600 recognized) links to a page to get NVidia to play along.  I don't understand what's going on at that page ([http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers)) and how it relates to the 1600 problems.  I don't see Hauppauge, 1600, or MythTV anywhere in the page.  If that's what I need to do, then I need some help translating the page into exactly which operations I need to perform.  

Then there is a back and forth between the OP and a different responder who helps, it appears, get everything working with me-tv (starting appx. post #67).  Is this something I need to look into?

WHEW! that was a lot.  Thanks for reading through all this and helping me figure things out.  I'm learning a lot, just not enough to anticipate and do things on my own yet.  soon...

---

### Post by Lester_Burnham on 2008-07-07
Hi,

I take it the signal is a digital TV signal on the DVB connection.

Have you tried doing a channel scan on the DVB interface, instead of "Fetch Channels from Listings Source". Then you will see if it can see a signal.

Lester

ps: I'd say that nvidia you see, is what you named your tuner in video sources.

---

### Post by azmanam on 2008-07-07
> I take it the signal is a digital TV signal on the DVB connection.

... sure!  I don't really know what you're asking, but only when I used DVB settings did anything appear to be recognized by the computer.

> Have you tried doing a channel scan on the DVB interface, instead of "Fetch Channels from Listings Source". Then you will see if it can see a signal.

I had not.  I tried with the physical cable plugged into the ATSC jack, Input = DVBInput, Frequency Table = broadcast, Mod = Terrestrial (8-VSB), ATSC Channel Separator = (51) None, Existing Channel Treatment = Minimal Updates ...  Output: Signal Strength = 0% for all, S/N = 0% for all. 'Time out -- no signal' for all channels. Tried again changing Frequency Table to Cable ... Output is the same.  Same output with all options under 'Frequency Table'.  Changing the Modulator to anything but Terrestrial (8-VSB) does not give a 'Scan Progress' Page and appears to do nothing when 'Next' is clicked.  Tried going back a page and unchecking 'Unencrypted Channels only'.  No change.  This sounds like a bad sign.

> ps: I'd say that nvidia you see, is what you named your tuner in video sources.

It's what I named my 'Display Name (optional) in Input Connections.  I changed it to 'Digital' when I attempted to set up a separate analogue option, and saw 'Digital' on the screen in Watch TV mode.




*Don't worry.  I wouldn't remember me, either.*

---

### Post by azmanam on 2008-07-07
New note:

I was walking around my file tree in a terminal and noticed when I downloaded all the files from 'Post #20' it appears the files were dropped into a newly created folder /home/*(username)*/v4l-dvb.

That seems to me like an odd place for them to be.  Does it matter where they are, or should they be in a more correct location?

If they are supposed to be in a more correct location, what are the command-line commands to do that? (or how do I manipulate the GUI file manager with su privileges?)

---

### Post by azmanam on 2008-07-20
see this thread ([http://ubuntuforums.org/showthread.php?p=5423082#post5423082](http://ubuntuforums.org/showthread.php?p=5423082#post5423082)) for the rest of this saga...

---

