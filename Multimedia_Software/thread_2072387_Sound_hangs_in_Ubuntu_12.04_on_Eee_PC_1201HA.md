---
title: "Sound hangs in Ubuntu 12.04 on Eee PC 1201HA"
date: 2012-10-17
forum: Multimedia Software
---

### Post by callfromtheabyss on 2012-10-17
Hi,

 I've got the following problem. How to put it (I'm not a native English speaker) - my sound keeps on hanging, i.e. you can hear a loop of a short piece of sound played at a time. It resumes shortly after you hit any button or move the touchpad. It happens as often as from seconds up to one minute during a playback. It happens both on speakers and headphones, both on youtube videos and music played via normal player like vlc.

 I'm a beginner in Linux so please forgive me if the information provided is too little. I will update it according to your guidelines.

 I'd appreciate any help. Thanks.

---

### Post by Raude on 2013-05-24
Hi,
i do have nearly the same problem on my Eee PC 1201HA. The only difference is that i use Xubuntu 13.04 and my sound lags the whole time. It doesn't matter if it's a video from the internet (youtube, the video itself is running without troubles) or a .mp3 file played with gmusic/vlc. I think there are some driver issues that i can't solve on my own. So i would be pleased if someone could help us, cause i think we have the same problem on two different distributions.

@callfromtheabyss
Is ubuntu running fluently on your device and which version do you use? Cause i had serious graphic-troubles with ubuntu on mine.

Thanks in advance

Edit: I managed to get rid off the problem... I do not really know how. All i did was to run the ubuntu bug report in terminal: ubuntu-bug -s audio and to install newest packages. After the bug report i realised that the problem was gone. I can't say what step got the issue under control cause i didn't try the audio till i read about the bug report.
Hope this helps people with the same problem.

Edit 2: THe problem is still there after restart. But after doing "ubuntu-bug audio" its gone! Is there somebody who can tell me what happens while the apport is running? So that i can put this in my starting routine. So i don't have to run th Ubuntu-bug audio after every restart...

---

### Post by rogier.delporte on 2014-01-03
@Raude 

Your audiofix worked a treat for rhythmbox, but not for youtube... I'd really love if someone could share what the problem is, I'm not the wizzkid when it comes to drivers. Plus, I haven't got all the time in the world with this netbook, it's my girlfriends'.

Edit: Hooray huzzah! I've found the solution [https://wiki.debian.org/DebianEeePC/Model/1101HA](https://wiki.debian.org/DebianEeePC/Model/1101HA) in the section fix sound. It works a treat for both youtube and rhythmbox! Could you guys try this fix, so this thread can be marked as solved?

---

