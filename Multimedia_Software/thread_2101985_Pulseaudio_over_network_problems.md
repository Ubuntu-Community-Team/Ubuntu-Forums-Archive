---
title: "Pulseaudio over network problems"
date: 2013-01-06
forum: Multimedia Software
---

### Post by load.runner on 2013-01-06
Hello,

I am trying to use pulseaudio over network (installed as daemon on headless pc) and it's not quite working.

When using Totem, the sound work, but the progress bar and the video freezes after a few seconds.
This happens in most players, even with audio files.

An exception is VLC, which basically works.
The video still gets slowly out of sync (it syncs every once in a while (a minute or so) or when I scroll) but at least it doesn't freeze.

I tried to run pulseaudio with -vvv and I get this output: (I stripped the irrelevant stuff)
```

...
I: [pulseaudio] module-tunnel.c: Server signalled buffer overrun/underrun.
...
D: [module-tunnel] protocol-native.c: Requesting rewind due to end of underrun.
D: [module-tunnel] protocol-native.c: Requesting rewind due to end of underrun.
D: [module-tunnel] protocol-native.c: Requesting rewind due to end of underrun.
...

```

All the computers use Ubuntu quantal.
The pulseaudio configuration is mostly default (I tried a few things but didn't help) and the network connection is fine.

Any advice?
Thanks.

---

### Post by wrzomar on 2013-08-15
I'm testing pulseaudio over WiFi since yesterday and must say that Ubuntu's default players from precise suck. I can listen rhythmbox from lucid on precise's pulseaudio but both, rhythmbox and totem, hang or crash while they're trying to connect to lucid's pulseaudio from precise. Audacious and mplayer (and SMplayer) both work but audio hangs every few minutes because of network problems. Is there a way to increase pulseaudio's buffer for network connections? I know that this will probably increase the delay.

---

### Post by ben-Nabiy_Derush on 2013-08-15
I am not sure if it is the same issue, but I was having a similar issue with pulseaudio over LTSP. If you are calling pulseaudio in --system mode, you need to add to the init command:```
-L module-suspend-on-idle \
```

That fixed the issue for me. Manually, I could kill the pulseaudio instance on the client, and reinitialize it, and it would be fixed as well.

But, as I said, this was in LTSP setup.

---

### Post by wrzomar on 2013-08-16
I think that module is already loaded and I'm not calling pulseaudio in system mode. Pulseaudio is almost perfect, I can watch movies using mplayer and there is no delay. I think this is because of:
> default-fragments = 8
default-fragment-size-msec = 10
They're good for localhost but are too small for network, increasing them will probably increase delay and there will be syncing problems in mplayer (but I can adjust A-V delay in mplayer). I'll try this: [http://forums.linuxmint.com/viewtopic.php?f=42&t=44862](http://forums.linuxmint.com/viewtopic.php?f=42&t=44862) solution but I'm afraid this could be even worse than now.

---

