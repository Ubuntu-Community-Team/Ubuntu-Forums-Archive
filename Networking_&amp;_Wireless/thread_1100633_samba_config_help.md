---
title: "samba config help"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by xkaliburx on 2009-03-19
Trying to figure out what /where the problem is as I am still not ubuntu saavy yet.  But I have a ubuntu 64 bit running, samba installed and when I browse from an xp machine I see it in the workgroup.

Clicking brings up the login prompt.  The local user doesn't work, but computername\root + userpassword get's me 1/2 way there as I see the share.

But when I click on the share it prompts again and neither the user nor root work.

I used the basic template given with the install here is what I think is needed to shed some light;

Security;
security=user
encrypt passwords=true

Shares;
[homes]
browsable = yes

I really don't see much else that would say allow root to 'connect' but not have access to the homes share.  Ideally I just want my user to login, not root.

THanks

---

### Post by rbc on 2009-03-19
Just a guess, but have you created the samba password?:
sudo smbpasswd -a "username of local user"
You will then be prompted twice for the samba password, which just for the sake of ease, I always make the same as the user's login password

---

