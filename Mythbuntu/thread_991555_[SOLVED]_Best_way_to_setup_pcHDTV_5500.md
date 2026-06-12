---
title: "[SOLVED] Best way to setup pcHDTV 5500"
date: 2008-11-23
forum: Mythbuntu
---

### Post by dmfrey on 2008-11-23
I recently rebuilt my mythbuntu system with 8.10 and a larger hard drive.

In this machine I have Firewire capture and a Haupauge 150 setup.  I recently also added a pcHDTV 5500.  I attempted to set this card up on 8.04 but I ran into a few snags.

I have two Schedules Direct lineups setup, one for HD and one for SD.

When I setup the pcHDTV card, I scanned for the higher frequencies and found the 20 or so channels that RCN offers unencrypted in the Lehigh Valley viewing area.  RCN, however, does not provide its channel information over these channels so I had to setup this information separately.  

After setting up the card, I could watch live tv without issue, but I had no guide data.  I then, through mythweb channel editor, added the xmltvids for the unknown channels and ran mythfilldatabase (channel updates only) to populate the data.  The problem was that it rewrote the channel numbers to be the ones from the Schedules Direct HD listings and I could no longer tune the channels on the pcHDTV card.

I was wondering if someone could provide me with the appropriate steps to follow to get this card setup correctly.  Here is what I got so far:

1. Setup pcHDTV 5500 as DVB card
2. Setup input connection to Schedules Direct HD lineup
3. Scan upper frequency channels
4. Fix lineup program data

It is step 4 that is broken for me.  Any help would be greatly appreciated.

---

### Post by klc5555 on 2008-11-24
> **dmfrey said:**
> I recently rebuilt my mythbuntu system with 8.10 and a larger hard drive.

In this machine I have Firewire capture and a Haupauge 150 setup.  I recently also added a pcHDTV 5500.  I attempted to set this card up on 8.04 but I ran into a few snags.

I have two Schedules Direct lineups setup, one for HD and one for SD.

When I setup the pcHDTV card, I scanned for the higher frequencies and found the 20 or so channels that RCN offers unencrypted in the Lehigh Valley viewing area.  RCN, however, does not provide its channel information over these channels so I had to setup this information separately.  

After setting up the card, I could watch live tv without issue, but I had no guide data.  I then, through mythweb channel editor, added the xmltvids for the unknown channels and ran mythfilldatabase (channel updates only) to populate the data.  The problem was that it rewrote the channel numbers to be the ones from the Schedules Direct HD listings and I could no longer tune the channels on the pcHDTV card.

I was wondering if someone could provide me with the appropriate steps to follow to get this card setup correctly.  Here is what I got so far:

1. Setup pcHDTV 5500 as DVB card
2. Setup input connection to Schedules Direct HD lineup
3. Scan upper frequency channels
4. Fix lineup program data

It is step 4 that is broken for me.  Any help would be greatly appreciated.

I use a couple of pcHDTV5500s along with a pvr 150 in  my master backend. I had some problem with channel conflation early on (particularly in scheduling recordings), and if I read your post correctly, this seems to be what you've got going on between your pcHD5500 and your firewire connection.

Probably the best way to do this would be, the backend setup, to set up a new Video Source specifically for the pchdtv55500, call it QAM or whatever. Set the new Video Source to download listings from SchedulesDirect just like your other Video Sources do. In Input Connections, connect your DVB0 tuner (the 5500) to the Video Source QAM, then have the 5500 scan for channels on QAM. The 5500 will find what it found before, presumably all UNKNOWN.

In Channel Editor, instead of "All Sources", for a moment just specify your source QAM, all its UNKNOWN channels pop up. Go into each one, add the xmlid information like you did before, assign each UNKNOWN to whatever free channel number you wish to, and, most important of all, give each one of these channels a Call Number which is unique from every other channel/station on your system that Mythtv knows about, from whatever source. Otherwise, Myth tends to get confused. If you already have a channel whose call-sign is "WWW-HD", then call the clear QAM one "WWW-QAM", or whatever, as long as it's unique. You may also "Name" the stations, though from Mythtv's perspective, this is not significant.

Now exit, run mythfilldatabase, and the QAM listings should fill up (starting "tomorrow" --look ahead in the schedule if you initially don't think you got any listings).

Now, all the channels your 5500 can see are visible in the general schedule, but the 5500 itself can only see the channels it can specifically tune. If you're watching TV on the 5500 and punch in a channel number it doesn't know about from the QAM Video Source, Mythtv automatically tries to pull up the correct tuner on the correct Video Source without further user intervention. 

In my own machine I have 2 video sources set up: Analog (for the PVR 150, and a couple of analog tuners on remote backends) and Digital (for the SD/HD QAM that the two 5500s receive). I imagine that if I were to go firewire for encrypted digital at some point, I would add a 3rd video source for the encrypted channels that only firewire could receive, and then let Mythtv and its scheduler sort it out as I scheduled recordings or punched in channel numbers, since that's basically the way Mythtv was designed to work. 

Cheers! :)

---

