---
title: "Potential Issue: QNAP NAS Firmware Update"
date: 2012-07-22
forum: Networking &amp; Wireless
---

### Post by ytene on 2012-07-22
All,

My QNAP TS-459 Pro II NAS was set to automatically check for new firmware updates. Yesterday I noticed that it had downloaded a new image and wanted a reboot, so gave the OK.

Today I am unable to access the NAS using NFS from my (12.04) ubuntu builds (either 32-bit or 64-bit) but can access it OK from my Mac Mini or a Windows 7 (64-Bit) machine. Windows is using CIFS, the Mac is using Apple's native network file system.

My QNAP itself claims to now be running 3.7.1 Build 20120615.

This is interesting, because the QNAP Downloads page, here:-

[http://www.qnap.com/en/index.php?lang=en&sn=848&c=351&sc=3351](http://www.qnap.com/en/index.php?lang=en&sn=848&c=351&sc=3351)

reckons that a new release was issued just yesterday [what a coincidence]. At the moment I am experiencing difficulties pulling in 20120722, but I will report back if/when I get it uploaded and if I can confirm whether or not this is the fix for the problem. 

In the interim, please be wary of the 0615 build. 

[ Note, there were a *lot* of patches released for 12.04 in the last 2 days, and I wondered if any of these were responsible, as they included updates to nfs-common. I have tried reverting back to an old 12.04 image (last patched on June 3rd) and I see the same problem. Whilst I can't categorically state that the latest updates are fully functional, I can state that a relatively old image sees the issues with the "new" QNAP firmware.

Updates to follow, if I get anything...

---

### Post by ytene on 2012-07-22
Sorry, should have said that this is how I am configured to access the QNAP from 12.04:

# QNAP TS-549 Pro II NAS
192.168.1.41:Public        /media/nas  nfs  rw,hard,intr   0     2
#

---

### Post by ytene on 2012-07-22
For what it's worth, this is the error message I can induce:-

# sudo mount -a
mount.nfs: requested NFS version or transport protocol is not supported
#

Nothing gets reported to syslog. 

Next step will be to revert the QNAP to an earlier firmware release [once I can get an image to download cleanly] then take it from there...

---

### Post by ytene on 2012-10-17
Sorry for such a delay in giving this update.

I spent quite a bit of time working with some very helpful folk over at the QNAP forums, and after a little bit of experimentation, I got this to work with 12.04:-

//192.168.1.41/Public                           /media/nas      cifs    defaults,rw,username={myUserID},password={MyPassword},file_mode=0777,dir_mode=0777

where {MyUserID} and {MyPassword} are substitutes for the real values for the purpose of this illustration. For what it's worth, I am now running Firmware 3.7.1 Build 20120615, although my QNAP has started to tell me that there is a newer build available, so I should probably start thinking about that at some point. 

Am a bit reluctant, as my experience so far is that any change to the QNAP Firmware has prompted more tinkering... [ So far I've been from CIFS to NFS and back to CIFS again ].

---

