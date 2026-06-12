---
title: "Mythpreviewgen taking tons of resources"
date: 2013-04-16
forum: Mythbuntu
---

### Post by dannyboy79 on 2013-04-16
Hey guys, I recently upgraded my backend mythtv server from 0.23+fixes to 0.25+fixes using Ubuntu 12.04 minimal, then I installed mythbuntu-desktop. It's a really old machine so I need the least amount of overhead but this just isn't working. I am constantly waiting for mythweb to reload and stuff is just dogging with the server. I even killed the x-server, lightdm, and the window manager since I am comfortable managing the server over ssh or even tty1. Here's a recent top
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                       
 1615 mythtv    20   0  683m  10m 2176 S  0.0  4.4  23:40.28 mythbackend                                                                                                                   
 1298 mysql     20   0  346m 8328 1232 S  0.3  3.4   1:24.31 mysqld                                                                                                                        
 6634 mythtv    29   9  162m 4868 3840 S  0.0  2.0   0:00.40 mythpreviewgen                                                                                                                
 6639 mythtv    29   9  162m 4956 3868 S  0.0  2.0   0:00.38 mythpreviewgen                                                                                                                
 6684 mythtv    29   9  162m 4996 3904 S  0.3  2.0   0:00.38 mythpreviewgen                                                                                                                
 6685 mythtv    29   9  162m 5724 4160 S  0.0  2.3   0:00.44 mythpreviewgen                                                                                                                
 6686 mythtv    29   9  162m 4916 3860 S  0.3  2.0   0:00.35 mythpreviewgen                                                                                                                
 6688 mythtv    29   9  162m 4196 3492 S  0.0  1.7   0:00.39 mythpreviewgen                                                                                                                
 6734 mythtv    20   0  109m  16m 7088 D  0.0  6.6   0:00.19 mythpreviewgen                                                                                                                
 6735 mythtv    20   0  109m  15m 7016 D  0.3  6.6   0:00.19 mythpreviewgen                                                                                                                
 6743 mythtv    20   0  109m  14m 6096 D  0.0  5.9   0:00.14 mythpreviewgen                                                                                                                
 6746 mythtv    20   0  109m  16m 7052 D  0.3  6.7   0:00.18 mythpreviewgen                                                                                                                
 6754 mythtv    20   0  109m  16m 7316 D  0.0  6.8   0:00.17 mythpreviewgen                                                                                                                
 6731 mythtv    20   0  109m 9624 3580 D  0.7  3.9   0:00.27 mythpreviewgen                                                                                                                
 2509 daniel    20   0 99408  460  328 S  0.0  0.2   0:00.33 pulseaudio                                                                                                                    
 2515 colord    20   0 45652  248  240 S  0.0  0.1   0:00.67 colord                                                                                                                        
 1352 debian-t  20   0 40200 1404  704 S  0.0  0.6   1:54.35 transmission-da        
```

as you can ssee there is just way to much virtual memory being used by mythpreviewgen and I am not even doing anything but showing the recordings tab within mythweb. Can anyone help me sort this out? If not, I may finally have to move away from this old dell dimension 8200 with only 256MB RAM. It's been a great little server for my file serving and mythtv needs as a master backend.

---

### Post by dannyboy79 on 2013-04-19
I just noticed the following within my backend log file.

```
Apr 19 01:01:15 dell mythlogserver: mythpreviewgen[19405]: E CoreContext mythplayer.cpp:952 (OpenFile) Player(0): Couldn't find an A/V decoder for: '/var/lib/mythtv/recordings/1043_20130419051800.mpg'
```

could someone please help me troubleshoot this? i have 1 PVR-350 and 1 PVR-500, I scheduled the above recording last night. I don't know why it can't find an A/V decoder for it when the recording was created with the PVR-350.

---

### Post by dannyboy79 on 2013-04-21
it turns out my hardware was just not up to the task with the way the new mythlogserver and mythpreviewgen worked (very memory intensive). I was running it on a 2Ghz P4 with only 256MB RAM, it was a Dell Dimension 8200. So I took all my hard drives and put them into a new case with a new MB, 2GB RAM, and a Intel(R) Celeron(R) CPU 2.66GHz and now everything runs very smoothly, no errors at all so it must have just been hardware limiting and my machine was locking up with all the mythpreviewgen and mythlogservers that were being spawned.

I am now running Mythbuntu 12.04.2 and MythTV 0.26+fixes

---

