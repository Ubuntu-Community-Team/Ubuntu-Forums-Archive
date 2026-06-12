---
title: "Sound on my computer is a little squeaky...."
date: 2010-05-31
forum: Multimedia Software
---

### Post by Shootist on 2010-05-31
Hello to all, my problem in Ubuntu 9.10 is the fact that on my computer the sound is a little squeaky, not to mention a little accelerated. It doesn't matter what I do in Ubuntu 9.10, ranging anywhere from playing an audio file in Totem to just the startup sound, it always sounds like Alvin & The Chipmunks have invaded my computer. The only way I can get around this is by using alsaplayer with the speed turned down to 93% (however I can't use alsaplayer because Totem is the only media player that I know of that can be used with non-free plugins {like the Fluendo MP3 plugin for GStreamer}). The curious part in all this is, with Ubuntu 8.10 the sound is just fine; I don't know why, but it is. 

I have put my PC specs in the attachment (for those who are interested), so that way I won't be making a very long post for no reason.

Hope for a response soon! :popcorn: 
[RIGHT][B]Signed, Shootist
[/B][LEFT]P.S. Do tell me if for some strange reason the attachment isn't there!

[ATTACH]158966[/ATTACH]
[/LEFT]
[/RIGHT]

---

### Post by lidex on 2010-06-01
Post this output please:
```
cat /etc/pulse/daemon.conf
```

---

### Post by Shootist on 2010-06-02
Okay, here's the output as requested:
------------------------------------------------------------------------------------------------
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

---

### Post by lidex on 2010-06-02
Hmm. Try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by Shootist on 2010-06-03
Are you sure this is a good idea? I have already had to reinstall Ubuntu 9.10 who cares how many times because of update issues, but that's another story......

Concerning the code you gave me, I did a little looking around, and I could only find /.pulse; aside from that, the other two things marked for deletion don't exist.:confused:

Got any ideas?

By the way, thanks for your help with this!:)

[RIGHT]**Signed, Shootist**
[/RIGHT]

---

### Post by kelocena on 2010-06-03
Have you tried upgrading to 10.04? 8D *shot*

Just wondering if there's a specific reason why you're still on 9.10. Not that you HAVE to upgrade. But it might solve the problem. Who knows? Sorry for being so useless.

---

### Post by Shootist on 2010-06-03
Well, to put it frankly kelocena, you're not being useless; to answer your question about why I haven't upgraded to 10.04, I did upgrade to 10.04, and I tried it for a while; unfortunately I then found out that it didn't solve my problems at all; it just added to them. The squeaky sound problem was still there, and in addition to that, Firefox couldn't be open for a long while before my computer froze and I had to shut it down & then turn it back on. So I went back to 9.10 and aside from the squeaky sound problem, everything's okay. I hope this answers your question. :)
[RIGHT]**Signed, Shootist**
[/RIGHT]

---

### Post by kelocena on 2010-06-03
Holy... moley. Such strange issues! I don't even know what to say. I hope you find the answer.

---

### Post by Shootist on 2010-06-05
Hello again, I tried getting rid of /.pulse, because as I had mentioned previously, that was the only thing that I found that I could delete (not because I didn't have the permissions to do it, but the other things that were mentioned to be deleted weren't there to begin with); I moved the folder out of where it was previously (in case anyone reading this doesn't know where this folder is, it's in your home folder). I restarted my PC and nothing was different. Got any other ideas?:)

[RIGHT]**Signed, Shootist**
[/RIGHT]

---

### Post by lidex on 2010-06-05
Maybe changing the resample method will help.
```
gksudo gedit /etc/pulse/daemon.conf
```
Change this line:
```
resample-method = speex-float-1
```
To look like this:
```
resample-method = src-sinc-best-quality
```
Logout/in

---

### Post by Shootist on 2010-06-08
Unfortunately changing the resample method didn't work. Can you think of any more things I could try? :)

By the way, thanks for your help with this!

[RIGHT]**Signed, Shootist**
[/RIGHT]

---

### Post by lidex on 2010-06-08
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Shootist on 2010-06-09
Here's the file as requested.

[ATTACH]159873[/ATTACH]

By the way, I zipped up the file because it wouldn't let me upload it otherwise. As a follow-up to my previous post, I found out two things: 1, your tip prior to your current one actually did do something; it just did the wrong something. What happened was is that it made my sound all choppy, I guess due to the fact it was trying to get as high of a quality as possible and, as you may know from the file I previously uploaded, the specs of my PC are not that impressive. The second thing was that I found out that with Ubuntu 9.10, I should only restart the PC and power it down. I say this because, I tried logging out and logging back in; the logging out was good, but when I got back in, I ended up making more quirks manifest themselves. The sound was muted when I logged on again, and that was not permanent, but now every time I start my PC, when the update manager pops up, the panels disappear and I think the icons do too, and then a few seconds later, everything shows up again. Let's just say I have had more than just a few problems with my system.

Thank you! :KS

[RIGHT]**Signed, Shootist**
[/RIGHT]

---

### Post by lidex on 2010-06-09
That is a an old version of alsa. Try the alsa-upgrade link in my sig to get something more recent.

---

