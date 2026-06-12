---
title: "HVR 1600 Digital working, No signal analog"
date: 2009-06-26
forum: Mythbuntu
---

### Post by ChocolateBob on 2009-06-26
I have reserved posting a question as a last option, however i'm so close to success i need the help more now than ever. 

Dell Percision 670
Dual 3.4 GHZ Xenon 
3GB ram 
NV Quadro 3450 
haupphauge 1600 (1199) 

Running Mythbuntu 9.04

I have the digital side of the card up and working properly. The analog side wont give me any picture or sound (at least on this reboot). I have reinstalled drivers (and mythbuntu itself several times), followed guides on the wiki page, tried random tweaks found in post etc to no avail. Sometimes the analog card is able to get signal data (comcast) when using fetch channels, other times it just gives "time out" 

Below is the interesting portion of the log file (mythbackend.log) 

2009-06-26 04:08:50.285 Using runtime prefix = /usr
2009-06-26 04:08:50.287 Empty LocalHostName.
2009-06-26 04:08:50.288 Using localhost value of quagmire
2009-06-26 04:08:50.298 New DB connection, total: 1
2009-06-26 04:08:50.304 Connected to database 'mythconverg' at host: localhost
2009-06-26 04:08:50.308 Closing DB connection named 'DBManager0'
2009-06-26 04:08:50.316 Connected to database 'mythconverg' at host: localhost
2009-06-26 04:08:50.326 New DB connection, total: 2
2009-06-26 04:08:50.331 Connected to database 'mythconverg' at host: localhost
2009-06-26 04:08:50.340 Current Schema Version: 1214
2009-06-26 04:08:50.352 Preview Error: Previewer file '/var/lib/mythtv/livetv/3201_20090626040846.mpg' is not valid.
2009-06-26 04:08:50.355 Preview Error: Run() file not local: '/var/lib/mythtv/livetv/3201_20090626040846.mpg'
2009-06-26 04:08:50.372 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/livetv/3201_20090626040846.mpg.png) exists: 0 readable: 0 size: 0
2009-06-26 04:08:50.476 AFD: Opened codec 0x1206ed0, id(MPEG2VIDEO) type(Video)
2009-06-26 04:08:50.479 AFD: codec AC3 has 6 channels
2009-06-26 04:08:50.480 AFD: Opened codec 0x1207410, id(AC3) type(Audio)
2009-06-26 04:08:50.747 Preview: Grabbed preview '/var/lib/mythtv/livetv/2091_20090626040826.mpg' 1920x1088@64s
2009-06-26 04:08:59.056 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-06-26 04:09:00.792 TVRec(2): HW Tuner: 2->2
2009-06-26 04:09:02.770 Finished recording Unknown: channel 3201
2009-06-26 04:09:02.867 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-06-26 04:09:02.899 Using runtime prefix = /usr
2009-06-26 04:09:02.903 Empty LocalHostName.
2009-06-26 04:09:02.904 Using localhost value of quagmire
2009-06-26 04:09:02.913 New DB connection, total: 1
2009-06-26 04:09:02.918 Connected to database 'mythconverg' at host: localhost
2009-06-26 04:09:02.921 Closing DB connection named 'DBManager0'
2009-06-26 04:09:02.923 Connected to database 'mythconverg' at host: localhost
2009-06-26 04:09:02.928 New DB connection, total: 2
2009-06-26 04:09:02.931 Connected to database 'mythconverg' at host: localhost
2009-06-26 04:09:02.936 Current Schema Version: 1214
2009-06-26 04:09:03.372 DTVSM(0) Error: Wrong PMT; pmt->pn(4) desired(6)
2009-06-26 04:09:03.375 DTVSM(0) Error: Wrong PMT; pmt->pn(10) desired(6)
2009-06-26 04:09:03.378 DTVSM(0) Error: Wrong PMT; pmt->pn(2) desired(6)
2009-06-26 04:09:03.382 DTVSM(0) Error: Wrong PMT; pmt->pn(1) desired(6)
2009-06-26 04:09:03.437 DTVSM(0) Error: Wrong PMT; pmt->pn(3) desired(6)
2009-06-26 04:09:03.438 DTVSM(0) Error: Wrong PMT; pmt->pn(9) desired(6)
2009-06-26 04:09:03.438 DTVSM(0) Error: Wrong PMT; pmt->pn(11) desired(6)
2009-06-26 04:09:03.443 DTVSM(0) Error: Wrong PMT; pmt->pn(7) desired(6)
2009-06-26 04:09:03.447 DTVSM(0) Error: Wrong PMT; pmt->pn(5) desired(6)
2009-06-26 04:09:03.454 DTVSM(0) Error: Wrong PMT; pmt->pn(8) desired(6)
2009-06-26 04:09:04.166 Finished recording Unknown: channel 2849
2009-06-26 04:09:05.195 Finished recording Unknown: channel 2849
2009-06-26 04:09:05.208 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-06-26 04:09:05.323 Using runtime prefix = /usr
2009-06-26 04:09:05.327 Empty LocalHostName.
2009-06-26 04:09:05.328 Using localhost value of quagmire
2009-06-26 04:09:05.337 New DB connection, total: 1
2009-06-26 04:09:05.342 Connected to database 'mythconverg' at host: localhost
2009-06-26 04:09:05.347 Closing DB connection named 'DBManager0'
2009-06-26 04:09:05.354 Connected to database 'mythconverg' at host: localhost
2009-06-26 04:09:05.363 New DB connection, total: 2
2009-06-26 04:09:05.372 Connected to database 'mythconverg' at host: localhost
2009-06-26 04:09:05.375 AFD: Opened codec 0xba9ff0, id(MPEG2VIDEO) type(Video)
2009-06-26 04:09:05.387 AFD: codec AC3 has 2 channels
2009-06-26 04:09:05.396 AFD: Opened codec 0xbaa530, id(AC3) type(Audio)
2009-06-26 04:09:05.403 AFD: codec AC3 has 2 channels
2009-06-26 04:09:05.412 AFD: Opened codec 0xbaab70, id(AC3) type(Audio)
2009-06-26 04:09:05.380 Current Schema Version: 1214
2009-06-26 04:09:05.446 Preview Error: Previewer file '/var/lib/mythtv/livetv/2849_20090626040901.mpg' is not valid.
2009-06-26 04:09:05.448 Preview Error: Run() file not local: '/var/lib/mythtv/livetv/2849_20090626040901.mpg'
2009-06-26 04:09:05.458 Preview Error: Preview process not ok.
            fileinfo(/var/lib/mythtv/livetv/2849_20090626040901.mpg.png) exists: 0 readable: 0 size: 0
