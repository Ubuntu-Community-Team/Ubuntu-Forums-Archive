---
title: "Can't connect to Samba share"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by t93ha07 on 2010-03-04
I am running Jaunty 9.0.4.  I used system-config-samba (gui) to configure Samba.  I put myself as a user and tried to map the drive from my local PC.  I am unable to map the drive.  On windows, I try to connect using a different user and when I select finish, it prompts me again and adds my workgroup before my user name. Does anyone know a way around this?  Many thanks.

---

### Post by Deadite81 on 2010-03-04
Hmm, I use Samba and the gui tool you mentioned.  I connect to an xp desktop and an xp laptop.  My user name was never important, It only matters if the workgroup is the same name.  If your sure that file sharing is enabled on the Windows pcs, and you are sure that all your firewalls are allowing your workgroup to "talk" to each other (ports 137-139 and 445) you should just be able to select "network" or "Connect to Network" in your places menu in Nautilus or your main menu and share the specified folders' content.  That should be it.

You may have to check, if your workgroup is not named the default "WORKGROUP", that your Samba program is actually changing the workgroup name.  You can check in  /etc/samba/samba.conf, line 38, workgroup = YOURWORKGROUP.
Other than that, I'm not sure I understand the question.

---

### Post by Morbius1 on 2010-03-04
Please post the output of the following command:

Open **Terminal**
Type **testparm -s**
Type **net usershare info**

>  I put myself as a user and tried to map the drive from my local PC.  I am unable to map the drive.I don't understand what that means. What do you mean "put yourself as user"? And are you trying to mount the share from that same machine that has the share?

> On windows, I try to connect using a different user and when I select finish, it prompts me again and adds my workgroup before my user nameI'm lost on that one too. Does the "different user" have a samba password defined on the Linux server?

---

### Post by Deadite81 on 2010-03-04
I should also note that it should work the other way around.  Opening the network folder in My Network Places should show your shares from Ubuntu automatically, as long as they're all part of the same workgroup.  Windows XP can be buggy about this, I have never used Vista, and Windows 7 makes it so easy you pretty much don't have to do anything.

---

### Post by t93ha07 on 2010-03-04
My firewall is off.  My workgroup is correct now.  Thanks it was "WORKGROUP" b4.  

I am trying to log in from my username created on unbuntu as I am one of the user allowed to access the share.

The samba share works when I let it open to everyone, but I can't authentic when I strict it to certain users.

---

### Post by Morbius1 on 2010-03-04
You need to create local users on the linux box and then create samba passwords for those users:

If you're trying to access the server share using the server users username and password:

Open **Terminal**
Type **sudo smbpasswd -a server-user-name**

If you're trying to access the server share using the clients username and password you have to create a new user on the server itself that corresponds to the client and then create a samba password for that user:

Let's say you have a remote user named john:

Open **Terminal**
Type **sudo useradd -s /bin/true john**
[COLOR=Blue]*This will create the user john on the server that has no local server logon capability and no server home directory.*[/COLOR]
Type **sudo smbpasswd -a john**
[COLOR=Blue][I]This will add AND activate the samba user john on the server.

[/I][/COLOR]>  I am trying to log in from my username created on unbuntu as I am one of the user allowed to access the share.That sentence still confuses me. It really would be helpful if you posted the output of** testparm -s**

---

### Post by t93ha07 on 2010-03-04
THanks guys,  Removing my samba account and redoing it did the trick. It works now.  Many thanks,

---

### Post by Deadite81 on 2010-03-04
Cool:D

---

### Post by samwisekoi on 2010-06-24
To twist this around a bit, I just upgraded my desktop to 10.04 64-bit desktop and my server to 10.04 server.

After which, Windows users (including a Win7 VM on my Ubuntu desktop) can see and connect to the Samba shares just fine, but my Ubuntu desktop itself cannot connect via Nautilus using SMB, SFTP or SSH.  Naturally I can SSH via the terminal, and gFTP works just fine as well.

But "Places:Connect to Server..." and "Places:Network"?  No dice.  I can get as far as a password prompt, but not to the shares.

I am getting tired of scp and gFTP...

Any thoughts, anyone?

 - Sam ;^)

OBTW, I *have* created the samba users and passwords - which I use to connect  from the Win7 VM and an XP box.  Just to be safe, I made sure my username/password was  the same on my desktop, the server and in samba on the server.

---

