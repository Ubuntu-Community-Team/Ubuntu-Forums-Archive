---
title: "Mythbuntu 10.04 and HD-PVR: No sound in videos!"
date: 2010-06-30
forum: Mythbuntu
---

### Post by golbez_88rule on 2010-06-30
Hello, I just completed a clean install of Mythbuntu 10.04 (I was using 9.10) and so far everything has worked.  I have not configured the Mythbackend yet, but my first step is to make sure the HD-PVR is able to record off of my cable box.  I've consulted the MythTV wiki page on the [HDPVR]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR") and made a test recording with the command ```
 cat /dev/video0 > test.ts
```

When I play back the recording, the video is fine but there is no sound. I have the HDPVR connected to my Scientific Atlanta 4250HD box with video component cables and SPDIF cable to get 5.1 channel AC3 sound for my recordings. I had this exact setup with Mythbuntu 9.10 and I had no issues with sound. Any ideas on where to track down the problem?

---

### Post by larsolav on 2010-07-01
Do you know if the missing sound is from a) the recording of the video or b) the playback of the video?

---

### Post by golbez_88rule on 2010-07-11
I've solved the issue!  First I verified by making a recording of a program and watching it on TV at the same time to make sure the source had sound. After some digging in the Myth HD-PVR wiki entry and some forum posts, I discovered that parameters for the HD-PVR are located in the /sys/module/hdpvr/parameters directory. One of the parameters is called default_audio_input and the file /sys/module/hdpvr/parameters/default_audio_input was set to 3, when it only has 2 possible values (1 or 2). Setting it to 2 corresponds to the SPDIF output that I am using on the HD-PVR. To change it, I created a file called /etc/modprobe.d/hdpvr.conf with the following contents:
```

options hdpvr default_audio_input=2 boost_audio=N

```
(I added boost_audio=N because I saw some users were having problems with that enabled). I then unloaded and reloaded the modules with the following:
```

sudo rmmod hdpvr
sudo modprobe hdpvr

```
Now every recording has actual sound. I used information from posts [here]("http://www.gossamer-threads.com/lists/mythtv/users/407009") and [here]("http://www.mythtv.org/pipermail/mythtv-users/2010-March/283082.html") that pointed me to the settings directory.

---

