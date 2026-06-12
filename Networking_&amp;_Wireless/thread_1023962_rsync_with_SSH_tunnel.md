---
title: "rsync with SSH tunnel"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by dplecto on 2008-12-28
Hey all,

       I have three machines - two are remote servers (machine A & B)  and the third (machine C) is local. Machine B cannot be accessed directly from the internet - only through machine A due to security issues.



However, I work from machine C that is located outside the network of A & B. I need to use rsync over ssh to sync machine C & B. Normally, to access B, I have to go through machine A - machine C uses a dynamic ip so can't be accessed from outside.

My solution for this has been to use tsocks which is working quite well for me. But, it can be done via a ssh tunnel right ?

So, how do I setup a automated ssh tunnel from B to C via A such that I can rsync my files between B & C ?


Thanks,

---

### Post by jgoguen on 2008-12-29
I haven't tested this, so YMMV.

Start a standard SSH login session with this parameter, in addition to any others you may need:
```
ssh -L 2222:machineb:22 user@machinea
```That will cause ssh on machine A to listen on port 2222 (accessible from the Internet!) and forward anything it gets on that port to port 22 on machine B.  This may not be desirable for security reasons, in which case I don't think this can be done.  If this is acceptable, continue onward.

Now that ssh is listening, try rsync with this parameter, in addition to any others you may use.
```
rsync -e 'ssh -l <machine b username> -p 2222' machinea
```Be careful with hosts and usernames.  The username you need to provide to rsync is the username on machine B, but the hostname (or IP) you provide is for machine A.  Remember to close your SSH session that you opened earlier!

IMO, this counts as making machine B directly accessible from the Internet, so this may not work for you if you absolutely must keep machine B completely inaccessible from the Internet.  If this is OK, then this would work, even though it's a little less convenient.  I don't know if there's a more automated way or a simpler way, but if there is I'm sure someone else will pop in and say so :)

---

