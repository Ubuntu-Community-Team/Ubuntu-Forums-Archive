---
title: "TBS-6284 quad DVB-T2 card"
date: 2012-03-29
forum: Mythbuntu
---

### Post by Chris Musampa on 2012-03-29
I just bought one of these babies, dropped it in a PCI-E slot, downloaded and compiled the driver and it works like a charm!

I'm using 11.10 64bit with Myth 0.24 to get UK Freeview (including HD channels).  I haven't tried the supplied remote as I use a mini wireless keyboard/trackpad  (Arctic K481) instead.

Just a heads up for anyone looking for a good option.

---

### Post by JesterFeckwit on 2012-04-07
Hi Chris,

I've just purchased one of these cards as well in the hope of building a MythTV backend server around it for DVB-T2 capture & streaming.

Sadly my installation experience hasn't been nearly as straightforward as your own!

This is the process that I used:

1) Installed Mythbuntu 11.10
2) Updated all packages
3) Compiled and installed the latest drivers from the TBS website
4) Power off
5) Insert TBS-6284 card
6) Restart
7) Run MythTV Backend Setup utility - no cards recognised.

I'm a complete Ubuntu / Myth novice (I like to bite plenty off...), do you have any ideas or suggestions please?

J.

---

### Post by Chris Musampa on 2012-04-07
Hi Jester, not sure I'll be able to help too much but there are folks on here who know far more about linux troubleshooting than I!  

First I'd check the card is showing up in the PCI devices, paste this command into a terminal:
lspci | grep -i saa

You should see something like this:
```
03:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 02)
```

Assuming that gives a result, try

dmesg | grep -i dvb

After successful driver compilation mine gives:
```

[   18.957482] DVB: registering new adapter (SAA716x dvb adapter)
[   19.687551] DVB: registering adapter 0 frontend 0 (TurboSight TBS 62x0 DVBT/T2 frontend)...
[   19.687671] DVB: registering new adapter (SAA716x dvb adapter)
[   19.771436] DVB: registering adapter 1 frontend 0 (TurboSight TBS 62x0 DVBT/T2 frontend)...
[   19.771539] DVB: registering new adapter (SAA716x dvb adapter)
[   20.466296] DVB: registering adapter 2 frontend 0 (TurboSight TBS 62x0 DVBT/T2 frontend)...
[   20.466412] DVB: registering new adapter (SAA716x dvb adapter)
[   20.550176] DVB: registering adapter 3 frontend 0 (TurboSight TBS 62x0 DVBT/T2 frontend)...

```

If you don't see similar then I guess there's a problem with the driver which would stop myth picking it up.

What instructions did you follow to compile the drivers and did it compile without error?

---

### Post by JesterFeckwit on 2012-04-10
Thanks for your help Chris!

I managed to get the card working over the weekend using the older drivers supplied with the device [v111118] rather than the ones from the TBS website [v120405] that I was trying to use before.

Which driver version are you using please?

J.

---

### Post by Chris Musampa on 2012-04-10
Hi Jester, glad you had some success but am I right in thinking that old driver only allows SD, thought I'd read that somewhere?

I'm using the February release 120216 (on onieric 64 bit), I didn't realise they'd had another release since, looks like you need the 120405 if you want the remote to work.  Not too bothered about the remote but might try that version when I can download the kernel update (which is being 'kept back' for some reason when I apt-get upgrade).

Not sure which instructions you used to compile the 120216 driver (you didn't say whether the compile was successful?), I followed these:
[http://linuxtv.org/wiki/index.php/TBS6280](http://linuxtv.org/wiki/index.php/TBS6280)

There's some crucial instructions in there to fix the file permissions after unpacking the archive.

---

### Post by JesterFeckwit on 2012-04-17
Hi again Chris, thanks for your continuing assistance!

Following some further testing (build, test, rebuild, test...) it would appear that the driver I'm currently using (v111118) does only support SD, so will try again using the latest version (v120405).

I've been following the instructions in the archive READMEs but these are quite different from those in the link you posted, so will try it the way you suggest instead.

The good news is that I've now successfully streamed live TV from this card to my ATV2 XBMC MythTV front end, so I am getting there slowly!

Once I have the TBS card working correctly with a Mythbuntu back-end server my next challenge will be to make it headless.

At present the system will only boot if it is connected to a monitor and so I can't VNC to it if the monitor isn't plugged in.

I've seen various posts about this issue but none of them seem particulalry elegant, I don't suppose you have any ideas I could try do you please?

JF

---

### Post by Chris Musampa on 2012-04-17
Hi Jester, I can't help with the headless question as I've never attempted it.  Good to see you're still progressing with your setup, you're probably learning some useful stuff while you're at it. :p

Please continue to post updates of you're success / failure with the drivers though as anyone googling 'tbs* myth*' in future will probably stumble across this thread.

---

### Post by ceejay on 2013-02-12
Hope I'll be excused for reviving an old thread ... but I'm trying to get a TBS-6280 card to work at the moment (which I guess is just half of a 6284!).

To contribute to the driver question: I downloaded the most recent version as I write - v130127 - and (once I remembered to make sure I was root throughout) it compiled and installed fine on 11.04

My problem now is playing back, specifically with VDPAU and an Nvidia GTX520.

For some time I have been happily using this hardware setup with no issues - but now when I try to play back any of the Freeview HD channels I get pretty much nothing.  If I switch to one of the software players, eg CPU++, then the channels play ok (therefore the tuner function is ok) but the picture is just a little too choppy ... ok but not great, and of course the whole point of HD is that I want great!

Any clues as to what I might need to do to get this playing back with VDPAU?

TIA

(ps - it's not a network issue between frontend and backend!)

---

### Post by ceejay on 2013-02-12
OK, answering my own question for now ... I discover that the inability to play HD only occurs with Live TV: if I set a recording and then go to watch the recording, it plays fine.

As this is with 0.24 and I hear that 0.25 makes a lot of changes to Live TV, I'll wait to see what happens when I try that, which will be shortly (in the middle of a lot of upgrading and changing at the moment!)

---

