---
title: "Remote Desktop Viewer Authentication Failure"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by gdonwallace on 2009-12-29
This problem started when I upgraded to 9.10 64 bit.  

I use the Remote Desktop Viewer that comes with Ubuntu.  There are currently 2 machines that I VNC into.  One is a NT machine (yes it is old) that we use as an FTP server for our clients to download data from our AS/400.  The other is a Fax server running XP that is also connected to the AS/400 for our clients to fax information.

I can connect to the Fax Server without any problems.  Remote Desktop asks me to authenticate, I enter the password and everything is fine.  However; when I connect to the FTP server, I enter the password to authenticate, and and I get a failure notice.  My first thought was that it was a ID-10-T error, and I was entering the wrong password.  So I went back to the machine, locked the screen, then CTRL-ALT-DEL to login, used the same password I am entering into Remote Desktop Viewer and it worked.  Its not the password.

I did a complete removal of Remote Desktop and re-installed everything.  Removed the history and .xml files from ~./local/apps/vinagre/ just to make sure there was nothing stored in those files that might be messing it up.  I removed the password that was saved in the keyring as well.  

Still nothing.  I get the same error every time I try to VNC into the NT machine.

Any suggestions?

---

### Post by afrodeity on 2010-06-30
Trying to VNC into my machine, but keep getting authentication error. Not sure what I have to setup?

---

