---
title: "Karmic: Sound works for root but not for user"
date: 2010-02-07
forum: Multimedia Software
---

### Post by JayDB on 2010-02-07
I cannot find a post that matches this scenario...the id created during the install (from CD) of Karmic has fully usable sound. However, users created from the Users and Groups app do not.

I have made sure that all users are defined to the audio, pulse, pulse-audio, and pulse-rt groups. No luck. 

I have followed every step I have read having to do with the alsamixer. No luck. 

I have verified that alsa and linux itself are at the latest versions.

Does anyone have any other suggestions?

Thanks,
JayDB

---

### Post by warp99 on 2010-02-07
Do the new users have privileges to use sound devices? Go to System > Administration > Users and Groups. Click on a user, then select properties. Check to see if audio devices is checked. If not back out of the dialog box then use the unlock button on the first screen so you can use your admin password. You can then change each user so they have the correct privileges.

---

### Post by JayDB on 2010-02-08
Thanks Warp99...I'll give that a try and let you know.

---

### Post by JayDB on 2010-02-08
I verified that all users have privileges to audio devices. Still not working. Any other ideas???

Thanks

---

### Post by warp99 on 2010-02-08
Run "cat /etc/group" and see if your users are in the audio group and that pulse is also in the audio group. You may want to look at /etc/group a little closer to see if your in a group that others are not.

---

### Post by JayDB on 2010-02-09
Thanks again warp99. I'll give that a try.

---

### Post by JayDB on 2010-02-10
Didn't work. I whittled back to two users on this machine: jay (admin) and norma. The norma id is the one that cannot get any sound. I have attached my group file.

Do you see anything I may be missing?
Thanks,
JayDB

---

### Post by warp99 on 2010-02-10
Here are the groups that one of my users have w/o admin rights:

```
adm dialout fax cdrom floppy tape audio dip video plugdev fuse powerdev sambashare
```

They're in the adm group, but not admin so they don't have access to sudo. The adm group is for system monitoring. You should most likely add that group to your users. Run the following:

```
groups norma
```

and add any groups that are missing:

```
sudo usermod -G $group,$group,$group norma
```

Of course replace $group with the missing groups and include the commas.

---

### Post by warp99 on 2010-02-11
If adding the groups doesn't help post the output of this command:

```
ls -ls /dev |grep audio
```

---

### Post by JayDB on 2010-02-13
For something that should be so simple...this is sure frustrating. I set up the group exactly as you indicated and nothing. I added pulse, pulse-access, and pulse-rt to it and still nothing. I have attached the current group list for norma and I have attached the ls results as you requested. I really appreciate your assistance with this. I'm almost at the point of just handing over my id for all to use (though I know that could quickly spell disaster).

JayDB

---

### Post by warp99 on 2010-02-15
Well your permissions under /dev are correct. If you gave user "norma" admin rights, for testing only, does the sound work?

Edit: I'm sure you know that you need to logout then login that user to have the new group permissions take effect.

---

