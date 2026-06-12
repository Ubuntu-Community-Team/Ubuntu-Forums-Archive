---
title: "Diskless 9.04 running but..."
date: 2009-05-12
forum: Mythbuntu
---

### Post by DrJohn999 on 2009-05-12
Running an ASUS P5WDG2WS-Pro / GeForce 7600GT --> Samsung 226 via DVI / 2 GB box with 9.04 diskless frontend (only) booting off 1 GB USB drive with image from 9.04 server / backend. Runs with nVidia 180.44. No plug-ins have been set up yet. This works well, except for:

1. Myth's time is 7 hours early (i.e. it's at GMT). In Watch TV, browse the current programs by pressing the up or down arrow: the time displays as 7 hours early and the program listing is for what was showing 7 hours earlier. Select a channel, and the OSD updates to show whats actually on now, via EIT I'm sure. The $> date command produces the correct result. The PC's internal clock (as seen in BIOS setup) has the right time, and the server PC has the right time. But not Myth on the diskless frontend...

2. In the (Alsa) mixer, the Front volume setting does not persist across boots; it always comes up muted and at zero volume. This control, Master, and PCM all must be on to get sound from the board's stereo output. The other Alsa settings do seem to persist.

3. Shutdown is not clean: the system attempts to access the aufs after the lan connection has gone down (timestamps not recreated here):

```
umount /cow
not mounted
SQUASHFS error: sb_bread failed on reading block device 0x4643e
unable to read cacheblock
unable to read directory block
nbd0: attempted send on closed socket
end request: I/O error, dev nbd0, sector 549020
```
This happens on shutdown either from the frontend, from the GUI, or via terminal shutdown command.

System is no longer responsive at this point, but does reboot successfully so no lasting harm apparent, more of an annoyance.

Each of these look like bugs to me -- anyone else having the same experience?

-- DJ

---

### Post by the_crowbar on 2009-05-13
1)
My Linux machines expect the hardware clock to be set to GMT. Windows expects it to be set to local time. If you do not dual boot try setting the bios clock ahead 7 hours to match GMT.

Look at the /etc/default/rcS file. It has a setting for whether the hardware clock is UTC or not. (try man rcS).

2)
The file that saves the alsa settings is /var/lib/alsa/asound.state. Try to move this file somewhere else and then execute 'sudo alsactl save'. Make sure a new asound.state file has been created. If it has then mute one or more alsa channels and try a 'sudo alsactl restore'. If the restore command brings the channels back to the correct sound level you should be ok.

3)
I don't do diskless clients so I can't help here.

---

### Post by rlowery on 2009-05-13
3) is supposedly fixed by [https://bugs.launchpad.net/ubuntu/+source/mythbuntu-diskless/+bug/292319](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-diskless/+bug/292319) but it did not work for me.

Note, this diff attached to this problem is not quite correct
-    mkdir -p /var/run/sendsigs.omit.d/
+    mkdir -p /lib/init/rw/sendsigs.omit.d/nbd-client

should be
-    mkdir -p /var/run/sendsigs.omit.d/
+    mkdir -p /lib/init/rw/sendsigs.omit.d/

Please let me know if you manage to get this working.  For now I am just using halt rather than shutdown

-Rob

---

### Post by DrJohn999 on 2009-05-17
> **the_crowbar said:**
> 1)
My Linux machines expect the hardware clock to be set to GMT. Windows expects it to be set to local time. If you do not dual boot try setting the bios clock ahead 7 hours to match GMT.

Look at the /etc/default/rcS file. It has a setting for whether the hardware clock is UTC or not. (try man rcS).

2)
The file that saves the alsa settings is /var/lib/alsa/asound.state. Try to move this file somewhere else and then execute 'sudo alsactl save'. Make sure a new asound.state file has been created. If it has then mute one or more alsa channels and try a 'sudo alsactl restore'. If the restore command brings the channels back to the correct sound level you should be ok.

3)
I don't do diskless clients so I can't help here.

1) The backend machine is not a dual-boot, the frontend is, so that may explain this problem. I plan to build a mythbuntu-only diskless frontend at some point, so I'll find out then.

2) The problem here is that only the one control, Front, is zeroed and muted but the others keep their settings, i.e. alsa settings are being saved, but not exactly correctly. Not a big deal since the frontend won't be booted too often anyway.

3) This fix should show up in a weekly build at some point, right?

---

### Post by the_crowbar on 2009-05-19
2) I had the exact same error on 8.10 upgraded to alsa 0.19. All settings except the front volume were restored. The newer version of alsa renamed some of the audio connections. My instructions above cause alsa to save an entirely new config file. It should fix your problem.

---

### Post by mal on 2009-05-20
> **rlowery said:**
> 3) is supposedly fixed by [https://bugs.launchpad.net/ubuntu/+source/mythbuntu-diskless/+bug/292319](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-diskless/+bug/292319) but it did not work for me.

Note, this diff attached to this problem is not quite correct
-    mkdir -p /var/run/sendsigs.omit.d/
+    mkdir -p /lib/init/rw/sendsigs.omit.d/nbd-client

should be
-    mkdir -p /var/run/sendsigs.omit.d/
+    mkdir -p /lib/init/rw/sendsigs.omit.d/

Please let me know if you manage to get this working.  For now I am just using halt rather than shutdown

-Rob

I was able to fix this problem with the following patch to /opt/ltsp/i386/etc/init.d/mythbuntu-diskless-client

- pidof nbd-client > /var/run/sendsigs.omit.d/nbd-client
+ pidof nbd-client > /lib/init/rw/sendsigs.omit.d/nbd-client

Frontends now shutdown correctly.

Mal

---

### Post by bturig on 2009-06-21
I had the SquashFS error too, but it was not clear to me how to use the debdiff, so taking advice above from mal, I did this.

On the diskless-server I edited the mythbuntu-diskless-client file with nano (nano is text file editor).
From the terminal to open up the file 
"sudo nano /opt/ltsp/i386/etc/init.d/mythbuntu-diskless-client"

Change "mkdir -p /var/run/sendsigs.omit.d/"
to "mkdir -p /var/run/sendsigs.omit.d/"

Change "pidof nbd-client > /var/run/sendsigs.omit.d/nbd-client"
to "pidof nbd-client > /lib/init/rw/sendsigs.omit.d/nbd-client"

Save and exit the file ctrl-O, ctrl-x

and then lastly to put the changes to the image, from the terminal "sudo ltsp-update-image". I rebooted my frontends, and now my shutdowns are pleasant.

---

### Post by mitchell2345 on 2009-08-06
I have having the squashfs error as well.  Running trunk.  Is this still not fixed?

~Mitchell

---

### Post by laga on 2009-08-13
Please report any bugs you find at [http://bugs.launchpad.net/mythbuntu](http://bugs.launchpad.net/mythbuntu)

---

