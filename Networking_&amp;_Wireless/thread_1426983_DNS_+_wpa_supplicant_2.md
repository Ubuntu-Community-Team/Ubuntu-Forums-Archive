---
title: "DNS + wpa_supplicant 2"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by sag47 on 2010-03-10
Hello I pop in every once in a while with a solution.

I'd like you to move this post to this thread: [http://ubuntuforums.org/showthread.php?t=275073](http://ubuntuforums.org/showthread.php?t=275073) because I found a solution to it.  I tried posting in the thread but got permission errors.

I had DNS problems when using wpa_supplicant and I could not ping google.com but I could ping 66.249.90.104 (google's IP).

The root of the problem is resolvconf.  When you type the command to update the dns you get an error.

NOTE: Do not type # or $ in the commands.  $ means the commands are typed as user.  # commands are typed as root.
```
$ sudo -i
# resolvconf -u
resolvconf: Error: /etc/resolv.conf must be a symlink
```

You can fix this by doing the following command sequence.

```
$ sudo -i
# cd /etc/
# mv resolv.conf resolv.conf.bak
# ln -s /etc/resolvconf/run/resolv.conf ./
# resolvconf -u
```

Now it's fixed.  Please move this to the thread specified because other people may need help with it and it is a possible solution.

Thanks,
SAM

---

