---
title: "Sharing files across my home network"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by bigwoof on 2009-04-13
Hi there 

I have been using ubuntu since intrepid was released and am loving it.  I have ditched XP on my laptop and Desktop, unfortunately I cant ditch my vista media centre yet (no drivers for my video capture card).  Anyway I digress.

Here is my problem.

I want to set up a share on my desktop (intrepid) so I can access it on both my laptop (intrepid) and my vista machine. I have no experience in networking so all my searching the forums had confused me.  Currently all the machines are connected to the router and have Internet access, so i assume that they are all on the network.  

I tried to set up the share by right clicking on the folder and selecting sharing options.  I used a variety of combinations and had no luck.

Tried to connect to the Windows Network via nautilus and I get:
Unable to mount location 
Failed to retrieve share list from server

I also tried to connect by using the Connect to Server... option under the Places menu and no luck.

I am really confused please can you help.

Thanks

Phil

---

### Post by hyper_ch on 2009-04-13
most convenient way would be to install openssh-server on the desktop and then access it from the notebook and desktop with sftp (most ftp clients support that).

On the notebook you could even install sshfs so that you can mount the desktop into folder on the notebook.

Otherwiese you might want to have a look at samba. Stormbringer has written a nice howto in the tutorial section.

---

### Post by bigwoof on 2009-04-13
> **hyper_ch said:**
> most convenient way would be to install openssh-server on the desktop and then access it from the notebook and desktop with sftp (most ftp clients support that).

On the notebook you could even install sshfs so that you can mount the desktop into folder on the notebook.

Otherwiese you might want to have a look at samba. Stormbringer has written a nice howto in the tutorial section.

Thanks for the help, I will give it a try.  and let you know.

Will I be able to connect my Vista machine to this share too?

cheers

Phil

---

### Post by inobe on 2009-04-13
> **bigwoof said:**
> Thanks for the help, I will give it a try.  and let you know.

Will I be able to connect my Vista machine to this share too?

cheers

Phil

setup samba and share folders !

here's how [https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

start with **"Sharing folders via the Shared Folders application"** in the link, steps **"1 to 11"**.

then if you want to have secure login scroll down to **"Accessing shared folders via Windows"** and follow steps **"1 to 6"**


i have setup numerous machines using this, it's pretty basic, secure and painless process.

---

### Post by bigwoof on 2009-04-13
thanks for that inobe, it is a great guide.  it dawned on me what I had done wrong.  I had installed firestarter on the laptop and forgot about it which was blocking the shares.  I should have thought of it earlier, sorry for wasting your time.  It does however bring up another question, do i realy need a firewall for ubuntu as it is very secure to start with?

cheers

Phil

---

### Post by hyper_ch on 2009-04-13
why even bother with firestarter?
no, you usually don't need a firewall.. have a look at the sticky topics in the security section.

---

### Post by jonandrews on 2009-04-14
I’ve put a step-step illustrated guide to networking between Ubuntu & Windows pc’s, aimed at people coming from a Windows background, on my website:
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Ahunt on 2009-04-17
And I have created a very brief article on how to file share between Ubuntu PCs using SSHFS and OpenSSH at [http://web.ncf.ca/adamandruth/ubuntu.html#Network](http://web.ncf.ca/adamandruth/ubuntu.html#Network)

---

### Post by Plumtreed on 2009-04-19
> **Ahunt said:**
> And I have created a very brief article on how to file share between Ubuntu PCs using SSHFS and OpenSSH at [http://web.ncf.ca/adamandruth/ubuntu.html#Network](http://web.ncf.ca/adamandruth/ubuntu.html#Network)

Thanks Ahunt, that was just what I was looking for. I need to explore a bit more to see how far I can go with this?? Thanks for a clear, concise 'how-to'....and you have a list of other things to look at!!!! 

:P

---

### Post by Ahunt on 2009-05-09
I am glad that was helpful!

---

### Post by bayvista on 2009-05-11
I have a small problem. I have a Desktop (wired) and a Laptop (wireless) connected to a router. The Desktop works fine. The Laptop only works if both wireless and wired connections are made. If I disconnect the wire, I cannot connect from the Desktop to the Laptop.

In summary, there is something wrong with the laptop networking. It should be possible to run EITHER connection and connect from the Desktop. It should not be neccessary to connect BOTH. This problem has only started in the last week and I suspect an Ubuntu upgrade as the problem.

A copy if my IFCONFIG is attached. Any suggestions welcome.

Problem solved: Edited /etc/resolv.conf and added
nameserver 192.168.0.1

Don't know why but everything works fine using Ethernet.

---

