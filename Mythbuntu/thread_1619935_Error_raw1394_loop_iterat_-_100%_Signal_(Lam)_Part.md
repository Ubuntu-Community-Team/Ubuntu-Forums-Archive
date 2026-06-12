---
title: "Error: raw1394_loop_iterat - 100% Signal (Lam) Partial Lock - No video"
date: 2010-11-12
forum: Mythbuntu
---

### Post by chrismurf2900 on 2010-11-12
I've got Mythbuntu 10.10, I can watch all unencrypted channels except for one (channel 122).  Upon going to this channel, I can't receive any video or audio.  It just sits there telling me that I have "100% Signal | (Lam) Partial Lock" but doesn't show me anything.

No errors on my frontend logs come up, only on the backend.  Here is the error I keep getting (and it keeps displaying that error a few times per second):

Note: GUID has been taken out
```
2010-11-12 10:54:02.810 LFireDev(GUID), Error: raw1394_loop_iterate
            eno: No such device (19)
2010-11-12 10:54:02.811 LFireDev(GUID), Error: raw1394_loop_iterate
            eno: No such device (19)
2010-11-12 10:54:02.811 LFireDev(GUID), Error: raw1394_loop_iterate
            eno: No such device (19)
```I've tried the firewire_tester, and everything works fine for point-2-point connection.

No other errors before or after that.  It doesn't appear that this channel is encrypted or anything (considering the error that comes up).  Any help would be great!

Thanks!

---

### Post by ian dobson on 2010-11-12
Hi,

Looking in the code I see

```
// Performs blocking read of next 4 bytes off bus and handles
// them. Most firewire commands do their own loop_iterate
// internally to check for results, but some things like
// streaming data and FireWire bus resets must be handled
// as well, which we do here...
int ret = raw1394_loop_iterate(GetInfoPtr()->fw_handle);
if (-1 == ret)
{
VERBOSE(VB_IMPORTANT, LOC_ERR + "raw1394_loop_iterate" + ENO);
}
```

Are you sure the device exists (as configured in myth-setup) and has to correct permissions so that mythtv can read/write to it.

Regards
Ian Dobson

---

### Post by chrismurf2900 on 2010-11-12
> **ian dobson said:**
> 
Are you sure the device exists (as configured in myth-setup) and has to correct permissions so that mythtv can read/write to it.

Regards
Ian Dobson

I can see other channels, except that one, and they are all on the same device (I only have one connection, a firewire connection).  The device it's specifying, does exist.

How can I check to make sure that there are correct permissions for read/write access?

Thanks Ian!

---

### Post by ian dobson on 2010-11-13
Hi,

Could you try rescanning your channels, If the error is only comming on on channel then it's got to be something with this channel.

Other than that I'm not sure. Is there a way to check if this channel works with a different program? Maybe vlc supports firewire based tuners.

Do you see any messages in the syslog (/var/log/syslog) when you tune to the dud channel.

Regards
Ian Dobson

---

### Post by chrismurf2900 on 2010-11-13
No messages in the syslog log file.

On mythTV bakend setup, the "scan for channels" option can't be selected, only "fetch channels from listing source" option can be clicked.
Is there another way to scan?

I don't know how to check via VLC whether I can view channel 122 or not.  Do you know how?

Thanks!

---

