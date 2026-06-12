---
title: "Creating a LInk to a MS Windows Server Folder?"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by Grrruff on 2012-03-05
Hi everyone!

Just installed Ubuntu 11.10. on a company PC.
The company runs MS Windows Server 2003.

I would like to make a link on my desktop to a folder on our network.  I pathed my way to the folder and created a link then
moved it to my Desktop. When I click on it it reports...

'The Link "Pack_Go Inventor Files" is Broken. Move it to Trash?'
'This link cannot be used because its target "/Pack_Go Inventor Files" doesn't exist.'

How can I create a link that supports the full path?

BTW **Zero** Ubuntu / Linux experience here.

---

### Post by drdos2006 on 2012-03-05
I would say you need to mount the shared folder on your desktop first.

Try this. From a terminal : sudo mkdir /media/sharedfolder
This makes a point to which the shared folder can be connected to.

Next : sudo mount <the-IP-address-of-the-server>:/shared-folder

I do not have Windows Server 2003 to test with.

regards

---

