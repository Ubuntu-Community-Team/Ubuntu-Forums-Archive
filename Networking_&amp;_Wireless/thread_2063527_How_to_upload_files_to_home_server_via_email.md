---
title: "How to upload files to home server via email?"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by Marcappuccino on 2012-09-27
Hello, I have a LAMP stack set up on xubuntu. I have it used as a fileserver, but, to upload files, I either have the option to go to /var/www/files, or put files on my shared folder (SAMBA?) in my local network.
  What I want to so is upload files to my server via email (example@my-public-ip.co.uk?), and possibly implement a password, so I would send an email to [email]example@my-public-ip.co.uk[/email], with the password.

PS Could I also set up a password on the server itself, like when I enter my public ip, a proompt window would launch, asking for a password?

PPS ifconfig returns something about ```
loopback
``` and ```
lo
``` interfaces. I would have thought that I would have a static IP, or DHCP. Does Ubuntu Server use static IPs?

---

### Post by Lars Noodén on 2012-09-27
It would be faster, safer, more efficient and easier to use just about anything else except for e-mail to transfer files.  e-mail is just not an adequate surrogate for a file system, it's also insecure. 

Two variations of the SSH theme would be SFTP or SSHFS.  Either one would be easy to set up and very secure.  Why not use those.  Have your router forward a port to your machine and set sshd to listen at that port and you're set.

---

