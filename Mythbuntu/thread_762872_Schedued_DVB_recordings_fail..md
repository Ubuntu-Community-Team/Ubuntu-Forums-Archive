---
title: "Schedued DVB recordings fail."
date: 2008-04-22
forum: Mythbuntu
---

### Post by paulyche on 2008-04-22
I'm having problems with recordings randomly (at least it looks random) failing. In the following backend log excerpt the program was scheduled and then failed to record. This is only an intermittent effect although some channels/programs **seem** to experience the effect more than others. This is really impacting the GAF, as the she keeps on missing Star Trek and Dexter.

On the below example, I scheduled a different recording immediately after the failure (same tuner) and this recorded fine.

I'm using a Nova-T 500 to capture terrestrial digital (DVB) broadcasts (UK Freeview). I'm not getting a particularly bad digital signal  only occasional and very minor artefacts.

This is on Mytbuntu 8.10 Beta (64 bit)

```
2008-04-21 19:58:00.039 Reschedule requested for id 0.
2008-04-21 19:58:00.180 Scheduled 32 items in 0.1 = 0.02 match + 0.12 place
2008-04-21 19:58:30.052 TVRec(2): ASK_RECORDING 2 29 0 0
2008-04-21 19:59:01.568 TVRec(2): Changing from None to RecordingOnly
2008-04-21 19:59:01.578 TVRec(2): HW Tuner: 2->2
2008-04-21 19:59:01.733 DVBChan(2:0) Error: Tune(): Setting Frontend tuning parameters failed.
                        eno: No such device (19)
2008-04-21 19:59:01.739 DVBChan(2:0) Error: SetChannelByString(20): Tuning to frequency.
2008-04-21 19:59:01.743 TVRec(2) Error: Failed to set channel to 20. Reverting to kState_None
2008-04-21 19:59:01.743 TVRec(2): Changing from RecordingOnly to None
2008-04-21 19:59:01.956 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-04-21 19:59:01.964 Canceled recording (Recorder Failed): Star Trek: The Next Generation "The Arsenal of Freedom": channel 1020 on cardid 2, sourceid 1
2008-04-21 19:59:02.965 Reschedule requested for id 0.
2008-04-21 19:59:03.075 Scheduled 32 items in 0.1 = 0.00 match + 0.10 place
2008-04-21 19:59:05.036 Error deleting '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/mythtvbox/1020_20080421195900.mpg': No such file or directory
2008-04-21 19:59:11.042 Reschedule requested for id 0.
2008-04-21 19:59:11.125 Scheduled 32 items in 0.1 = 0.01 match + 0.07 place

```

---

### Post by laga on 2008-04-22
Do you see anything funky in dmesg when this happens?

---

### Post by paulyche on 2008-04-22
I'm getting a load of mt2060 I2C read failed messages in the dmesg output.
```

[88824.921658] mt2060 I2C read failed
[88824.930416] mt2060 I2C read failed
[88824.938508] mt2060 I2C read failed
[88824.945077] mt2060 I2C read failed
[88824.953094] mt2060 I2C read failed
[88824.961084] mt2060 I2C read failed
[88824.969099] mt2060 I2C read failed
[88824.977077] mt2060 I2C read failed

```

I've googled this and it looks likes the card is disconnecting. There was a known issue with this but I thought it was fixed?

I set up my card with this guide 

[http://mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI]("http://mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI")


I'm using the **dvb-usb-dib0700-1.10.fw** firmware and I'm running a 2.6.24 kernel
```
paul@mythtvbox:/etc/modprobe.d# uname -a
Linux mythtvbox 2.6.24-15-generic #1 SMP Fri Apr 4 03:10:59 UTC 2008 x86_64 GNU/Linux
```

I don't know how to find out what version of the v4l-dvb drivers I'm using



for completeness **dmesg | grep -i dvb** gives
```

[89025.373223] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully deinitialized and disconnected.
[89025.742977] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[89025.743010] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[89025.743192] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[89025.858497] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[89026.374561] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[89026.374774] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[89026.383594] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[89026.972235] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:03:05.2/usb2/2-1/input/input7
[89027.004333] dvb-usb: schedule remote query interval to 150 msecs.
[89027.004344] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.

```

---

### Post by Hugolp on 2008-04-28
I installed hardy a couple of days ago and I am having the same problem. Same message in dmesg, plus randomly the card refuses to work. No hang ups or any other thing, I just get a recording failed, and the system continues to work. I am runing kernel 2.6.22-14-generic (the one that installed from default with the alternate ubuntu cd).

Anyone has found a solution?

---

### Post by paulyche on 2008-04-28
I'm trying MythWatch (see this thread: [http://ubuntuforums.org/showthread.php?t=618546&highlight=mythwatch&page=2]("http://ubuntuforums.org/showthread.php?t=618546&highlight=mythwatch&page=2"))

Only installed yesterday though; I'll keep you posted.

---

### Post by Hugolp on 2008-04-28
> **paulyche said:**
> I'm trying MythWatch (see this thread: [http://ubuntuforums.org/showthread.php?t=618546&highlight=mythwatch&page=2]("http://ubuntuforums.org/showthread.php?t=618546&highlight=mythwatch&page=2"))

Only installed yesterday though; I'll keep you posted.

My problem is not the backend hanging. In fact it hasnt hang up. The problem is that the turners stop working and I get no signal or the recordings dont happen. But the backend keeps on working "fine".

---

### Post by paulyche on 2008-04-28
> **Hugolp said:**
> My problem is not the backend hanging. In fact it hasnt hang up. The problem is that the turners stop working and I get no signal or the recordings dont happen. But the backend keeps on working "fine".

My backend isn't hanging either... The error I put in my first post above was from the backend log file at the point when a recording is meant to commence; however, the backend will continue to work fine (and may record on the other tuner).

I've found that a backend restart fixes the tuner disconnect problems though

---

### Post by Hugolp on 2008-05-01
Paulyche and anyone having this problem you can report to this bug in launchpad so it will get more attention and hopefully be solved quicker:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204857](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204857)

