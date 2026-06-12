---
title: "noob question re: SSH keys"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by badperson on 2010-02-21
I'm reading thru the [docs ]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")on SSH keys, and, for example, when it tells you to enter this in the terminal:

> The first step involves creating a set of RSA keys for use in authentication.

To create your public and private SSH keys on the command-line:

mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa

is that the server or client machine it's talking about? 
thanks, 
bp

---

### Post by Brandon Williams on 2010-02-21
You can run those commands on either the client or the server, but they will generally be run on the client. Those command are for creating the full key (private and public halves), and you will frequently (though not always) use a different key for each possible client machine. In that case, the private half will only ever be needed on one client, so you will create the key on that client machine and then add the public half of the key to the .ssh/authorized_keys on each machine you want to be allowed to connect to using the key.

---

### Post by 2hot6ft2 on 2010-02-21
> **Brandon Williams said:**
> You can run those commands on either the client or the server, but they will generally be run on the client. Those command are for creating the full key (private and public halves), and you will frequently (though not always) use a different key for each possible client machine. In that case, the private half will only ever be needed on one client, so you will create the key on that client machine and then add the public half of the key to the .ssh/authorized_keys on each machine you want to be allowed to connect to using the key.
I found that to be confusing as well. Perhaps you can suggest an edit to the instructions there that will make the instructions more clear?
If you would care to look at the page here
[http://help.ubuntu.com/community/SSH/OpenSSH/Keys](http://help.ubuntu.com/community/SSH/OpenSSH/Keys)

And suggest the re-wording for this part
> Generating RSA Keys

The first step involves creating a set of RSA keys for use in authentication.

To create your public and private SSH keys on the command-line:

mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa

You will be prompted for a location to save the keys, and a passphrase for the keys. This passphrase will protect your private key while it's stored on the hard drive and be required to use the keys every time you need to login to a key-based system:

I can make the edits but I don't want it to make it even more confusing OR wrong.

---

### Post by 2hot6ft2 on 2010-02-21
Nevermind. In the paragraph above that it leads to the conclusion that it would be done on the client so I edited it to this:
> Generating RSA Keys

The first step involves creating a set of RSA keys for use in authentication.

This should be done on the client.

To create your public and private SSH keys on the command-line: 
I hope that's correct.

---

