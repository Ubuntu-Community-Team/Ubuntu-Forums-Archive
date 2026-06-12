---
title: "lirc stopped working in edgy update of 2.6.17-11 kernel"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by beazizo on 2007-03-24
Recently I applied updated my edgy machine.  This included a kernel update from 2.6.17-10 to  2.6.17-11.  I rebuilt my lirc module using module assistant.  However, after rebooting, my remote (Happuage PVR-250 silver remote) stopped working.  Niether lircd or lircmd was running after restarting.  /var/log/syslog showed the following:

lircd-0.8.0[7304]: lircd(userspace) ready
lircd-0.8.0[7304]: accepted new client on /dev/lircd
lircd-0.8.0[7304]: could not open /dev/lirc
lircd-0.8.0[7304]: default_init(): No such device
lircd-0.8.0[7304]: caught signal

So i checked and there was in fact no /dev/lirc.  There where /dev/lircd and /dev/lircmd devices.  

lsmod showed that lirc_i2c and lirc_dev kernel modules were loading correctly.

I tried removing all the lirc related packages/modules/builds and and rebuilt with module assistant again with no luck.

So I switched back to kernel 2.6.17-10 and the remote works again.  lirc processes started correctly and my remote still works when booted under that.  There is are /dev/lirc0, /dev/lircd, /dev/lircm devices.

I'm fine with sticking with 2.6.17-10 kernel but does anyone know what the issue is?

---

### Post by Dubstar_04 on 2007-03-24
Same here. I just rebuilt my mythbox and lirc won't compile when using the guide supplied by superm1. The thing is i have used this guide about 8 / 9 times with older kernals and i have never had a problem before!!

---

### Post by beazizo on 2007-03-28
The latest edgy updates to lirc and lirc-modules-source fixed the problem and lirc and my remote now  works in kernel 2.6.17-11.

---

### Post by kernelsandirs on 2007-03-29
Dang it, there was a lirc update tonight, I cannot get any remote to work now, irkick connects to lirc but no events happen when buttons pressed, no ir events are being received. I am using kernel 2.6.17-11. all of my lirc configs are the same as always.

Update, nevermind I just had to go into /usr/share/lirc/remotes/YOURREMOTE and re-copy the default config to /etc/lirc/lircd.conf

---

### Post by racmar on 2007-03-29
Sure enough, the latest update **0.8.1+cvs20070310-0ubuntu1~edgy1** just borked my mythtv lirc stuff.

I used synaptic to force a downgrade to the old version until it gets resolved.  Interestingly, I didn't have to downgrade liblircclient0, just lirc.  Also, does anyone know the apt- or dpkg command to lookup an older version of a package, and the corresponding command to force the version number?

---

