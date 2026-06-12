---
title: "Nova-S Channel Scan / Import Problems"
date: 2008-09-09
forum: Mythbuntu
---

### Post by fibble on 2008-09-09
Hi,

I have been running with a single Nova-T DVB-T tuner on Mythbuntu 8.04 and things have been great.

I have just installed two Nova-S PCI cards, hooked them up to a new Quad LNB and tried scanning for channels in Myth-Setup. No luck.

I tried frequency: 10773000  sym rate: 10773000  
And  frequency: 10773000 sym rate: 10773000

both with no luck via MythSetup.

Doing a scan from the command line works on both Nova-S cards (dvb devices 0 and 1, the Nova-T is device 2)

```
scan -a 0 /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E

scan -a 1 /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E

```

That outputs a long list of channels as expected.

I tried outputting the results of the scan to /tmp/channels.conf, and using the "Import Channels" feature in mythsetup instead of a scan, I see a progress bar for a split second, then an empty channel list.

Am I missing something here? Have I done this correctly?

Has anyone else on the forums got a working setup using Nova-S PCI cards? If so how did you get your channels scanned or imported?

Any tips / ideas would be most gratefully accepted! 

The channels.conf I tried to Import has lots of content, like:

```
BBC 1 London:10773:h:0:22000:5000:5001:6301
BBC 2 England:10773:h:0:22000:5100:5101:6302
ETV:10773:h:0:22000:5300:5301:6306
BBC TES 3:10773:h:0:22000:5200:5201:6315
BBC FOUR:10773:h:0:22000:5300:5301:6316
loads more below....

```

I have remote access to this box, so if any other output would be useful please ask and I can provide.

Thanks,

Andy

---

### Post by AlecJ on 2009-01-30
Hi try scanning with Myth
Freq Khz 104729000 
polarity H
sym rate 22000000

Should see Channel 4

Ive just setup my Nova-S with a brand new 8.04 fully updated install.

What I did was to make a new Video Source called Astra, then using this web site
[http://www.lyngsat.com/astra2d.html](http://www.lyngsat.com/astra2d.html)
I manualy scaned each freqency, going back to the scan after each freq had finished.
I then set Astra as the Video source for the DVB-S cards and the normal EIT for the DVB-T cards.
Ok it takes some time in the channel editor sorting through the channels, but this is Mythtv.

There is a guide on here for DVB-s install's, but sounds like your passed that point.

---

### Post by ian dobson on 2009-01-30
Hi,

The format for your channels.conf file doesn't look correct.

Try using wscan, I've used that several times when myth didn't want to scan for channels itself.

Have a look here [http://mythtv.org/pipermail/mythtv-dev/2006-September/050835.html](http://mythtv.org/pipermail/mythtv-dev/2006-September/050835.html)  or
 [http://www.bioinfo-user.org.uk/dokuwiki/doku.php?id=notes:mythtv](http://www.bioinfo-user.org.uk/dokuwiki/doku.php?id=notes:mythtv)
or [http://edafe.org/vdr/w_scan/](http://edafe.org/vdr/w_scan/)

Regards
Ian Dobson

---

### Post by tobiz on 2009-04-11
> **fibble said:**
> Hi,

I have been running with a single Nova-T DVB-T tuner on Mythbuntu 8.04 and things have been great.

I have just installed two Nova-S PCI cards, hooked them up to a new Quad LNB and tried scanning for channels in Myth-Setup. No luck.

I tried frequency: 10773000  sym rate: 10773000  
And  frequency: 10773000 sym rate: 10773000

both with no luck via MythSetup.

Doing a scan from the command line works on both Nova-S cards (dvb devices 0 and 1, the Nova-T is device 2)

```
scan -a 0 /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E

scan -a 1 /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E

```

That outputs a long list of channels as expected.

I tried outputting the results of the scan to /tmp/channels.conf, and using the "Import Channels" feature in mythsetup instead of a scan, I see a progress bar for a split second, then an empty channel list.

Am I missing something here? Have I done this correctly?

Has anyone else on the forums got a working setup using Nova-S PCI cards? If so how did you get your channels scanned or imported?

Any tips / ideas would be most gratefully accepted! 

The channels.conf I tried to Import has lots of content, like:

```
BBC 1 London:10773:h:0:22000:5000:5001:6301
BBC 2 England:10773:h:0:22000:5100:5101:6302
ETV:10773:h:0:22000:5300:5301:6306
BBC TES 3:10773:h:0:22000:5200:5201:6315
BBC FOUR:10773:h:0:22000:5300:5301:6316
loads more below....

```

I have remote access to this box, so if any other output would be useful please ask and I can provide.

Thanks,

Andy
fibble,
Exactly the same problem as you re mythtv and scan for dvb-s channels; did you ever get it to work if so how?  I tried others in the post but no success.

---

### Post by nickrout on 2009-04-11
your symbol rate is certainly wrong. go [here]("http://www.lyngsat.com/europe.html") 

choose the correct satellite (astra 2A 2B or 2C by the look of it)

but also, have you set up your lnb first?

---

### Post by singedwings on 2009-11-28
Try this great guide

[http://parker1.co.uk/mythtv_freesat.php]("http://parker1.co.uk/mythtv_freesat.php")

---

### Post by pootle1 on 2009-11-28
I had problems when I first tried to use the satellite card:


[LIST=1]
[*]Have you set up disequC in the capture card setup - the dialogue was a bit broken when I did it, but try arrow keys and select and it should work enentually
[*]I found in post [http://ubuntuforums.org/showthread.php?t=1312818](http://ubuntuforums.org/showthread.php?t=1312818) that you can input just 1 set of channel info to scan and tt will then find everytthing on Astra
[/LIST]
```
The details for the Channel 4 transponder on Astra 2D are :-
Freq: 10714000
Polarity: h
Symbol rate: 22000000
Mod Sys: DVB-S
FEC: 5/6
Modulation: qpsk
Inversion: <leave at auto>
Rolloff: <leave at 0.35
```

so you don't need to mess around with scan (on karmic and myth 0.22 at least)

Note if you are using a mix of T and S cards you will need to tie down the cards to specific adapter numbers (otherwise they randomly change on boot which is pretty terminal :) )

I use this method:
create the file /etc/modprobe.d/DVBoptions.conf and put in (include the lnb stuff from later while you're at it) 
 ```
# force nova-t numbers up high to get consistent names
options dvb_usb_dib0700 adapter_nr=4,5

# force dvb-s card to higher number
options cx88_dvb adapter_nr=6

```
but if you have two cards the same you will need something more sophisticated.

And Garry Parker's site is great - but didn't wuite get me all the way....

---

