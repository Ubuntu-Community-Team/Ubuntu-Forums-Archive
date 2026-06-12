---
title: "Getting MPD (Media Player Daemon) to start on reboot"
date: 2013-12-07
forum: Multimedia Software
---

### Post by cryptotheslow on 2013-12-07
Hi,

I'm trying to get MPD set up on a headless 12.04 server. As the universe repo version is way out of date I installed it from source.

It works fine if I ssh in and start it with my usual login, likewise if I su to root I can start it fine (either way with the command *mpd /etc/mpd.conf* )

What is being problematic is to get it to start at boot time as a service or automatically.

I have tried calling it from /etc/rc.local and by creating an upstart config for it based on the upstart script I found here: [https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/910567](https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/910567), either way it's either not starting at all or it is bailing out for some reason.

Using the upstart method if I add some "logger" commands to the script I can see the log entries in /var/log/syslog, so I know that upstart is picking it up and trying at least.

I suspect I am missing some environment or path variables when trying to get it started like this..... and it's driving me maaaad!

Any ideas?

Thanks
crypto

---

### Post by tgalati4 on 2013-12-08
I presume that you have a static IP address set up and you have the addresses for both the server and client in /etc/hosts.

The upstart script expects configuration files in /etc/default (/etc/default/mpd in this case).

You would have to go through the section on creating the PID directory and file to make sure it is defined in your mpd configuration file and that the script is creating it properly.  That would cause mpd to stall.

---

### Post by cryptotheslow on 2013-12-08
At the moment eth0 (ethernet to the LAN) is set as static while eth1 (3G broadband interface to the internet) is set as dynamic....
 
```
crypto@ubuserver:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.67
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255

# The secondary network interface
auto eth1
iface eth1 inet dhcp
```

I can certainly change eth1 to static as well.

What's the need for the entries in the hosts file? At the moment it only has loopback entries for the server.....
```
crypto@ubuserver:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    ubuserver.lan    ubuserver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

I've had a look what's in /etc/default, at the moment the main mpd conf file is at /etc/mpd.conf - I take it the conf files in /etc/default are something else entirely? I notice some of them don't actually contain anything e.g. the one for cron is just 3 commented out lines, so maybe I can just create an empty file in there for mpd as well.

As for the PID file - I currently have that option disabled in mpd.conf - good spot it may well be baulking at that point, although I have a logger command in the upstart script beyond that point that is triggering - I'll change that logger command to log exactly what it is about to exec i.e. the $MPDCONF value and then look at changing the mpd.conf to use a PID file if it looks wrong.

Thanks for the help - as is probably obvious I'm not all that familiar with upstart configuration so I'd hit a dead end - now I have something more to go on :)

---

### Post by cryptotheslow on 2013-12-08
This is still being an absolute pig!

On a test install of server 12.04 in VirtualBox I installed the standard repository version of mpd just to see what it setup. As it goes that uses a /etc/init.d script rather than Upstart. So I copied that setup across to my live server and edited it to suit the install from source. Having done that calling */etc/init.d/mpd start* or */etc/init.d/mpd stop* works perfectly either as a standard user or as root.

All the symlinks have been created in the /etc/rcX.d folders. Yet it still refuses to start on system startup.

In the meanwhile, I've written a little script that checks for the mpd pid file, checks it is valid and if mpd is not running starts it by calling the init.d script. This I have running from cron every 2 minutes. Now this works but is far from ideal :(

---

### Post by tgalati4 on 2013-12-08
The boot process uses *upstart* to start most services.  Try making a copy of /etc/mpd.conf to /etc/default/mpd.  The purpose of defining static IP's in /etc/hosts is because some older services break when a static IP is used but not defined in /etc/hosts--and with no warning!  Why it won't start in /etc/rc.local is a mystery.  

Make sure you (as administrator) are added to group audio.  That can sometimes cause problems accessing audio hardware:

```
groups
```

It might look like:

tgalati4@tpad-Gloria7 ~ $ groups
tgalati4 adm dialout cdrom **audio** video plugdev fuse lpadmin netdev pulse-rt admin sambashare phcusers

---

### Post by cryptotheslow on 2013-12-08
Yep the groups look to be fine:

```
crypto@ubuserver:~$ groups
crypto adm dialout cdrom audio plugdev lpadmin sambashare admin
crypto@ubuserver:~$ sudo groups
[sudo] password for crypto: 
root audio
crypto@ubuserver:~$ sudo su -
root@ubuserver:~# groups
root audio
root@ubuserver:~# 

