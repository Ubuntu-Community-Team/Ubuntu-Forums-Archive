---
title: "plink aborts with SSH2_MSG_CHANNEL_FAILURE"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by Newbunto on 2012-12-17
Fairly reproducibly plink will abort with the following error

Disconnected: Received SSH2_MSG_CHANNEL_FAILURE for half-open channel 258
FATAL ERROR: Disconnected: Received SSH2_MSG_CHANNEL_FAILURE for half-open channel 258

when being used for port forwarding.

I think this used to happen on Windows too. On Ubuntu plink is identifying itself as

SSH-2.0-PuTTY_Local:_Mar__5_2012_09:49:21

I found one page that said that this is a PuTTY bug ( [http://askldjd.wordpress.com/2010/07/07/a-fix-for-puttys-portfwd-corrupt-bug/](http://askldjd.wordpress.com/2010/07/07/a-fix-for-puttys-portfwd-corrupt-bug/) ) but I have also seen claims that this is a bug in the SSH server.

Does anyone know which is true? If it's a PuTTY bug, is a fix available in the Ubuntu version?

---

### Post by Newbunto on 2012-12-17
Update: Booted up an ancient Windows box and PuTTY 0.59 works reliably while PuTTY 0.61 does not.

Are there other command line SSH forwarding clients that have the same functionality as plink available on Ubuntu that I should be looking at?

---

### Post by chadk5utc on 2012-12-17
I use putty and winscp all the time at work and at times at home. I am not sure what versions I have at the office but I believe the ones at home are current. and my ssh server is also current.

You might check your connection options in Putty?

---

### Post by Newbunto on 2012-12-18
Some progress: I changed my plink command into an ssh command. The functionality seems very comparable. Importantly though ssh does not abort where plink does.

The situation where plink aborts seem to relate to a large number of short connections that are forwarded. I am forwarding insecure HTTP over SSH. I see a lot of forwarded connections in a short space of time.

For my purposes I think this is "solved" even though the underlying problem is clearly not solved.

---