### Post by dmfrey on 2008-11-24
> Probably the best way to do this would be, the backend setup, to set up a new Video Source specifically for the pchdtv55500, call it QAM or whatever. Set the new Video Source to download listings from SchedulesDirect just like your other Video Sources do. In Input Connections, connect your DVB0 tuner (the 5500) to the Video Source QAM, then have the 5500 scan for channels on QAM. The 5500 will find what it found before, presumably all UNKNOWN.

I think this is where I might have been messing up.  I was trying to get another SchedulesDirect lineup and not specifying a new Video Source on the myth box.  I will try this out tonight and see how it goes.

One thing to clarify...The Firewire Connection does not allow viewing of encrypted channels.  I really wish it did, then I could integrate with OnDemand, and other digital content.  However, even though the box has a live firewire connection, it still cannot decode encrypted streams out of that connection.  The only solution in the foreseeable future is the HD box from Haupauge that will be supported in Myth .22 which allows you to hook up component outputs from the converter box.

Thanks for your help and ideas.

---

### Post by dmfrey on 2008-11-25
klc5555,
Thanks for your pointers.  This solved my issue.

---

### Post by rbsrao79 on 2008-12-10
Hi,
    I recently bought the same card and managed to setup with relative ease. I too however have a problem withthe lineup  program data. Here are the details

1. source : schedules_direct (comcast digital) 
2. scan for channels with dvb (I see my digital channels(eg. KTVU 2.1) however, the analog channels are marked as unknown
3. scan for channels with analog (that doesn't change the "unknown" channels
4. When I look at the database channel table, I see that the xmltvid has not been populated ALL my channels (there are about 136) Not surprisingly, mythfilldatabase fails to provide the program listings. 

 Is this because there is a discrepency between the channels scanned by my card and listing in schedules_direct ? Should I be looking for a different lineup ? Or is it normal for people to fill in this data manually ? Is there a script available to parse schedules_direct lineup report populate the table ?

my apologies for hijacking this thread, but I since original posters setup is almost identical to mine, I thought it was a good place.

---

### Post by klc5555 on 2008-12-10
> **rbsrao79 said:**
> Hi,
    I recently bought the same card and managed to setup with relative ease. I too however have a problem withthe lineup  program data. Here are the details

1. source : schedules_direct (comcast digital) 
2. scan for channels with dvb (I see my digital channels(eg. KTVU 2.1) however, the analog channels are marked as unknown
3. scan for channels with analog (that doesn't change the "unknown" channels
4. When I look at the database channel table, I see that the xmltvid has not been populated ALL my channels (there are about 136) Not surprisingly, mythfilldatabase fails to provide the program listings. 

 Is this because there is a discrepency between the channels scanned by my card and listing in schedules_direct ? Should I be looking for a different lineup ? Or is it normal for people to fill in this data manually ? Is there a script available to parse schedules_direct lineup report populate the table ?

my apologies for hijacking this thread, but I since original posters setup is almost identical to mine, I thought it was a good place.

Though the xmlid numbers are supposed to fill in automagically after the analog scan and mythfilldatabase, this has never actually happened in my own experience with Comcast analog. I've always had to fill in the appropriate info manually. 

Log into SchedulesDirect and print out your analog lineup, including the xmlid numbers. You can add these numbers to your "Unknown" channels, name these channels (if you wish) and --important!-- assign them callsigns that are different than the callsigns of their digital counterparts. This may be done from the backend's Channel Editor, or, from the frontend by simply tuning each channel in LiveTV and hitting the "e" shortcut to edit the contents of the channel. 

After this process, when mythfilldatabase is run (at its scheduled time or from a prompt), the lineup information will fill in starting with "tomorrow" (unless --refresh-today is explicitly set). 

A mild PITA with 50-odd analogs; more so in your case with 130-odd. But I've never gotten it to work properly with Comcast without entering the data.

Cheers! :)

---

### Post by rbsrao79 on 2008-12-10
Thanks. Funnily enough, although the call signs were correct for the digital channels, the xmltvids were missing.  The schedules_direct website does not show these channels at all. For example

The comcast listing in schedules_direct shows 
2 	10760 	KTVU 	KTVU

However, I don't see any entry for 2.1 KTVU-HD. Do they use the same xmltvid ?

Rajeev

---

### Post by klc5555 on 2008-12-11
> **rbsrao79 said:**
> Thanks. Funnily enough, although the call signs were correct for the digital channels, the xmltvids were missing.  The schedules_direct website does not show these channels at all. For example

The comcast listing in schedules_direct shows 
2 	10760 	KTVU 	KTVU

However, I don't see any entry for 2.1 KTVU-HD. Do they use the same xmltvid ?

Rajeev

Nearly all of the digital and HD variants of existing analog channels broadcast the same program schedule among all the variants. (My local PBS affiliate tried for a while to use different programming lineups for SD and HD, but eventually gave it up).

For all these variations of the same station broadcasting the same schedule, you use the same xmltvid number. Just be sure each variant is given a unique callsign, even if you make it up (e.g. KTVU, KTVU-HD, KTVU-DT1, KTVU-DT2, etc.). Because if the callsigns in mythconverg are not unique, Mythtv will become confused when one variant is scheduled to record, and will attempt to record from all variants simultaneously, often with unsatisfactory results.

Cheers!:)

---

