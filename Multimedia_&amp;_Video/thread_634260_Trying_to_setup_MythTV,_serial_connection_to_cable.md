---
title: "Trying to setup MythTV, serial connection to cablebox,. channel.bin permission denied"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by Mysticle31 on 2007-12-07
I've been trying to configure MythTV. I'm excited in that this is the closest I have gotten to a working Linux install! It's been a nice crash course.


I'm running Kubuntu
I started having this problem after following the directions here:

[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)



steve@Desktop -$ channel 54
bash: /usr/local/bin/channel: Permission denied
steve@Desktop:~$ sudo channel 54
[sudo] password for steve:
sudo: channel: command not found
steve@Desktop:~$ cd /usr/local/bin
steve@Desktop:/usr/local/bin$ channel 54
bash: /usr/local/bin/channel: Permission denied
steve@Desktop:/usr/local/bin$ sudo channel 54
sudo: channel: command not found

Then I did this
steve@Desktop:/usr/local/bin$ sudo chmod +x /usr/local/bin/channel
steve@Desktop:/usr/local/bin$ channel

Did nothing but a blinking cursor, so I abborted with Ctrl+C

steve@Desktop:/usr/local/bin$ setserial /dev/ttys0
/dev/ttys0: Input/output error
steve@Desktop:/usr/local/bin$ channel 54
channel: /dev/ttyS0: Resource temporarily unavailable


I think I would much rather have access denied and help fixing that than resource temporarily unavailable What did I do! Someone help dig me out of my little hole. How do I make this work?

On a side note, I tried to skip this step and just see if my capture card would just play whatever channel my cable box is set to, and it wouldn't.  So I have more problems to investigate after this one :P.
__________________

---

### Post by Mysticle31 on 2007-12-09
I just tried it again on a new Xubuntu installation.  Same thing.

steve@Desktop:/usr/local/bin$ channel 54
bash: /usr/local/bin/channel: Permission denied
steve@Desktop:/usr/local/bin$ sudo channel 54
sudo: channel: command not found
steve@Desktop:/usr/local/bin$ sudo echo $path

steve@Desktop:/usr/local/bin$ sudo ./channel 54
sudo: ./channel: command not found
steve@Desktop:/usr/local/bin$ dir
channel
steve@Desktop:/usr/local/bin$ ls
channel
steve@Desktop:/usr/local/bin$

sorry for the shameless bump

---

