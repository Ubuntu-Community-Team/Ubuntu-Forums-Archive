---
title: "How do I see VPN connected Windows machine folders on my server?"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by UlfDunkel on 2012-01-23
Hello all, I'm new to this forum and have searched for any answers on my question before I decided to start this new thread. Please forgive if this has already been answered and point me to the right direction.

I run a Ubuntu server in a server farm, where my ISP has already prepared VPN for me.

I am now able to connect a Windows 7 PC via VPN to the server, and I can successfully ping both machines from both sides. I can see a default web space folder's content (/var/vhosts/default/) in any browser on my Win7 PC.

But I would like to see a certain drive or folder of the PC on the Ubuntu server. I would like to be able and copy or delete files from the server to this PC folder, via VPN.

I have no idea how to mount a certain drive or folder from the Win7 PC on my server. I have root access to my server, no GUI, and am familiar with some Linux console stuff, but I am totally new to VPN and networking. My ISP isn't familiar with the Windows side of this problem.

Can you help me how to configure both sides of this connection, please?

---

### Post by Pyraxic on 2012-01-23
There is an article about it. Take a look at it:
[https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

---

### Post by UlfDunkel on 2012-01-23
Thank you for your quick reply, Pyraxic, but I wonder what to do with that information. I have no Ubuntu GUI, as I am only accessing my server console via puTTY from a remote PC.

I would like to be able to do file operations in a folder on that PC, but from the Ubuntu console. So I am not sure if the article which you mentioned really helps me. I expected to mount some VPN connected drive on my server console, so that I could be able to list its content from say /mnt/ on the server console.

Did I miss something from that article?

---

### Post by UlfDunkel on 2012-01-23
Just to kind of emphasize what I want to do:

**S** is my Ubuntu Server, somewhere in a server farm far away from me. I can only access its system via puTTY from a PC right here.

**R** is my Remote Windows PC which I use to control my server via puTTY.

**C** is a Client Windows PC which I connected to **S** via VPN. (Of course, C can be R or any other PC.)

Now I want to see a defined** target folder on C** from the S console, handled on R via puTTY.

Then I would like to copy files **from a defined source folder on S** **to the defined target folder on C**, done via puTTY console commands on **R**.

Later I would like to automatize the file handling from S to C by Perl scripts or PHP scripts, replacing the manual file handling via puTTY.

Then I would like to add more clients **C2, C3, C..., Cn** which should then be accessible via VPN from the server **S**.

I cannot see any Ubuntu GUI, no desktop, no icons to click on, no menu items, just the pure Ubuntu Linux console. That's my situation, folks.

---

### Post by redmk2 on 2012-01-24
> **UlfDunkel said:**
> ...
I run a Ubuntu server in a server farm, where my ISP has already prepared VPN for me.
Just curious -- what is the purpose of this server in your network.  Is it a web server that you wish to upload data to?  Is it for storage as a NAS?> 
I am now able to connect a Windows 7 PC via VPN to the server, and I can successfully ping both machines from both sides. I can see a default web space folder's content (/var/vhosts/default/) in any browser on my Win7 PC.

But I would like to see a certain drive or folder of the PC on the Ubuntu server. I would like to be able and copy or delete files from the server to this PC folder, via VPN.

I have no idea how to mount a certain drive or folder from the Win7 PC on my server. I have root access to my server, no GUI, and am familiar with some Linux console stuff, but I am totally new to VPN and networking. My ISP isn't familiar with the Windows side of this problem.

Can you help me how to configure both sides of this connection, please?
If you have installed the Samba services and client on the server, then  all you need to do is share a folder on the PC and check to make sure it is available using the following command from the server```
smbtree
```

Have you installed Samba?  The VPN is the encrypted tunnel.  You also need file services that both Linux and Windows understand.  Linux uses Samba to communicate with Windows, which has file sharing built-in.

====== 

[QUOTE=UlfDunkel] Re: How do I see VPN connected Windows machine folders on my server?
Just to kind of emphasize what I want to do:

S is my Ubuntu Server, somewhere in a server farm far away from me. I can only access its system via puTTY from a PC right here.
[/QUOTE]This logs you on as a local user on the server.> 

R is my Remote Windows PC which I use to control my server via puTTY.


C is a Client Windows PC which I connected to S via VPN. (Of course, C can be R or any other PC.)

Now I want to see a defined target folder on C from the S console, handled on R via puTTY.

Then I would like to copy files from a defined source folder on S to the defined target folder on C, done via puTTY console commands on R.
The VPN is only the encrypted tunnel between these hosts.  You will need another protocol to interact between these hosts (Samba).  Rather than "pulling the files from the PC to the server you are better off pushing them from the PC to the server if these are initiated by the user. > 
Later I would like to automatize the file handling from S to C by Perl scripts or PHP scripts, replacing the manual file handling via puTTY.

Then I would like to add more clients C2, C3, C..., Cn which should then be accessible via VPN from the server S.
 If this is for backup there are better ways to do this other than a VPN.  SSH allows you to use either rsync or rsnapshot to automate backups.> 

I cannot see any Ubuntu GUI, no desktop, no icons to click on, no menu items, just the pure Ubuntu Linux console. That's my situation, folks. 

The CLI is all you need.  :-)

