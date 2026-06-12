---
title: "Running Jack as root to enable realtime - is there another way?"
date: 2008-04-02
forum: Multimedia Production
---

### Post by peterdines on 2008-04-02
I have to run Jack as root to get it to use the realtime flag. Consequently, only apps also running as root can connect to Jack. 

Is there an easier way to do this with setuid or some other trickery? Otherwise, what's the point of having application menu entries for Jack and apps that use it?

---

### Post by Stochastic on 2008-04-03
hmm, you really shouldn't need to do that with jack.

Are you running the realtime kernel?

---

### Post by eric71 on 2008-04-04
You need to make sure you have an audio group and that your user ia in it. Realtime priorities are given only to the audio group. You also need to sudo execute this command in a terminal>

sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'

---

### Post by peterdines on 2008-04-05
Hmmmm, I'm a member of the audio group - it was working for a while, then the gremlins changed something and now only root can run Jack with the realtime flag set.

edit: whoops, my mistake, now Jack won't run for a regular user at all, realtime flag or not.Could this have something to do with the way I'm loading the firmware for my m-audio USB sound card?

---

### Post by Stochastic on 2008-04-05
Well now you'll need to post some error messages before we can guess the problem/solution.  Turn the verbose flag on in settings and post what spews out of the messages window along with your settings and how you loaded your soundcard.

---

### Post by peterdines on 2008-04-07
OK, this is weird... now it seems to work for me as a non root user, but I don't think it's setting the realtime properly:

```
15:49:14.857 Patchbay deactivated.
15:49:14.905 Statistics reset.
15:49:15.058 MIDI connection graph change.
JACK tmpdir identified as [/dev/shm]
15:49:15.126 MIDI connection change.
15:49:50.364 Startup script...
15:49:50.364 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
sh: artsshell: not found
15:49:50.590 Startup script terminated with exit status=32512.
15:49:50.590 JACK is starting...
15:49:50.590 /usr/bin/jackd -v -R -dalsa -dhw:1,0 -r44100 -p256 -n2 -i2 -o2 -zt
15:49:50.597 JACK was started with PID=7040 (0x1b80).
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
apparent rate = 44100
creating alsa driver ... hw:1,0|hw:1,0|256|2|44100|2|2|nomon|swmeter|-|32bit
control device hw:1
new client: alsa_pcm, id = 1 type 1 @ 0x805bab0 fd = -1
configuring for 44100Hz, period = 256 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback
Triangular dithering at 16 bits
JACK: unable to mlock() port buffers: Cannot allocate memory
new buffer size 256
JACK: unable to mlock() port buffers: Cannot allocate memory
registered port alsa_pcm:capture_1, offset = 1024
registered port alsa_pcm:capture_2, offset = 2048
registered port alsa_pcm:playback_1, offset = 0
registered port alsa_pcm:playback_2, offset = 0
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
7040 waiting for signals
load = 0.1895 max usecs: 22.000, spare = 5782.000
15:49:52.649 Server configuration saved to "/home/peter/.jackdrc".
15:49:52.651 Statistics reset.
15:49:52.653 Client activated.
15:49:52.655 Audio connection change.
15:49:52.687 Audio connection graph change.
new client: qjackctl-7034, id = 2 type 2 @ 0xb6b5f000 fd = 15
++ jack_rechain_graph():
client alsa_pcm: internal client, execution_order=0.
client qjackctl-7034: start_fd=5, execution_order=0.
client qjackctl-7034: wait_fd=10, execution_order=1 (last client).
-- jack_rechain_graph()
JACK tmpdir identified as [/dev/shm]
cannot lock down memory for RT thread (Cannot allocate memory)
load = 0.3704 max usecs: 32.000, spare = 5772.000
load = 0.4350 max usecs: 29.000, spare = 5775.000
load = 0.5707 max usecs: 41.000, spare = 5763.000
load = 0.5524 max usecs: 31.000, spare = 5773.000
load = 0.5260 max usecs: 29.000, spare = 5775.000
load = 0.5301 max usecs: 31.000, spare = 5773.000
load = 0.5493 max usecs: 33.000, spare = 5771.000
load = 0.5589 max usecs: 33.000, spare = 5771.000
load = 0.5724 max usecs: 34.000, spare = 5770.000
```

Here's the contents of /etc/udev/rules.d/42-madfuload.rules:

```
# madfuload.rules - udev rules for loading firmware into M-Audio DFU devices

# DEVPATH=="/*.0" selects interface 0 only
# (some udev versions don't work with SYSFS{bInterfaceNumber})

# Audiophile
# ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2803/*", RUN+="/usr/local/sbin/madfuload -l -n -f /usr/local/share/usb/maudio/ma003101.bin"
# MobilePre
# ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2804/*", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma004103.bin"
# Sonica
# ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2805/*", RUN+="/usr/local/sbin/madfuload -l -n -f /usr/local/share/usb/maudio/ma005101.bin"
# Transit
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2806", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma006100.bin -D $env{DEVNAME}"
# ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2806/*", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma006100.bin"
# Ozone
# ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/2808/*", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma008100.bin"

# vim: ft=conf
```

I'm pretty sure if I reboot in a few minutes, it won't work for me at all. This has been what it's like for the past few days.

---

### Post by gravometric on 2008-04-28
I've got the same problem with Hardy Final.  I can run in realtime only if I ```
gksudo qjackctl
```

the following is in my /etc/security/limits.conf file:
```
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

@audio          -       rtprio          99

# End of file
```

I even had to create an "audio" group because there was none.  Ubuntu said I was a member of it, but there was no "audio" group. :confused:  Anyway, I'm guessing from here I've got to figure out what files the "audio" group needs to be assigned to.  Any suggestions other than the /dev files which already have their permissions set for the audio group?

---

### Post by Endolith on 2008-05-07
Same problem here.

> JACK: unable to mlock() port buffers: Cannot allocate memory

cannot lock down memory for RT thread (Cannot allocate memory)

It works as sudo, but not as regular user.

I did the commands [here]("https://help.ubuntu.com/community/UbuntuStudioPreparation#head-65151de671e4c5f7a362c970e2c55f035084534a") to get rid of the "cannot use real-time scheduling (FIFO at priority 10)" error.  Why does this have to be so difficult?  I thought they had it working out of the box by now.

---

### Post by Endolith on 2008-05-07
> **Endolith said:**
> I did the commands [here]("https://help.ubuntu.com/community/UbuntuStudioPreparation#head-65151de671e4c5f7a362c970e2c55f035084534a")

Oh wait.  The "memlock" line was removed from that page for Hardy, which I assumed meant it wasn't necessary anymore, but "memlock" in limits.conf and an error that says "cannot lock down memory" seem kind of related, huh?  :)  So I'm guessing that line *is* actually needed.  I wonder why it was removed.

---

