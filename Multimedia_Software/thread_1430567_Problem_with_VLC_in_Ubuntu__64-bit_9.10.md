---
title: "Problem with VLC in Ubuntu  64-bit 9.10"
date: 2010-03-15
forum: Multimedia Software
---

### Post by vmsda on 2010-03-15
Hi-fi enthusiasts tend to favour Apple as their sound solution; since VLC is multiplatform, I decided to try it out after doing a clean 9.10 install.

1. The sound has to go out of Ubuntu via a usb-attached cable. After doing some reading I configured the VLC audio output via Tools > Preferences > Audio, with Output Type as "UNIX OSS audio output", and Device as "/dev/dsp1".

2. I downloaded three 24bit/96khz flac files and tried to play them; the first time everything went ok with the first file, which I interrupted to try another; the second file stopped of its own accord after a couple of minutes; same for the third file.

3. After doing some more reading, I was convinced that Pulse Audio was the culprit and I should therefore get rid of it, which I did. Now the files normally do not give any sound although VLC is obviously (graphically) working on them; sometimes all I get is a very brief sound for a split second, but that is all. Then I tried to play music from a CD inserted into the DVD drive, and the result is the same.

4. I then decided to investigate the log (system) and watch it as I tried to play something, and this is the output:

wpa_supplicant[635]: CTRL-EVENT-SCAN-RESULTS 
Mar 15 18:13:15 vasco-laptop kernel: [ 2377.552012] 2:1:1: cannot get freq at ep 0x1
Mar 15 18:13:15 vasco-laptop kernel: [ 2377.558722] 2:1:1: cannot get freq at ep 0x1
Mar 15 18:13:57 vasco-laptop kernel: [ 2419.221068] 2:1:1: cannot get freq at ep 0x1
Mar 15 18:13:57 vasco-laptop kernel: [ 2419.227079] 2:1:1: cannot get freq at ep 0x1

Anyone has a suggestion as to the way forward, short of migrating out to Apple or Windows for my music listening?

---

