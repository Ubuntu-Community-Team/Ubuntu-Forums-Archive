---
title: "Nautilus: how to configure a cipher for the sftp protocol?"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by martinr on 2012-10-01
How can one configure the cipher that is used by the sftp protocol from within the Nautilus file manager?

I've got a hunch that Nautilus does not use the /etc/ssh/ssh_config file or uses SSH protocol version 1, because file transfers with scp (protocol version 2 with default as well as explicit configurations of the "aes-ctr" cipher) go much faster than the same transfer over sftp from within Nautilus.

Judging from the actual speed, it looks like Nautilus uses the "des" cipher, which turns out to be the default cipher for ssh protocol version 1 and is insecure nowadays.

Do you know how to configure the cipher to use by sftp from within the Nautilus file manager?

---

### Post by albandy on 2012-10-01
> **martinr said:**
> How can one configure the cipher that is used by the sftp protocol from within the Nautilus file manager?

I've got a hunch that Nautilus does not use the /etc/ssh/ssh_config file or uses SSH protocol version 1, because file transfers with scp (protocol version 2 with default as well as explicit configurations of the "aes-ctr" cipher) go much faster than the same transfer over sftp from within Nautilus.

Judging from the actual speed, it looks like Nautilus uses the "des" cipher, which turns out to be the default cipher for ssh protocol version 1 and is insecure nowadays.

Do you know how to configure the cipher to use by sftp from within the Nautilus file manager?

Nautilus uses ssh2
Simply check /var/log/auth.log from your server and you will see it.

This is my auth.log when tranfering files throught nautilus:

Accepted password for user from XX.XX.XX.XX port 34776 ssh2
Oct  1 15:35:01 Server133 sshd[10881]: pam_unix(sshd:session): session opened for user user by (uid=0)
Oct  1 15:35:02 Server133 sshd[11144]: subsystem request for sftp

---

### Post by martinr on 2012-10-01
> **albandy said:**
> Nautilus uses ssh2
Simply check /var/log/auth.log from your server and you will see it.

This is my auth.log when tranfering files throught nautilus:

Accepted password for user from XX.XX.XX.XX port 34776 ssh2
Oct  1 15:35:01 Server133 sshd[10881]: pam_unix(sshd:session): session opened for user user by (uid=0)
Oct  1 15:35:02 Server133 sshd[11144]: subsystem request for sftp

Thanks for you reply! 
You're right I do see ssh2 in my auth.log:

```
Oct  1 09:50:17 Server sshd[5236]: Accepted publickey for XXX from XXX.XXX.XXX.XXX port 42167 ssh2
Oct  1 09:50:17 Server sshd[5236]: pam_unix(sshd:session): session opened for user XXX by (uid=0)
Oct  1 09:50:41 Server sshd[5304]: subsystem request for sftp

```

That leaves part two of my hypothesis. Why do I witness a 50% speed penalty between Nautilus sftp and scp when transferring the same big file to the same location?
The only thing that I can explain it with is a difference in the used cipher.

How can I find out what cipher sftp within Nautilus uses?
Or how can I configure the cipher for Nautilus?

---

### Post by Lars Noodén on 2012-10-02
> **martinr said:**
> 
Or how can I configure the cipher for Nautilus?

From what I can figure, Nautilus does use ~/.ssh/config  So you should be able to set the cipher there using  [Ciphers](http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html).

---

### Post by martinr on 2012-10-02
> **Lars Noodén said:**
> From what I can figure, Nautilus does use ~/.ssh/config  So you should be able to set the cipher there using  [Ciphers](http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html).

Thanks for your reply, but nope, I'm sure scp does use that configuration but Nautilus' behaviour differs from that of scp. The speed difference is about 50% on my rig whilst transferring the same file to and from the same locations.

The question remains, how can one configure the cipher to use by Nautilus, for the sftp protocol?

---

### Post by martinr on 2012-10-03
Now I've tested to transfer an identical big file with sftp from the command line as well as that same file with Nautilus (sftp) from and to the same locations.

From the command line I observerd:
Transfer speed: 1.8 MB/s
and I was not asked for a password because I set up public keys on both hosts in ~/.ssh

From Nautilus I got the following results:
Transfer speed: 1.2 MB/s
I was asked to enter a user name and password for the remote host.

From this last observation I conclude that the ~/.ssh dir is not used by Nautilus and hence gets its configuration data from elsewhere.

Who knows where Nautilus pulls its ciphers configuration data from?

---

### Post by martinr on 2012-10-04
I've come across two open bug reports that have been around since 2008 that notice the same speed impairments with sftp in Nautilus. They are:

Ubuntu launchpad bug report: [slow bulk sftp transfers]("https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/250517")

Gnome bugzilla report: [slow download using sftp://]("https://bugzilla.gnome.org/show_bug.cgi?id=532951")

If you are affected by the same problem, please vote for the bug [here]("https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/250517/+affectsmetoo").

---

