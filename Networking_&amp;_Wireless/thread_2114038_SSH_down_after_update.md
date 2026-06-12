---
title: "SSH down after update"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by tom hallward on 2013-02-09
Hello all,

I have an SSH server set up on my desktop. I recently ran an Ubuntu system update and ever since the SSH login hangs. I've searched through the config files for an obvious fix, but I am not quite sure which config files are for the server and which are for the client.  From what I can tell, there is a discrepancy in the ecdsa verification. I tried to delete the keys and start over, but no luck. Also, I tried --purge deleting and reinstalling the server and client, but I am left with the same error. Here is my output when I run ssh -v:

```

OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to MY_IP[MY_IP] port 22.
debug1: Connection established.
debug1: identity file /home/robert/.ssh/id_rsa type -1
debug1: identity file /home/robert/.ssh/id_rsa-cert type -1
debug1: identity file /home/robert/.ssh/id_dsa type -1
debug1: identity file /home/robert/.ssh/id_dsa-cert type -1
debug1: identity file /home/robert/.ssh/id_ecdsa type -1
debug1: identity file /home/robert/.ssh/id_ecdsa-cert type -1

```and here it hangs for a while before saying exiting with an error. I have two questions.

1) Where is the config file to eliminate all the options but a password login on the host side? How do I implement that change? (I imagine it is just commenting out a line or two but I am a serious noob)

2) What kind of error am I experiencing here, and how can I correct it without eliminating the ecdsa verification?

Thanks for the help.

---

