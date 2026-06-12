---
title: "Backend start and udev rule race condition"
date: 2010-06-16
forum: Mythbuntu
---

### Post by Naoyuki Tai on 2010-06-16
I installed Lucid MythBuntu, and am having a problem with the backend starting too early.

I have a udev rule whch aliases a IVTV encoder (Happauge PVR-150) to "/dev/mpeg_encoder".

```
$ cat /etc/udev/rules.d/62-videodev.rules 
KERNEL=="video*",ATTR{name}=="ivtv* encoder MPG",KERNELS=="0000:03:06.0",SYMLINK+="mpeg_encoder"
KERNEL=="video*",ATTR{name}=="ivtv* encoder PCM",KERNELS=="0000:03:06.0",SYMLINK+="pcm_audio"

```

Apparently, the backend starts before the rule executes and sets up the alias. As a result, the backend sees the encoder missing.
Once I do "/etc/init.d/mythtv-backend restart", the backend sees the /dev/mpeg_encoder and works.

I guess /etc/init.d/udev is running after /etc/init.d/mythtv-backend.
How can I make mythtv-backend to start after udev? 

Thanks.

---

### Post by tgm4883 on 2010-06-16
What is the full version of mythtv that you are using?

```
dpkg -l mythtv-backend
```

---

### Post by tgm4883 on 2010-06-16
This looks to be related to [https://bugs.edge.launchpad.net/ubuntu/+source/mythtv/+bug/556204](https://bugs.edge.launchpad.net/ubuntu/+source/mythtv/+bug/556204)

Which is fixed in auto-build 
[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by Naoyuki Tai on 2010-06-17
> **tgm4883 said:**
> What is the full version of mythtv that you are using?

```
dpkg -l mythtv-backend
```
$ dpkg -l mythtv-backend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  mythtv-backend                    0.23.0+fixes24158-0ubuntu2        A personal video recorder application (server)


I have a theory. I need to test but the right answer is probably to change "/etc/init/mythtv-backend.conf".

```
$ cat mythtv-backend.conf
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo_ and started udev_)
stop on starting shutdown

#expect fork
respawn

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend $ARGS
end script

```so that the mythtv-backend waits for the udev is done its job.

This also solves my IrDA devices aliasing too.

If you have multiple devices (capturing, IrDA, or ethernet interfaces for that matter by "/etc/udev/rules.d/70-persistent-net.rules" ) and a daemon is relying on a stable name assigned by udevd, the daemons have to start after udev. (or udev-finish?).

I'm not sure I need to use udev or udev-finish. I wish I knew where I can find the documentation for this. But, I'm pretty sure that this should be considered as MythBuntu's bug of starting many services without waiting for udevd's to finish setting up the device aliases.

-- Tai

---

### Post by tgm4883 on 2010-06-17
> **Naoyuki Tai said:**
> $ 

I'm not sure I need to use udev or udev-finish. I wish I knew where I can find the documentation for this. But, I'm pretty sure that this should be considered as MythBuntu's bug of starting many services without waiting for udevd's to finish setting up the device aliases.

-- Tai

No, this isn't considered Mythbuntu's bug anymore strictly because I already fixed that. If you upgrade to auto-builds you would get the update.

---

