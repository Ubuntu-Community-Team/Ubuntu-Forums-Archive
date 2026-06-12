---
title: "Pulseaudio No Longer Detecting Sound Card"
date: 2009-12-05
forum: Multimedia Software
---

### Post by ilikes2shred on 2009-12-05
Hello.  I started using linux a little over a month ago.  I am running Ubuntu Studio 9.10.

When I installed Ubuntu, PulseAudio seemed to be working fine.  However, a few days ago it stopped working (I no longer hear any sound from any application).  Under "Output Devices" in PulseAudio Volume Control, it used to show my sound card (an Intel HDA) in one entry, as well as some other device.  Now it just shows "Dummy Output."  It seems that, for some reason, PulseAudio no longer detects my sound card.  

The problem seems to be exclusive to Pulseaudio;  when I type lspci into a terminal, one line of the output is "00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)" so I assume that the sound card is still detected on the operating system level.  

Before Pulseaudio stopped detecting the sound card altogether, it would not detect it *sometimes, *just like the problem this person has>> [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/455417](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/455417) .  Restarting the computer would normally solve the problem.  However, restarting the computer does not solve the problem anymore.  

I have also tried reinstalling PulseAudio using Synaptic Package Manager.

I don't remember messing with any PulseAudio configuration files prior to this problem occurring, but I may have run the Update Manager, if that could have something to do with it.

I have searched the Internet for the past few days, but I have not found a solution.  I am not sure where to go from here, so hopefully one of you out there can help me.

I am not sure what other information you need to help me, so please tell me if you  do need to know something else.

Thanks in advance for any help.

---

### Post by ilikes2shred on 2009-12-05
I now know a little more about what may have caused the problem.  I checked the history in synaptic and I this was the update installed prior to the sound failure:
```
Commit Log for Wed Dec  2 18:06:40 2009


Upgraded the following packages:
chromium-browser (4.0.260.0~svn20091129r33244-0ubuntu1~ucd1~karmic) to 4.0.261.0~svn20091201r33442-0ubuntu1~ucd1~karmic
chromium-codecs-ffmpeg (0.5+svn20091028r30374-0ubuntu1~ucd2) to 0.5+svn20091202r33521-0ubuntu1~ucd1~karmic
sreadahead (1.0-5) to 1:0.90.3-2
x11-common (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xorg (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg-input-all (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xserver-xorg-video-all (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10
xutils (1:7.4+3ubuntu7) to 1:7.4+3ubuntu10

Installed the following packages:
ureadahead (0.90.3-2)
```The important thing here is the xorg stuff.  Could the update have messed up some configuration files so X.org (and not pulseaudio) is causing the problem?  I could try to reconfigure Xorg with
```
dpkg-reconfigure xserver-xorg
```but I don't want to mess up my system any more than it already is.  Any help is much appreciated.

---

