---
title: "X server crashes randomly when starting to play videos in Feisty"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by jasonxh on 2007-06-17
I'm using ATI X1300 card with fglrx driver in the official repo (currently 8.34.8 ). I have tried both mplayer and totem-xine, configured to use Xv as video output. Both players crash X server randomly (not very often though) when I start to play a video file. :( Didn't notice similar problem in Edgy even with the same version of fglrx driver.

Does anyone have the same problem?

---

### Post by jasonxh on 2007-06-25
Am I the only one with this problem???

Below is the syslog around a recent crash.

```

Jun 25 02:33:52 jason-laptop kernel: [ 5736.376000] [fglrx:create_buffer_queue] *ERROR* aperture == NULL
Jun 25 02:33:52 jason-laptop kernel: [ 5736.376000] [fglrx:create_buffer_queue] *ERROR* aperture == NULL
Jun 25 02:33:57 jason-laptop kernel: [ 5741.448000] [fglrx:create_buffer_queue] *ERROR* aperture == NULL
Jun 25 02:33:57 jason-laptop kernel: [ 5741.448000] [fglrx:create_buffer_queue] *ERROR* aperture == NULL
Jun 25 02:34:03 jason-laptop kernel: [ 5747.628000] [fglrx:create_buffer_queue] *ERROR* aperture == NULL
Jun 25 02:34:03 jason-laptop kernel: [ 5747.628000] [fglrx:create_buffer_queue] *ERROR* aperture == NULL
Jun 25 02:35:05 jason-laptop kernel: [ 5808.856000] [fglrx:create_buffer_queue] *ERROR* aperture == NULL
Jun 25 02:35:05 jason-laptop kernel: [ 5808.856000] [fglrx:create_buffer_queue] *ERROR* aperture == NULL
Jun 25 02:35:08 jason-laptop kernel: [ 5812.176000] [fglrx:create_buffer_queue] *ERROR* aperture == NULL
Jun 25 02:35:08 jason-laptop last message repeated 3 times
Jun 25 02:35:08 jason-laptop gdm[9905]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jun 25 02:35:09 jason-laptop scim-bridge: Failed to open the panel socket
Jun 25 02:35:10 jason-laptop last message repeated 2 times
Jun 25 02:35:10 jason-laptop scim-bridge: Cleanup, done. Exitting...
Jun 25 02:35:10 jason-laptop Cleanup, done. Exitting... 
Jun 25 02:35:12 jason-laptop kernel: [ 5815.700000] [fglrx] PCIe has already been initialized. Reinitializing ...
Jun 25 02:35:12 jason-laptop kernel: [ 5815.712000] [fglrx] total      GART = 130023424
Jun 25 02:35:12 jason-laptop kernel: [ 5815.712000] [fglrx] free       GART = 114032640
Jun 25 02:35:12 jason-laptop kernel: [ 5815.712000] [fglrx] max single GART = 114032640
Jun 25 02:35:12 jason-laptop kernel: [ 5815.712000] [fglrx] total      LFB  = 66977792
Jun 25 02:35:12 jason-laptop kernel: [ 5815.712000] [fglrx] free       LFB  = 47034368
Jun 25 02:35:12 jason-laptop kernel: [ 5815.712000] [fglrx] max single LFB  = 47034368
Jun 25 02:35:12 jason-laptop kernel: [ 5815.712000] [fglrx] total      Inv  = 0
Jun 25 02:35:12 jason-laptop kernel: [ 5815.712000] [fglrx] free       Inv  = 0
Jun 25 02:35:12 jason-laptop kernel: [ 5815.712000] [fglrx] max single Inv  = 0
Jun 25 02:35:12 jason-laptop kernel: [ 5815.712000] [fglrx] total      TIM  = 0

```

---

### Post by lamborghiniwang on 2007-08-10
I'm having the same problem. Tried to play an H.264 media file and X crashes with the same " aperture == NULL" fglrx error message. :(

---

### Post by bboozzoo on 2007-09-22
got the same problem with X1300 card on Thinkpad T60

---

### Post by bnuytten on 2007-11-03
I can play video's but I have this problem when I want to watch TV using mythtv frontend. The error can be easily reproduced.

```
fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6473 (8.37.6)

```

---

