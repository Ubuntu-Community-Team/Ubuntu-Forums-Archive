---
title: "KNetworkManager doesn't run script in /etc/NetworkManager/dispatcher.d"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by SeijiSensei on 2010-09-20
I'm trying to get KNetworkManager to run a script after my wireless connection is activated.  I created the script in /etc/NetworkManager/dispatcher.d using the same format as [scripts to start firewalls]("https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20Startup%20for%20NetworkManager"), but it doesn't seem to run.  I can run the script successfully from the command prompt, but it doesn't happen automatically.  Any hints?

Kubuntu 10.10

---

### Post by marshcast on 2011-01-24
bump.

I have the same problem, but running peppermint.

checks so far are that script is:
- a regular file
- owned by root
- not writeable by group or other
- not setuid
- executable by owner

- has 99xxx for filename

still script doesn't run.

any offers?

---

