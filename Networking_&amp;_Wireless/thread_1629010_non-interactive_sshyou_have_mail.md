---
title: "non-interactive ssh/you have mail"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by scottch.eezem on 2010-11-23
Hey all been googeling this for a couple of days now and coming up empty handed.  basically i have a couple of scripts that involve something like

result = `ssh command | user@localhost`

with public keys set up so there is no fuss about passwords and all that.  

non-interactive ssh used to work fine before I did a distro-upgrade, but now no matter what I am getting mail notifications with interactive and non-interactive ssh sessions.  how do I disable it?  I tried putting CheckMail no in my sshd_config, but sshd just complains when I try and restart it. All of this was working just fine in 10.04


Thanks

---

### Post by scottch.eezem on 2010-11-23
fwiw the method for invoking a non-interactive ssh session has changed.

while 

echo "command" | ssh user@localhost

used to do it

it appears to now be

ssh user@localhost 'command'

---

