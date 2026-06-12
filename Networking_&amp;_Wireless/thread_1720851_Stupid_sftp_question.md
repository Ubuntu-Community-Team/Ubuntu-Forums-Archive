---
title: "Stupid sftp question"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by freshtoast on 2011-04-03
As the title says: a stupid sftp question

I have an openssh server running which I use for vnc and socks proxy.

What I would like to do is transfer files from the command line, but I am getting nowhere with it. 

Everytime I try to use a sftp command all I get is the usage instructions (which unfortunately don't make very much sense to me!)

Can somebody please give me the syntax for a simple file copy of 'test.doc' from the home directory of [email]username@hostname.com[/email] to the local machine? (and is this run from the local machine before I set up the ssh tunnel, or from the remote machine after establishing the tunnel?)

Many thanks!

Edit: figured it out :)
while ssh requires -p (lowercase) for setting the port, sftp requires -P (uppercase)

---

