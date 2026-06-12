---
title: "Sound Stops Working"
date: 2011-09-17
forum: Multimedia Software
---

### Post by DaimyoKirby on 2011-09-17
On my computer, a Pavilion dv6000, running Ubuntu 11.04, my sound is acting funny.

I'll boot up my computer, and the sound will probably be working. But then, at some random time when I'm using it, my sound will just all of a sudden stop working.

I found a fix for it [here]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"), using this code:

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r) libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r)  libasound2; killall pulseaudio; rm -r ~/.pulse*
```

It works, by what seems to be reinstalling some sound-related stuff, and when I restart my computer, the sound will work fine.

But just today, my sound has stopped working twice now (normally it only happens every other day or so), and I find it very annoying to have to keep running this and restarting my computer.

So does anyone know if there's anything I can do to permanently fix my sound?

---

### Post by DaimyoKirby on 2011-09-17
Just let me know if you need any other information. (bump)

---

### Post by DaimyoKirby on 2011-09-18
Anyone?

Please...?...

---

### Post by DaimyoKirby on 2011-09-18
Found the fix:

I opened up PulseAudio Device Chooser, and set it to start on session login; I believe that's the fix. But I also changed some other settings, so I can't really be sure.

Either way, it works now. Just let me know if you want/need to know exactly what I changed.

---

### Post by DaimyoKirby on 2011-09-22
Nevermind...
That worked for a little while, but now it stopped working again.

I've gone back to running through the steps on the [website]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") I mentioned in my first post.

So I'm still trying to find if anyone knows what I can do...

---

### Post by DaimyoKirby on 2011-09-22
**EDIT:** Sorry, accidental double post.

Nevermind...
That worked for a little while, but now it stopped working again.

I've gone back to running through the steps on the [website]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") I mentioned in my first post.

So I'm still trying to find if anyone knows what I can do...

---

### Post by pytheas22 on 2011-09-24
Is pulseaudio running when your sound stops working?  To check, see if:

```
ps -e | grep pulse
```

returns any output.  (If it does not, pulseaudio is not running.)  The issue could simply be that pulseaudio is crashing periodically for some reason, in which case a simple band-aid solution would be to restart it every so often with a cron job.

---

### Post by DaimyoKirby on 2011-09-24
Ok, I will. Right now, though, my sound is somehow working (your hypothesis of the problem may be correct), but when it stops working again, I will post the results of your code.

---

### Post by DaimyoKirby on 2011-09-25
Ok, so here are the results:
```
alden@alden-laptop:~$ ps -e | grep pulse
 1452 ?        00:00:29 pulseaudio
```

---

### Post by pytheas22 on 2011-09-25
Well, it looks like pulseaudio was still running when the problem occurred, so that hypothesis doesn't seem to be the key.  I wonder if anything relevant is being logged to syslog, however.  What output do you get from:
```

