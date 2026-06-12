---
title: "Same channel on digital &amp; analog"
date: 2008-05-17
forum: Mythbuntu
---

### Post by ian dobson on 2008-05-17
Hi All,

I currently have a PVR-500 analog tuner in my mythtv backend and I'm quite happy with the picture quality (philips tuner). My cable provider has now started sending out some channels per DVB-C and analog. I have installed a DVB-C card in the system and I'm getting the channels that I expected.

Is it possible to have the same channel (RTL for example) in both the analog and digital groups and that MythTV choses which one to record from based on which tuner is free.

Regards
Ian Dobson

---

### Post by volkswagner on 2008-05-17
What versions are you running, mythtv .21?  Does RTL have the same channel number in both digital and analog?  Do they share the same xmltv ID number?
Do you have a separate source for each?

---

### Post by ian dobson on 2008-05-18
Hi,

OK running mythtv ver .21
Source 1 is analog, Source 2 is digital.
Here's a dump from the channels db:-

   chanid  channum  freqid  sourceid  callsign  name   icon  finetune  videofilters  xmltvid  tvformat  
     7        7      319250    1         RTL2   RTL2   /root/.mythtv//channels/rtl2.jpg 0   rtl2.de Default 
  32438 30438   2 RTL2 RTL2 /root/.mythtv//channels/rtl2.jpg 0     Default 

If both channels have the same channel number and the same xmlid Mythtv will chose which one to record, is that what your trying to say?

Regards
Ian Dobson

---

### Post by volkswagner on 2008-05-18
Yes, these channels show up in two different lineups.  They have a different channel number.  When you select guide for scheduling a recording these two channels should show up twice.  

When you schedule a recording, your arguments should allow what you want.  Myth can search your title and will avoid conflicts.  You should see this while scheduling a recording via guide.  You don't want to use arguments such as "record at anytime on this channel".  After you select the frequency for the recording, go to scheduling options.  You want to make sure use any available input is selected.

You can verify this, by scheduling several recordings.  Select a show that is avail in both lineups.  Then schedule another show for the same time, which is only avail on one lineup.  When you go to upcoming recordings, the input number is shown for each recording.

Short answer, yes.  Myth will avoid conflicts.  You can also select priorities for your important shows.

---

### Post by the_grizzlybear on 2008-08-06
Is there anyway to make the channels show up in one lineup? I am also using analog and digital tuners together. They are both receiving the same channels, but of course with different frequencies.

I tried to make the channel number (channum) the same for both the digital as the analog channel, but that gave some unexpected results.

Is there any way to do it?


***********************************************************************************************

I found the answer on the MythTV users-mailing list: 
([http://mythtv.org/pipermail/mythtv-users/2008-August/229792.html](http://mythtv.org/pipermail/mythtv-users/2008-August/229792.html))

> Almost...  The channel number is /only/ used as a means to tell Myth 
> which channel to watch during LiveTV (i.e. provides a means for you to 
> switch to a channel directly by entering the proper "code"--the channel 
> number).  You can set the channel number to any value you want (so you 
> can remap the channels when your stupid cable company puts Fox 35 on 
> channel 5 or something).  Generally, though, every channel defined on a 
> Myth box should have a unique channel number to allow you to change to 
> the channel you want without having to worry about what capture 
> card/card input is currently in use before typing the channel number.
> 
> The channel callsign, on the other hand, is used to tell Myth that two 
> channels carry "substantially" identical content (i.e. should be treated 
> as the same channel for the purpose of scheduling).  At this point, Myth 
> will schedule any "this channel" rules to record off either source.  
> ("This channel" rules are defined by channel callsign, not channel 
> number or channel ID or source or ...)
> 
> However, in this instance--where two channels with the same content are 
> given the same callsign--we have the one exception to the "unique 
> channel number for all channels" rule:  if you want the program listing 
> for both channels "merged" into one line in the program guide, you 
> should set the channel numbers to the same value.  If given the same 
> callsign and channel number, the listings for those "same" channels will 
> be shown only once.
> 
> > , as long as the EPG data is the same.
> 
> Exactly.
> 
> Mike


> **volkswagner said:**
> Yes, these channels show up in two different lineups.  They have a different channel number.  When you select guide for scheduling a recording these two channels should show up twice.  

When you schedule a recording, your arguments should allow what you want.  Myth can search your title and will avoid conflicts.  You should see this while scheduling a recording via guide.  You don't want to use arguments such as "record at anytime on this channel".  After you select the frequency for the recording, go to scheduling options.  You want to make sure use any available input is selected.

You can verify this, by scheduling several recordings.  Select a show that is avail in both lineups.  Then schedule another show for the same time, which is only avail on one lineup.  When you go to upcoming recordings, the input number is shown for each recording.

Short answer, yes.  Myth will avoid conflicts.  You can also select priorities for your important shows.

---

