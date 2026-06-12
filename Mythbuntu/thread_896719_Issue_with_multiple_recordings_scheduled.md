---
title: "Issue with multiple recordings scheduled"
date: 2008-08-21
forum: Mythbuntu
---

### Post by kreegor on 2008-08-21
I have two tuners. A Dvico Fusion HDTV DVB-T Plus and a Leadtek DTV1000T. When I had installed mythbuntu 7.10 I was able to record 2 channels simultaneously via the program guide but now since I clean installed 8.04 I can't do this anymore. For some reason the scheduler says that there is a conflict even though I have 2 programs scheduled on different channels with a slight over lap in time.

The weirdest thing is that I can watch one channel, start recording that by pressing record on the remote, exit to the menu and use the other tuner to watch a different channel and record that.

Anyone have any idea what is going on? This is really starting to drive me crazy

---

### Post by ian dobson on 2008-08-21
Hi,

I have 4 tuners (2 digital and 2 Analog) in my backend and I can schedule multiple programs at the same time, no problems. I know that doesn't help you much but it appears to work.

It sounds as if you've got a problem with the database configuration. Maybe my database check script might provide abit more info. Have a look here for the forum post :- [http://ubuntuforums.org/showthread.php?t=885411](http://ubuntuforums.org/showthread.php?t=885411)

Regards
Ian Dobson

---

### Post by kreegor on 2008-08-21
Thanks. I will have a look at that. I should add that I upgraded from 7.10 to 8.04 via the updater in mythbuntu and it all worked great.

I think this issue started about 2 weeks ago. I bought a new PSU and had to take one of the cards out to put power to the motherboard. Ever since then it started having issues with recording simultaneously.

---

