---
title: "Use windows command prompt over a network connection"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by sgmbest12321 on 2009-10-05
Hello,
I was wondering if there was anyway to connect to a windows machine (i need windows 7 or vista but if you have something for an older version please post it) and access the machine using windows command prompt.
My situation is i have an ubuntu server at home that i use a web,ftp, ssh, bittorrent, everything server. what i would like to do is connect to that server via ssh and then run [this program] and have access to the command prompt on a windows machine on the local network.  It would make my life alot easier.
Thanks in advance.
Steve Mitchell

---

### Post by skatinjj on 2009-10-05
Lemme think on this for a moment, I didn't realize something that was in the post.

---

### Post by skatinjj on 2009-10-05
Could use WinSSHD (free non-commercial version) to be able to connect to the windows box via ssh.  Just make sure port 22 is open.

---

### Post by kevdog on 2009-10-05
I don't understand your setup.  Which computer is the client, and which is the server?

---

### Post by sgmbest12321 on 2009-10-06
@kevdog
My Setup:
My Laptop --> SSH --> Ubuntu Server --> Some Program --> Windows computers
I want it to go through the Ubuntu Server because otherwise i would have to have a different port forwarding rule for every windows computer

@skatinjj
Thats what i might end up doing but i was looking for something that is already on windows and wouldnt need any additional software.

---

### Post by skatinjj on 2009-10-06
> **sgmbest12321 said:**
> @kevdog
@skatinjj
Thats what i might end up doing but i was looking for something that is already on windows and wouldnt need any additional software.


Have you tried opening a port on your windows machine and try telneting into it on the open port? (haven't used telnet for a while so I don't know if its what you need.  I would test but i only have one windows box)

---

