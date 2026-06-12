---
title: "mythbuntu 10.04 pvr-150 hvr-1600 conflict"
date: 2010-05-24
forum: Mythbuntu
---

### Post by zapstrap on 2010-05-24
I have a machine with a pvr-150 and an hvr-1600.  It's a fresh install of 10.04, and I've managed to successfully add the tuners.  The machine is using ACPI to power down and wake-up on RTC alarm.  This all works, but the tuner cards don't come up consistently on restart.  When myth tries to record an analogue program, better than half the time the tuners either aren't recognized, or don't work properly.  I was treated to a one hour recording of a red screen with no sound last week, instead of the program I expected.  Searching /var/log/messages shows this:

Initial boot:
```

kernel: [   16.679703] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
kernel: [   17.333316] ivtv0: Registered device video1 for encoder MPG (4096 kB)

```Five minutes later, issuing a sudo shutdown -r now, I get:
```

kernel: [   16.253885] ivtv0: Registered device video0 for encoder MPG  (4096 kB)
kernel: [   16.806268] cx18-0: Registered device video1 for encoder MPEG  (64 x 32.00 kB)
```The first attempt loaded the hvr-1600 card as video0, whereas teh second attempt loaded up the pvr-150 as video0.  This is causing myth to become understandably confused, and usually respond by deleting either one or both analogue tuners, and all I get left is the digital tuner of the hvr-1600.

Anybody know how to make this start up consistently?

---

### Post by klc5555 on 2010-05-24
> **zapstrap said:**
> I have a machine with a pvr-150 and an hvr-1600.  It's a fresh install of 10.04, and I've managed to successfully add the tuners.  The machine is using ACPI to power down and wake-up on RTC alarm.  This all works, but the tuner cards don't come up consistently on restart.  When myth tries to record an analogue program, better than half the time the tuners either aren't recognized, or don't work properly.  I was treated to a one hour recording of a red screen with no sound last week, instead of the program I expected.  Searching /var/log/messages shows this:

Initial boot:
```

kernel: [   16.679703] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
kernel: [   17.333316] ivtv0: Registered device video1 for encoder MPG (4096 kB)

```Five minutes later, issuing a sudo shutdown -r now, I get:
```

kernel: [   16.253885] ivtv0: Registered device video0 for encoder MPG  (4096 kB)
kernel: [   16.806268] cx18-0: Registered device video1 for encoder MPEG  (64 x 32.00 kB)
```The first attempt loaded the hvr-1600 card as video0, whereas teh second attempt loaded up the pvr-150 as video0.  This is causing myth to become understandably confused, and usually respond by deleting either one or both analogue tuners, and all I get left is the digital tuner of the hvr-1600.

Anybody know how to make this start up consistently?

The traditional and easiest way would have been to make a module options file for your pvr 150's ivtv module (under /etc/modprobe.d/ )where there would be a line: 

options ivtv ivtv_first_minor=1

which would compel your pvr150 to load only as /dev/video1