grep pulse /var/log/syslog
```

when the problem occurs?

---

### Post by DaimyoKirby on 2011-09-25
```
alden@alden-laptop:~$ grep pulse /var/log/syslog
Sep 24 08:29:36 alden-laptop pulseaudio[1416]: pid.c: Failed to open PID file '/home/alden/.pulse/53742b339b16123983676d184e6976b1-runtime/pid': No such file or directory
Sep 24 08:29:36 alden-laptop pulseaudio[1416]: pid.c: Failed to open PID file '/home/alden/.pulse/53742b339b16123983676d184e6976b1-runtime/pid': No such file or directory
Sep 24 08:29:36 alden-laptop pulseaudio[14929]: module.c: Module "module-zeroconf-discover" should be loaded once at most. Refusing to load.
Sep 24 08:29:36 alden-laptop pulseaudio[14929]: module-gconf.c: pa_module_load() failed
Sep 24 08:29:36 alden-laptop pulseaudio[14943]: pid.c: Daemon already running.
Sep 24 08:29:36 alden-laptop pulseaudio[14944]: pid.c: Daemon already running.
Sep 24 08:29:36 alden-laptop pulseaudio[14945]: pid.c: Daemon already running.
Sep 24 08:29:36 alden-laptop pulseaudio[14946]: pid.c: Daemon already running.
Sep 24 08:29:36 alden-laptop pulseaudio[14947]: pid.c: Daemon already running.
Sep 24 08:29:36 alden-laptop pulseaudio[14948]: pid.c: Daemon already running.
Sep 24 08:35:21 alden-laptop pulseaudio[1461]: module.c: Module "module-zeroconf-discover" should be loaded once at most. Refusing to load.
Sep 24 08:35:21 alden-laptop pulseaudio[1461]: module-gconf.c: pa_module_load() failed
Sep 24 08:35:21 alden-laptop pulseaudio[1461]: module-rtp-send.c: connect() failed: Network is unreachable
Sep 24 08:35:21 alden-laptop pulseaudio[1461]: module.c: Failed to load  module "module-rtp-send" (argument: "source=@DEFAULT_MONITOR@ loop=0"): initialization failed.
Sep 24 08:35:21 alden-laptop pulseaudio[1461]: module-gconf.c: pa_module_load() failed
Sep 24 23:12:25 alden-laptop pulseaudio[1452]: module.c: Module "module-zeroconf-discover" should be loaded once at most. Refusing to load.
Sep 24 23:12:25 alden-laptop pulseaudio[1452]: module-gconf.c: pa_module_load() failed
Sep 24 23:12:25 alden-laptop pulseaudio[1452]: module-rtp-send.c: connect() failed: Network is unreachable
Sep 24 23:12:25 alden-laptop pulseaudio[1452]: module.c: Failed to load  module "module-rtp-send" (argument: "source=@DEFAULT_MONITOR@ loop=0"): initialization failed.
Sep 24 23:12:25 alden-laptop pulseaudio[1452]: module-gconf.c: pa_module_load() failed
Sep 25 01:00:31 alden-laptop pulseaudio[1452]: pid.c: Failed to open PID file '/home/alden/.pulse/53742b339b16123983676d184e6976b1-runtime/pid': No such file or directory
Sep 25 01:00:31 alden-laptop pulseaudio[1452]: pid.c: Failed to open PID file '/home/alden/.pulse/53742b339b16123983676d184e6976b1-runtime/pid': No such file or directory
Sep 25 01:00:35 alden-laptop pulseaudio[23460]: module.c: Module "module-zeroconf-discover" should be loaded once at most. Refusing to load.
Sep 25 01:00:35 alden-laptop pulseaudio[23460]: module-gconf.c: pa_module_load() failed
Sep 25 01:00:35 alden-laptop pulseaudio[23489]: pid.c: Daemon already running.
Sep 25 01:00:35 alden-laptop pulseaudio[23490]: pid.c: Daemon already running.
Sep 25 01:00:35 alden-laptop pulseaudio[23491]: pid.c: Daemon already running.
Sep 25 01:00:35 alden-laptop pulseaudio[23492]: pid.c: Daemon already running.
Sep 25 01:00:35 alden-laptop pulseaudio[23493]: pid.c: Daemon already running.
Sep 25 01:00:35 alden-laptop pulseaudio[23494]: pid.c: Daemon already running.
Sep 25 01:00:35 alden-laptop pulseaudio[23495]: pid.c: Daemon already running.
Sep 25 01:00:35 alden-laptop pulseaudio[23496]: pid.c: Daemon already running.
Sep 25 08:06:59 alden-laptop pulseaudio[1556]: module.c: Module "module-zeroconf-discover" should be loaded once at most. Refusing to load.
Sep 25 08:06:59 alden-laptop pulseaudio[1556]: module-gconf.c: pa_module_load() failed
Sep 25 08:07:00 alden-laptop pulseaudio[1556]: module-rtp-send.c: connect() failed: Network is unreachable
Sep 25 08:07:00 alden-laptop pulseaudio[1556]: module.c: Failed to load  module "module-rtp-send" (argument: "source=@DEFAULT_MONITOR@ loop=0"): initialization failed.
Sep 25 08:07:00 alden-laptop pulseaudio[1556]: module-gconf.c: pa_module_load() failed
```

---

### Post by pytheas22 on 2011-09-25
I'm not positive, but I think, based on that output, that pulseaudio is trying to start multiple times, which it shouldn't.

When the sound stops working, can you fix it by killing all of the existing pulseaudio daemons and then restarting pulseaudio?  To kill the existing daemons, first find their PIDs using the command:

```
ps -e | grep pulse
```

You will get a result like:

```
 1452 ?        00:00:29 pulseaudio
```

where 1452 is the PID.  (If there is more than one line, it means you have multiple pulseaudio processes running, and you will need to kill each one.)

To kill the process, do:

```
kill 1452
```

(or whatever the PID is).

Then run "ps -e | grep pulse" again to make sure the process is dead.  (If it's not, try typing "kill -9 1452")

Then restart pulseaudio with:
```

