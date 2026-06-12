---
title: "Pulseaudio stuttering when not being run by root"
date: 2010-01-04
forum: Multimedia Software
---

### Post by Flyn on 2010-01-04
After lots of investigation, I managed to narrow down the cause of my sound stuttering issues to whether or not it is being run by root. When Pulseaudio is being run by a normal user, it gets a -15 priority but still stutters. 

The Pulseaudio session that is being run as root has the following command line:

```
pulseaudio -vvv --system --realtime=1 --log-target=syslog
```While the normal user runs it as:


```
pulseaudio -vvv --realtime=1 --log-target=syslog
```Anyone have any idea what could be causing this and how to resolve it?

I'm attaching the relevant syslog entries for each of the Pulseaudio sessions.

Thanks in advance,
Adam

---

### Post by duanedesign on 2010-01-04
[Here is a guide]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") for troubleshooting sound in Karmic.

[This thread]("http://ubuntuforums.org/showthread.php?t=789578") is also a good resource for sound problems
-
-
-

---

### Post by Flyn on 2010-01-05
Ok,

I'm not sure how I missed this exactly, but using the following command line switches in /usr/local/etc/pulse/client.conf and in /etc/pulse/client.conf seems to have solved the problem:

```
 extra-arguments = --log-target=syslog --realtime=1 --high-priority=1 --fail=1 -vvv
```Thanks for all the help anyways, hope this helps someone.

Adam

---

### Post by markbuntu on 2010-01-05
You should file a bug report about this at launchpad so the maintainers can be made aware of this issue and hopefully fix it for everyone.

---

