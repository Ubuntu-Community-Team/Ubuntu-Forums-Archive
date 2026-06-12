---
title: "Problems with composite in, and other features"
date: 2010-11-12
forum: Mythbuntu
---

### Post by Sum Guy on 2010-11-12
Since I've been posting several threads for help, I'd figure I'd try and keep the rest in one thread. The first problem is a composite input I'm trying to set up. The card is a Pinnacle card of some kind, marked Pinnacle Systems GmbH EMPTYV, and it uses a Conexant Fusion 878a chip. According to LinuxTV, this chip is supported by the V4L drivers (which I'm using), although I don't know about the card itself; it is a hybrid tuner, according to info on the Conexant chip, and it has on the back an antenna port, S-Video and Composite capture ports (I'm pretty sure), and a 3.5mm audio out (it doesn't appear to have onboard audio processing). I would like to set it up so that the audio in (fed in to the sound card) and the composite video are combined into one stream which can be recorded or streamed through LiveTV. I've followed the instructions for the Hauppauge PVR series to set up composite, and I can get the card to display the video footage, but it is severely distorted by static so that it is almost not visible (it looks like analog TV static). Strangely, the inputs on the card appear as composite0, composite1, composite2 and the S-Video in. There are no options for the card's tuner. I also don't know how to associate the Line In on the sound card with the Video Source I created for it. Does this sound like a faulty card, faulty driver, or bad configuration?

I also have a minor problem when starting up. The computer is a combined frontend/backend using its external IP address to allow external backends/frontends. The problem is that MythWelcome tries to poll the server before the WiFi connects, meaning that it can't see the backend, so it complains, and for some reason changes the theme to Terra (only the welcome screen, not the front end, and only the actual appearance, not the setting). Is there any way to make the backend accept connections on the loopback device and the external IP address, to eliminate the need for a network to use the machine, but still allow external connections? Failing that, is there a way to make the frontend/MythWelcome wait until the network connects before polling the server?

Finally, what is the best way to install 3rd party themes, the ones available in tar.gz and tar.bz2?

Thanks to all of you for this help, its making set up far more painless than it should be with these (relatively minor) problems.

---

### Post by Sum Guy on 2010-11-14
Just updated the post with some info I missed the first time around - the inputs as seen by MythTV and that the card itself doesn't appear to be explicitly stated as supported by Linux, just the tuner chip. Any ideas?

---

### Post by Sum Guy on 2010-11-15
OK, failing that, can anyone confirm if the Leadtek Winfast DTV 1000T composite in works correctly?

Also, any input on the themes, or the network interface? (2nd paragraph and last 2 lines).

Thanks.

EDIT: I was trying to test the card again, on my remote front end, and it killed LiveTV in both front ends, even after I tried deleting the card from setup altogether. Upon choosing LiveTV from the menu, the front end displays a loading screen, then returns to the menu. The back end says the remaining cards are working fine, and doesn't seem to be complaining. In addition, LiveTV was working fine immediately before attempting to use the tuner when I first turned on LiveTV and it displayed TV from the working tuners. Note that media streaming still works and that there is enough memory for MythTV to record another 2 hours of LiveTV (currently using a rather small hard drive).

Any ideas?

---

### Post by Sum Guy on 2010-11-17
For some reason, after a couple of reboots, LiveTV is again working fine. Anyway, I still need to organize some way of capturing analogue composite signals and sorting out the weird network problem. Can anyone recommend a hybrid tuner with composite capture that works? I would rather get a hybrid card so I can get full use of the extra tuner. Thanks.

---

### Post by nickrout on 2010-11-18
> **Sum Guy said:**
> For some reason, after a couple of reboots, LiveTV is again working fine. Anyway, I still need to organize some way of capturing analogue composite signals and sorting out the weird network problem. Can anyone recommend a hybrid tuner with composite capture that works? I would rather get a hybrid card so I can get full use of the extra tuner. Thanks.

delay the startup of mythbackend until the card is connected.

---

### Post by Sum Guy on 2010-11-18
I managed to get LiveTV back up and running, but the main problem is that even when this card works, it gives a completely unusable picture. I was hoping someone could point me to a hybrid card with composite capture working in MythTV as an alternative to trying to get this to work. Either PCI or USB is fine.

Additionally, any way to get the front end on my combined machine to stop trying to connect to the back end until the network connects would be appreciated.

Thanks for the help, anyway.

---

### Post by nickrout on 2010-11-20
edit the script that starts mythfrontend to add a test for the backend running before it starts the frontend.

---

### Post by Sum Guy on 2010-11-22
Do you know where I can find this script, and will editing this script delay MythWelcome?

I've also started having some stability issues that seem to be related to RAM. The computer in question is a 2.66GHz P4 with 1.5Gb of RAM, but according to the backend status it runs with only 30Mb RAM free, and it often crashes. When it crashes, the last second of sound loops with a black screen for a while, then it reboots. I'm using a dual tuner card that is allowed to run 4 recordings (1 extra per tuner), but I have a large surplus of RAM over what the wiki suggests (2*512Mb for 2 tuners), plus mostly unused, 1Gb of swap. Note that it is recording 720p video, with occasional 1080i recordings, both of which are digital TV (so no encoding needed) and it often crashes while playing a recording even if otherwise idle. This behavior is rather annoying, partly because it interrupts both viewing and recording, but it also seems to be corrupting the ad break database, and I don't know how to run the MySQL repair program. Do I need more RAM, or do I need to change a setting?

Thanks again for all this help!:)

