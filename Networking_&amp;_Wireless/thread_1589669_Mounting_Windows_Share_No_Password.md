---
title: "Mounting Windows Share No Password"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by mooreted on 2010-10-06
We have a computer here with stuff on it we all use. If I load up my Windows XP VM and open it through My Network Places it loads up just fine. In Ubuntu Nautilus complains that it cant mount the share. If I do:

sudo mount -t cifs //tech1/e /mnt/tech1

it asks for a password. There is no password.

---

### Post by dmizer on 2010-10-07
Are you sure that it's asking for a share password and not a local password for sudo?

If it really is asking for a share password, try this:
```
sudo mount -t cifs //tech1/e /mnt/tech1 -o guest
```

---

### Post by mooreted on 2010-10-07
> **dmizer said:**
> Are you sure that it's asking for a share password and not a local password for sudo?

If it really is asking for a share password, try this:
```
sudo mount -t cifs //tech1/e /mnt/tech1 -o guest
```

Yeah, I tried my sudo password and it just said "try again". I tried the -o guest and got "connection refused", I assume the guest account is disabled. The user is Frank so I tried -o Frank and it went back to asking for a password.

Frank claims there's no password. But maybe Windows just logs him in automatically and there is a password. I think I'll try logging out on his machine and see if it asks for a password to get back in. Although, Windows doesn't ask for a password when I connect from a Windows machine.

Also - thinking out loud here - I better try using the IP address instead of the hostname. There may be a DNS problem.

---

### Post by mooreted on 2010-10-07
Well, darn, using the IP address didn't work. It first asks for the sudo password then asks for the share password.

Frank is now granting "Everyone" access. We'll see what that does.

---

### Post by mooreted on 2010-10-07
Ah ha, that worked.

So, even if you give a Windows share read/write access, you still need to add "Everyone" to the permissions to connect from your Linux box.

---

### Post by dmizer on 2010-10-07
> **mooreted said:**
> Ah ha, that worked.

So, even if you give a Windows share read/write access, you still need to add "Everyone" to the permissions to connect from your Linux box.

Good to hear you got it working!

---