### Post by kreegor on 2008-08-21
> **ian dobson said:**
> Have a look here for the forum post :- [http://ubuntuforums.org/showthread.php?t=885411](http://ubuntuforums.org/showthread.php?t=885411)

Regards
Ian Dobson

Hey Ian. I don't know how to execute that script. I have made it executable but when I run it I get this

```
DBI connect('mythconverg:MythBox','craig',...) failed: Can't connect to MySQL server on 'MythBox' (111) at CheckMythDB.pl line 394
Couldn't connect to database: Can't connect to MySQL server on 'MythBox' (111) at CheckMythDB.pl line 394.

```

---

### Post by newlinux on 2008-08-21
Do these two tuners have the same video source?

---

### Post by kreegor on 2008-08-21
> **newlinux said:**
> Do these two tuners have the same video source?

Hey newlinux. My antenna is plugged into the DTV1000T with another coax cable going from the Ant Out of that card to the Ant In on the DVICO card. I have different sources for each card. One called Aus (I'm in Australia) and the other Aus1 (very original).

This has worked for me for the last year and a half, it's only been in the last 2 weeks since I changed my PSU and had to take one of the cards out that it has stopped. Like I said, I can watch one channel and hit record to start recording. Exit and go back to watch tv on the other tuner and other source, hit record and that records too. Next time I leave and go back to watch tv it says that tuner 1 is busy with <insert first recording> and tuner 2 is busy with <second recording> and I have the options of watching either of these recordings or going back to the menu. So I know it can use both the tuners and the sources at the same time but I cannot schedule 2 recordings at the same time on 2 different channels without there being a conflict.

I am wondering if it has something to do with the input source in the input connections menu. When I assign Aus to DVB0 and go to next it has a menu that asks to assign input groups. These are all generic. Would it have anything to do with that? I have tried them as all generic (I am pretty sure that is what it was in the first place), I have tried the first group as generic and the second as something else, i have tired the second group as generic and the first as something else, I have tried them all as something different,.... you name it I have tried the combination.

So yeah, any help would be very much appreciated because I haven't had much sleep the last 2 days/nights.

---

### Post by newlinux on 2008-08-21
The reason I asked was to double check that the two programs you are trying to record are available on the 2 different respective inputs you are trying to record on (I'm sure you've already checked this, but I thought I'd mention it anyway. If you only had 1 video source it would be a moot point). The inputs  should all be in the Generic group, as far as I know since they don't have any conflicts with running at the same time (this is the way mine are setup).

have you tried specifying the specific tuner when scheduling a recording (assigning 1 recording to one tuner and the other to the other tuner?). You shouldn't have to, but I'm curious if that will work.

---

### Post by kreegor on 2008-08-21
> **newlinux said:**
> have you tried specifying the specific tuner when scheduling a recording (assigning 1 recording to one tuner and the other to the other tuner?). You shouldn't have to, but I'm curious if that will work.

Yeah I have tried that and it still conflicts :(

EDIT: I think I will reset the BIOS, double check all the internal connections (PSU etc) to make sure it isn't another bit of hardware affecting it.... I can't see how it would be though

---

### Post by ian dobson on 2008-08-21
Hi,

If you start my script with the -H option it'll display help. For some reason the script can't connect to the MySQL server using the information it grabbed from the mysql.txt file.

You could try manually setting the Host,UserName,Password using the -h Host -u User -p Password options.

Regards
Ian Dobson

---

### Post by kreegor on 2008-08-22
Thanks Ian. I will try that when I get home.

I have found something else. It is my leadtek card (or at least the leadtek source) that seems to be having issues. I schedule a recording via mythweb using the guide and set it to record on the leadtek card. Then I schedule another one at the same time and set it to the Dvico card. The Leadtek recording says there is a conflict.

So I do the opposite. Set the Dvico card first and then the leadtek one and again it comes up again with the conflict. I will have to borrow my bro in laws card to see if it is the card or something else.

---

### Post by ian dobson on 2008-08-23
> **kreegor said:**
> Hey Ian. I don't know how to execute that script. I have made it executable but when I run it I get this

```
DBI connect('mythconverg:MythBox','craig',...) failed: Can't connect to MySQL server on 'MythBox' (111) at CheckMythDB.pl line 394
Couldn't connect to database: Can't connect to MySQL server on 'MythBox' (111) at CheckMythDB.pl line 394.

```

Sorry it's taken so long to get back to you, things have been abit crazy at work for the last few days.

I've updated the script abit so that it uses the mysql.txt defined SQLhost name, that should fix your problem. I'm still interested in seeing what's causing your problem, but I'll be out of the country/no internet next week so it might take a while for me to answer any questions you have.

Regards
Ian Dobson

---

### Post by kreegor on 2008-08-25
Thanks Ian.

I didn't get a chance to run that script because I managed to fix the problem. I am still not sure why it was happening though.

Basically I borrowed another Leadtek DTV1000 T from my brother in law. Put that in my box and the 2 tuners worked fine. No scheduling issues at all. I thought I would test the Dvico card in his machine to see if the card was stuffed but it worked fine! I set the card up in the backend tried to schedule two recordings at the same time on different channels and it worked fine. It didn't conflict and it recorded both. So I bought another Leadtek card but still not sure what I will do with the Dvico card.

Does anyone know how much they are worth second hand? Might sell it somewhere.

Cheers for all your help though guys. Much appreciated

---

### Post by kreegor on 2008-08-26
Hmmm scratch that. After a few reboots and a few days it has started conflicting again. I now have 2 of exactly the same cards in the machine.

This is utter crap. It must be a hardware issue... maybe my motherboard or something but I don't understand it at all :confused: :confused:

---

### Post by volkswagner on 2008-08-26
I have seen where folks fixed this sort of oddness by only deleting all cards in the backend and adding them back.  It is not elegant and increases the card number but it may be worth a shot.

Do you have any relevant information in the backend log when the conflict occurs?

Have you run a database repair?

---

### Post by kreegor on 2008-08-26
Yeah I tried that and also ran a database optimisation and repair and it worked for a few hours and then stopped again.

It has the issue even from a clean install and I originally thought it was a power issue as it started when I changed my PSU from a generic 420W to a Antec Earthwatts 380W, but I put in my bro in laws Corsair VX450 and it still did the same thing.

I am happy for people to connect to it via VNC and/or Putty to see if they can work it out because I am puzzled by it.

EDIT: I have found out that it is only certain channel combinations that register a conflict. I am in Australia so not sure if this will be helpful but I have a list of combo's that don't work:

[LIST]
[*]9 and 7 conflict - 7 shows the conflict
[*]9 and ABC conflict - ABC is the conflict
[*]9 and SBS conflict - SBS is the conflict
[*]9 and SBS News conflict - 9 is the conflict
[/LIST]

channel 9 works with channel 10 though but it seems to me that 9 is the problem... so far at least... I will build on the list when I have some more time to play with it

---

### Post by ian dobson on 2008-08-27
Hi,

It sounds like something is really badly wrong with your multiplex table (You can record upto 3 programs on the same tuner if all the channels are on the same multiplex).

Are you sure the system is actually seeing both tuner cards?
What do you see in the mythbackend log when myth-backend starts and you see conflicts? If you see something like "problem with tuner XXX" then you have a hardware problem of some sort.

Regards
Ian Dobson

---

### Post by kreegor on 2008-08-27
Hi. This is the latest output in the backend log when I schedule and get a conflict

```
2008-08-28 07:42:47.672 MainServer::HandleAnnounce Monitor
2008-08-28 07:42:47.673 adding: craig-desktop as a client (events: 0)
2008-08-28 07:42:48.525 MainServer::HandleAnnounce Monitor
2008-08-28 07:42:48.526 adding: craig-desktop as a client (events: 0)
2008-08-28 07:42:48.950 MainServer::HandleAnnounce Monitor
2008-08-28 07:42:48.952 adding: craig-desktop as a client (events: 0)
2008-08-28 07:42:51.752 MainServer::HandleAnnounce Monitor
2008-08-28 07:42:51.755 adding: craig-desktop as a client (events: 0)
2008-08-28 07:42:51.787 Reschedule requested for id 76.
2008-08-28 07:42:51.815 Scheduled 1 items in 0.0 = 0.01 match + 0.02 place
2008-08-28 07:42:51.828 scheduler: Scheduled items: Scheduled 1 items in 0.0 = 0.01 match + 0.02 place
2008-08-28 07:42:53.748 MainServer::HandleAnnounce Monitor
2008-08-28 07:42:53.755 adding: craig-desktop as a client (events: 0)
2008-08-28 07:42:55.019 MainServer::HandleAnnounce Monitor
2008-08-28 07:42:55.022 adding: craig-desktop as a client (events: 0)
2008-08-28 07:42:57.630 MainServer::HandleAnnounce Monitor
2008-08-28 07:42:57.633 adding: craig-desktop as a client (events: 0)
2008-08-28 07:42:57.665 Reschedule requested for id 77.
2008-08-28 07:42:57.698 Scheduled 2 items in 0.0 = 0.01 match + 0.02 place
2008-08-28 07:42:57.705 scheduler: Scheduled items: Scheduled 2 items in 0.0 = 0.01 match + 0.02 place
2008-08-28 07:42:59.941 MainServer::HandleAnnounce Monitor
2008-08-28 07:42:59.950 adding: craig-desktop as a client (events: 0)
2008-08-28 07:43:00.668 MainServer::HandleAnnounce Monitor
2008-08-28 07:43:00.670 adding: craig-desktop as a client (events: 0)
2008-08-28 07:43:01.322 MainServer::HandleAnnounce Monitor
2008-08-28 07:43:01.325 adding: craig-desktop as a client (events: 0)
```

and this is the output I get from a dmesg

```
[   36.440191] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 20 (level, low) -> IRQ 21
[   36.440243] cx88[0]: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21,autodetected]
[   36.440246] cx88[0]: TV tuner type 4, Radio tuner type -1
[   36.609932] cx88[0]/0: found at 0000:04:00.0, rev: 5, irq: 21, latency: 32, mmio: 0xea000000
[   36.610021] cx88[0]/0: registered device video0 [v4l2]
[   36.610055] cx88[0]/0: registered device vbi0
[   36.610112] cx88[0]/2: cx2388x 8802 Driver Manager
[   36.610129] ACPI: PCI Interrupt 0000:04:00.2[A] -> GSI 20 (level, low) -> IRQ 21
[   36.610138] cx88[0]/2: found at 0000:04:00.2, rev: 5, irq: 21, latency: 32, mmio: 0xeb000000
[   36.610198] cx88[1]: subsystem: 107d:665f, board: WinFast DTV1000-T [card=35,autodetected]
[   36.610201] cx88[1]: TV tuner type 4, Radio tuner type -1
[   36.779421] input: cx88 IR (WinFast DTV1000-T) as /devices/pci0000:00/0000:00:1e.0/0000:04:02.2/input/input4
[   36.824817] cx88[1]/2: cx2388x 8802 Driver Manager
[   36.824836] ACPI: PCI Interrupt 0000:04:02.2[A] -> GSI 18 (level, low) -> IRQ 20
[   36.824846] cx88[1]/2: found at 0000:04:02.2, rev: 5, irq: 20, latency: 32, mmio: 0xed000000
[   36.824896] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.824904] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   36.825035] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   36.826041] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 18 (level, low) -> IRQ 20
[   36.826052] cx88[1]/0: found at 0000:04:02.0, rev: 5, irq: 20, latency: 32, mmio: 0xec000000
[   36.826097] cx88[1]/0: registered device video1 [v4l2]
[   36.826119] cx88[1]/0: registered device vbi1
[   36.826251] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   36.826267] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   36.863554] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   36.913649] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   36.913653] cx88/2: registering cx8802 driver, type: dvb access: shared
[   36.913657] cx88[0]/2: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21]
[   36.913660] cx88[0]/2: cx2388x based DVB/ATSC card
[   37.013506] DVB: registering new adapter (cx88[0])
[   37.013510] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[   37.013748] cx88[1]/2: subsystem: 107d:665f, board: WinFast DTV1000-T [card=35]
[   37.013750] cx88[1]/2: cx2388x based DVB/ATSC card
[   37.047178] DVB: registering new adapter (cx88[1])
[   37.047183] DVB: registering frontend 1 (Conexant CX22702 DVB-T)...
[   37.493621] lp0: using parport0 (interrupt-driven).
[   37.752656] Adding 6072528k swap on /dev/sda5.  Priority:-1 extents:1 across:6072528k
[   38.455502] EXT3 FS on sda1, internal journal
[   39.991247] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.826769] No dock devices found.
[   42.975829] NET: Registered protocol family 10
[   42.976107] lo: Disabled Privacy Extensions
[   44.898509] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   44.898514] apm: disabled - APM is not SMP safe.
[   52.990477] r8169: eth0: link down
[   52.993366] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   69.854816] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[   69.927179] NET: Registered protocol family 17
[   87.609979] ath0: no IPv6 routers present

```

I don't know what I am looking for and if you have any other suggestions of what to run please let me know.

Thanks

---

### Post by Lindsay.Mathieson on 2008-08-27
> **kreegor said:**
> It has the issue even from a clean install and I originally thought it was a power issue as it started when I changed my PSU from a generic 420W to a Antec Earthwatts 380W, but I put in my bro in laws Corsair VX450 and it still did the same thing.

Hi kreegor - I had a very similar configuration (Antect Earthwatts 380 & WinFast1000T) and I'm in Australia (Brisbane).

I discovered my Earthwatts was putting out a *lot* of inteference that was wrecking my reception on Channel 7,  BE over 15000. I fixed it by replacing it with a Corsair vx450W, but you've tried that haven't you :)

Some questions:
[LIST]
[*]What EPG grabber are you using - shepherd? (recommended)
[*]When your tuners are playing up have you checked what adaptors you have under /dev/dvb, you should have one per tuner.
[/LIST]

Also I'd recommend doing a:
[LIST=1]
[*]Delete *ALL* tuners
[*]Delete *All* Video Sources
[/LIST]
And recreate them from scratch. Its the safest way to get past DB screwups.

---

### Post by kreegor on 2008-08-27
> **Lindsay.Mathieson said:**
> Hi kreegor - I had a very similar configuration (Antect Earthwatts 380 & WinFast1000T) and I'm in Australia (Brisbane).

I discovered my Earthwatts was putting out a *lot* of inteference that was wrecking my reception on Channel 7,  BE over 15000. I fixed it by replacing it with a Corsair vx450W, but you've tried that haven't you :)

Some questions:
[LIST]
[*]What EPG grabber are you using - shepherd? (recommended)
[*]When your tuners are playing up have you checked what adaptors you have under /dev/dvb, you should have one per tuner.
[/LIST]

Also I'd recommend doing a:
[LIST=1]
[*]Delete *ALL* tuners
[*]Delete *All* Video Sources
[/LIST]
And recreate them from scratch. Its the safest way to get past DB screwups.

Hey thanks for the reply. I am not having an issue with reception at all since changing the PSU. Reception for every channel is still crystal clear. I am using shepherd for my EPG but I haven't looked at /dev/dvb to see what is going on there. I just wish I could use Putty at work to check that :(

I have removed all tuners and all video sources a few times already. I even did a few clean installs of mythbuntu 8.04 and the issue was still there. I will borrow the VX450 again and do a bit more fiddling around and see if that does change anything but I don't think it is that.

It is just weird that channel 7 and channel 9 clash when setting a scheduled recording. To me that sounds like a software issue.

I will post the results in /dev/dvb later on today.

---

### Post by volkswagner on 2008-08-30
Silly question,

Have you verified in system status that both tuners show as available?

---

### Post by kreegor on 2008-08-31
> **volkswagner said:**
> Silly question,

Have you verified in system status that both tuners show as available?

No I haven't. how do I do that?

---

### Post by volkswagner on 2008-08-31
> **kreegor said:**
> No I haven't. how do I do that?

From the frontend:
>information center>system status>tuner status

---

### Post by kreegor on 2008-09-01
Both the tuners are available. I think it might be an issue with the source's. I will try and get that sorted out tonight

---

### Post by Lindsay.Mathieson on 2008-09-01
> **kreegor said:**
> Both the tuners are available. I think it might be an issue with the source's. I will try and get that sorted out tonight

Sources? you only need one video source which is shared between the tuners. If you have two sources that could be the cause of the problem.

---

### Post by kreegor on 2008-09-01
> **Lindsay.Mathieson said:**
> Sources? you only need one video source which is shared between the tuners. If you have two sources that could be the cause of the problem.

Oh ok. I have always had 1 source per card and this is the first time I have had an issue in about a year. I will try only 1 source and see what happens.

---

### Post by kreegor on 2008-09-01
Woo-freaking-hoo! Having 1 source and setting that to both cards works great! Thank you! I am a bit puzzled though because I have always had a seperate source for each card and never had a problem before this.... but it's fixed now and that is all that matters.

Now I just have to work out why it randomly crashes to desktop when I play DVD's :)

---

### Post by Lindsay.Mathieson on 2008-09-01
> **kreegor said:**
> Woo-freaking-hoo! Having 1 source and setting that to both cards works great! 

Excellent! 

> I am a bit puzzled though because I have always had a seperate source for each card and never had a problem before this.... but it's fixed now and that is all that matters.

It could be down to minor changes in Shepherd or MythTV.

> Now I just have to work out why it randomly crashes to desktop when I play DVD's :)


I get that too :( The higher end DVD's seem to be more problematic - Lord of the Rings (Extended Version) crashes very fast unless I invoke the DVD Root menu ASAP. Have you tried that?

mplayer seems more stable in that regard but its not nearly so well integrated as the internal player :(

---

### Post by kreegor on 2008-09-01
> **Lindsay.Mathieson said:**
> It could be down to minor changes in Shepherd or MythTV.

I don't know. It did it when I was testing with just the on air guide and also when I tried a clean install of Mythbuntu 7.10 (I was getting desperate). Who knows, maybe I just got lucky the first time.

> **Lindsay.Mathieson said:**
> 
I get that too :( The higher end DVD's seem to be more problematic - Lord of the Rings (Extended Version) crashes very fast unless I invoke the DVD Root menu ASAP. Have you tried that?

mplayer seems more stable in that regard but its not nearly so well integrated as the internal player :(

Yeah I have tried mplayer. Not a huge fan of it for DVD's. I have found a few places that have some scripts that will auto start the frontend again if it stops. That way I don't have to whip out the keyboard and  my wife doesn't have to reboot the machine when it happens.

Is there a way to auto start a DVD at the root menu? That would make things a lot simpler

---

### Post by Lindsay.Mathieson on 2008-09-01
> **kreegor said:**
> Is there a way to auto start a DVD at the root menu? That would make things a lot simpler

I don't know - the [Myth Wiki Internal Player]("http://www.mythtv.org/wiki/index.php/Internal_player") doesn't list any options for it.

I'll take it to the mail list.

---

### Post by Lindsay.Mathieson on 2008-09-01
Hmmm according to this [WhirlPool thread]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/1028498.html") we're probably out of luck but it should be an option in Myth 0.22 or if we want we can patch the 0.21 sources and rebuild it. Not keen on that myself, I can wait.

---

### Post by kreegor on 2008-09-01
> **Lindsay.Mathieson said:**
> Not keen on that myself, I can wait.

Same. I have 'broken' the box too many times recently that if I 'break' it again my wife will kick my butt :) I will wait too

---

### Post by Lindsay.Mathieson on 2008-09-01
> **kreegor said:**
> same. I have 'broken' the box too many times recently that if i 'break' it again my wife will kick my butt :) i will wait too

not to touch teh pvr on painz oz deth okthxbye

---

### Post by kreegor on 2008-09-01
Not when there are 'important' things to watch. Chicks watch the worst crap

---

### Post by Lindsay.Mathieson on 2008-09-02
Heh. I've only got crap wireless access to the mythbox but I'm stringing cable this weekend so I can play video from it on my Desktop :)

Having said that my SO and I actually have very similar tastes - she loves SciFi, Fantasy and offbeat shows. Australia's Top Physic was the only thing I really puked over.

---

### Post by kreegor on 2008-09-02
Yeah mines connected via wireless. I hate wireless.....!

Just one other question that is back on topic. I added the single source to each card and I can schedule recordings fine but now one of the cards can't lock channels. To watch tv wife has to switch inputs in live tv.

All I remember doing is:
[LIST=1]
[*]Deleting both sources and then creating one source to rule them all
[*]Setting that source for each tuner card
[*]Scanning for channels
[*]Running shepherd again to get some EPG data
[*]Changing settings so a recording doesn't interrupt live TV
[*]Rebooting
[*]Running out the door to catch the bus
[/LIST]

---

### Post by Lindsay.Mathieson on 2008-09-02
> **kreegor said:**
> 
[LIST]
[*]Running out the door to catch the bus
[/LIST]

There's your problem right there :) Bet you're popular

Just to clarify - the first tuner won't lock at all, not for scheduled recordings or Live TV?

Did you delete all channels before scanning?

What part of Australia are you in?

To diagnose I'd check a scann with the tuner in question can get a lock, eg.

```
scan au-<Locations>
```

---

### Post by kreegor on 2008-09-02
> **Lindsay.Mathieson said:**
> Just to clarify - the first tuner won't lock at all, not for scheduled recordings or Live TV?


I'm not sure. I am at work at the moment and no one is home to test so I will do that when I get home. I would do it via vnc or putty but the wireless on my mythbox has disconnected and obviously hasn't been able to reconnect. Freaking wireless!

> **Lindsay.Mathieson said:**
> 
Did you delete all channels before scanning?


Yeah. I deleted every source I had and then created a new one from scratch.

> **Lindsay.Mathieson said:**
> 
What part of Australia are you in?


Adelaide... Please don't hold that against me ;)

> **Lindsay.Mathieson said:**
> 
To diagnose I'd check a scann with the tuner in question can get a lock, eg.

```
scan au-<Locations>
```

Cool. Will do when I get home.

---

### Post by Lindsay.Mathieson on 2008-09-02
> **kreegor said:**
> I'm not sure. I am at work at the moment and no one is home to test so I will do that when I get home. I would do it via vnc or putty but the wireless on my mythbox has disconnected and obviously hasn't been able to reconnect. Freaking wireless!

Word, have the same problem with my wireless - if the router restarts then I have to reboot the mythbox for it to reconnect.

Coincidently I am at work too, puttied onto my home box. I love MythWeb.

> Yeah. I deleted every source I had and then created a new one from scratch.

I don't think that deletes the channels (could be wrong). There is a "Delete Channels" option in the Channel Editor (mythtv-setup)



> Adelaide... Please don't hold that against me ;)

*::sympathy::* :)

Actually I have nothing against Adelaide, never been there. I'm originally from NZ - please don't beat me!

Regards the scanning - tell me to suck eggs if you already know this ...

scan is not installed by default:
```
sudo apt-get install dvb-utils
```

au-Adelaide is installed at
```
/usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Adelaide
```
Just copy it local.

To scan the first adaptor:
```
scan -a 0 au-Adelaide
```
Second:
```
scan -a 1 au-Adelaide
```
etc.

Also LiveTV is not smart enough to use a different adaptor if the first one is tied up recording something but has a multirec channel free :(

---

### Post by kreegor on 2008-09-02
Both tuners say this

> scanning au-Adelaide
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter1/frontend0': 16 Device or resource busy


Even though neither of them are being used.

---

### Post by Lindsay.Mathieson on 2008-09-02
By default mythbackend has them permanently locked. You'll need to stop it first

```
sudo /etc/init.d/mythtv-backend stop
```

---

### Post by kreegor on 2008-09-02
Doh! I thought that would have been the case

Tuner0:

```
scanning au-Adelaide
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 226500000 1 3 9 3 1 1 0
initial transponder 177500000 1 2 9 3 1 1 0
initial transponder 191625000 1 3 9 3 1 1 0
initial transponder 219500000 1 3 9 3 1 1 0
initial transponder 564500000 1 2 9 3 1 2 0
>>> tune to: 226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TR                                                                             ANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
0x0000 0x0250: pmt_pid 0x0102 ABC -- ABC HDTV (running)
0x0000 0x0251: pmt_pid 0x0100 ABC -- ABC1 (running)
0x0000 0x0252: pmt_pid 0x0101 ABC -- ABC2 (running)
0x0000 0x0253: pmt_pid 0x0103 ABC -- ABC1 (running)
0x0000 0x0254: pmt_pid 0x0104 ABC -- ABC3 (running)
0x0000 0x0256: pmt_pid 0x0105 ABC -- ABC DiG Radio (running)
0x0000 0x0257: pmt_pid 0x0106 ABC -- ABC DiG Jazz (running)
Network Name 'ABC Adelaide'
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TR                                                                             ANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
0x0000 0x0550: pmt_pid 0x0500 Seven Network -- 7 Digital (running)
0x0000 0x0554: pmt_pid 0x0540 Network Seven -- 7 HD Digital (running)
0x0000 0x0551: pmt_pid 0x0510 Seven Network -- 7 Digital 1 (running)
0x0000 0x0552: pmt_pid 0x0520 Seven Network -- 7 Digital 2 (running)
0x0000 0x0553: pmt_pid 0x0530 Seven Network -- 7 Digital 3 (running)
Network Name 'Seven Network'
>>> tune to: 191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TR                                                                             ANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
0x0000 0x0451: pmt_pid 0x0000 Nine Network -- NINE Digital (running)
0x0000 0x0458: pmt_pid 0x0000 Nine Network -- NINE HD (running)
Network Name 'Nine Network'
>>> tune to: 219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
Network Name 'Network TEN'
0x0000 0x0651: pmt_pid 0x0101 Ten Adelaide -- TEN HD (running)
0x0000 0x0655: pmt_pid 0x0100 Ten Adelaide -- TEN Digital (running)
0x0000 0x0658: pmt_pid 0x0107 Ten Adelaide -- TEN HD (running)
>>> tune to: 564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
0x0000 0x0340: pmt_pid 0x0400 SBS -- SBS HD (running)
0x0000 0x0341: pmt_pid 0x0401 SBS -- SBS (running)
0x0000 0x0342: pmt_pid 0x0402 SBS -- SBS NEWS (running)
0x0000 0x0343: pmt_pid 0x0408 SBS -- SBS 2 (running)
0x0000 0x034e: pmt_pid 0x0403 SBS -- SBS RADIO 1 (running)
0x0000 0x034f: pmt_pid 0x0404 SBS -- SBS RADIO 2 (running)
Network Name 'SBS NETWORK'
>>> tune to: 571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 585625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 585625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (23 services)
ABC HDTV:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2314:0:592
ABC1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:593
ABC2:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2307:2308:594
ABC1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:595
ABC3:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:596
ABC DiG Radio:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:2317:598
ABC DiG Jazz:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:2318:599
7 Digital:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1360
7 Digital 1:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1361
7 Digital 2:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1362
7 Digital 3:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1363
7 HD Digital:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1345:0:1364
NINE Digital:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1105
NINE HD:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:513:0:1112
TEN HD:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:0:1617
TEN Digital:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1621
TEN HD:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:0:1624
SBS HD:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:832
SBS:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:833
SBS NEWS:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:162:83:834
SBS 2:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:835
SBS RADIO 1:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:201:846
SBS RADIO 2:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:202:847
Done.
```

Tuner1:
```
scanning au-Adelaide
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
initial transponder 226500000 1 3 9 3 1 1 0
initial transponder 177500000 1 2 9 3 1 1 0
initial transponder 191625000 1 3 9 3 1 1 0
initial transponder 219500000 1 3 9 3 1 1 0
initial transponder 564500000 1 2 9 3 1 2 0
>>> tune to: 226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
0x0000 0x0250: pmt_pid 0x0102 ABC -- ABC HDTV (running)
0x0000 0x0251: pmt_pid 0x0100 ABC -- ABC1 (running)
0x0000 0x0252: pmt_pid 0x0101 ABC -- ABC2 (running)
0x0000 0x0253: pmt_pid 0x0103 ABC -- ABC1 (running)
0x0000 0x0254: pmt_pid 0x0104 ABC -- ABC3 (running)
0x0000 0x0256: pmt_pid 0x0105 ABC -- ABC DiG Radio (running)
0x0000 0x0257: pmt_pid 0x0106 ABC -- ABC DiG Jazz (running)
Network Name 'ABC Adelaide'
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
0x0000 0x0550: pmt_pid 0x0500 Seven Network -- 7 Digital (running)
0x0000 0x0554: pmt_pid 0x0540 Network Seven -- 7 HD Digital (running)
0x0000 0x0551: pmt_pid 0x0510 Seven Network -- 7 Digital 1 (running)
0x0000 0x0552: pmt_pid 0x0520 Seven Network -- 7 Digital 2 (running)
0x0000 0x0553: pmt_pid 0x0530 Seven Network -- 7 Digital 3 (running)
Network Name 'Seven Network'
>>> tune to: 191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
Network Name 'Nine Network'
0x0000 0x0451: pmt_pid 0x0101 Nine Network -- NINE Digital (running)
0x0000 0x0458: pmt_pid 0x0100 Nine Network -- NINE HD (running)
>>> tune to: 219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
0x0000 0x0651: pmt_pid 0x0101 Ten Adelaide -- TEN HD (running)
0x0000 0x0655: pmt_pid 0x0100 Ten Adelaide -- TEN Digital (running)
0x0000 0x0658: pmt_pid 0x0107 Ten Adelaide -- TEN HD (running)
Network Name 'Network TEN'
>>> tune to: 564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
0x0000 0x0340: pmt_pid 0x0400 SBS -- SBS HD (running)
0x0000 0x0341: pmt_pid 0x0401 SBS -- SBS (running)
0x0000 0x0342: pmt_pid 0x0402 SBS -- SBS NEWS (running)
0x0000 0x0343: pmt_pid 0x0408 SBS -- SBS 2 (running)
0x0000 0x034e: pmt_pid 0x0403 SBS -- SBS RADIO 1 (running)
0x0000 0x034f: pmt_pid 0x0404 SBS -- SBS RADIO 2 (running)
Network Name 'SBS NETWORK'
>>> tune to: 571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 585625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 585625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (23 services)
ABC HDTV:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2314:0:592
ABC1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:593
ABC2:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2307:2308:594
ABC1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:595
ABC3:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:596
ABC DiG Radio:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:2317:598
ABC DiG Jazz:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:2318:599
7 Digital:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1360
7 Digital 1:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1361
7 Digital 2:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1362
7 Digital 3:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1363
7 HD Digital:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1345:0:1364
NINE Digital:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1105
NINE HD:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:513:0:1112
TEN HD:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:0:1617
TEN Digital:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1621
TEN HD:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:0:1624
SBS HD:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:832
SBS:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:833
SBS NEWS:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:162:83:834
SBS 2:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:835
SBS RADIO 1:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:201:846
SBS RADIO 2:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:202:847
Done.
```

Seems to be quite a few differences

---

### Post by kreegor on 2008-09-02
I removed all the channels and deleted the sources. Created one source applied it to both cards, scanned for channels with both cards and now it works fine.

Freaking YAY!!! :)

---

### Post by Lindsay.Mathieson on 2008-09-03
Excellent, good news. Cross fingers knock on wood :)

---

### Post by kreegor on 2008-09-03
Yeah for sure. So glad that is fixed, now I just have to work out audio over DVI->HDMI and how to transfer my current install over to the new bigger hard drive I have.

Thanks heaps for all your help. Much appreciated

---

### Post by Lindsay.Mathieson on 2008-09-03
> **kreegor said:**
> Yeah for sure. So glad that is fixed, now I just have to work out audio over DVI->HDMI

I'm pretty sure you can't, for that you need HDMI-HDMI, also the support for it is still pretty dodgy under linux.

> and how to transfer my current install over to the new bigger hard drive I have.

Have fun with that :) You can't just add it as an extra drive?

Cheers,

Lindsay

---

### Post by kreegor on 2008-09-03
I have a 160 Gig IDE drive which I want to take out and use as a backup drive for our personal files etc. So I want to transfer my current MythBuntu install from the 160 to the 500 and put the 160 into an external enclosure.

---

