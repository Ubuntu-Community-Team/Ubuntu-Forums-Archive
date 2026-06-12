---
title: "SSH forwarding"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by drhiii on 2011-01-04
I am not sure of the terminology so pardon the newb terms.

I have an Ubuntu server installed with a public IP address that I access.  I have a second Ubuntu server installed behind the router with a static IP on the private network (10.1.10.xxx).  

I am trying to learn how to ssh into the public server and have the SSH session forwarded to the secondary private addressed server.  A client wants to be able to access some files from other locations on this server on the private side.  

I suppose I could port forward from the router to the private side server, but that makes me nervous.  Is there a way to do this via the public side server?  Would this provide any enhanced security?

thanks for any advice....

---

### Post by PatchesTheCaveman on 2011-01-04
If the public server has access to the private server, you could just SSH into the public server, then SSH into the private server from there.  That has the advantage of zero configuration, and completely shields the private server from the Internet.

If you wanted, you could even create an account on the public server just for that purpose and set its shell to a script that opens an SSH connection to the private server and optionally prompts for a username.

Otherwise you might as well port forward the router, as doing the port forwarding on the public server really won't add any additional security.

---

### Post by drhiii on 2011-01-04
Thankx for your response.  Yes, the more I think about it, port forwarding from the router may be the way to go.  I can set up some ACLs and required certificate only access, and a few other things, to make it more secure.  

Tx for this.  Stimulates ideas towards this...



> **PatchesTheCaveman said:**
> If the public server has access to the private server, you could just SSH into the public server, then SSH into the private server from there.  That has the advantage of zero configuration, and completely shields the private server from the Internet.

If you wanted, you could even create an account on the public server just for that purpose and set its shell to a script that opens an SSH connection to the private server and optionally prompts for a username.

Otherwise you might at well port forward the router, as doing the port forwarding on the public server really won't add any additional security.

---

