---
title: "Plex Service failing to start in 14.04"
date: 2016-11-27
forum: Multimedia Software
---

### Post by ccReynolds on 2016-11-27
I recently installed the following version of Plex:
plexmediaserver_1.2.7.2987-1bef33a_amd64.deb

I get the following in /var/log/syslog, as the service keeps trying to restart:
plexmediaserver main process xxxx terminated with status 132
traps: Plex Media Serv xxxx trap invalid opcode ip:7fe3bf1166ab sp:7fff5a898590 error:0 in libopencv_imgproc.so.2.4[7fe3bef99000+252000]

Not really sure where to go from here.

---

### Post by TheFu on 2016-11-28
Is your CPU 64-bit intel compatible?
Have you verified the download isn't corrupted? Use the checksum.
Google isn't helping based on the invalid opcode. Could be an incompatible library.  If the 1st 2 things are correct for your system, I'd try a different release of plex.  Running 0.9.16.6 here still.

---

### Post by ccReynolds on 2016-11-29
> **TheFu said:**
> Is your CPU 64-bit intel compatible?
Have you verified the download isn't corrupted? Use the checksum.
Google isn't helping based on the invalid opcode. Could be an incompatible library.  If the 1st 2 things are correct for your system, I'd try a different release of plex.  Running 0.9.16.6 here still.

```
~$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
....

```
```
~$ uname -a
Linux Li 3.13.0-101-generic #148-Ubuntu SMP Thu Oct 20 22:08:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```
[URL="https://downloads.plex.tv/plex-media-server/1.2.7.2987-1bef33a/plexmediaserver_1.2.7.2987-1bef33a_amd64.deb"]Ubuntu 64-bit (10.04 Lucid or newer)
SHA-1 Checksum
864652a94a5d3cc31991407ad2267d8d775b3908[/URL]
```
~/Downloads$ sha1sum plexmediaserver_1.2.7.2987-1bef33a_amd64.deb
864652a94a5d3cc31991407ad2267d8d775b3908  plexmediaserver_1.2.7.2987-1bef33a_amd64.deb

```
Dumb question, but I was going to try getting an older version of it, but I couldn't find an older version on the Plex site.  Their download page seemed to force you into one version.

---

### Post by TheFu on 2016-11-29
I'm running the same kernel as you.  Took a little searching, but archive.org has some of the older releases.
[https://web.archive.org/web/20130910125628/http://wiki.plexapp.com/index.php/Downloads](https://web.archive.org/web/20130910125628/http://wiki.plexapp.com/index.php/Downloads)

Archive.org, or the way-back machine as it is commonly known, is great for this sort of stuff.  I've used it to recover an old static website that I had decades ago. Handy trick for your basket.

---

### Post by ccReynolds on 2016-12-03
I tried version 0.9.12 and it had the same issue.  So I went all the way back to 0.9.8 and that worked. I didn't want to run the old version for security reasons.  After doing some googling, it looks like the opencv libraries they pack with the newer versions of Plex require SSE3 instructions. In my case the processor didn't support SSE3:

```
$ cat /proc/cpuinfo
...
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good nopl lahf_lm vmmcall
...

```

To fix I downloaded the opencv library, Unpacked the zip file, switched to the unpacked opencv folder and compiled it with the following options:

```

$ mkdir build && cd build && cmake -DENABLE_SSE3=OFF .. && make && sudo make install

```

Then I added a .old extension to libopencv_core.so.2.4 and libopencv_imgproc.so.2.4 in the/usr/lib/plexmediaserver folder.  Finally I copied the compiled libraries from  /usr/local/lib to /usr/lib/plexmediaserver.  Now version 1.2.7 is running.

---

### Post by TheFu on 2016-12-03
Thanks for sharing the solution. 

Makes sense **invalid opcode** now.  Plus the fact that you were prepared to compile and link the needed library isn't something I would have assumed from a normal plex user. Nice.

Out of curiousity - what CPU was being used?

---

### Post by ccReynolds on 2016-12-04
It was an AMD 3500+.  Trying to find a way to consolidate the music, videos and photos the family has collected.  Not 100% sure I want to go the Plex route, but seems to have some good features.

---

### Post by TheFu on 2016-12-05
Completely understand the hesitance towards Plex.  It isn't F/LOSS.  My Plex stuff is read-only, so it won't screw things up.  Used XBMC before that, but as different parts of the house wanted access, it became clear that a central DB was needed. XBMC needs to be tricked for a central DB.  Prior to that, I used just organized directories. Fortunately, my directories were almost the same as what Plex/XBMC like.  

The thing that pushed me to plex was the ability to transcode video on-the-fly to whatever a client needs.  Those cheap video players like a chromecast are pretty picky about video/audio codecs they like.  None of the TV shows I record are compatible because those devices don't support AC3 audio.  Plex can transcode the audio to AAC.  I already convert the video to h.264, which is well supported by roku, chromecast, android, r-pi devices.  My raspberry Pi can handle almost any audio and allows changing the audio track for playback, which is handy. 

Should also say that I've never had a plex account and don't use any of their clients for playback.  Have reasonable access from anywhere in the world thanks to a SOCKS proxy setup using ssh to the plex media web-app running inside my network. It can stream DVD quality video over the internet through an encrypt tunnel.  Music works too, but I prefer Clementine for that, so using **sshfs** makes that available world-wide. No plex account needed. No extra firewall ports opened except the port I use for ssh.  If sshd is secured, basically you can have complete access to your LAN data, services, files, almost anything.

Anyway. Just sharing what is possible with little effort.  If you search for "SOCKS proxy ssh", the remote tunnel for remote web access will be found. Basically, you can tunnel all traffic though your home connection when using open wifi elsewhere. Better security without paying for a reputable VPN service.

---