```

I've now changed my crontab to be @reboot so it only triggers once.

That group membership does trigger a question in my mind - what effective user are init, rc.local and upstart jobs executed by? Is it root? Or "nobody"? Just thinking maybe the issue is that the effective user at that point is not in the audio group. I'll have to research that some more.

I changed it over from an upstart configuration to using init.d because that is how the standard Ubuntu repository version of mpd is configured. I'll move it back over to upstart - at least that provides some level of logging in /var/log/upstart

---

### Post by cryptotheslow on 2013-12-08
OK - so I have changed it back to an upstart configuration and now have some logging that highlights the problem

```
crypto@ubuserver:/var/log/upstart$ sudo cat mpd.log
[sudo] password for crypto: 
server_socket: bind to '0.0.0.0:6600' failed: Address already in use (continuing anyway, because binding to '[::]:6600' succeeded)
path: SetFSCharset: fs charset is: UTF-8
db: reading DB
output: No 'audio_output' defined in config file
output: Attempt to detect audio output device
output: Attempting to detect a alsa audio device
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
alsa_output: Error opening default ALSA device: No such file or directory
output: Attempting to detect a oss audio device
oss_output: Error opening OSS device "/dev/dsp": No such file or directory
oss_output: Error opening OSS device "/dev/sound/dsp": No such file or directory
fatal_error: line -1: Unable to detect an audio device

