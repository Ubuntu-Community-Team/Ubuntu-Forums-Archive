---
title: "Windows &lt;-&gt; Linux Sharing Issues"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by zephyrcat on 2009-04-18
I have having two issues sharing files between Linux and Windows:

1. On the Windows (Vista) side, I can see the shared folders and access them if they are set to guest access, but if I don't enable guest access, it prompts me for a username and password. I entered my username and password, but it rejected it. Is there a different username/pass I am supposed to use?

2. I can see the Windows machines on the Linux side, but when I click on them, no shared folders are recognized.

Thanks!

---

### Post by Iowan on 2009-04-19
> **zephyrcat said:**
>  Is there a different username/pass I am supposed to use? The username/pass should be the linux/samba one.  There *may* be a couple of different ways this gets done anymore.  I'm more familiar with setting up a Samba user with **smbpasswd**.

---

### Post by zephyrcat on 2009-04-19
When I run that and go through the steps I get this error:

```
Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE

```

I am putting in nothing for the password, since I have never set the password before. Is there a default password?

---

