---
title: "Samba + Authentication"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by Novo Artis on 2010-03-02
Hi
I currently am trying to setup an Ubuntu file server with all clients being various windows machines.

How can I setup a samba share so that when I try to access it from windows I am prompted for a username and password?

Is this possible without domains and additional network setting changes?
eg. A new computer connects to the network and without any configuration is able to access the folders (required they have the correct username and password)

(think of it as a public network with password protected folders on the samba server)

---

### Post by Morbius1 on 2010-03-02
Create a share in /etc/samba/smb.conf that looks something like this:

[share]
path = /share
read only = no

By default it will be browsable but will not allow guest access.

You will have to set up user accounts and samba passwords for all your remote users first:

Let's say you have a remote user named john:

Open **Terminal**
Type **sudo useradd -s /bin/true john**
[COLOR=Blue]*This will create the user john on the server that has no local server logon capability and no server home directory.*[/COLOR]
Type[B] sudo smbpasswd -a john
[/B][COLOR=Blue][I]This will add AND activate the samba user john on the server.

[/I][COLOR=black]You will also have to make sure that the shared directory on the server has the permissions set to accommodate a write from the remote user:[/COLOR][B][COLOR=Black]

sudo chmod 777 /share[/COLOR][/B]
[/COLOR]

---

### Post by Novo Artis on 2010-03-02
It worked! Thank you very much for your help.

I had been searching for days now on how to achieve this and yet the answer is so simple. :oops:

Here is some info for people who might come across this thread in search:
[INDENT]From the command line in windows type "*net use*" to see what shares you are logged into.

Type "*net use \\yourserver\share /d*" to log out (sorry if this is the incorrect terminology) of the share.

[/INDENT]For ease I created a batch file inside each share that contains that line.

---

