---
title: "mythfrontend.real running hot"
date: 2009-02-13
forum: Mythbuntu
---

### Post by dmfrey on 2009-02-13
After a recent update, I started to notice some choppy playback.  I saw that mythcommflag was running but after running top, I noticed that mythfrontend.real was continually running around 196%.  This slows the commercial flagging down to a crawl; it actually takes days to flag the recordings.

Has anyone run into this?  If so, have you found a cause and a cure?

Thanks.

---

### Post by dmfrey on 2009-02-27
Is anyone else experiencing this?

Firstly, htop (in tree view) shows mythfrontend.real running under 9 distinct pids.

secondly, two of those pids are each taking 99% cpu (there are 2 cores on the processor).

thirdly, strace -p for each of the pids show similar results.
```

select(30, [29], NULL, NULL, {0, 500000}) = 1 (in [29], left {0, 500000})
ioctl(29, FIONREAD, [0])                = 0
select(30, [29], NULL, NULL, {0, 500000}) = 1 (in [29], left {0, 500000})
ioctl(29, FIONREAD, [0])                = 0
select(30, [29], NULL, NULL, {0, 500000}) = 1 (in [29], left {0, 500000})
ioctl(29, FIONREAD, [0])                = 0
select(30, [29], NULL, NULL, {0, 500000}) = 1 (in [29], left {0, 500000})
ioctl(29, FIONREAD, [0])                = 0
select(30, [29], NULL, NULL, {0, 500000}) = 1 (in [29], left {0, 500000})
ioctl(29, FIONREAD, [0])                = 0
select(30, [29], NULL, NULL, {0, 500000}) = 1 (in [29], left {0, 500000})
ioctl(29, FIONREAD, [0])                = 0
select(30, [29], NULL, NULL, {0, 500000}) = 1 (in [29], left {0, 500000})
...

```
This just continually happens over and over until I stop mythfrontend.

This only just started happening a few weeks ago.  It has seriously degraded my performance on the box.  Also, since there is no cpu left, things like commercial flagging take days to complete instead of an hour or so.

Any ideas?

---

### Post by dmfrey on 2009-03-10
Bump...anyone?

---

### Post by newlinux on 2009-03-10
maybe post your logs, and tell us a little more about your hardware and which version of ubuntu you are running. What type of content are you trying to watch? Do you normally use XvMC? Did your playback profiles get changed at all? 

Gotta watch those updates... Do you know what was included in the one that seemingly broke your system.

---

### Post by nickrout on 2009-03-10
I don't think you should have that many mythfrontend.real's. 

Do you have a button on your remote that is programmed to start the frontend? If so are you perhaps sitting on that button and firing off multiple instances of the frontend?

Try killing X (ctrl-alt-bkspace) and letting mythfrontend restart after X comes back. How many instances are running then?

---

