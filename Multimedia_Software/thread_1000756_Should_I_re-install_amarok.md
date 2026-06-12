---
title: "Should I re-install amarok?"
date: 2008-12-03
forum: Multimedia Software
---

### Post by lil_rich on 2008-12-03
Hi All,

I'm trying to get a sansa fuze working with amarok on Hardy. It isn't supported with the repository version of libmtp, but is in the latest version (0.3.3) on their website. I installed libmtp from source (I didn't remove the version already installed), and got it working. When I run mtp-detect, I get:

libmtp version: 0.3.3

Listing raw device(s)
   Found 1 device(s):
   SanDisk: Sansa Fuze (0781:74c0) @ bus 0, dev 3

Plus loads of other stuff that makes it look like it's working. I can post if You need it.

Next up, I do:
ln -s /usr/lib/libmtp.so.8 /usr/lib/libmtp.so.7
(So that if amarok is looking for v.7, it sees the new one, v.8).

Now, I start amarok from command line, try to connect, and it gives me:
Device 1 (VID=0781 and PID=74c0) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session

And then crashes (closes completely).

Any ideas? I'm wondering if I need to install amarok from source, but was avoiding it if I didn't need to. Let me know if you need more info.

Cheers.

---

### Post by lil_rich on 2008-12-03
Sorry, but I'm bumping.

Maybe I'll ask another way: If I install libmtp from source, so I need to uninstall amarok, and install that from source, also? If not, how do I get it to use the correct version of libmtp?

Cheers.

---

