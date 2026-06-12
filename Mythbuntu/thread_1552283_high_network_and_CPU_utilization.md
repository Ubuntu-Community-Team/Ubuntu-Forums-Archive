---
title: "high network and CPU utilization"
date: 2010-08-13
forum: Mythbuntu
---

### Post by marcw on 2010-08-13
Myth noobie, but long time Ubuntu user,

Yesterday I apt-get installed Myth on my 32bit 10.04 desktop and am using it with my new HDHomeRun OTA mainly to be able to watch and record things without bothering the wife.  All went well.  I'm very impressed.  Now I know what people see in MythTV.  But now my computer is doing couple of strange things when I'm NOT watching TV.

ntop tells me my computer has been downloading lots of something from the HDHomeRun for several hours now.  While doing this, top tells me that mythbackend is using a fair chunk of CPU.  This has been constant for the past several hours.

What is mythbackend downloading from the HDHomeRun and when will it stop?

(I should probably add that so far I have changed only a few of the million config items from their default values.)

Thanks for any advice!!

---

### Post by ian dobson on 2010-08-13
Hi,

I don't know the HDHomeRun code paths but could your high load be caused by the EIT scanner? Where do you get your EPG data from?

If your EPG data is comming from the HDHomeRun then maybe try increasing the EIT timeout, this will reduce the number of mysql database updates/load on the system.

Regards
Ian Dobson

---

### Post by marcw on 2010-08-13
> **ian dobson said:**
> I don't know the HDHomeRun code paths but could your high load be caused by the EIT scanner? Where do you get your EPG data from?

If your EPG data is comming from the HDHomeRun then maybe try increasing the EIT timeout, this will reduce the number of mysql database updates/load on the system.

Thanks.  Your solution is partly accurate.  Myth's problem is indeed EIT related.  However, adjusting the timeout to the limit (both ways) made no difference.  But when I turned off EIT altogether the network chatter and CPU issues went away.

I'm quite content to leave EIT turned off but now the problem becomes how to insure that the guide's listings are up to date.

Any ideas?

---

### Post by nickrout on 2010-08-13
where are you? If in North America then Schedules direct is your best bet. If not there may be a xmltv solution.

---

### Post by ian dobson on 2010-08-14
> **marcw said:**
> Thanks.  Your solution is partly accurate.  Myth's problem is indeed EIT related.  However, adjusting the timeout to the limit (both ways) made no difference.  But when I turned off EIT altogether the network chatter and CPU issues went away.

I'm quite content to leave EIT turned off but now the problem becomes how to insure that the guide's listings are up to date.

Any ideas?

So how High did you set the EIT timeout? On my backend I've set it to 6 (minutes). What the value means is: The EIT scanner tunes to a multiplex and reads the EPG data updating a temporary table in the mysql db. After 6 minutes (in my case) it copies the new data into the programs db (this is what causes the heavy load), then tunes to the next channel. 

Can you give us abit more information about your hardware (CPU,Ram,Harddisk etc), it could be you don't have enough ram/the cpu is abit slow etc.

Regards
Ian Dobson

---

### Post by marcw on 2010-08-14
> **ian dobson said:**
> So how High did you set the EIT timeout? 

The default was 5.  I've set it at 1, 5, 10, 15.  Behavior was the same for all.


> **ian dobson said:**
> Can you give us abit more information about your hardware (CPU,Ram,Harddisk etc)

desktop:
CPU - dual core AMD 6000+ (1Ghz)
Mem - 4Gb (rarely swapped)
HDD - 160GB (105GB free)
Vid - nVidia 8500 512MB vdpau enabled

---

### Post by ian dobson on 2010-08-14
Hi,

Did you restart the backend after changing the value?

Regards
Ian Dobson

---

### Post by marcw on 2010-08-14
> **ian dobson said:**
> Did you restart the backend after changing the value?

Yes.  Every time I run mythtv-setup I am prompted to have mythbackend stopped for me.  And then when I exit mythtv-setup, mythbackend auto starts.  That's how Ubuntu installed it.  Pretty slick.

Back to my problem - the constant network chatter with HDHomeRun and moderate CPU usage when EIT is enabled.  The network chatter I speak of hovers around 10-11 mbps - the same as if I was watching TV.  Likewise, the CPU load avg which hovers around 1.00.

Here's something that would be handy to know - how log should an EIT scan take for 20 OTA channels?

---

### Post by ian dobson on 2010-08-14
Hi,

The EIT data is encoded in the data stream from the HDHomeRun so mythtv has to read the entire stream to be able to pull the EPG data from it.

It takes afew minutes per multiplex to get all the EPG data.

Maybe you can use schedules direct to get the EPG data or maybe some other xmltv grabber.

Regards
Ian Dobson

---

### Post by marcw on 2010-08-14
Doh, I probably should've mentioned this before.

It's not that I'm not getting EPG data.  I am.  The EPG is stiing there right now with about 2 weeks worth.  I just don't know how long it took to get all of that.

Maybe I should just enable EIT once a week or so and let it run for a couple hours.

---

### Post by ian dobson on 2010-08-14
Hi,

Does the HDHomeRun have a webinterface that contains the EPG data? If so then it might be possible to write a simple xmltv grabber that grabs the program page and outputs xmltv that mythtv can read.

Regards
Ian Dobson

---

### Post by bgiannes on 2010-11-23
i fix this problem on my system by install a second network card (only need a cheap 10/100 NIC) in the mythtv-backend machine and connect directly to the hdhomerun.

I install dhcp services on the backend machine to setup the hdhomerun with a fixed IP on a different subnet as the main home network.

---

