---
title: "Yet Another Person with PVR-150 Remote Problems"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by tonyr1988 on 2007-08-15
I've looked through some other threads and websites, but haven't found anything yet. I could've overlooked something, though. Here are the quick details:

I have a PVR-150. It works fine, so now I'm doing the remote. I have the gray-black remote with 4 colored buttons on the bottom. I'm primarily using [this]("https://help.ubuntu.com/community/Install_Lirc_Feisty") guide. I haven't gotten any error messages so far. The problem starts when I get to the irw command. It stalls like it's supposed to, but it won't do anything when I push buttons. I know the remote is working (I held it up to my digital camera, and can see the light come on).

There are two possible errors I can see. dmesg says:

> [   58.348000] lirc_dev: IR Remote Control driver registered, at major 61 
**[   58.416000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.**
[   58.744000] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[   58.744000] lirc_dev: lirc_register_plugin: sample_rate: 10
[   58.860000]  [<f96300b8>] init_module+0x48/0x50 [lirc_pvr150]

/var/log/syslog shows:

> Aug 15 19:43:57 ubuntu-desktop lircd-0.8.2-CVS[12979]: lircd(userspace) ready
Aug 15 19:44:15 ubuntu-desktop lircd-0.8.2-CVS[12979]: accepted new client on /dev/lircd
Aug 15 19:46:02 ubuntu-desktop lircd-0.8.2-CVS[12979]: removed client
Aug 15 19:54:00 ubuntu-desktop lircd-0.8.2-CVS[12979]: accepted new client on /dev/lircd
Aug 15 19:54:16 ubuntu-desktop lircd-0.8.2-CVS[12979]: removed client
Aug 15 19:55:33 ubuntu-desktop lircd-0.8.2-CVS[12979]: caught signal
Aug 15 19:55:47 ubuntu-desktop lircd-0.8.2-CVS[14606]: lircd(userspace) ready
Aug 15 19:55:49 ubuntu-desktop lircd-0.8.2-CVS[14606]: accepted new client on /dev/lircd
[B]Aug 15 19:55:49 ubuntu-desktop lircd-0.8.2-CVS[14606]: could not get file information for /dev/lirc/0
Aug 15 19:55:49 ubuntu-desktop lircd-0.8.2-CVS[14606]: default_init(): Not a directory [/B]
Aug 15 19:55:49 ubuntu-desktop lircd-0.8.2-CVS[14606]: caught signal
Aug 15 19:56:07 ubuntu-desktop lircd-0.8.2-CVS[14628]: lircd(userspace) ready
Aug 15 19:56:08 ubuntu-desktop lircd-0.8.2-CVS[14628]: accepted new client on /dev/lircd
Aug 15 19:56:22 ubuntu-desktop lircd-0.8.2-CVS[14628]: removed client
Aug 15 20:01:01 ubuntu-desktop lircd-0.8.2-CVS[14628]: caught signal
Aug 15 20:05:40 ubuntu-desktop lircd-0.8.2-CVS[16341]: lircd(userspace) ready
Aug 15 20:05:42 ubuntu-desktop lircd-0.8.2-CVS[16341]: accepted new client on /dev/lircd
Aug 15 20:05:55 ubuntu-desktop lircd-0.8.2-CVS[16341]: removed client
Aug 15 20:07:55 ubuntu-desktop lircd-0.8.2-CVS[16341]: caught signal

I don't have a /dev/lirc/0. I have a /dev/lirc0 and a /dev/lircd. I'm not sure where to go from here. Any help is appreciated.

---

### Post by tonyr1988 on 2007-08-16
*sigh* I feel so stupid. Turns out that the IR cable just wasn't situated correctly in the card. I didn't even think about it, since it fit snugly the first time I plugged it in.

I glanced in the setup guide, and it says, real big and bold: If the remote doesn't work, move the plug around. I just never bothered to read it, since it only covered Windows installation, and I obviously wasn't doing that. :D

---

