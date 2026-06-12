---
title: "Hauppauge PVR 150 and pcHDTV 5500"
date: 2008-07-28
forum: Mythbuntu
---

### Post by Angryartichoke on 2008-07-28
I'm having trouble setting up these cards to work nicely together. The PVR-150 is used to capture the analogue broadcast signals, while the 5500 is for the HD channels (QAM 256).

In mythtv, if only one card is functional, it works perfectly. If I try and set it up so that mythtv will have a group of broadcast channels for the PVR and QAM for the 5500, it goes black when I try and switch between them. When they are both installed, I can scan all their respective channels in in the backend setup. I'm stumped :confused:

I'm currently using DVB for the 5500, and MPEG2 for the PVR.

My best guess is that I need to modify /etc/modprobe.conf somehow because mythtv may be confused, but it doesn't exist (using Gutsy). Any help would be greatly appreciated.

---

### Post by ian dobson on 2008-07-28
Hi,

Try swapping the cards around in the PCI slots.

In ubuntu you don't have a modprobe.conf, rather you have the directory /etc/modprobe.d/ where you can create config files.

Regards
Ian Dobson

---

### Post by Angryartichoke on 2008-07-28
Sure, I'll try it this weekend when I can get back to work on the computer. Also, I found this thread: [http://www.uluga.ubuntuforums.org/showthread.php?p=1789411](http://www.uluga.ubuntuforums.org/showthread.php?p=1789411)

I think I might retry the steps listed in the thread. When I have time to work on it again, I'll post screen shots of the settings I have.

EDIT: Also, I just realized I have an old thread that is kind of similar to this. I hope it doesn't anger any of the mods.

---

### Post by Angryartichoke on 2008-08-04
I did some tinkering over the weekend and I believe I have pinpointed the problem.

I can switch between channels that use the same card perfectly. I can switch from the analogue to HD channels just fine as well. However, when I switch from the HD (pchdtv 5500) to the analogue (pvr) I get the black screen. When I hit 'Y' to manually change the input device, it works. 

My question is: How do I bind a capture card to a channel so that mythtv will ONLY use the pchdtv card for the QAM 256 and the pvr 150 ONLY for the broadcast channels?

Thanks in advance.

---

### Post by newlinux on 2008-08-04
Setup different video sources for both of them. Setup a QAM only video source and PVR only video source each only with the channels you want for each tuner.

---

### Post by Angryartichoke on 2008-08-04
Ok I'll try this next:
Use Schedules Direct for channels 2-71 for the PVR-150.
Use XMLTV id's for the 5500 with no listings grabber.

Now in order to bind them to a specific type (QAM or ATSC) would I change the "Channel frequency table" setting? Or will mythtv automatically bind them to whatever channels their listings dictate?

---

### Post by newlinux on 2008-08-04
I just created two different schedules direct lineups and associated them with different video sources. Then in input connections associate the appropriate video source with the appropriate tuner. My QAM providers transmits PSIP information for all the channels I care about so they matched channels in the Schedules direct lineup. If you input the xmltvids and those exist in your video source it will automatically bind them when you run mythfilldatabase.

---

### Post by Angryartichoke on 2008-08-04
Ok, I just went on the schedules direct website and created an additional lineup. Now I have "Comcast" and "Comcast - Digital" lineups. I'll update the mythtv backend next time I have access to it. Then I'll post my results. Thanks!

---

### Post by Angryartichoke on 2008-08-11
Ok, here's the update:
I successfully binded the digital and analogue lineups to each card. The analogue lineup comes fine with all the channel scheduling (excluding the channel names) when mythfilldatabase is ran. I can get the missing channel names/info by running "mythfilldatabase --refresh-all"

However, I don't get anything with the digital lineup. I know that Mythtv is rather finicky about the order and fashion you run mythfilldatabase in. I can't seem to get any info on the digital channels (local HDTV), but I know there's got to be some special order to input the info in Mythtv. I have the channels correctly selected in the lineup on Schedules Direct. Is there any documented process I can go about getting these without having to manually enter the XMLTVID's? Even simply linking a thread I've overlooked would help. Thanks.

---

### Post by newlinux on 2008-08-11
do your digital stations have the right the channel numbers via PSIP? If they don't have xmltvids or the right channel number there isn't an easy way for mythfilldatabase to map them to the schedules direct data. The only ones that work automatically for me are the ones that have PSIP channel numbers that match my schedules direct video source channel numbers. Any other ones I want I have to enter the channel #s or enter the xmltvid (once I figure out which channel it is). It is pretty quick to do using mythweb once you know what the channels are.

I don't have to do anything in any special order to get it to work, at least not that I noticed.

---

### Post by klc5555 on 2008-08-11
> **Angryartichoke said:**
> Ok, here's the update:
I successfully binded the digital and analogue lineups to each card. The analogue lineup comes fine with all the channel scheduling (excluding the channel names) when mythfilldatabase is ran. I can get the missing channel names/info by running "mythfilldatabase --refresh-all"

However, I don't get anything with the digital lineup. I know that Mythtv is rather finicky about the order and fashion you run mythfilldatabase in. I can't seem to get any info on the digital channels (local HDTV), but I know there's got to be some special order to input the info in Mythtv. I have the channels correctly selected in the lineup on Schedules Direct. Is there any documented process I can go about getting these without having to manually enter the XMLTVID's? Even simply linking a thread I've overlooked would help. Thanks.

