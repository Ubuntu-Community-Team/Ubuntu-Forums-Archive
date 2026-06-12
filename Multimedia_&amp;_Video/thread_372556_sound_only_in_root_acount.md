---
title: "sound only in root acount"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by przemek on 2007-02-28
Hello 

I've got a bit strange problem with sound in Kubuntu. It works only when I'm logged as a root.
When I log as a normal user there is no sound, and system cannot find any sound device.

here's the listing from aplay -l command

przemek@przemek:~$ sudo aplay -l
Password:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
przemek@przemek:~$ aplay -l
aplay: device_list:219: no soundcards found...
przemek@przemek:~$         

I'm working on kernel: 2.6.15-26-amd64-generic with Kubuntu 6.06 LTS Dapper Drake

I will be greatfull for any help

---

### Post by sisco311 on 2007-02-28
```
sudo adduser [username] audio
```
where [username] is your username

---

### Post by przemek on 2007-03-01
Thank you for fast reply, and your solution.
It worked. I've got sound, but still some problems with it's quality, This is connected ( i suposse ) with my ICH7 family Intel audio like we can see here [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and here [http://ubuntuforums.org/showthread.php?t=370120]("http://ubuntuforums.org/showthread.php?t=370120")
. So I've got to fight with it a bit more.](*,)

---