Hugo

---

### Post by duckville on 2008-05-01
The issue you've got is with the firmware the card uses I believe. I was using Nova T 500s with the latest firmware for the cards, but no joy.

I'm just using my old Nova T PCIs on my servers now.

[http://ubuntuforums.org/showthread.php?t=726813](http://ubuntuforums.org/showthread.php?t=726813)

---

### Post by xykevinr on 2008-05-01
Hi All, 

I seem to have exactly the same issues as hugolp. 

I'm new to Mythbuntu - about 3 weeks so far. Used 7.10 with a NovaT500 for the first 2weeks with no problems. 

'Upgraded' to 8.04 a few days ago. About 1 in 10 recordings is working all others fail.  Backend stays up, can still watch the few recordings I have. I get lots of  "mt2060 I2C read failed" from dmesg.

I think I'm going back to 7.10. 

I've not posted in any other forums / bug lists etc - as a new user I'm a little bewildered by the massive number of seemingly similar forms and still learning.

Kevin

VIA EPIA 800Mhz, 1GHz and another 1Ghz !
A NovaT 500

---

### Post by Al_Vampyre on 2008-05-02
> **paulyche said:**
> I'm trying MythWatch (see this thread: [http://ubuntuforums.org/showthread.php?t=618546&highlight=mythwatch&page=2]("http://ubuntuforums.org/showthread.php?t=618546&highlight=mythwatch&page=2"))

Only installed yesterday though; I'll keep you posted.

That's what I was going to suggest, seems to have sorted my issues with the Nova T 500.

---

### Post by Hugolp on 2008-05-03
> **xykevinr said:**
> Hi All, 

I seem to have exactly the same issues as hugolp. 

I'm new to Mythbuntu - about 3 weeks so far. Used 7.10 with a NovaT500 for the first 2weeks with no problems. 

'Upgraded' to 8.04 a few days ago. About 1 in 10 recordings is working all others fail.  Backend stays up, can still watch the few recordings I have. I get lots of  "mt2060 I2C read failed" from dmesg.

I think I'm going back to 7.10. 

I've not posted in any other forums / bug lists etc - as a new user I'm a little bewildered by the massive number of seemingly similar forms and still learning.

Kevin

VIA EPIA 800Mhz, 1GHz and another 1Ghz !
A NovaT 500

@xykevinr
Hi

DaveMorris has the same setup I have, and has helping me to find out what is going on, because he has no problems. The only difference in our setups is that I have set 0 ms delay to change between chanels, while he added some time. I have tried that solution an hour ago so I can not speak about results yet. You may want to try that to check if that solves your issues. You have to go to the mythtv-backend configuration, and for each turner you can edit the options. Edit the options of the two turners corresponding to the nova-t-500 and add some delay. I can not confirm this will solve the issue yet, but is the only difference between DaveMorris working nova-t-500 setup and mine (that is not working), so you might want to try.

Hugo

@Al_Vampyre

That is just a temporary and bad solution, because it breaks your recordings if this is triggered in the middle of one. Or what about if you are watching some livetv while this is triggered and the tv goes off because the backend is restarting?

Hugo

---

### Post by Al_Vampyre on 2008-05-03
> **Hugolp said:**
> 

@Al_Vampyre

That is just a temporary and bad solution, because it breaks your recordings if this is triggered in the middle of one. Or what about if you are watching some livetv while this is triggered and the tv goes off because the backend is restarting?

Hugo

I would tend to agree, funny thing is it has never happened during live TV but has occasionally happened during a recording. i started using MythWatch because I was having partial lock issues when the myth box had been idle overnight or when I was out at work. I would come home, switch on the TV and not get a lock on the channel.

---

### Post by Hugolp on 2008-05-05
Ok. Its been two days now, and the nova-t-500 has NOT failed once, and dmesg has NOT shown any of the IC2 warnings. I have made quite a few recordings over the weekend plus I have watched livetv and the nova-t-500 has worked perfectly without any reboot.

So, thanks to Dave Morris for pointing to the solution:

- Go to the backend setup and in the two turners that correspond to the nova-t-500 turners go to options and add some delay to change channels (in my case I have only tried with 75ms). That will stop your nova-t-500 from failing, and nobody can feel 75 ms delay, so its all good.

Hugo

---

### Post by xykevinr on 2008-05-12
Hi,

I swapped back to 8.04 a couple of days ago. Added the change channel delay (I used 100mS), everything was fine for a few hours, then the same dmesg and failed recordings.

I'm back on 7.10 again (I have 2 HDDs). 

I'll try the disable EIT scanning and disabling the remote - as I dont have the remote thingy attached - next (as I've found on another thread). 

Kev

---

