---
title: "Amarok Random Crashes"
date: 2010-12-21
forum: Multimedia Software
---

### Post by rich86 on 2010-12-21
Hi,

I've recently (since upgrade to Ubuntu 10.10) being having problems with Amarok randomly crashing.
There doesn't seem to be any pattern and it normally just disappears and music stops. Occasionally it comes up with the KDE crash tracker but it can't retrieve the debug information (although i do have amarok-dbg installed, not sure what else i need for that to work though)

Anyway i have run it from the terminal and this is the output i got towards the end:

```
amarok(7287)/kio (KIOJob) KIO::TransferJob::slotMimetype: mimetype() emitted again, or after sending first data!; job URL = KUrl("http://upload.wikimedia.org/wikipedia/commons/thumb/f/fd/Portal-puzzle.svg/16px-Portal-puzzle.svg.png") 
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
amarok(7287)/kio (KIOJob) KIO::TransferJob::slotMimetype: mimetype() emitted again, or after sending first data!; job URL = KUrl("http://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/Gnome-mime-audio-openclipart.svg/50px-Gnome-mime-audio-openclipart.svg.png") 
amarok(7287)/kio (KIOJob) KIO::TransferJob::slotMimetype: mimetype() emitted again, or after sending first data!; job URL = KUrl("http://upload.wikimedia.org/wikipedia/commons/thumb/4/4a/Commons-logo.svg/30px-Commons-logo.svg.png") 
KCrash: Application 'amarok' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/richard/.kde/socket-richards/kdeinit4__0
Assertion 'pa_close(fds[0]) == 0' failed at pulsecore/core-util.c:2215, function pa_close_pipe(). Aborting.
Unable to start Dr. Konqi


```
I think the interesting part is:

Assertion 'pa_close(fds[0]) == 0' failed at pulsecore/core-util.c:2215, function pa_close_pipe(). Aborting.

but i can't find much/anything useful on Google.

Thanks in advance,

Richard

---

### Post by mrw on 2010-12-22
Rich, I have a similar problem after upgrading from 10.04 to 10.10
In my case Amarok doesn't run at all without crashing. I reported the bug.
When I run it from the terminal as sudo, here's what I get:


Error: "/var/tmp/kdecache-mrw" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-mrwCUiDJH" is owned by uid 1000 instead of uid 0.
Home directory /home/mrw not ours.
ALSA lib conf.c:1665:(snd_config_load1) :18:1:Unexpected }
ALSA lib conf.c:3441:(snd_config_hook_load) /home/mrw/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3302:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3687:(snd_config_update_r) hooks failed, removing configuration
amarok: conf.c:1625: snd_config_load1: Assertion `config && in' failed.
KCrash: Application 'amarok' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/mrw/.kde/socket-mrw-ubuntu/kdeinit4__0
<unknown program name>(18571)/: Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.amarok was not provided by any .service files" " 

Doesn't make much sense to me.

mrw

---

### Post by rich86 on 2010-12-23
I don't know why your running it as sudo in the terminal, there is no need to run amarok as a root user. Try just running it as a normal user and see what output you get.

Richard

---

