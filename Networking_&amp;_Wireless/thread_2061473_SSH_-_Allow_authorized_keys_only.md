---
title: "SSH - Allow authorized keys only"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by KdotJ on 2012-09-22
Hey all,

I have a server on my network and I perform all tasks on it via SSH but only from inside my local network. The server does a whole bunch of stuff including act as a git server (so it already has a populated authorized_keys file). However, it has come to a point where I will need to access the server and push/pull from it outside of the local network.

What I want: for the server to only allow SSH connections from authorized hosts AND require a password to login. (i.e. if I try to SSH in from a machine that isn't authorized I won't be able to, regardless of if I know the password or not.

How can I configure this?


Thanks in advance

---

### Post by Lars Noodén on 2012-09-22
I was going to suggest using Match in sshd_config for restricting addresses, but it does not work the way I expected it to.  Perhaps it is clear to you.  So failing that, it leave xinetd or iptables to restrict addresses which can connect to SSH.  However, since you will allow connections from the outside world I would recommend disabling password authentication and using just keys for authentication.

---

### Post by KdotJ on 2012-09-22
Thanks for your reply!

> **Lars Noodén said:**
> However, since you will allow connections from the outside world I would recommend disabling password authentication and using just keys for authentication.

So if I understand, doing this will mean I get password-less logins for authorized keys, but no login otherwise? If so that will do just fine.

---

### Post by Lars Noodén on 2012-09-23
To do that set [PasswordAuthentication](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html) to "no" and you're set.  Don't forget to set PermitRootLogin to "no" also.

By the way the logins will only be passwordless if you neglect to put in a passphrase.  There are two ways to mitigate that.  One is to use [command=](http://manpages.ubuntu.com/manpages/precise/en/man8/sshd.8.html) in the authorized_keys file to narrow the mischief the account can get into.  Another is to use a good passphrase, but load the key into an agent so the passphrase only needs to be entered once.

---

### Post by Lars Noodén on 2012-09-23
It looks like the key to [match](http://manpages.ubuntu.com/manpages/precise/en/man5/sshd_config.5.html) was the spacing.  Don't use spaces.  So something like this should work to allow password authentication only from a subnet:

```

PasswordAuthentication yes

Match address *,!192.168.100.0/24
        PasswordAuthentication no

```

Or this

```

PasswordAuthentication no

Match address 192.168.100.0/24
        PasswordAuthentication yes

```

---

### Post by KdotJ on 2012-09-23
Thanks Lars Noodén, this is great

---

### Post by c-m on 2013-04-25
Setting PasswordAuthentication no only turns off password authentication when an authorised key is used. If you try to connect from a device that doesn't have an authorised key the SSH server will default back to password authentication. This isn't secure.

---

