---
title: "Mythbuntu DVB-t channel setup for friio (Japan)"
date: 2010-06-17
forum: Mythbuntu
---

### Post by IamHungry on 2010-06-17
Mythbuntu 10.04 
White USB Friio (No cable or BS)
Using the driver included in kernel


 I am working to get my ISDB-T friio digital receiver. The new driver in the kernel shows the device as a DVB device.  I also use the fuse_b25 decoder to get an unscrambled signal.  I am able to view the HD channel in mplayer with a channel.conf like this:
CH1:503142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_7_8:FEC_1_2:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:8192:8192:41010
CH2:515142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_7_8:FEC_1_2:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:8192:8192:41080
CH3:515142857:INVERSION_AUTO:BANDWIDTH_6_MHZ:FEC_7_8:FEC_1_2:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:8192:8192:41081

All three of these channels play fine in mplayer.  I can use "tab" to move between the different programs in the stream ( I think there are usualy 3).  I can also view the channels in VLC, but they usually don't play unless I specify the audio and video PID.

The beauty of the driver is that the device shows up as a DVB device and can be tuned as if it were one.  dvbsnoop shows me my streams are "unscrambled."

And yet, only the second two channels in that list will show up and work if I scan them into mythtv.  (There are of course more channels, but for clarity I chose these 3) The second two channels are, I believe on the same multiplex, and are "public access" channels, so may be encrypted differently.  They both play fine in mythtv.  But the first channel which will play just fine in mplayer and vlc will not get past LAM_ Partial Lock (no c).  

I cannot find any messages in the front or back end logs which hint at trouble.  Mythtv seems to think everything went fine, but the screen stays black with partial lock.  I spent quite a while going over the differences of the channels through PhpMyadmin, but can't find any differences.

I have used VLC to transcode the friio stream and give it to Myth through apache for a few years, but I think the new driver may make VLC an unnecessary step.

But I am not sure what to try next.  The other 8 OTA channels are the same, stuck at partial lock.  

Does anyone have any idea what else I could try to get Myth to recognize and lock on the channels?

---

