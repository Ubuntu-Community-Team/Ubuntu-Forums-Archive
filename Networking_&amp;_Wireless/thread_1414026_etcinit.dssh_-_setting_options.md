---
title: "/etc/init.d/ssh - setting options?"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by phaemon on 2010-02-23
Hi there,

I have a problem with ssh, in that it's extremely slow when using putty to connect from Windows. A bit of googling suggested that I should use -u0 as a startup option since there's no DNS entry for this machine.

So, at the risk of sounding stupid, how do I put this options in to the /etc/init.d/ssh file? I tried adding it in the the "set" part but got an error, tried adding another "set" line and got an error and tried adding it to the first command there, but also got an error! Where does it go?

Thanks!

phaemon

---

### Post by Skaperen on 2010-02-23
Try adding a line with "UseDNS no" in your /etc/ssh/sshd_config file.

---

### Post by phaemon on 2010-02-23
Thanks, that's much faster now. I guess that fixes that. Still confused as to how to get that options into the /etc/init.d/ssh file though: is it deprecated or something?

---

### Post by puppywhacker on 2010-02-23
What skaperen said, plus restart ssh-server. Also if you experience slow transfers with winscp try using blowfish or arcfour as encryption method. They are less secure than aes, but generally a factor 2 quicker.(if your a little bit concerned about security, use blowfish and not rc4)

---

### Post by Skaperen on 2010-02-23
If you really Really ReAlLy REALLY wanted to do it via an option, edit /etc/default/ssh and change the line with SSHD_OPTS= to```
SSHD_OPTS="-u0"
```

---