However, this method is reputed to have stopped working since 9.10. (My only surviving 150 is on a 9.04 machine). If this method is truly kaputt, then your only plan B would be to set up udev rules to assign the devices correctly at boot. The relevant thread to show how to do this is [http://ubuntuforums.org/showthread.php?t=753434](http://ubuntuforums.org/showthread.php?t=753434)

Good luck.

---

### Post by zapstrap on 2010-05-24
Thanks for the info.  I ran the python script, and it works as promised.  This, unfortunately, did not solve the problem.  The script locks down the video devices as desired, however now the machine boots and I get no pvr150, and a blank screen when trying to tune the hvr1600 to an analogue channel.  I've gone from having three tuners to only the digital tuner in the hvr1600 card.  On the occasional boot that works, I get no audio on the hvr1600 card as often as not.  I had these two tuner cards in an older Asus P4P800-E Deluxe machine with a 3ghz single core processor.  Now they've been moved to a 2.66ghz core2 machine (ABIT LG-95C mobo), and the speed is great, but it'd be nice if the tuners actually worked.

---

### Post by klc5555 on 2010-05-25
> **zapstrap said:**
> Thanks for the info.  I ran the python script, and it works as promised.  This, unfortunately, did not solve the problem.  The script locks down the video devices as desired, however now the machine boots and I get no pvr150, and a blank screen when trying to tune the hvr1600 to an analogue channel.  I've gone from having three tuners to only the digital tuner in the hvr1600 card.  On the occasional boot that works, I get no audio on the hvr1600 card as often as not.  I had these two tuner cards in an older Asus P4P800-E Deluxe machine with a 3ghz single core processor.  Now they've been moved to a 2.66ghz core2 machine (ABIT LG-95C mobo), and the speed is great, but it'd be nice if the tuners actually worked.

Disappointing. 

But you only have two tuner cards. So (without establishing udev rules) if you blacklist the cx18 module, so that the machine only tries to load the pvr150 at boot, does the 150 consistently come up as /dev/video0 ? If it does, then you might try leaving the cx18 module blacklisted and starting the 1600 with a "modprobe cx18" line in the /etc/rc.local file instead. If the cx18 driver is loaded much later in the boot process than the ivtv, the /dev/videoX's may sort themselves out in a single repetitive order.


No or degraded audio on the analog side of the 1600 after bootup became less frequent for me after the 2.6.26 series kernels came into use, but was still common enough to be annoying. Normally reloading the driver module and reloading it was all that was required (sudo) -- "rmmod cx18" and "modprobe cx18".  However that, too, proved to be inconvenient, and so my "final" interim remedy about a year ago was to invoke a simple script at the end of the rc.local, which consisted of a "rmmod cx18" followed by a "sleep 5" and a "modprobe cx18". So at boot the cx18 for my two 1600 cards is always loaded, unloaded, and reloaded and I haven't had an audio failure with the cards since.

---

### Post by zapstrap on 2010-05-25
Good stuff.  It sounds like you're proposing two different possible  remedies.  The first would be to block loading the cx18 module, then  load it with a modprobe cx18 or something in a script run from rc.local.   The second would be to let the two modules load up, then nuke the cx18,  wait 5 seconds and reload it.  

The first solution seems better as it may solve the video[01] assignment  problem and the missing sound problem all in one swell foop.  So,  naturally I want that.  The only part I don't fully grasp is how to  "blacklist" the cx18 module?

---

### Post by klc5555 on 2010-05-26
> **zapstrap said:**
> Good stuff.  It sounds like you're proposing two different possible  remedies.  The first would be to block loading the cx18 module, then  load it with a modprobe cx18 or something in a script run from rc.local.   The second would be to let the two modules load up, then nuke the cx18,  wait 5 seconds and reload it.  

The first solution seems better as it may solve the video[01] assignment  problem and the missing sound problem all in one swell foop.  So,  naturally I want that.  The only part I don't fully grasp is how to  "blacklist" the cx18 module?

Two possible solutions, one for each problem.

First, to try to load the drivers and assign the /dev/videoXs in a consistent order, blacklist the cx18 module by adding it to the blacklist.conf file usually found under /etc/modprobe.d/ You can then have it load later in the boot process with a modprobe line in the rc.local. This is a type of trick which is frequently used to fix balky wireless driver issues in Ubuntu. Hopefully, the pvr150 will always land on /dev/video0 by this process, and the cx18 gets what's left (/dev/video1). Maybe.

Second problem: degraded or missing analog audio from the cx18 module after bootup. This usually requires that the cx18 be unloaded, then reloaded, whereupon the audio is fine. You can test this manually next time you notice missing 1600 audio by doing a "sudo rmmod cx18" followed by a "modprobe cx18". Mythbuntu tends to be more in-your-face than other distros when you do this, and you may have to stop the backend first. The device nodes for the cx18 will be assigned the same as they were previously after the reload.

I have 2 1600s (analog-only for DTA output capture --I don't use them for actual digital) on a Slackware remote backend. I found that one or the other would lack audio (or have degraded audio) after boot maybe one time in four. Accordingly I put a rmmod, sleep, modprobe script at the end ofthe rc.local so that the module loads, unloads, and reloads at every boot. Over the last year plus, this method has failed once (necessitating another reload from a prompt). Of course, since it's a Slack box it doesn't get rebooted all that often. 

The question for current Mythbuntu is, does the backend start up before rc.local finishes. This may cause a problem for the above solution. My Ubuntu 10.04 machines are frontend-only laptops (running Myth 0.21), so I don't know the answer.

---

### Post by zapstrap on 2010-06-03
So, I tried blacklisting the cx18 module and doing a modprobe cx18 in rc.local.  The cx18 driver refused to load, complaining about an unknown symbol in the module file cx18.ko.  The symbol is ir_codes_hauppauge_new_table.  I tried unblacklisting the module, and now I get the same complaint after booting when I run dmesg | grep cx18.  Perfect.  Now I have no tuners at all.

---

### Post by klc5555 on 2010-06-04
> **zapstrap said:**
> So, I tried blacklisting the cx18 module and doing a modprobe cx18 in rc.local.  The cx18 driver refused to load, complaining about an unknown symbol in the module file cx18.ko.  The symbol is ir_codes_hauppauge_new_table.  I tried unblacklisting the module, and now I get the same complaint after booting when I run dmesg | grep cx18.  Perfect.  Now I have no tuners at all.

This is outside my expertise, but so far as I know, the unknown symbol error usually happens when a module has not been properly compiled to the running kernel. That is, the kernel is different than the last time you tried to load the module, so that the module can't find the space the kernel has allocated for it. Usually in this case the module has to be compiled to the kernel actually being used.

It can, I think, also happen when the modules that define the symbol referenced by the cx18 have not been loaded by the kernel by the time modprobe/insmod is happening for the cx18. For ir_codes_hauppauge_new_table this might imply that perhaps ir-common and/or ir-keymaps are not being loaded at boot, as per [http://rswiki.csie.org/lxr/http/ident?i=ir_codes_hauppauge_new_table](http://rswiki.csie.org/lxr/http/ident?i=ir_codes_hauppauge_new_table)  

But again I have no kernel expertise, and I gladly defer to those who do who could set me straight.

---

### Post by zapstrap on 2010-06-11
I think I've got back to where I was.  Here's what I had to do:

cd /usr/src/v4l-dvb
sudo make install

...this fixed up the installation so the right version of the cx18 module is loaded.

After rebooting, the channels came back, but now I get the famous no-audio problem on the analogue side of the card.  I tried this:

sudo service mythtv-backend stop
sudo rmmod cx18

and got grief about the cx18 module being in use by cx18_alsa.  Next, I tried this:

sudo rmmod cx18_alsa
sudo rmmod cx18
sudo modprobe cx18
sudo modprobe cx18_alsa
sudo service mythtv-backend start

...I have sound! :)

I'll try blacklisting both the cx18_alsa and cx18 modules, then load them from rc.local next.  If it works, I may be able to get back to using acpi to wakeup the machine for recordings.


New problem:

The PVR-150 card next to the HVR-1600 is now misbehaving.  Every time the machine reboots, myth loses the PVR-150, and I have to stop the front-end, run the back-end, and rescan the channels on the card.  I get the usual bitching about failing to add new channels, yet I can see it's locking on all the analogue channels I have.  The weird thing is, when I get back to the front end, the PVR-150 will only properly tune channels 2-13.  Anything outside of this range shows up as static, even though the channels were found and in the database for the card.  UHF channnels were working initially.  I'd be surprised if the UHF part of the card died within a week of moving it from the old P4 machine to the new core2 machine.  I should probably put this in it's own thread, but the ivtv driver shows as part of the cx2341x module.  Is it possible this card is getting confused and using the wrong kernel module?

---

### Post by klc5555 on 2010-06-12
At least part of your problem appears to be a known timing issue with the 150 and 10.04: the backend is initializing before the 150's driver has loaded. A casualty perhaps of 10.04's alleged extra-zippy bootup speed.

One way around seems to have been to simply restart the backend (rather than stopping the backend and rescanning via mythtv-setup, as you seem to have been doing). Other workarounds appear to have involved various methods of delaying the starting of mythbackend at boot. One relevant thread appears to be here: [http://ubuntuforums.org/showthread.php?t=1481488&highlight=backend+timing](http://ubuntuforums.org/showthread.php?t=1481488&highlight=backend+timing)

Not sure at the moment about the UHF portion of the problem.

---

### Post by zapstrap on 2010-06-12
klc5555 u da man! :)

I think I've got it licked.  Here's what I did:

Step 1: Edit /etc/modprobe.d/blacklist.conf, and add the following at the end:

```
blacklist cx18
blacklist cx18_alsa
```

Step 2: Edit /etc/rc.local, and add the following at the end (above the last line: exit 0)

```
# See /etc/modprobe.d/blacklist.conf for backlisting of cx18 modules.
# Load it...
service mythtv-backend stop
modprobe cx18
sleep 1
modprobe cx18_alsa
sleep 4
# Unload it...
rmmod cx18_alsa
rmmod cx18
sleep 4
# Load it again...
modprobe cx18
sleep 1
modprobe cx18_alsa
service mythtv-backend start
```

I've rebooted several times, and everything now comes up, so far so good.  I'm not sure about all the sleep statements, as once I got it working consistently, I stopped fiddling with it.

The second problem, the PVR-150 not tuning above channel 13, turned out to be a configuration issue with the backend.  Here's what I did:

Exit the front end, launch MythTV Backend Setup from the System pull-down menu.

In General, on the second screen, Locale Settings, set the Channel frequency table to us-cable, or whatever your setup is.  Mine already was, but just to make life easier in the future, make sure it matches your setup.

In Video sources, select the source associated with your card, and make sure at the bottom of the screen, Channel frequency table is either default (which you just set) or is set to your system (us-cable in my case).  It was us-bcast, and that's what was burning me.

In Input connections, select your input, hit Scan for channels, and make sure Channel frequency table matches your configuration.  In my case it was right, and I had checked it so many times I thought I was going to go mad.  Had I realized the Video source was wrong, this would have been much easier.

This seems a little overly complex, but it's working now, so hurray for small miracles.

Thanks for all your suggestions.

---

### Post by klc5555 on 2010-06-12
Well done!

Glad it all works!

Now on to the important part --watching TV :)

Cheers!

---

### Post by BenTheN00bie on 2010-06-13
I am getting the same no audio behavior with my hvr-1600.  I have read the recommend solution, and even implemented the modprob additions to rc.local and the blacklist.conf.

It sounds (no pun intended) that I need to run the rmmod and modprobe commands until the sound starts working....

But, when I run the sudo rmmod cx18_alsa command I get the following error:
ERROR: Module cx18_alsa is in use

Any suggestions

And just for safe measure here is a lsmod fixed on cx18
cx18_alsa               6242  1 
cx18                  109952  1 cx18_alsa
dvb_core               85914  1 cx18
cx2341x                12404  1 cx18
v4l2_common            17381  4 cx18,cs5345,tuner,cx2341x
videodev               42138  4 cx18,cs5345,tuner,v4l2_common
tveeprom               11038  1 cx18
snd_pcm                70886  4 cx18_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    54148  17 cx18_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  2 cx18,i915


Thanks in advance

---

### Post by zapstrap on 2010-06-13
Is the backend still running?  If the driver's in use, well, it has to be by a process somewhere.  Try this first:

sudo service mythtv-backend stop

Then try the rmmod command.

After you're done, make sure you turn the backend back on: sudo service mythtv-backend start

Before bothering with rc.local, I wrote a little script so I could tune everything:

```
#!/bin/sh
# fix the tuners...

echo Shutting down myth backend...
sudo service mythtv-backend stop

echo Removing cx18 modules from kernel...
sudo rmmod cx18_alsa
sudo rmmod cx18
sleep 2

echo Inserting cx18 modules back into kernel...
sudo modprobe cx18
sudo modprobe cx18_alsa
sleep 2

echo Restarting backend...
sudo service mythtv-backend start

echo PVR-150 requires backend restart to be found, so it should work now.
echo done.

```The order of removing cx18_alsa and cx18 and reinstalling them is important too.

The note about the pvr-150 at the end is just there to remind me that the tuner requires the backend to be restarted in order to be found, lest I forget.

---

### Post by BenTheN00bie on 2010-06-14
I changed the script to stop mythbackend from starting at startup, rebooted the machine and then was able to perform the rmmod command on cx18 and cx18_alsa.

Then I modprobe cx18 and cx18_alsa and started the mythbackend service.  I then tested the sound on LiveTV but did not have any luck with the sound still.

I went ahead and stopped the service via a "stop mythbackend" and checked ps -e | grep -i mythbackend to check if any mythbackend services running.  For save measure I did perform the stop service mythbackend command just to make sure that service is completely stopped.  In both instances, it looked like mythbackend was not running on my computer. 

I went ahead and proceeded to run the rmmod commands, and yet again I get the "Module In use error", as I eluded to earlier.

I am I am wondering if I need to try to rmmod on all the other (dependent) modules when I ran the lsmod fixed on cx18.  

Thanks in advance.

---

### Post by zapstrap on 2010-06-14
What version of the cx18 driver are you running?  How did you build it?  I recall having to edit one of the build scripts to get it to work.

I don't think I've heard of anyone else having to touch cx18_alsa.  The only reason I removed it was because I couldn't remove the cx18 module unless I pulled cx18_alsa first.  If you can do an rmmod cx18 and not bother with cx18_alsa, you might be able to get your sound working that way:

sudo service mythtv-backend stop
sudo rmmod cx18
sleep 2
sudo modprobe cx18
sleep 2
sudo service mythtv-backend start

I admit I'm guessing.

---

### Post by klc5555 on 2010-06-14
It might be worth testing whether the sound is working in applications outside of mythtv. 

If sound is working outside mythtv, then it might be worth asking whether sound has ever worked, even defectively, in this mythtv installation with the 1600 (how about the dvb half of the tuner also or any other tuners?). After however many cold boots (not just warm restarts). If there is not and never has been any mythtv sound whatever from this installation, then the sound problem may not be the fault of the ever-wonky cx18 driver (which should kick right in after a single reload after boot, and should load correctly in a plurality of cold starts under any circumstances). Your problem may be a configuration or an alsa issue with the OS installation in general, or even something as simple as the mixer being muted.

---