```

So the above is the output of the mpd command when run by upstart.

When run by me from the command line:
```
crypto@ubuserver:/var/log/upstart$ mpd /etc/mpd.conf
server_socket: bind to '0.0.0.0:6600' failed: Address already in use (continuing anyway, because binding to '[::]:6600' succeeded)
path: SetFSCharset: fs charset is: UTF-8
db: reading DB
output: No 'audio_output' defined in config file
output: Attempt to detect audio output device
output: Attempting to detect a alsa audio device
output: Successfully detected a alsa audio device
daemon: opening pid file
daemon: daemonized
daemon: writing pid file
```


Curious!

---

### Post by tgalati4 on 2013-12-08
Try setting a default audio output device in the mpd configuration file.  For some reason, the sound card detection routine does not work during boot--perhaps a timing issue?  Maybe the sound modules are not quite initialized yet?  You can probably set the server_socket as well to your LAN address to remove that error.

---

### Post by ian-weisser on 2013-12-08
Alsa uses Upstart to start at boot, too.

Does your mpd Upstart job require alsa-restore, alsa-state, and alsa-store  to be up before starting?

---

### Post by cryptotheslow on 2013-12-08
I can try setting the audio output device. But this is not just during boot it is also when calling *sudo service mpd start* long after boot, the same log messages appear.

I'm only using ALSA on this server (I really don't wan't to throw pulseaudio in the mix as well at this point!). So my mpd.conf alsa section looks like this: 

```
#audio_output {
##      type            "alsa"
##      name            "default"
##      device          "hw:0,0"        # optional
##      mixer_type      "hardware"      # optional
##      mixer_device    "default"       # optional
##      mixer_control   "Master"        # optional
##      mixer_index     "0"             # optional
#}
```

And *aplay -l* gives:
```
crypto@ubuserver:/var/log/upstart$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```


I had it working before with the alsa section uncommented, but then broke it again - I couldn't work out what needed to be in the name variable and the logs just complained about not being able to find whatever device I named there. I'm guessing from the above aply out put it needs to be *name "Intel [HDA Intel]"*.

Time to experiment again :)

---

### Post by cryptotheslow on 2013-12-08
> ian-weisser

All my upstart job seems to require is filesystem and static network up....

```
start on (filesystem and static-network-up)
```

Looking in /etc/init I can only see alsa-restore.conf and alsa-store.conf - nothing for alsa-state.

Should I add alsa-restore and alsa-store to my "start on" clause?

---

### Post by ian-weisser on 2013-12-08
> **cryptotheslow said:**
> 
Looking in /etc/init I can only see alsa-restore.conf and alsa-store.conf - nothing for alsa-state.
Should I add alsa-restore and alsa-store to my "start on" clause?

Yes, but only after the alsa config is fixed. One break at a time.

---

### Post by cryptotheslow on 2013-12-08
> **ian-weisser said:**
> Yes, but only after the alsa config is fixed. One break at a time.

Eek - my alsa config is broken? Or did you mean fix the alsa section of the /etc/mpd.conf file?

As an experiment I removed myself from the audio group and tried to start mpd from the command line - I get the exact same messages about not being able to find an alsa device as I'm seing in the upstart logs.

For the furthering of my understanding... when I call *sudo service mpd start* that actually calls on the upstart init daemon to start mpd?
And that init daemon is running as root?
And root doesn't need to worry about group membership right?

Please correct my misunderstandings, it's the only way to learn.

I'll go and sort out the alsa section of my mpd.conf file so it works right now. As you say one thing at a time - wise words :)

---

### Post by ian-weisser on 2013-12-08
> **cryptotheslow said:**
> Eek - my alsa config is broken? Or did you mean fix the alsa section of the /etc/mpd.conf file?

Sorry for not being clear: Your big problem is getting alsa to work, regardless of how it starts. After you get it working without lots of errors in the log, then it's time to tweak the startup. Having mpd wait for alsa to start first at boot seems like a low priority.

> **cryptotheslow said:**
> For the furthering of my understanding... when I call *sudo service mpd start* that actually calls on the upstart init daemon to start mpd?
And that init daemon is running as root?
And root doesn't need to worry about group membership right?

Yes, the **service** command merely tells init to start/stop something.
Yes, init runs as root.
Init usually doesn't worry about groups and permissions (it has all permissions). For example, servers like MPD usually shouldn't run as root; it's a security hole. Init (as root) can start MPD (as mpd-user) without any problems or special hacking. Normal. Nothing special needed in the config file.

---

### Post by cryptotheslow on 2013-12-08
OK - fixed up the ALSA section of my /etc/mpd.conf file so it reads thus:

```
# An example of an ALSA output:
#
audio_output {
        type            "alsa"
        name            "Intel [HDA Intel]"
        device          "hw:0,0"        # optional
        mixer_type      "hardware"      # optional
        mixer_device    "default"       # optional
        mixer_control   "Master"        # optional
        mixer_index     "0"             # optional
}
#
```

And that starts up fine from a command line with *mpd /etc/mpd.conf*

So I killed it and tried *sudo service mpd start* which resulted in this /var/log/upstart/mpd.log entry:
```
path: SetFSCharset: fs charset is: UTF-8
db: reading DB
daemon: opening pid file
daemon: daemonized
daemon: writing pid file
```

And mpd is again started successfully.

And finally to see if it can start on a cold boot, I removed /var/log/mpd.log and issued an "init 0" - then powered up again,

Et voila!
```
crypto@ubuserver:~$ cd /var/log/upstart
crypto@ubuserver:/var/log/upstart$ ps aux | grep mpd
crypto    1058  0.7  0.2 152520  4636 ?        Ssl  04:33   0:00 mpd /etc/mpd.conf
crypto    1561  0.0  0.0   9392   932 pts/0    S+   04:34   0:00 grep --color=auto mpd
crypto@ubuserver:/var/log/upstart$ sudo cat mpd.log 
[sudo] password for crypto: 
path: SetFSCharset: fs charset is: UTF-8
db: reading DB
daemon: opening pid file
daemon: daemonized
daemon: writing pid file
crypto@ubuserver:/var/log/upstart$
```

SUCCESS!!!

Thank you everyone!

BUT  - I still don't understand the "why?" and that annoys me to hell and  back. All that I changed was to define the alsa device rather than  auto-detect. Why would mpd started via the service command fail to  auto-detect an alsa device when mpd run from the command line by a user  succeded? grrrr


Thanks for the clarification Ian, I know it would be a bad thing for something like MPD to run as root - given that it's sat there listening for network connections. In MPD's own conf files it asks for a user to run as and it seems when it is run by upstart it forks off the process to run under that user as my *ps aux* shows. I'm still annoyingly puzzled about why the auto-detect for the alsa device doesn't work when called via *service / init*.

I swear the more I learn the more I realise I have yet to learn! :D

---

### Post by cryptotheslow on 2013-12-09
UGH!! I spoke too soon! MPD is starting fine but as soon as I connect a client and try to play anything I get this in the logs:
```
Dec 09 05:03 : decoder: audio_format=44100:24:2, seekable=true
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
Dec 09 05:03 : alsa_output: Failed to open "Intel [HDA Intel]" [alsa]: Failed to open ALSA device "hw:0,0": No such file or directory
```

My mpd.conf alsa section looks thus:
```
audio_output {
        type            "alsa"
        name            "Intel [HDA Intel]"
        device          "hw:0,0"        # optional
        mixer_type      "hardware"      # optional
        mixer_device    "default"       # optional
        mixer_control   "Master"        # optional
        mixer_index     "0"             # optional
}
```


And aplay -l looks thus:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

What has a guy to do to just play some tunes around here? :D

---

### Post by tgalati4 on 2013-12-09
I know that you don't want the overhead of pulseaudio on your server, but I have the feeling that pulseaudio has the hooks to make this work.  Pulseaudio is the unified, system-wide audio framework for directing streams to audio hardware.  Because you don't have it, there may be breakage for some packages that need it.  In the days before pulseaudio, applications each had their own method for calling alsa and sometimes two applications would fight over the sound card.  Pulseaudio fixed a lot of this with a unified audio framework--not without problems, but in general it now works pretty well.

So you can try to reinstall pulseaudio and see if that fixes your issue, or continue to chip away without it.

---

### Post by cryptotheslow on 2013-12-09
OK - I finally sorted it out by replicating a repository install type setup.

Created user "mpd" with primary group "audio", set the mpd user's home dir to /var/lib/mpd and moved all the mpd files (database, playlists etc) to there and chowned them over to mpd:audio.

Now mpd runs fine as a service with user = "mpd"

And in the process of doing that I noticed this section in the mpd.conf file....
```
# This setting specifies the group that MPD will run as. If not specified
# primary group of user specified with "user" setting will be used (if set).
# This is useful if MPD needs to be a member of group such as "audio" to
# have permission to use sound card.
#
# group                         ""
```

Sooo - a complete failure to read on my behalf, I could have just set user = "crypto" and group = "audio" all along!!! D'OH! Well I'm not changing it back now it's working :D

---

