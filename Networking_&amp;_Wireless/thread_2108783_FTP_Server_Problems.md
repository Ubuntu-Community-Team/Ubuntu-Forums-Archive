---
title: "FTP Server Problems"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by UnderwaterCE on 2013-01-25
Hello All!

I'm attempting to set up an FTP Server on a new/old machine that I just put together.  It's running Ubuntu Server 12.04.  Within my local network the server works fantastic.  Files transfer up and down flawlessly.  Now the challenge comes in. When I attempt to access it from the outside world, using it's domain name or it's IP address does not affect the outcome.  The connection establishes and the password is accepted.  All works well until the LIST command, then it hits the fan.  I get an error saying "Connection Timed Out" then "Failed to retrieve Directory listing".  I'm connecting to the outside world from behind a Linksys Router which I have opened ports 20,21 and 61556.  That didn't fix it so I enabled the DMZ and pointed it at the internal IP of the server,  still no go.  I'm completely out of ideas.  Can someone please help?

Thanks!!

---