---

### Post by nickrout on 2010-11-22
/usr/bin/mythfrontend

we can't read your log files for you so can't comment on the crashes.

---

### Post by Sum Guy on 2010-11-23
I tried adding an until statement to the start of the script, in between the first comments and the first command, before it proceeds with anything else, with no effect. The statement:

until [ "$(pidof mythbackend)" ]; do
       wait 5
done

If this works as intended, the idea is to get the mythfrontend script to check for mythbackend, then wait 5 seconds and try again, in a loop. When mythbackend is detected, the script proceeds as normal.

As this is not happening, clearly I'm doing something wrong. Is this a suitable manner to add a test for mythbackend? Is this the script that starts mythwelcome, when it is used? As I'm using mythwelcome, this is where the error occurs, with the front end itself booting normally when triggered manually.

Also, I'll check the logs soon, and post back with more info.

Thanks again for the help.

---

### Post by nickrout on 2010-11-23
> **Sum Guy said:**
> I tried adding an until statement to the start of the script, in between the first comments and the first command, before it proceeds with anything else, with no effect. The statement:



If this works as intended, the idea is to get the mythfrontend script to check for mythbackend, then wait 5 seconds and try again, in a loop. When mythbackend is detected, the script proceeds as normal.

As this is not happening, clearly I'm doing something wrong. Is this a suitable manner to add a test for mythbackend? 

I wonder if your logic is backwards? I get awfully confused by true and false in programming, try (and i may be wrong)

```
while [ "$(pidof mythbackend)" ]; do
       wait 5
done
```

---

### Post by Sum Guy on 2010-11-24
Strangely, preliminary testing of your suggested modification indicates that it also failed, but somehow stopped MythWelcome from changing themes when it didn't see the backend. Unfortunately, it has disabled booting of MythFrontend, where the Welcome screen has the button pressed, but no front end appears. I found a file called mythwelcome in that directory, but it does not appear to contain human readable information.

Thanks for suggesting that command.

---

