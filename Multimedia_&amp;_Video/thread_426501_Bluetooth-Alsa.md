---
title: "Bluetooth-Alsa"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by Meir on 2007-04-28
Does anyone have Bluetooth-Alsa working in Feisty. I followed their directions and if I run it when I'm not root it gives me the error bellow and if I run is as root (not recommended on their site) I don't see any new Audio Devices listed under XMMS. Any help would really be appreciated.

A2DPD[12:42:32.964]: a2dp_make_listen_socket: (errno=13:Permission denied)Cannot bind socket 6 for psm 25
A2DPD[12:42:32.964]: main_loop: Cannot get AVDTP socket
A2DPD[12:42:33.970]: main_loop: 
A2DPD[12:42:33.970]: make_server_socket: 
A2DPD[12:42:33.970]: main_loop: (errno=98:Address already in use)Cannot get UNIX socket

---

### Post by Roner on 2007-04-29
See if my post [here]("http://ubuntuforums.org/showthread.php?t=426828&highlight=feisty+bluetooth") helps you.

---

### Post by Meir on 2007-04-30
Thanks, now it at least runs as root. Its working decently but I feel like the sound was better in windows.

---

