---
title: "MythVideo file scan keeps waking up NAS"
date: 2009-12-02
forum: Mythbuntu
---

### Post by kja999 on 2009-12-02
Hi,

I have just moved all my video files for MythVideo onto a NAS and I can't work out why Myth keeps mapping the drive and then pulling the NAS out of sleep mode.

I have disabled the UPNP server which was doing a poll every 30 mins, but something is still doing it even though it is not being logged.

Does anyone know what mythvideo (or myth itself) is doing scanning the video directory when not in use ?


Cheers

---

### Post by ian dobson on 2009-12-02
Hi,

I imagine it's the backend checking how much free space is on the drive/if any recordings should be auto deleted.

Regards
Ian Dobson

---

### Post by kja999 on 2009-12-02
I thought that for a while, but the TV recordings are held on a local disk not the NAS ?!

---

### Post by nickrout on 2009-12-02
> **kja999 said:**
> I thought that for a while, but the TV recordings are held on a local disk not the NAS ?!

lsof will list all open files and the app that is using them.

---

### Post by SiHa on 2009-12-03
If you're using 9.10 - it's not JAMU doing someting via cron is it? Is there something in **/etc/cron.hourly**.
```
$ crontab -e
```...will edit the crontab for the logged in user

---

### Post by kja999 on 2009-12-03
Aha ! Good spot .. yes its the Jamu script..

Disabled and all sorted ! Let the electricity bill settle back down a little now :p


Cheers

---