I run a PVR 150 and 2 pcHDTV5500s (on Gutsy and Myth 0.20.2), and I found that after running the initial QAM-256 scan (on Comcast) I had to manually enter the XMLTVIDs for each found digital signal in order for mythfilldatabase to insert their lineup information. I haven't found a way around it. Digital signals I didn't intitially identify stayed "Unknown" permanently in the guide until I identified them and entered their XMLTVIDs. Then the next regularly scheduled mythfilldatabase picked them up. 

Also, where local stations have both SD and HD signals, I found needed to generate unique (although bogus) station "call signs" to differentiate the SD and HD versions, otherwise when setting up a recording on one of them, mythtv could not tell them apart,  and would insist on recording both versions simultaneously. Different channel assignments and names weren't enough, the call signs had to be unique.  

All the best.

---

### Post by Angryartichoke on 2008-08-11
Thank you both for the quick responses! I suppose adding the XMLTVID's isn't that difficult. I already created a spreadsheet from an earlier attempt. So here's what I'll do in my next attempt!

After the cards are installed and lineups/sources created and correctly configured:
1. Scan broadcast terrestrial channels on PVR-150
2. Scan QAM-256 with HD 5500
3. Manually enter XMLTVID's for the HD channels I want to keep
4. Exit mythbackendsetup and run mythfilldatabase when prompted
5. Run mythfilldatabase --refresh-all to get channel names for terrestrial channels
6. *magic and luck*
7. Open up the frontend with a fully working program guide! :)

---

### Post by newlinux on 2008-08-11
> **klc5555 said:**
> I run a PVR 150 and 2 pcHDTV5500s (on Gutsy and Myth 0.20.2), and I found that after running the initial QAM-256 scan (on Comcast) I had to manually enter the XMLTVIDs for each found digital signal in order for mythfilldatabase to insert their lineup information. I haven't found a way around it. Digital signals I didn't intitially identify stayed "Unknown" permanently in the guide until I identified them and entered their XMLTVIDs. Then the next regularly scheduled mythfilldatabase picked them up. 

The only way around it is if your provider transmits PSIP information, which you will know if they do if you look at the channel info and see a real station number and call sign as opposed to a station number that corresponds to the transponder.
I use comcast as well, and they started transmitting PSIP info for some stations a year ago. But this is different from region to region even with the same provider

> 
Also, where local stations have both SD and HD signals, I found needed to generate unique (although bogus) station "call signs" to differentiate the SD and HD versions, otherwise when setting up a recording on one of them, mythtv could not tell them apart,  and would insist on recording both versions simultaneously. Different channel assignments and names weren't enough, the call signs had to be unique.  

All the best.


All my local stations actually have a separate XMLTVID than their HD  counterpart.  This would fix your problem if you find them in your are. At the very least you could use digital OTA XMLID for your HD feed and the analog cable XMLTVID for your SD stations.

---

### Post by klc5555 on 2008-08-12
> **newlinux said:**
> The only way around it is if your provider transmits PSIP information, which you will know if they do if you look at the channel info and see a real station number and call sign as opposed to a station number that corresponds to the transponder.
I use comcast as well, and they started transmitting PSIP info for some stations a year ago. But this is different from region to region even with the same provider




All my local stations actually have a separate XMLTVID than their HD  counterpart.  This would fix your problem if you find them in your are. At the very least you could use digital OTA XMLID for your HD feed and the analog cable XMLTVID for your SD stations.

Ah, that would explain it then. My area is apparently not being transmitted PSIP info.

I use the XMLTVID numbers that SchedulesDirect indicates for the Comcast stations in my area, and I notice that, with two exceptions, all variants of any particular station --analog, digital, and HD if present-- have identical XMLTVID numbers in my SchedulesDirect listings. 

But since I had to assign channel numbers and add XMLTVID numbers to all the SD/HD stations anyway, assigning unique call signs was no particular extra effort, once I realized why duplicate recording listings kept popping up in "upcoming recordings", and that one of the duplicates could not be cancelled without killing them both.

Thanks! :)

---

### Post by Angryartichoke on 2008-08-18
Ok, I got it working perfectly. Here's how I did it, in case anyone else is stumped like I was:
1. Set up each card. PVR-150 as mpeg2 and the 5500 as a DVB card with the analogue option enabled. For my use, I didn't have anything binded to the analogue tuner on the 5500.
2. Create 2 different lineups on the schedules direct site. One with the broadcast channels (2-71) and one with the digital HD channels (whatever yours are). Make sure you create a list beforehand of the XMLTVID's of the HD channels you plan on watching. Sadly, there are more home shopping and spanish channels than the ones I wanted to keep, so a lot of deleting was needed.
3. Bind the lineups to the respective video sources and do a channel scan for the HD channels. Filter only the channels you want, and add the XMLTVID's to each. Then scan for the broadcast channels. Ensure the HD channels don't conflict with the broadcast channels (8_1 for example has the same ID as channel 8 )
4. Run mythfilldatabase on exit
5. run mythfilldatabase --refresh-all  (this will give their proper names and update the XMLTVID information)
6. Run mythfilldatabase again.
7. Enjoy :)

---

### Post by newlinux on 2008-08-18
Just a couple notes,

For 3, if you know your analog channels ahead of time you don't have to scan for them, you can just set them up in schedules direct and download them (fetch from listings). But the scan is pretty quick so it doesn't really matter.

you could replace 4,5, and 6 with just running mythfilldatabase --refresh-all, or you could replace 4 and 5 with mythfilldatabase --do-channel-updates.

There is no replacing number 7 :)

---

