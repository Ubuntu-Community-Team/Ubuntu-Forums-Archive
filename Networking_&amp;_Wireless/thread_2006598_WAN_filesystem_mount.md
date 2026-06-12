---
title: "WAN filesystem mount"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by greenyouse on 2012-06-19
Hi I need some advice, 

What's the fastest way of mounting a filesystem over an encrypted WAN and can this be done without installing tons of program dependencies?  Could this also work on a public computer just for a one-time connection to the server  (maybe deleting encryption keys after the mount is done)?   I could carry a copy of my encryption keys with me in a jump drive or store them in a private location on the internet for initiating the connection.

I've done a little research and it looks like it may be possible to run NFS (for *nix) or SAMBA (for Windows) within an SSH tunnel inside a main SSH tunnel (done for speeding up the connection [http://protempore.net/~calvins/howto/ssh-connection-sharing/]("http://protempore.net/%7Ecalvins/howto/ssh-connection-sharing/") and using PUTTY for Windows).  Alternatively, IPsec (with FreeS/Wan or strongSwan) could be used but I don't really know very much about IPsec.  Finally, I could just use a VPN but will it be a pain to install?  

I know this is kinda a large question but thanks for any help!

---