pulseaudio
```

Does the sound work now?

---

### Post by gaelicdarkwater on 2011-09-25
Hi, I'm having a similar problem.  I installed Natty and have had intermittent sound problems.  I'll get it to work, and it will be fine for a few days.  Then I'll get an automatic update and woosh, no sound again. Most times I've just had to go into systems settings, then sounds, then tell it to use my USB speakers, not analog speakers.  Today however, that's not working.  

When I typed in ps -e | grep pulse I got:
 1702 ?        00:01:49 pulseaudio

When I did grep pulse /var/log/syslog I got:
Sep 25 16:30:33 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:30:33 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:30:33 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:30:33 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:30:33 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:30:33 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:30:33 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:30:33 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:30:33 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:57:38 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:16 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:16 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:16 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:16 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:16 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:16 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:16 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:16 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:24 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:25 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:25 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:25 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:25 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:25 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:25 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:27 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:27 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:27 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:27 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:27 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:27 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:27 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:27 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:27 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:27 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:27 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:27 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:27 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:27 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:27 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:27 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:51 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:53 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:53 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:53 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:53 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:58:53 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:58:53 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:59:23 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:59:23 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:59:23 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:59:23 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:59:23 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:59:23 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:59:23 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 16:59:23 Darkwater pulseaudio[2702]: sink-input.c: Failed to create sink input: sink is suspended.
Sep 25 16:59:43 Darkwater pulseaudio[2702]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Sep 25 17:17:55 Darkwater pulseaudio[2702]: module.c: Module "module-zeroconf-discover" should be loaded once at most. Refusing to load.
Sep 25 17:17:55 Darkwater pulseaudio[2702]: module-gconf.c: pa_module_load() failed
Sep 25 17:37:40 Darkwater pulseaudio[1702]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Sep 25 17:37:40 Darkwater pulseaudio[1702]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_usb_audio'. Please report this issue to the ALSA developers.
Sep 25 17:37:40 Darkwater pulseaudio[1702]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

I'm using Ubuntu 11.04  Natty Narwhal
 when I enter "apt-cache policy pkgname" I get N: Unable to locate package pkgname


I did report a bug at ALSA as it said to, but I'm still trying to find a way to get my sound back.

---

### Post by DaimyoKirby on 2011-09-25
This is everything that I inputted, and all that was outputted, following your instructions to the letter:
```
alden@alden-laptop:~$ ps -e | grep pulse
 1404 ?        00:00:00 pulseaudio
alden@alden-laptop:~$ kill 1404
alden@alden-laptop:~$ ps -e | grep pulse
 1899 ?        00:00:00 pulseaudio
alden@alden-laptop:~$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```

What does it mean if something showed up when I checked again with "ps -e | grep pulse"? Do I have to keep killing them until nothing shows up when I check?

---

### Post by .... on 2011-09-25
If the sound device keeps disappearing from aplay, the problem runs deeper than pulseaudio.

It would be interesting to see any dmesg output when your sound stops working.

---

### Post by pytheas22 on 2011-09-26
**gaelicdarkwater**: the error messages you're getting are different, so it's not certain that your problem is the same.  Unfortunately, after googling a little I'm not sure what the problem is or how you might fix it.

**DaimyoKirby**: hmmm, it seems that pulse is automatically respawning itself whenever the process is killed--that's why it keeps appearing with a new PID.  I'm not positive what to make of that.

Both of you might want to try just uninstalling pulseaudio altogether.  There are instructions in the second post of [this thread]("http://ubuntuforums.org/showthread.php?t=1432747") for doing that easily.  The graphical volume tools may not work afterwards, but you should still be able to control the volume by typing "alsamixer" in a terminal.

---

### Post by lidex on 2011-09-27
> hmmm, it seems that pulse is automatically respawning itself whenever the process is killed--that's why it keeps appearing with a new PID. I'm not positive what to make of that.
That's default behavior.

@DaimyoKirby
Try resetting your pulse configuration.
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Next this output:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

And more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by DaimyoKirby on 2011-09-27
Hey, just so you all know, my sound has been working fine lately (I reinstalled PulseAudio); I have a little hunch it might have been my speakers overheating, but I have no way to know for sure. I'll keep this page bookmarked in case it stops working again, in which case I'll try your suggestion, lidex, right away, and tell you what happens.

Thanks everyone for your wonderful help! Let's all hope my sound keeps working, and I never have to return to this page for my computer again.

---

### Post by DaimyoKirby on 2011-09-30
Ok, so I installed Xubuntu, removing Ubuntu, and my sound stopped working. Even though the problem might have changed, I tried your code, lidex, anyway.

The output is [here]("http://www.alsa-project.org/db/?f=64d393c6c745a8e3a98a77a5b629ce00a5ed7e65"), and it seems to me like I don't have any sound stuff installed, judging by the output***.

Am I right in guessing?
Should I now try starting at the beginning of this thread, and start with your first troubleshooting?

*****EDIT:**
And this was the output of the two commands you told me to run after rebooting:
```
alden@Laptop:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for alden: 
Specified filename /dev/dsp* does not exist.
Specified filename /dev/seq* does not exist.
alden@Laptop:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-09-30 23:26:21--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-09-30 23:26:24--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,247      58.7K/s   in 0.5s    

2011-09-30 23:26:28 (58.7 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.w2p66IDrWZ/alsactl.tmp: No such file or directory
Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=64d393c6c745a8e3a98a77a5b629ce00a5ed7e65

Please inform the person helping you.
```

---

