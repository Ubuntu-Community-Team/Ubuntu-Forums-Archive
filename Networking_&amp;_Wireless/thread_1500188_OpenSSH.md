---
title: "OpenSSH"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by JimmieC on 2010-06-02
New to SSH and need a little help. I installed OpenSSH on Ubuntu Server 10.04, generated a Key pair on my desktop and copied the public key to ~/.ssh/authorized_keys on the server. There are really two problems:

1) When I ssh in to server I must use ssh user@ipaddress instead of ssh user@hostname. If I try to ssh in using ssh user@hostname then I get an error message saying the server name is not recognized.

2) When I ssh in I have to use password for user rather than password for key pair. Is the key pair being used, or am I still using just the password for user?

Hope I'm being clear.

Thanks for any advice.

Jim

---

### Post by Kokopelli on 2010-06-02
1) it means your host name is not recognized by the client.  This really is not a ssh issue.  If you can ping the hostname ssh will work too.  (you could add it to /etc/hosts if it is an internal address)

2) You are not using the cert. try "ssh -i <key file>".  This could be because the server side is not set up right or the client. If I were a betting man I would guess your cert was not set up correctly server side.  Usually I would recommend building on the client using "ssh-keygen" and then pushing to the server using "ssh-copy-id <host>"

---

### Post by JimmieC on 2010-06-03
Kokopelli,

Thanks for the response. My internal ip address and server name is in the hosts file. I will try to copy the .pub to the server in the way you suggested.

Thanks,

Jim

---

### Post by JimmieC on 2010-06-03
Kokopelli,

An update.

When speaking of the /etc/host file I didn't realize I had to place the server hostname in the client /etc/host file. When I finally realized that, then I was able to fix one of my problems.

My second problem was that I thought ~/.ssh/authorized_keys was a directory. I realized it was file and deleted the ~/.ssh/authorized_keys/ directory and then ssh-copy-id ~/.ssh and now everything works.

I did have a bit of a problem with permissions. I don't know if this is a good idea but I set my server ~/.ssh/authorized_keys to 0755. It's a local system and everything works so, for now, I'm happy.

By the way, it was your comments that helped me to fix my ssh issues.

Thanks,

Jim

---