2009-06-26 04:09:05.465 Preview: Grabbed preview '/var/lib/mythtv/livetv/3201_20090626040849.mpg' 528x480@64s
2009-06-26 04:09:21.956 TVRec(2): Changing from WatchingLiveTV to None
2009-06-26 04:09:22.619 Finished recording Unknown: channel 2849
2009-06-26 04:09:56.329 Reschedule requested for id 3.
2009-06-26 04:09:56.448 Scheduled 1 items in 0.1 = 0.09 match + 0.03 place
2009-06-26 04:09:56.451 TVRec(1): ASK_RECORDING 1 0 0 0
2009-06-26 04:09:56.520 TVRec(1): Changing from None to RecordingOnly
2009-06-26 04:09:56.524 TVRec(1): HW Tuner: 1->1
2009-06-26 04:09:56.589 

Not ivtv driver??


2009-06-26 04:09:56.599 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2009-06-26 04:09:56.603 Started recording: Family Court With Judge Penny: channel 1003 on cardid 1, sourceid 1
2009-06-26 04:10:21.363 TVRec(1): Changing from RecordingOnly to None
2009-06-26 04:10:21.370 Finished recording Family Court With Judge Penny: channel 1003
2009-06-26 04:10:21.370 Reschedule requested for id 0.
2009-06-26 04:10:21.387 Scheduled 1 items in 0.0 = 0.00 match + 0.01 place
2009-06-26 04:10:22.141 Finished recording Family Court With Judge Penny: channel 1003
2009-06-26 04:10:22.254 Using runtime prefix = /usr

I am at a loss here. Sometimes the analog "watch TV" view comes in as solid grey background, or solid black, or solid red / pink. Some random times a picture comes in with crackle sound spikes, other times it has come in fine (untill i reboot) 

If anyone can tell me what these logs mean i would greatly appreciate the help.

---

### Post by klc5555 on 2009-06-26
The cx18 driver tends to be a bit fussy, and very often doesn't load quite right at bootup.

_Without_ rebooting, try reloading the module with the commands:

sudo rmmod cx18

sudo modprobe cx18

Assuming that goes without incident, give livetv another shot and see what you have.

On some occasions, I've had to do the above twice in succession --the first time to go from blank or pink screen to just the sound cracklies, and then on the second run everything loads and runs fine.

---

### Post by ChocolateBob on 2009-06-26
Sweet sassy mollassy! Thanks for the help! so this worked right off the bat. 

So i'm wondering if there is some script or something that can do this automatically? The reason i'm asking is because i would eventually like to have the auto-wake options setup so i can record shows without having to be here (or leave the box on for days at a time). Sorry to be such a bugger, but again any help is apreciated. Thanks for your time.

Addition: i had to stop the myth backend before it would sudo rmmod cx18 would work. I used

sudo /etc/init.d/mythtv-backend stop 

sudo rmmod
sudo modprob cx18

sudo /etc/init.d/mythtv-backend start 

then it worked

---

### Post by klc5555 on 2009-06-26
> **ChocolateBob said:**
> Sweet sassy mollassy! Thanks for the help! so this worked right off the bat. 

So i'm wondering if there is some script or something that can do this automatically? The reason i'm asking is because i would eventually like to have the auto-wake options setup so i can record shows without having to be here (or leave the box on for days at a time). Sorry to be such a bugger, but again any help is apreciated. Thanks for your time.

