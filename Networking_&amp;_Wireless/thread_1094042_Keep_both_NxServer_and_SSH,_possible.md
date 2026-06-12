---
title: "Keep both NxServer and SSH, possible?"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by choco140 on 2009-03-12
Hi,

I managed to get NxServer working the way I wanted (connection through SSH with internel NxServer database).

My only issue is that my SSH access is not working anymore because Nx is only authorizing its own ssh key.

Does anybody know a way to be able to use BOTH NxServer to remotely connect AND ssh connection through public/private key with paraphrase?

I would like, if possible, to avoid to have to run two sshd daemons at the same time.

Thanks.

---

### Post by kevdog on 2009-03-12
Just a few questions -- your NX server ssh key is installed as root? correct? -- and your personal ssh key is within you ~/.ssh directory?  I'm not sure where the conflict is?

---

### Post by choco140 on 2009-03-12
Nope,

1. NXServer placed an authorized_keys2 file in my ~/.ssh folder, not root's.

2. No mention of that key is done in sshd_config but if I setup that key as one the authorized key in the conf file (AuthorizedKeysFile %h/.ssh/authorized_keys2), NX still works. 

3. If I generate a key myself with ssh-keygen and call it authorized_keys and  modify sshd_config to authorize that key, access is not granted to NXServer.

I could use PasswordAuthentication in SSH and have both working but I am sure I can find a way to have both access working with public/private keys.

---

### Post by choco140 on 2009-03-12
Here is the message I got if I remove authorized_keys2 from home

NX> 502 ERROR: Public key authentication failed
NX> 502 ERROR: NX server was unable to login as user: gdn
NX> 502 ERROR: Please check that the account is enabled to login,
NX> 502 ERROR: the user's home directory, the directory ~/.ssh
NX> 502 ERROR: and the file ~/.ssh/authorized_keys2 have correct
NX> 502 ERROR: permissions setting according to the StrictModes
NX> 502 ERROR: of your SSHD configuration.
NX> 999 Bye.
NX> 280 Exiting on signal: 15

---

### Post by choco140 on 2009-03-13
My issue is that I do not even know how to setup this theoretically.

After I could play around to try and make it work.

What I would like to achieve
1. Access to SSH with public/private key with paraphrase

AND

2. Connect to NXServer using the internal NX Database for credential and public/private key for SSH (without paraphrase - NX does not support that).

Anybody has an idea how to do that?

---

