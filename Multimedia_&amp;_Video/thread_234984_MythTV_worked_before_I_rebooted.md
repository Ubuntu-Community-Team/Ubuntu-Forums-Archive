---
title: "MythTV worked before I rebooted"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by chadk on 2006-08-12
Well, I don't know why they can't make MythTV a little smarter, or at least the error messages a bit more descriptive.  It seems to take very little to break MythTV.

```
2006-08-12 09:15:29.160 RingBuf(/home/chad/Desktop/MythTV/1024_20060812091523.mpg): Invalid file (fd 17) when opening '/home/chad/Desktop/MythTV/1024_20060812091523.mpg'. 1 retries remaining.
2006-08-12 09:15:29.668 RingBuf(/home/chad/Desktop/MythTV/1024_20060812091523.mpg): Invalid file (fd 17) when opening '/home/chad/Desktop/MythTV/1024_20060812091523.mpg'. 0 retries remaining.
2006-08-12 09:15:30.180 Disable DPMS
2006-08-12 09:15:30.321 NVP::OpenFile(): Error, file not found: /home/chad/Desktop/MythTV/1024_20060812091523.mpg
2006-08-12 09:15:30.332 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2006-08-12 09:15:30.483 TV Error: LiveTV not successfully started
2006-08-12 09:15:30.494 Enable DPMS

```

/home/chad/Desktop/MythTV is a symlink to /MythTV which is /dev/hdb1
/MythTV has chmod 777 and chown chad:chad
I'm not sharing the folder with NFS or SAMBA.

Any ideas?

---

### Post by chadk on 2006-08-12
I got past that, I had the wrong video encoder selected in mythtv-setup.  Seems the error had nothing to do with that. Anyway... now I see this:
```
2006-08-12 09:38:14.844 VideoOutputXv Error: Could not find suitable XVideo surface.
2006-08-12 09:38:14.844 VideoOutputXv: Falling back to X shared memory video output.
                              *** May be slow ***

```

---

