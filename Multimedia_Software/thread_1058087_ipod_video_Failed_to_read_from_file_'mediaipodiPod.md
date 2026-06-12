---
title: "ipod video: Failed to read from file '/media/ipod/iPod_Control/iTunes/iTunesDB'"
date: 2009-02-02
forum: Multimedia Software
---

### Post by richunger on 2009-02-02
Hello folks,

I'm hoping I'm not the only one seeing this of late...

After recent updates on Ibex, I've found that my ipod video appears (when disconnected) to be empty.

The ipod mounts, and when browsing the filesystem I can see the full directory structure that should appear in an ipod.  All the mp3 files are there, the iTunesDB file is there, and I can cat it.

When trying to load the ipod in gtkpod, I see:

Could not open "(null)" for reading extended info.
Extended info will not be used.
iPod Database Import Failed: 'Failed to read from file '/media/ipod/iPod_Control/iTunes/iTunesDB': Input/output error'

dmesg reveals:

[260387.296944] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[260387.298917] sd 10:0:0:0: [sdc] 58605120 512-byte hardware sectors (30006 MB)
[260387.300043] sd 10:0:0:0: [sdc] Write Protect is off
[260387.300047] sd 10:0:0:0: [sdc] Mode Sense: 68 00 00 08
[260387.300052] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[260387.301667] sd 10:0:0:0: [sdc] 58605120 512-byte hardware sectors (30006 MB)
[260387.302787] sd 10:0:0:0: [sdc] Write Protect is off
[260387.302791] sd 10:0:0:0: [sdc] Mode Sense: 68 00 00 08
[260387.302793] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[260387.302799]  sdc: sdc1 sdc2
[260387.310221] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[260387.310333] sd 10:0:0:0: Attached scsi generic sg3 type 0
[262255.499439] attempt to access beyond end of device
[262255.499448] sdc2: rw=0, want=58444470, limit=58444469
[262255.659568] attempt to access beyond end of device
[262255.659576] sdc2: rw=0, want=58444470, limit=58444469
[262255.659584] attempt to access beyond end of device
[262255.659586] sdc2: rw=0, want=58444470, limit=58444469
[262256.574061] attempt to access beyond end of device
[262256.574071] sdc2: rw=0, want=58444470, limit=58444469
[262256.574076] attempt to access beyond end of device
[262256.574077] sdc2: rw=0, want=58444470, limit=58444469
[262557.988667] attempt to access beyond end of device
[262557.988675] sdc2: rw=0, want=58444470, limit=58444469
[262557.988890] attempt to access beyond end of device
[262557.988893] sdc2: rw=0, want=58444470, limit=58444469
[262783.724531] attempt to access beyond end of device
[262783.724541] sdc2: rw=0, want=58444470, limit=58444469
[262783.724989] attempt to access beyond end of device
[262783.724993] sdc2: rw=0, want=58444470, limit=58444469
[263108.872865] attempt to access beyond end of device
[263108.872876] sdc2: rw=0, want=58444470, limit=58444469
[263108.873425] attempt to access beyond end of device
[263108.873428] sdc2: rw=0, want=58444470, limit=58444469

The ipod appears empty in rhythmbox, and simply does not appear in songbird.

My google-fu has come up empty.  Any pointers truly appreciated.

Thanks,
Rich

---

### Post by hackerlife on 2009-02-08
I'm having almost the same problem
I get the same error, but I can actually play the music in Rhythmbox.
My ipod I bought off a friend, and haven't reformatted it or anything because I wanted to save all the music he had on it.
The Ipod Nano I got I reformatted, and that one works fine.
Perhaps this is our problem?
I don't really want to have to reformat 25 gigs of music!

---

