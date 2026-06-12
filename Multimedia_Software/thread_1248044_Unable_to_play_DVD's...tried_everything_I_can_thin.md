---
title: "Unable to play DVD's...tried everything I can think of"
date: 2009-08-23
forum: Multimedia Software
---

### Post by us3598 on 2009-08-23
Hi all. Any help with this issue would be greatly appreciated. I recently installed all of the restricted packages for ubuntu, kde, and xfce. I have also installed mythtv, all to no avail. When attempting to play ANY dvd in the drive, xine pops up the following message: "The source can't be read. Maybe you don't have enough rights for this, or source doesn't contain data. (Error reading NAV packet)". Here is a readout of /var/log messages:
Aug 23 15:28:58 hussam-laptop kernel: [  113.472640] __ratelimit: 46 callbacks suppressed
Aug 23 15:28:59 hussam-laptop kernel: [  114.875149] UDF-fs: Partition marked readonly; forcing readonly mount
Aug 23 15:28:59 hussam-laptop kernel: [  114.948354] UDF-fs INFO UDF: Mounting volume 'HARRY_POTTER_GOBLET_OF_FIRE', timestamp 2005/12/21 18:34 (1000)
Aug 23 15:29:33 hussam-laptop kernel: [  148.451831] __ratelimit: 38 callbacks suppressed
Aug 23 15:33:45 hussam-laptop pulseaudio[4131]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Aug 23 15:33:45 hussam-laptop pulseaudio[4131]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Aug 23 15:33:45 hussam-laptop pulseaudio[4131]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
Aug 23 15:33:46 hussam-laptop pulseaudio[4134]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 23 15:33:46 hussam-laptop pulseaudio[4134]: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
Aug 23 15:33:46 hussam-laptop pulseaudio[4134]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug 23 15:34:05 hussam-laptop kernel: [  421.071065] __ratelimit: 56 callbacks suppressed
Aug 23 15:47:27 hussam-laptop -- MARK --
Aug 23 16:07:27 hussam-laptop -- MARK --
Aug 23 16:27:27 hussam-laptop -- MARK --
Aug 23 16:35:13 hussam-laptop kernel: [ 4088.307754] __ratelimit: 88 callbacks suppressed
Aug 23 16:36:27 hussam-laptop kernel: [ 4162.158616] __ratelimit: 58 callbacks suppressed
Aug 23 16:47:27 hussam-laptop -- MARK --


Any help...please, would be greatly appreciated. I just want to play a DVD!

---

### Post by HappyFeet on 2009-08-23
Did you install **libdvdcss2** ?

---

### Post by us3598 on 2009-08-23
what is the terminal command to install it? I tried sudo apt-get install libdvdcss2 but it doesn't work, and I can't find it in synaptic

---

### Post by HappyFeet on 2009-08-23
Copy and paste:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```
Then:
```
sudo apt-get install libdvdcss2
```
What you are doing is installing the medibuntu repos. You should do this after every install.

---

### Post by us3598 on 2009-08-23
Thank you for the knowledge. Your solution worked perfectly. Now I know!

---

### Post by ajgreeny on 2009-08-23
+1 for the medibuntu repositories.  It's the first thing I do after installing as so many applications are available in slightly different, and better versions, from those repos than the default ubuntu repos.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

