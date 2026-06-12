---
title: "how can i use latest linux-dvb modules?"
date: 2008-12-13
forum: Multimedia Software
---

### Post by txutxe on 2008-12-13
hi,

i've been googling for days now and trying every possible solution... but no luck no far.

The thing is that i'm running a server with kubuntu 8.04.

In this machine i've got a satellite tunner card, lifeview pci trio (saa7134).

Kubuntu recognises the card perfectly. However, dvb modules have a problem with diseqc that is fixed in the newest releases.

So... i decided to give it a try and download and compile the new modules.

i ran "configure" and "make". Then i tried to load the module manually without "make install" , just in case. 

Then i tried to load the modules manually, with "insmod",

and i keep getting messages like this in "dmesg":

**************
[ 26.380810] saa7134: disagrees about version of symbol videobuf_streamoff
[ 26.380819] saa7134: Unknown symbol videobuf_streamoff
[ 26.380954] saa7134: disagrees about version of symbol videobuf_poll_stream
[ 26.380957] saa7134: Unknown symbol videobuf_poll_stream
*************

then i thought that i should may be run "make install" and reboot. I did so, and now i'm not able to load 7134 modules anymore, as the "default  modules" from ubuntu's kernel were replaced with the latest release and they keep saying:

****************
26.382391] saa7134: Unknown symbol videobuf_qbuf
[ 26.382468] saa7134: disagrees about version of symbol video_device_alloc
[ 26.382470] saa7134: Unknown symbol video_device_alloc
[ 26.382500] saa7134: disagrees about version of symbol videobuf_read_one
[ 26.382502] saa7134: Unknown symbol videobuf_read_one
****************

i've already asked the linux-dvb guys, but they assure me that is issue is related to suse and ubuntu distros, they haven't experienced the same in other distro's.

has anyone expierenced such problem while compiling the newest dvb release? Is there a fix for this?

Thanks.

---

