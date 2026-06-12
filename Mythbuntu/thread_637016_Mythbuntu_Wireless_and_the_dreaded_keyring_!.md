---
title: "Mythbuntu Wireless and the dreaded keyring !"
date: 2007-12-10
forum: Mythbuntu
---

### Post by drifting on 2007-12-10
Can some kind soul help me please?

Just installed Mythbuntu (and very nice too I might add) onto a previous Ubuntu + Myth box.
The wireless keyring pain I hoped had been sorted in 7.10 but apparently not. I have followed so many threads all offering conflicting advice most of which is either inaccurate, or just plain over my head. 

How can I stop the keyring so that that my mythbuntu box does not require a keyboard? I am using WPA encryption.

Regards Paul.

---

### Post by superm1 on 2007-12-10
Check out libpam-keyring.  I've heard varied successes with it.

---

### Post by KillerKiwi on 2007-12-11
You may need to check your key chain password is the same as your login password.

If you have changed your password.. you will need to change the keychain password as well

---

### Post by camelreef on 2007-12-12
> **drifting said:**
> Can some kind soul help me please?

Just installed Mythbuntu (and very nice too I might add) onto a previous Ubuntu + Myth box.
The wireless keyring pain I hoped had been sorted in 7.10 but apparently not. I have followed so many threads all offering conflicting advice most of which is either inaccurate, or just plain over my head. 

How can I stop the keyring so that that my mythbuntu box does not require a keyboard? I am using WPA encryption.

[There was just a thread on mythtv-users just about that]("http://www.gossamer-threads.com/lists/mythtv/users/304553").

The solution is to use a hard config in /etc/network/interfaces and stop using NetworkManager:

Nico

---

