---
title: "Sshd -D at startup; how to remove the -D option"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by InkyDinky on 2011-05-19
Somehow the -D option got tacked on to my sshd when I start up.
How do I remove the -D option when sshd is started at boot? 
I'm guessing I need to edit something in /etc/init.d but not sure what.
I checked System->Preferences->Startup Applications and the ssh server daemon isn't listed there.
And since it is a command line option /etc/ssh/sshd_config is of no help.

Thanks,
Nick

---

### Post by stomp442 on 2011-05-19
Have you checked out:

/etc/init/ssh.conf

or

/etc/default/ssh

Seems that you can kill it by commenting out the last line in ssh.conf

Stomp442

---

### Post by InkyDinky on 2011-05-19
Thanks!
I'm pretty sure that /etc/init/ssh.conf will do the trick

---

