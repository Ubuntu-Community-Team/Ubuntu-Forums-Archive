---
title: "Mythbuntu 12.04 LTS - Is user mythtv locked out of SSH login by default?"
date: 2014-01-11
forum: Mythbuntu
---

### Post by neutron68 on 2014-01-11
I'm wondering if user mythtv is locked out of SSH login by default?

I looked in the /etc/ssh/sshd_config file and I do NOT see any lines that say "DenyUsers mythtv".

Either user mythtv can login via SSH, or user mythtv is locked out of SSH login, and it isn't obvious where that restriction is made.

Curious,
Eric

---

### Post by tuat2 on 2014-01-11
User mythtv is a system user and has no password. That should prevent SSH login.

---

### Post by neutron68 on 2014-01-12
Thanks for that answer.

In the past (2008-ish), we had to put the "DenyUsers mythtv" into the /etc/ssh/sshd_config file to prevent the mythtv user from SSH logins.

How is this system user (no login) distinction made, now?  
Is there a particular config file that sets this status?

Thanks,
Eric

---

### Post by steeldriver on 2014-01-12
... something in the back of my mind says that setting no password on an account only disables password-based login, and key-based SSH would still be enabled. Don't quote me on that though.

---

### Post by tuat2 on 2014-01-12
@steeldriver:
That's right, but wouldn't that require keys to be created + copied to the client?

---

### Post by neutron68 on 2014-01-13
> **steeldriver said:**
> ... something in the back of my mind says that setting no password on an account only disables password-based login, and key-based SSH would still be enabled. Don't quote me on that though.

Are you thinking that some config file somewhere has a line that says something like "NoPassword mythtv"?
Any idea which config file?

Thanks!

---

### Post by tgm4883 on 2014-01-13
> **neutron68 said:**
> Are you thinking that some config file somewhere has a line that says something like "NoPassword mythtv"?
Any idea which config file?

Thanks!

No, he's saying that the mythtv user doesn't have a password set, and that accounts that don't have passwords set can't login via SSH.

---

### Post by steeldriver on 2014-01-13
sorry, just to clarify what I meant was that *if* the mythtv user had set up valid key based SSH authorization (or an admin user had created an inserted the keypair for the account) then just removing the account password would *not* be sufficient to prevent SSH login - it would only prevent password-based SSH login

---

### Post by neutron68 on 2014-01-15
> **tgm4883 said:**
> No, he's saying that the mythtv user doesn't have a password set, and that accounts that don't have passwords set can't login via SSH.

So, as long as making a user (with the newuser command) with no password is not prohibited, its ok to do so?

Eric

---

