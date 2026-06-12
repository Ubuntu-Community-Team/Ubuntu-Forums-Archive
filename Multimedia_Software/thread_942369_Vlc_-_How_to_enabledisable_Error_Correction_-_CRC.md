---
title: "Vlc - How to enable/disable Error Correction - CRC"
date: 2008-10-09
forum: Multimedia Software
---

### Post by scuba123 on 2008-10-09
Hi All,

I am doing an experiment on running a video packets on a multicast network and I use vlc as a video server and a video client. I also run a program in order to inject error in mpeg2 ts packets. The multicast network and vlc work out pretty well. However I am facing some problems when I use a program to inject errors in video packets (mpeg2 ts).
1. I have checked the traces of wireshark/ethereal whether or not injected errors arrived into vlc. I can see some bytes "0"/errors (depending on my implementation) in the trace. However, I don't see any changes on my screen (which is supposed to show some errors/scrambling pictures on my screen). Is this because vlc can perform error correction and disable/ignore the injected errors? Could you give me more information on this?

2. If vlc performs error correction by default, is there a way to disable it so that I can see changes (errors) on my screen/vlc client (vlc client = vlc running on a workstation to receive multicast video packets)?
I ran the following command and played around with the following options. I still don't see the changes.

```
vlc --no-ffmpeg-dr --ffmpeg-vismv=7 --ffmpeg-error-resilience=0 udp:@239.255.0.1:1234

```

3. Or, is there a way to disable CRC on vlc ?

Please help. Thanks in advance.

Regards,

scuba123

---

