---
title: "sftp not reading ~/.ssh/config"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by uqbar on 2012-11-30
It looks like that sftp doesn't read the local user configuration file ~/.ssh/config, while ssh and scp do.
Am I missing something or what?
TIA.

---

### Post by ajgreeny on 2012-11-30
What exactly are the symptoms of this problem?
Are you able to connect to an ssh server, or is this where the problem lies?
Have you installed openssh-server on the server machine?
On my machines I don't have a file called config in **~/.ssh**, only **known_hosts**; most of the configuration for ssh is in **/etc/ssh/ssh_config** and **/etc/ssh/sshd_config**

---

### Post by uqbar on 2012-11-30
Symptoms are that whatever I write in ~/.ssh/config is gracely ignored by SFTP and kept in consideration by SSH.

---