### Post by Sum Guy on 2010-11-25
OK, the theme change problem is solved. After a bit of searching, I happened upon this thread:
[http://ubuntuforums.org/showthread.php?t=1068511](http://ubuntuforums.org/showthread.php?t=1068511)

It involves an unrelated problem, but the problem's solution involved modifying the mythfrontend script to modify the behavior of mythwelcome. By editing the autostart script (~/.config/autostart/mythtv.desktop), instructing it to execute a script instead of mythwelcome, and writing the script with 3 commands, mythbackend, sleep 8, and mythfrontend --service (the original command in the script), I was able to delay the frontend's start up without delaying the backend. Interestingly, mythfrontend --service starts the backend if it isn't running, but the option appears to be part of starting mythwelcome as well. In addition, simply delaying the command, without starting the backend, seems to mean that the frontend can connect to the database (as the network has connected), even if the backend isn't running, and although it complains that there is no backend, the theme doesn't revert to Terra. It seems that the theme issue is related to the database's availability, rather than the backend.

I'll check through the logs and post relevant info shortly.

Thanks again.

---

### Post by Sum Guy on 2010-12-02
Sorry for the delay.

I checked the logs shortly after a crash, and found that the only item in the log that coincides with the time of the crash is an auto expiry and subsequent deletion. I'm sure the 2.66GHz P4 CPU can take on 1 deletion and playback on one frontend simultaneously, especially on XFS and with slow file deletion, and I'm sure the hard drive can also handle it, since it uses SATA. As such, the only thing I can think of is RAM shortage, but I can't work out how the backend can't get by on 1.5GB of RAM when the minimum is a lot less. Is there any way to see if MythTV is using RAM inefficiently? It seems to run with less than 100MB free after the RAM fills up past this point, even when idle for a short time.

Also, I had a one time problem with the tuner cards, where all recordings on the unit failed on one day (2 recordings, one per tuner). The logs said that the cards malfunctioned, but the next day (after a cold boot) the tuners were fine, which seems to indicate software problems. Is this something that might happen again?

I also have a slight problem with tuner names. The first tuner is under the names 1 and 6, while the second is called 2 and 7 (2 recordings max per tuner). Is there any way to renumber the tuners?

Finally, I'm still looking for suggestions on a hybrid tuner with a working composite input.

Thanks for the help so far, its helped to improve the system a lot.

EDIT: I also forgot to mention a weird problem I'm having with MythWeb remote, which has slowed down substantially for no apparent reason. Does MythWeb use its own system to control the frontend, or does it use the network interface? If it does, would using a different network remote interfere with its function by slowing it down, or simply stopping it working? Thanks.

EDIT 2: Something else I forgot, I can't get the screen resolution set correctly. For some reason the screen extends slightly beyond the display in each direction. Strangely, all video appears to be displayed perfectly sized for the display. I can't find any way to set the screen up so it matches the display perfectly. I'm using DVI out on a Radeon X1650 (open source drivers only) through a HDMI adapter into a 720p TV.

Thanks for the help.

---

### Post by nickrout on 2010-12-03
> **Sum Guy said:**
> Sorry for the delay.

I checked the logs shortly after a crash, and found that the only item in the log that coincides with the time of the crash is an auto expiry and subsequent deletion. I'm sure the 2.66GHz P4 CPU can take on 1 deletion and playback on one frontend simultaneously, especially on XFS and with slow file deletion, and I'm sure the hard drive can also handle it, since it uses SATA. As such, the only thing I can think of is RAM shortage, but I can't work out how the backend can't get by on 1.5GB of RAM when the minimum is a lot less. Is there any way to see if MythTV is using RAM inefficiently? It seems to run with less than 100MB free after the RAM fills up past this point, even when idle for a short time.

Also, I had a one time problem with the tuner cards, where all recordings on the unit failed on one day (2 recordings, one per tuner). The logs said that the cards malfunctioned, but the next day (after a cold boot) the tuners were fine, which seems to indicate software problems. Is this something that might happen again?

I also have a slight problem with tuner names. The first tuner is under the names 1 and 6, while the second is called 2 and 7 (2 recordings max per tuner). Is there any way to renumber the tuners?

Finally, I'm still looking for suggestions on a hybrid tuner with a working composite input.

Thanks for the help so far, its helped to improve the system a lot.

EDIT: I also forgot to mention a weird problem I'm having with MythWeb remote, which has slowed down substantially for no apparent reason. Does MythWeb use its own system to control the frontend, or does it use the network interface? If it does, would using a different network remote interfere with its function by slowing it down, or simply stopping it working? Thanks.

EDIT 2: Something else I forgot, I can't get the screen resolution set correctly. For some reason the screen extends slightly beyond the display in each direction. Strangely, all video appears to be displayed perfectly sized for the display. I can't find any way to set the screen up so it matches the display perfectly. I'm using DVI out on a Radeon X1650 (open source drivers only) through a HDMI adapter into a 720p TV.

Thanks for the help.

faulty ram? try memtest

---

### Post by Sum Guy on 2010-12-03
Your suggestion for the instability was spot on! I'm pretty sure I can figure out why the problem is occurring now, thanks again for suggesting memtest.

Any ideas with respect to the other issues?

Thanks again.

---

### Post by nickrout on 2010-12-03
> **Sum Guy said:**
> 

Any ideas with respect to the other issues?



Briefly:

**tuner numbers** - the only way to fix it is to delete all tuners in backend setup and start again from scratch.

If you do, set up each one as one tuner only, then go back and set to a higher number. 

**hybrid tuner?**

sorry can't help

**screen res** you have overscan, it's very common and the BEST way to fix it is if your TV can be set to pixel mapping. Look here for more details:

[http://pixelmapping.wikispaces.com/Pixel+mapping+explained](http://pixelmapping.wikispaces.com/Pixel+mapping+explained)

**mythweb remote** - I believe this uses the telnet interface, try it via the telnet command and see if you can see any errors happening

---

### Post by Sum Guy on 2010-12-25
Sorry for the delayed response.

I now have a lot more information with respect to system stability. Despite the motherboard's ATX 2.x power connectors, the PSU is only ATX 1.x compliant. Could the missing power lines cause this instability?

In addition, sensor data indicates that the GPU and PSU are running hot. The most worrying sensor data is that the 3.3 and 5 volt lines report around 1.3V. This sounds extreme considering that the computer is still running, but could it mean that the PSU is causing problems?

Finally, when I changed the theme, I noticed that the stability issues changed slightly. For instance, some actions inside MythTV led to the frontend quitting, returning me to MythWelcome. In addition, it started crashing when streaming to a remote frontend, something which it didn't do before. The crash frequency on the local frontend seemed to reduce slightly. To mitigate this I switched it to the Mythbuntu theme. All the themes shipped with the OS.

Thanks for helping out so far.

---