---

### Post by UlfDunkel on 2012-01-24
> **redmk2 said:**
> Just curious -- what is the purpose of this server in your network.  Is it a web server that you wish to upload data to?  Is it for storage as a NAS?

This is a quite normal web/mail/subversion/everything server in the net. I am preparing a new website for a customer and want to **push files from the server to various clients**, not via HTTP or FTP, but via VPN / Samba.

> **redmk2 said:**
> Have you installed Samba?  The VPN is the encrypted tunnel.  You also need file services that both Linux and Windows understand.  Linux uses Samba to communicate with Windows, which has file sharing built-in.

I will check this. Sounds as if this is the missing link I was looking for.

> **redmk2 said:**
> Rather than "pulling the files from the PC to the server you are better off pushing them from the PC to the server if these are initiated by the user.  If this is for backup there are better ways to do this other than a VPN. SSH allows you to use either rsync or rsnapshot to automate backups.

No, it’s the other way round. I want to distribute files once from my server to various clients with least possible traffic „costs“. This is why my ISP recommended to build VPN connections and push the files from the server to the clients, rather than requesting them via client browsers from the server. (I’m talking about advertisement video clips which will then be played in loops on the clients, so HTTP requests wouldn’t be first choice here.)

---

### Post by redmk2 on 2012-01-24
> **UlfDunkel said:**
> This is a quite normal web/mail/subversion/everything server in the net. I am preparing a new website for a customer and want to **push files from the server to various clients**, not via HTTP or FTP, but via VPN / Samba.

I will check this. Sounds as if this is the missing link I was looking for.

No, it&#8217;s the other way round. I want to distribute files once from my server to various clients with least possible traffic &#8222;costs&#8220;. This is why my ISP recommended to build VPN connections and push the files from the server to the clients, rather than requesting them via client browsers from the server. (I&#8217;m talking about advertisement video clips which will then be played in loops on the clients, so HTTP requests wouldn&#8217;t be first choice here.)
I understand now.  The VPS (server) is the distribution point.  The biggest obstacle is whether to to mount the partition or share.  In fact you don't need to mount the share if you use sFTP (this is part of SSH).  

