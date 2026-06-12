---
title: "[SOLVED] Watch Videos module doesn't load after updates"
date: 2008-03-15
forum: Mythbuntu
---

### Post by freymann on 2008-03-15
After installing MythBuntu 7.10 on a server, client and server/client, all 3 machines have gone through the updates (137+) and things are going well. LiveTV produces video on the clients.

But when I try to watch my videos, or even double check the path to the videos in the setup, nothing happens.

I think this may be talked about already? From my frontend log:

```

2008-03-15 09:34:00.863 Unable to initialize plugin 'mythstream'.
/usr/lib/mythtv/plugins/libmythvideo.so: undefined symbol: _ZN18ConfigurationGroup6byNameE7QString
2008-03-15 09:34:00.865 MythPlugin::init() dlerror: /usr/lib/mythtv/plugins/libmythvideo.so: undefined symbol: _ZN18Con
figurationGroup6byNameE7QString
2008-03-15 09:34:00.865 Unable to initialize plugin 'mythvideo'.
Failed to bind for SIP connection 192.168.0.2

```

I guess I'll do some more reading...

---

### Post by murbanci on 2008-03-15
I think this might be what you are looking for.  Hope it helps.
[http://ubuntuforums.org/showthread.php?t=724733](http://ubuntuforums.org/showthread.php?t=724733)

---

### Post by freymann on 2008-03-15
After reading some posts on further pages, the "fix" wasn't too difficult.

On all machines:

```

sudo apt-get update
sudo apt-get upgrade
sudo dist-upgrade

```

On the main backend/frontend:

```

sudo apt-get install mythvideo

```

That was the easy part.

Then on all of the frontends (I have 3)

1. Unmount any NFS shares on the main backend
(I just sudo pico /etc/fstab and rem'd out the 4 lines I had and rebooted)

2. sudo apt-get install mythvideo

3. Remount any NFS shares on the main backend
(I did a sudo pico /etc/fstab and uncommented out what I did before, rebooted).

I had to go back to the main backend and re-add my capture card in order for LiveTV to work again. Not sure if that's related to these updates.

And now I have everything working again!

2 days setting up 4 boxes under MythBuntu and I have a complete system! Yippie!

7 or 8 days tinkering with one LinuxMCE core and a few test Media Directors and went nowhere fast. LinuxMCE is definitely not ready to the mass public yet.

Left to do:

-damn, reformat my 500GB IDE drive as EXT3 and then use for my media storage instead of the main drive

-figure out how to make the system change the channel on the external set top boxes

---

