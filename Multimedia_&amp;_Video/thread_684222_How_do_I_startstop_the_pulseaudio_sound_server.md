---
title: "How do I start/stop the pulseaudio sound server?"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by rgeddes on 2008-01-31
Normally, I start/stop daemons via their init script in /etc/init.d/service by running:

sudo /etc/init.d/service [start | stop]

but the pulseaudio script does nothing...

I noticed the following lines that probably make the script exit before any of the start/stop sections can be executed:

```
PULSEAUDIO_SYSTEM_START=0
DISALLOW_MODULE_LOADING=1
test -f /etc/default/pulseaudio && . /etc/default/pulseaudio
test "$PULSEAUDIO_SYSTEM_START" != "1" && exit 0
```

in particular, the PULSEAUDIO_SYSTEM_START variable is set to 0, and later in /etc/default/pulseaudio that variable is set again.

Here's the section of /etc/default/pulseaudio related to PULSEAUDIO_SYSTEM_START:
```
# Start the PulseAudio sound server in system mode.
# (enables the pulseaudio init script)
# System mode is not the recommended way to run PulseAudio as it has some
# limitations (such as no shared memory access) and could potentially allow
# users to disconnect or redirect each others audio streams.
# 0 = don't start, 1 = start
PULSEAUDIO_SYSTEM_START=0
```

Is the "init script" referred in /etc/default/pulseaudio the same as /etc/init.d/pulseaudio?  The wording seems to advocate "don't start".  I changed this value to 1 and I started getting status messages about the server starting/stopping... even though it didn't show up in ps.

The only way to get /etc/init.d/pulseaudio to run is to set PULSEAUDIO_SYSTEM_START=1 otherwise 
```
test "$PULSEAUDIO_SYSTEM_START" != "1" && exit 0
```
will exit the script.

The other part of the /etc/default/pulseaudio file is equally vague:
```
# Prevent users from dynamically loading modules into the PulseAudio sound
# server. Dynamic module loading enhances the flexibilty of the PulseAudio
# system, but may pose a security risk.
# 0 = no, 1 = yes
DISALLOW_MODULE_LOADING=1
```

Does this refer to the modules that I set up in the /etc/pulse/default.pa file? or some other modules?

---

### Post by rgeddes on 2008-02-01
I found out from the PA mailing list that version 0.9.6 (the version packaged in Gutsy) does not support 32-bit sound samples, only 16 bit sound samples... and for that reason the server is refusing to start on my card (M-Audio Delta 66) which uses 32-bit sound samples... seems there would be some backward compatibility....  Version 0.9.8 does have this capability... so, I will try that.

---

