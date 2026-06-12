---
title: "Viedeo grabbing stops after several tenths"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by petopjotr on 2008-01-31
I'm trying to grabb viedo in Gutsy Gibon but it stops after some tenths of second. I tried Kino, DVgrab and kdenlive. In kdenlive grabbing didn't strat. I don't know what to do with it.
Thank's for your answer.

---

### Post by petopjotr on 2008-02-01
no one knows?

---

### Post by disturbed1 on 2008-02-01
Without listing at least what you've got connected to your PC, I doubt anyone would be able to offer some advice. (My car is doing this thing help!!!! ;) )

Just because you listed Kino, doesn't automatically equate to using a DV Camera. There are other firewire capture devices. As well as different cameras. Some need to be powered on before connecting to the PC, some have to be powered off, some (most) can be controlled across firewire (play stop FF/RW) others have poor standards implementations. Just too many variables. Start with some of those things. Try connecting with the power off and/or on. Use the camera's own control to start playback before recording.

What error messages are present.

What did dvgrab print out when you attempted to use it on the command line?

---

### Post by petopjotr on 2008-02-02
So,
I have DV camera Sony DCR-TRV330E, this camera needs to be powered on when I want grabb video, when it is off, computer don't find it. It is controled by computer, but in Kino and also in DVgrab when it strats grabbing, starts playing, but after theese several teths grabbing stopped, but camera don't , I must stop and rewind it manually. Kino shows no error message, but DVgrab writes this:
```
"dvgrab-001.avi": buffer underrun near: timecode 00:00:00.21 date 2007.12.26 11:51:03
This error means that the frames could not be written fast enough.
```

---

### Post by disturbed1 on 2008-02-02
That error message is stating that your PC is too slow to keep up with DV grabbing. 

Do you have any other programs running while attempting to transfer the footage?

Are you trying to transfer footage to a local hard drive?

Unless your PC is really old (486 era) it should be more than enough to transfer DV footage. It takes almost 0 cpu, but does require ~4-5mb/s throughput for the hard discs.

---

### Post by petopjotr on 2008-02-02
My PC has processor Intel Core2Duo 2 GHz, 2015 MB Ram, I have NVidia GeForce 8400 M graphic card. During transfering only firefox and thunderbird was running, and I was trying to transfer it to local hrad drive.

---

### Post by disturbed1 on 2008-02-02
Let's test hard drive throughput -

```

dd if=/dev/zero of=null.bin bs=1024 count=300000
```this creates a dummy file of 307mb called null.bin, after it's done you should see something like this
```

300000+0 records in
300000+0 records out
307200000 bytes (307 MB) copied, 4.44175 seconds, 69.2 MB/s
```

Average systems should be between 35-80 MB/s. If it seems slow, check to see if an indexing daemon is running (beagle/tracker).

You could try to increase the buffers
dvgrab -buffers 200 foo.avi

Also, check to make sure your attempting to capture to a directory you have write permission to. Like your home directory.

---

### Post by petopjotr on 2008-02-03
so, I tried the first command, you wrote, I had 80 MB/s, I checked indexing daemon and tracker is running, then I tried to increase buffers and I'm sure, that I have permision to write to destination directory, but it made same error as before.

---

