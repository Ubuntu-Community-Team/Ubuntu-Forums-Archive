---
title: "Trying to pin down serious hardware isues"
date: 2008-10-19
forum: Mythbuntu
---

### Post by amphibem on 2008-10-19
Hey all,

I have been away for a while, running my media center on Windows so as to use NZ's H.264/AAC system. I have just gone back to myth on a shiny new WD 640GB drive, with extra patches for improved H.264 support and AAC support. However I am having some major issues and need help trying to figure them out. In order of importance:

1) Machine hard locks after a period of time. Can run for a number of hours, then will lock. Happens under load (such as commflagging or file transfers) or not. I have tried with 2 sticks of RAM (old plus new), the old stick and the new stick seperately. Always locks up, eventually. Nothing in mytht's logs about seg faults, however..

2) Massive logs. Both frontend and backend fill up with this:
```
2008-10-20 07:37:05.897 [h264 @ 0x7f66c7de2300]number of reference frames exceeds max (probably corrupt input), discarding one
2008-10-20 07:37:05.898 [h264 @ 0x7f66c7de2300]number of reference frames exceeds max (probably corrupt input), discarding one

```

And yes, that is every 0.001 seconds. I just did a log rotate, the old ones where 357MB (backend) and 940MB (frontend). This seems to have no effect on the playback ability, I can watch TV fine and this happens when I am not trying to watch TV. In fact my backend log is growing right now, and the TV isn't playing.

3) Network disconnects. Not certain what the cause of this is but, under ubuntu and vista, this machine often losses its local netwrok connection. It is at the end of a long cable run (~15m), don't know if that is at fault. Anyway, this is a lower priority to the other stuff.

I am going to disable myth logging now, could do without that load on the hard drives. Maybe it is causes the crashes, would be an easy solution!

Any thoughts appreciated.

Edit: System is in sig, did a manual partion on the hard drive with a small Ext3 partition mounted at /, with a large partition mounted at /var formatted as JFS. Just in case its relevant.

---

