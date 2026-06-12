---
title: "XP style shared directory with Samba"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by Clive McCarthy on 2011-06-07
I recently solved (with some help from folks on this forum) a problem I had with getting Ubuntu & Samba to provide a SharedDocs directory similar to that in Windows XP. 
The difficulty I had was that the permissions on the shared directory are, by default, restricted to the _owner_ of the file. So even if you sent the file (or directory) to yourself, from another Ubuntu machine, you don't automatically have rights to it. It's possible, of course, to subsequently gain full permission to the files but it's not automatic.

It's relatively easy to set up sharing. Create a directory somewhere and right click it to set up sharing. If Samba isn't already installed you will be prompted to install it. It's a bit tedious, but straightforward.

With traditional Windows XP SharedDocs directories anything goes. If you have a benign environment, such as a home network, it generally doesn't matter that everyone and anyone can mess with these files -- sharing with XP is like that.

To get Samba to closely emulate the XP behavior, two lines need to be added to the Samba configuration file:

[COLOR="Blue"][B]force create mode = 0777 
[/B][/COLOR]   and 
[COLOR="blue"][B]force directory mode = 0777
[/B][/COLOR]

To do this open a terminal and then type:

**[COLOR="Lime"]sudo gedit /etc/samba/smb.conf[/COLOR]**

Scroll down until you are just below the **workgroup** assignment and add the two lines. Mine looks like this:
[B][INDENT][COLOR="Blue"]workgroup = CLIVEWORKGROUP
force create mode = 0777
force directory mode = 0777
[/COLOR][/INDENT][/B]

Save the file and reboot.
It does cause all the shared files to become potentially executable which will frighten some people. It's therefore a little brutal but it will get the job done.

---

