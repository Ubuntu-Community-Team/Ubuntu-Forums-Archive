---
title: "Dell RAC Error: &quot;Connection failed, Socket creation error.&quot;"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by martycombs on 2009-01-09
I have not seen any previous discussions which have referred to this specific error.

We have several Dell servers which we manage using their remote access cards (RAC).  I have a tarball install of firefox-2.x and have manually installed the Dell plug-ins using instructions found at 
([http://blog.wazollc.com/Lists/Posts/Post.aspx?ID=10](http://blog.wazollc.com/Lists/Posts/Post.aspx?ID=10)).

When I attempt to connect to the remote console display I get a box with the error message "Connection failed, Socket creation error."  I have tested this on Ubuntu 7.10 and 8.10 with the same error message being displayed.  However I can run an install of Fedora 10 or RedHat AS4 under VMWare on the Ubuntu system and the remote console display works just fine.  I have not yet tested on another Debian based distro to determine whether this error is specific to Ubuntu or affects all Debian based distros.

I have been able to run the "vv.sh" script within firefox's plugin/videoviewer directory and duplicate the error message.

If anyone has any leads, I would love to solve this mystery.

Regards,
Marty

---