If you are going to mount a share to the local system (//windows_PC/share to /mnt/data) you will need at least [**_[COLOR="Blue"]cifs-utils[/COLOR]_**]("http://wiki.samba.org/index.php/LinuxCIFS_utils").  The current Ubuntu package is described [**_[COLOR="Blue"]here[/COLOR]_**]("http://packages.ubuntu.com/oneiric/cifs-utils").  All these options can be implimented via the CLI.

Edit:  FWIW -- I'm not sure I agree with the ISP.  I would rather my clients get the files when they need them (download not play).  That way the files just need to be available.  A VPN means you are part of your clients LAN.  A public facing server with untrusted (no control) LAN connections.  Hmmmmm.

---

### Post by UlfDunkel on 2012-01-24
> **redmk2 said:**
> I'm not sure I agree with the ISP.  I would rather my clients get the files when they need them (download not play).  That way the files just need to be available.  A VPN means you are part of your clients LAN.  A public facing server with untrusted (no control) LAN connections.  Hmmmmm.

These clients will not be used for anything else than just playing advertisement video clips (in say endless loops) in a fullscreen-mode browser. Kind of black boxes behind monitors. Kind of Point-of-Sale advertisement presentation.

If you can give me any information how to download a file only once and play it on demand in a loop of n files in your local browser, I’d be more than happy to rather implement this solution than handling the VPN stuff. But I’m not aware of any clean method to store files downloaded from the web automatically on your local machine.

---

### Post by redmk2 on 2012-01-24
> **UlfDunkel said:**
> These clients will not be used for anything else than just playing advertisement video clips (in say endless loops) in a fullscreen-mode browser. Kind of black boxes behind monitors. Kind of Point-of-Sale advertisement presentation.

If you can give me any information how to download a file only once and play it on demand in a loop of n files in your local browser, I&#8217;d be more than happy to rather implement this solution than handling the VPN stuff. But I&#8217;m not aware of any clean method to store files downloaded from the web automatically on your local machine.

Short and sweet, as it is late here and I need sleep.

Install an ssh server on your Windows hosts.  Then you can use SSH (via rsync) or SCP to sent the data via an encrypted SSH connection at your convenience.

[**_[COLOR="Blue"]Here is a tutorial[/COLOR]_**]("http://www.petri.co.il/setup-ssh-server-vista.htm") on the installing SSH on a windows host. 

[**_[COLOR="Blue"]Here is a short tutorial transferring files using SSH[/COLOR]_**]("http://www.cyberciti.biz/faq/transfer-files-from-unix-server/").  See the bottom section.

Finally, here is a Google search on [**_[COLOR="Blue"]SSH and SCP[/COLOR]_**]("https://www.google.com/search?q=scp+ssh&btnG=Go!").

---

### Post by UlfDunkel on 2012-01-24
Thank you for your efforts. I will now study your given information. Have a good night. :-)

Edit: Well, after studying the SSH stuff on the Web, I&#8217;m not sure if I can use it to push files from a Ubuntu server to a Windows client without any user action on the Windows PC but this is exactly what I want.

I need a way to push files to the Windows PC which is permanently connected to the server somehow. There is no client user doing anything, just me pushing the files from the server to the clients, and deleting them there somewhen in the future.

Is this really possible with SSH?

---

### Post by redmk2 on 2012-01-24
> **UlfDunkel said:**
> Thank you for your efforts. I will now study your given information. Have a good night. :-)

Edit: Well, after studying the SSH stuff on the Web, I’m not sure if I can use it to push files from a Ubuntu server to a Windows client without any user action on the Windows PC but this is exactly what I want.

I need a way to push files to the Windows PC which is permanently connected to the server somehow. There is no client user doing anything, just me pushing the files from the server to the clients, and deleting them there somewhen in the future.

***Is this really possible with SSH?***

Sure it is.  

I also need to get clear in my mind the state of your network.  These "clients" are not controlled your business clients, but rather, "remote hosts" in your network.  You control them.  Maybe some terms need to be defined```
Host = any machine with an OS (real or VM)
server = any host that provides services
client = any host that requests services
hostname = the name given any host
```
We can refer to you hosts by there hostname rather than their roles in your network. 

In your situation you can use either VPN/FTP or SSH to do what you want.  Both provide an encrypted tunnel and a method of manipulating files (moving and deleting).

From a more technical point of view, the VPN works at a lower-level on the TCP/IP stack.  A VPN works at the network level and can secure all network traffic. SSH works at the application level and secures individual connections.

From a practical point of view you already have the VPN setup, so you can just use FTP (and Telnet for remote login).

Am I correct in that all hosts are under your control?  

To summarize -- either setup will work as both provide encryption and file manipulation.

Does this help?

---

