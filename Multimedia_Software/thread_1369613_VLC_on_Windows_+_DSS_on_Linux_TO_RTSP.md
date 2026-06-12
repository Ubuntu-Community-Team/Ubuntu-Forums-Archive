---
title: "VLC on Windows + DSS on Linux TO RTSP"
date: 2010-01-01
forum: Multimedia Software
---

### Post by mr_pro_2020 on 2010-01-01
hi all 


i have seen alot of posts like my problem but i have no replays for my Qs

So ; Plz try to help
 
```

PC 1 : Linux Mint + DSS + With webcam                ,IP:192.168.1.120
PC 2: Windows XP with VLC  + TVCard                  ,IP:192.168.1.124
```

i want to stream my TV Card From PC2  To PC 1 With DSS 

the both in one local network, my Dss working great i have tried to stream my webcam and the stream was working good

so the problem how to make my PC2 access PC1 and start stream

i used some thing like that

```
 C:\Program Files\VideoLAN\VLC\vlc.exe -vvv -I rc --ttl 12 dshow:// {MY Direct Show} --sout=#rtp{mux=ts,dst={PC1IP},port=5004}

```

but i don't know about the port !!

DSS not Giving any ablity  to select any port -- As i poorly now

i have made a relay on PC1

```
Relay name dbv1
status : enabled

Source settings :
source hostname :192.168.1.124
Mount Point : /dbv1.sdp
wait for announced streams

destenation 1of 1
Hostname :127.0.0.1
announced UDP :
mount point : blank
user: blank
pass: blank

```

am using vlc 1.0.3 , Dss 5.5.5

---

### Post by mr_pro_2020 on 2010-01-01
Any Ideas ?!

---

