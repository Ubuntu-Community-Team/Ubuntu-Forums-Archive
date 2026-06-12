---
title: "gpg keyserver error"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by rolibalicas on 2009-06-21
Hi All,
I'm trying to add a repository but I can't do so because I can't connect to the Ubuntu key server. When I execute the command to add I get the verbiage below:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com   67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

I tried to ping the ubuntu key server but it was reachable. Has anyone encountered the same?

---

### Post by Aeonsies on 2009-06-22
I haven't experienced that exact error message but I have dealt with something similar recently.  When trying to apt-get update a GPG error signature problem happens.

Perhapse my solution might help you.  

Go to your /etc/apt directory and mv the sources.list file to sources.list.backup

DO NOT REMOVE THIS FILE, we simply want to rename it temporarily.

Now, run sudo apt-get update.

Now mv sources.list.backup to sources.list again and re-run sudo apt-get update.  If this trick worked you should start seeing your repository update.

Hope this helps.

---

