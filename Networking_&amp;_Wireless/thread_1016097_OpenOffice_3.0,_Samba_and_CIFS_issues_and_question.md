---
title: "OpenOffice 3.0, Samba and CIFS issues and questions"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2008-12-19
Okay - apparently there's a problem with Samba and OpenOffice that is in the package manager for Ubuntu - people are ending up with corrupted OpenOffice files when saving files to network drives.

On the OpenOffice forums, it was suggested to move up to OpenOffice 3.0.  However, OpenOffice 3.0 seems to have it's own file browser packaged with the application - and it doesn't recognize the samba-mounted drives.  For a work around, it was suggested to use CIFS to mount the network drives.  It seems to take care of the issues with OpenOffice, but now I'm having problems with boot-up and shut down - especially shut down.  It goes through the Ubuntu screen, then something like apcid shutting down, then a two line error message saying it's not getting a response from the CIFS server.

So, I have a question - what's the best way to fix all this?  I've pretty much given up on Windows, so there's no real reason to have something that will talk with a Windows box.  Should I remove Samba from my server (running Ubuntu 8.04), I have a lot of information on that box, so I'm kind of afraid to muck around with it much.  Any suggestions?

Thanks,

---

