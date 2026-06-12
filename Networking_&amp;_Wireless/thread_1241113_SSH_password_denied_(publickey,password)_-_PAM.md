---
title: "SSH password denied (publickey,password) - PAM??"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by l3git.h4cker on 2009-08-15
I recently changed a remote computer's PAM to use blowfish instead of the regular MD5 encryption.
Then did:
sudo passwd user_name
and entered in the same password as before.
Then I logged out of the ssh connection I made earlier, then tried logging back in with the same username/pass combo.

I keep getting this error:
Password denied (publickey,password).

I tried removing the known_hosts file in /home/me/.ssh/ directory, and still no luck.

Is there an option somewhere to make ssh use blowfish such that the remote computer can recognize the password??

I am not 100% sure what is going on here...:confused:

---

### Post by l3git.h4cker on 2009-08-15
Nevermind, I found the fix.

For others who have this problem (or anything similar) here is the fix:

In the directory /etc/pam.d, there are 3 files other than common-password.
These are common-auth, common-session, and common-account.

In each of these, replace 'pam_unix.so' with 'pam_unix2.so'

Done!

---

