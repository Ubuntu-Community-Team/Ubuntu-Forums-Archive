---
title: "SSH Connection Problem"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by JimmieC on 2009-11-14
First try at SSH and I'm a bit confused. I'm using Ubuntu 9.10, created a SSH key pair on my computer and then uploaded the public key to the shared server which is hosted by Siteground. 

I attempt to login using ssh USER@HOST and after I hit enter key the cursor goes to new line and blinks. After 5 min terminal gives message, connection to HOST on port 22 timed out. (HOST = ip address of server)

Does this timed out message mean I was connected to my server?? Also, if I attempt to connect using the -p parameter using another port number then I get a Permission Denied (publickey) error.

If I am connected then do I login to my website through my browser, sorry, but I am really confused?

Thanks,

Jim

---

### Post by driftertx on 2009-11-14
Uhm, usually site hosting websites don't give you shell access and only give you ftp access. When you get 'connection timed out' that means the destination is either a) not running the SSHD service b) is filtering you via a firewall.

---

### Post by JimmieC on 2009-11-14
I enabled ssh-agent and was able to connect to the Siteground server but all I have is a prompt in my terminal window. what I want is to connect to my website backend, [www.website.com/administrator](www.website.com/administrator). I know this has to be simple but, like I said, this is my first run at SSH.

Jim

---