Addition: i had to stop the myth backend before it would sudo rmmod cx18 would work. I used

sudo /etc/init.d/mythtv-backend stop 

sudo rmmod
sudo modprob cx18

sudo /etc/init.d/mythtv-backend start 

then it worked

Thanks for telling me about the mythtv-backend issue, which I was unaware of --my 1600 is on one of my Slackware machines, which don't care whether a daemon like mythbackend -d is running or not when you unload and reload modules.

On that particular machine I've occasionally added the two module commands (without sudo, of course) to the end of the rc.local and it's worked mostly OK. Except on those occasions when the module needs to be reloaded twice. Since I don't reboot that machine often, I usually prefer to take care of the process manually.

Here, however, on a Mythbuntu machine, I don't know whether rc.local executes first, or mythtv-backend starts up first. So you may have to experiment. What you don't want is the situation where the backend tries to start in the time between when the cx18 module has unloaded but before it has been reloaded.

Also cx18 doesn't fail to load properly _all_ the time at boot. Just often enough to be annoying. 

All the best.

From time to time

---

### Post by stonebit on 2009-11-17
Hey thanks! This fixed my error too! I was getting a red screen. When i reinitialize the driver, it works. Any idea how to script this to make it work every time on reboot?

---

### Post by klc5555 on 2009-11-17
> **stonebit said:**
> Hey thanks! This fixed my error too! I was getting a red screen. When i reinitialize the driver, it works. Any idea how to script this to make it work every time on reboot?

What I ended up doing on the machine that has my 1600 (which is a Slackware machine, not Ubuntu) was add the following to my rc.local:

rmmod cx18

sleep 5

modprobe cx18

and it seems to work. On a relatively fussier Ubuntu machine, your mileage may vary. The "sleep 5" was added because following the rmmod immediately with a modprobe frequently did not reinitialize the card correctly. Also one of the other cards in the machine (a new-style AverMedia 180) turned out to be persnicketty about whether its specialized modprobe command line preceded or followed the above sequence (it had to follow). So you may also have fine tuning of that sort involved.

Cheers!

---

### Post by tdiaz on 2009-11-23
This also works for me, in principal, I'm still having issues with artifacting on the playback on both the local and remote front ends while looking at live TV. I have not recorded anything yet. I should try that now. 

On the analog side, there's a white line on the lower 1/4 of the screen that "wraps", like if you're adjusting the hold on a TV. 

What I have not been able to fully figure out is if the advice given in numerous places is required to do with karmic mythbuntu

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

While the lower part of this page does say it was modified on 22-November.. do we still need to do with the latest mythbuntu distribution?

The machine it's in, is a dual xeon 2.8 with 4GB RAM and it's writing to a RAID5 2TB on a SATA 300 RAID controller. The swap and / are one separate physical drives.

---

### Post by klc5555 on 2009-11-24
> **tdiaz said:**
> This also works for me, in principal, I'm still having issues with artifacting on the playback on both the local and remote front ends while looking at live TV. I have not recorded anything yet. I should try that now. 

On the analog side, there's a white line on the lower 1/4 of the screen that "wraps", like if you're adjusting the hold on a TV. 

What I have not been able to fully figure out is if the advice given in numerous places is required to do with karmic mythbuntu

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

While the lower part of this page does say it was modified on 22-November.. do we still need to do with the latest mythbuntu distribution?

The machine it's in, is a dual xeon 2.8 with 4GB RAM and it's writing to a RAID5 2TB on a SATA 300 RAID controller. The swap and / are one separate physical drives.

The digital side of the 1600 has frequently been signal-challenged, which is why I use mine analog-only. (Made more palatable, I guess, by Comcast nuking clear QAM on the few stations I actually care about in favor of encryption, so it ends up being DTA to analog.)

But there has been an awful lot of work of late into the cx18 driver itself and into 3rd-party patches to this driver.

See: [http://linuxtv.org/hg/v4l-dvb/log?rev=cx18](http://linuxtv.org/hg/v4l-dvb/log?rev=cx18) for recent changes. In particular, the addition from 3 weeks ago seems interesting : "mxl5005s: provide ability to override QAM gain for HVR-1600" 

Experimental QAM optimized drivers for the 1600 exist at: [http://www.kernellabs.com/hg/~dheitmueller/hvr-1600-perf-2](http://www.kernellabs.com/hg/~dheitmueller/hvr-1600-perf-2)

Now none of this stuff has been moved to the kernel tree, so would have to be compiled and installed on your own, at your own risk.

I certainly can't vouch for the effectiveness of either of these -- I have so far tried only to compile the modified cx18 mercurial source from V4L, but the module seems to require kernel 2.6.31 to compile, whereas the machine with the 1600 is on a custom 2.6.27.7 kernel (with a cx18 compiled in February) that I'm not quite ready to move off of. I haven't examined the other driver at all.

Good luck.

---

