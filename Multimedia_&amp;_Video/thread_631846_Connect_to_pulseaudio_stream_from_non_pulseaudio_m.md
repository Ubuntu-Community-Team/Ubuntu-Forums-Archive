---
title: "Connect to pulseaudio stream from non pulseaudio machine?"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by features on 2007-12-04
Hi all.

I have a machine on my LAN set up as a music server. It has pulseaudio installed, and a tcp stream set up (see config below). I want all the other machines on my LAN to be able to connect to this machine's audio stream.  Some of these machines don't (and can't) have pulseaudio installed.  One of them is a Mac running OS X.  

Is there any way to set up pulseaudio to create a stream that non pulseaudio clients can connect to?

here is my /etc/pulseaudio:

```
# Start the PulseAudio sound server in system mode.
# (enables the pulseaudio init script)
# System mode is not the recommended way to run PulseAudio as it has some
# limitations (such as no shared memory access) and could potentially allow
# users to disconnect or redirect each others audio streams.
# 0 = don't start, 1 = start
PULSEAUDIO_SYSTEM_START=0

# Prevent users from dynamically loading modules into the PulseAudio sound
# server. Dynamic module loading enhances the flexibilty of the PulseAudio
# system, but may pose a security risk.
# 0 = no, 1 = yes
DISALLOW_MODULE_LOADING=0

load-module module-null-sink sink_name=rtp
load-module module-rtp-send source=rtp.monitor
set-default-sink rtp
load-module module-esound-protocol-tcp auth-ip-acl=127.0.0.1;192.168.0.0/16
load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1;192.168.0.0/16
load-module module-zeroconf-publish
```

---

### Post by sedi911 on 2008-03-04
bump

I also would like to know if this is possible. If not, has anyone tried using pulseaudio in Windows? I downloaded the binaries, but when I run pulseaudio from the command line, I get an error. There does not seem to be any documentation on this topic anywhere. Hopefully, someone here can help!

Eddie

---

### Post by hugmenot on 2008-03-09
[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

(The last item)

---