### Post by newlinux on 2009-03-11
the output of htop can be somewhat deceiving with regards to number of processes running  (I believe it shows all threads for a process - top doesn't, which is probably why you only saw one mythfrontend process in the top output). What does:
```

ps aux | grep mythfrontend

```
return? If that has multiple mythfrontends listed then you should be concerned. Otherwise, that is probably not an issue.

---

### Post by nickrout on 2009-03-11
Actually on my machine htop shows many instances (threads) of mythfrontend.real too. So thats a red herring. Sorry if I distracted anyone.

---

### Post by dmfrey on 2009-03-11
> **newlinux said:**
> maybe post your logs, and tell us a little more about your hardware and which version of ubuntu you are running. What type of content are you trying to watch? Do you normally use XvMC? Did your playback profiles get changed at all? 

Gotta watch those updates... Do you know what was included in the one that seemingly broke your system.

My box is an AMD64 FX 5400 with 4 Gb of RAM and a 500 Gb hard drive.  It has 3 tuners configured: firewire, pcHDTV 5500 and PVR 150. It is running Mythbuntu 8.10 (amd64).  It is a combined frontend/backend.

XvMC is configured and is confirmed to be running by checking the XOrg log.

I watch SD and HD content.

Unless the playback profiles changed in the update, I have not modified them from the stock profiles.

I have gone in and periodically tailed the frontend logs and they show very little activity.

---

### Post by dmfrey on 2009-03-11
> **nickrout said:**
> I don't think you should have that many mythfrontend.real's. 

Do you have a button on your remote that is programmed to start the frontend? If so are you perhaps sitting on that button and firing off multiple instances of the frontend?

Try killing X (ctrl-alt-bkspace) and letting mythfrontend restart after X comes back. How many instances are running then?

There is no button on my remote configured to restart the X or mythfrontend.real.

I kill X all the time, but that is so I can get commercial flagging to complete in a timely manner.

---

### Post by dmfrey on 2009-03-11
> **newlinux said:**
> the output of htop can be somewhat deceiving with regards to number of processes running  (I believe it shows all threads for a process - top doesn't, which is probably why you only saw one mythfrontend process in the top output). What does:
```

ps aux | grep mythfrontend

```
return? If that has multiple mythfrontends listed then you should be concerned. Otherwise, that is probably not an issue.

Here is the output:
```
dmfrey    3467  191  6.3 686804 242316 ?       SLsl Mar10 2917:46 /usr/bin/mythfrontend.real --logfile /var/log/mythtv/mythfrontend.log
```

Only on shows up.  Top shows mythfrontend.real taking 190% cpu (this number seems odd). htop shows two of the mythfrontend.real processes each taking between 93 and 97% cpu.  Above I posted an strace of previous processes...this is what they are still doing.

Thanks for everyone's help.  Hopefully this can be resolved.

---

### Post by nickrout on 2009-03-11
I think you might have better luck getting this resolved on the mythtv-user mailing list.

---

### Post by newlinux on 2009-03-12
Couple more questions - Does mythfrontend use this much CPU even when it is not watching content, just when it is running? Which graphics card do you have? You might want to double check all of your playback settings, and check the logs to make sure it is using the playback settings you think it is. You may want to turn up the verbosity of the logs to get more information.

---

### Post by newlinux on 2009-03-12
> **dmfrey said:**
> Here is the output:
```
dmfrey    3467  191  6.3 686804 242316 ?       SLsl Mar10 2917:46 /usr/bin/mythfrontend.real --logfile /var/log/mythtv/mythfrontend.log
```

Only on shows up.  Top shows mythfrontend.real taking 190% cpu (this number seems odd). htop shows two of the mythfrontend.real processes each taking between 93 and 97% cpu.  Above I posted an strace of previous processes...this is what they are still doing.

Thanks for everyone's help.  Hopefully this can be resolved.

Top (by default) doesn't intuitively show information correctly for multi core/CPU machines. If you press the "1" key while using top it will show total usage for each core/CPU, but the individual processes work differently. So if you have 2 cores, technically a process can be using 200% max (100% of each core). So in your case 190% ~= 93% + 97% you saw with the multiple threads in htop.

If you only get the CPU spikes after or during playback, you will definitely want to double check and expirement with you playback settings to try and pinpoint the problem...

---

### Post by dmfrey on 2009-03-14
> **newlinux said:**
> Top (by default) doesn't intuitively show information correctly for multi core/CPU machines. If you press the "1" key while using top it will show total usage for each core/CPU, but the individual processes work differently. So if you have 2 cores, technically a process can be using 200% max (100% of each core). So in your case 190% ~= 93% + 97% you saw with the multiple threads in htop.

If you only get the CPU spikes after or during playback, you will definitely want to double check and expirement with you playback settings to try and pinpoint the problem...

Thanks for the tip on Top.  I was not aware of that one.  I need to research Top a bit more.

The other night, I killed the frontend so that get commflag to complete and I started it before I headed off to bed the other night.  I checked it first thing in the morning and it was back up to the high levels again...nothing had recorded and nothing was watched in that time frame.  I am gonna try to increase the verbosity of the logs to see if something else seems to be going on.

---

### Post by kem on 2011-10-26
CONFIRMATION: I have experienced very same issue. Several instances of mythfrontend.real are running and using 100% resources of my 4thread processor.

Frequently, frontend keeps crash-restarting cycle. 

I am using builds from [http://ppa.launchpad.net/mythbuntu/0.24/ubuntu](http://ppa.launchpad.net/mythbuntu/0.24/ubuntu)

I wonder if this issue affects just launchpad version or stable version too.

kem

---

### Post by thatguruguy on 2011-10-27
For the record, you are referring to a completely different version of mythbuntu than the one the OP was writing about.  You may want to start a new thread.

---

### Post by keepitsimpleengr on 2011-10-27
An htop screen shot of my mythbuntu 10.10·.24 recording two programs, playing back one while comflagging.  Done over Putty/vinagre (which accounts for large X CPU usage.

Hope this helps...

[htop for mythtv 10.10/.24]("http://docs.google.com/open?id=0B2Z1PtrPT-grODRiZjgwNGMtY2NmMi00OWEyLWIxZTItMzIyM2JiZjYwNWEy")

My system combo client/server, AMD 3 CPU 3.1MHz, 2250 Hauppage 2xtuner card, 240 nvidia, 4GB memory, 2x2TB satas and a 320GB sata for system and a little extra recording storage. I comm-flag immediately after starting a recording.

---

