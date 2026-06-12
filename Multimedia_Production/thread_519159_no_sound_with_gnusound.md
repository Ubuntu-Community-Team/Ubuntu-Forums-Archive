---
title: "no sound with gnusound"
date: 2007-08-06
forum: Multimedia Production
---

### Post by Svictor on 2007-08-06
Hi everyone,
I have a problem with gnusound: it doesn't play anything.  I tried alsa, jack and even oss. With jack, it simply crashes. With alsa and oss, nothing happens. I push the play button but nothing moves, no counter starts rolling... nothing.

The play button is effective though. When I launch gnusound in a terminal and press the button, corresponding output is: 
```
/bin/sh: /usr/bin/esd: not found
player_start:1049: reaping player thread...
player_start:1051: player thread reaped
player_start:1076: waiting for player thread to initialize...
player_start:1090: ok, player thread initialized.
msg_send:74: sending message history::committed
msg_send:83: recipient: view-history-changed
view_history_changed:34: history changed
player_thread:807: chunk size: 128
mixer_buffers_alloc:894: mixer buffers allocated: muxbuf: 8192 bytes@0x84f8e18, srcbufs: 512 bytes (* 16)
mixer_buffers_alloc:894: mixer buffers allocated: muxbuf: 8192 bytes@0x8570c10, srcbufs: 512 bytes (* 16)
player_thread:830: starting driver
alsa_open:630: initializing playback device
set_hwparams:420: format: 14, channels: 2, rate: 48000, access: 3
set_hwparams:457: rate: 48000
set_hwparams:466: rrate: 48000
set_hwparams:474: buffer time: 1000
set_hwparams:502: buffer size: 2048
set_hwparams:524: period_size: 1024
player_thread:840: player running, record_mode: 0, record_replace: 0

```
Then, for "stop" button:
```
/bin/sh: /usr/bin/esd: not found
view_button_stop_clicked:391: stop
cmd_play_stop_player:64: shl->player->player_running: 0
msg_send:74: sending message history::committed
msg_send:83: recipient: view-history-changed
view_history_changed:34: history changed

```
I guess the /usr/bin/esd stuff is not critical, since gnusound is not supposed to play through esd anyway. 

I only have this problem with gnusound. Audacity (which uses oss) is ok. Xmms (through alsa) also, and I can use jackd as I want.

I wonder if it could be because I use xfce instead of gnome ? Is anyone using gnusound on something else than gnome ?

Thanks.

---

