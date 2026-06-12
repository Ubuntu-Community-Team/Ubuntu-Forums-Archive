---
title: "Network setup"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by IronArjen on 2009-07-02
In short my question is "How to setup a network"

I run a small bioinformatics lab and wish to be able to connect my three Ubuntu operated PCs to each other. Basically I have no system management backup. All three PCs run on Jaunty and connect to the same Wifi router. If i go to Places>Network I end up in a Windows network (must be the neighbors) but i do not see the two other PCs. Most networking posts seem to deal with internet connections but since Ubuntu also has aserver version there should be a way to do this. Are the any howtos?

---

### Post by MaindotC on 2009-07-02
Just connect to the machines via IP.

---

### Post by IronArjen on 2009-07-02
I am afraid I do not fully know how to do that.
Typing in an address in a browser somehow results in the text:

It works!

But then what? Connecting via my Gnome-commander seems not to work, probably I need to add more information like the port.

Most likely I completely miss the point.

---

### Post by MaindotC on 2009-07-02
I don't know what you are talking about with this "Gnome-commander" business.  If you want to view the web service that is running on the machine, then you enter the IP address in the web browser - hence why you see "it works!" in a web browser when you type in the IP address because the machines must be running the apache web server and thus the default page shown from a default apache installation is a web page that says "It Works!"

If you want to ssh into the machines, make sure the sshd service is running and from a command prompt type:
```

ssh <username>@<ip_address>

```
where <username> is the name of the account on the machine in which you would like to connect and <ip_address> is the ip address of the machine in which you would like to connect.

If you want to connect to the machines for file transfers, make sure the FTP service is running (I use vsftpd) and type in a browser:
```

ftp://<ip_address>

```
or in a command prompt type:
```

ftp <ip_address>

```
and follow the prompt options.  Those are three examples of how to connect to other machines.

---

### Post by aromo on 2009-07-02
> **IronArjen said:**
> In short my question is "How to setup a network"

I run a small bioinformatics lab and wish to be able to connect my three Ubuntu operated PCs to each other. Basically I have no system management backup. All three PCs run on Jaunty and connect to the same Wifi router. If i go to Places>Network I end up in a Windows network (must be the neighbors) but i do not see the two other PCs. Most networking posts seem to deal with internet connections but since Ubuntu also has aserver version there should be a way to do this. Are the any howtos?

The network is set up already by the DHCP server if you can ping each machine.

If sharing files is what you want, search NFS (not NTFS, which is a Windows filesystem).  With NFS you can mount folders in remote *NIX machines as if they were local.  If you need to do this with Windows machines, you'll have to use Samba instead.

Hope this helps...

---

### Post by Iowan on 2009-07-02
[Here]("https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html") is a network configuration help page.  
probably the easiest way to share files between Ubuntu machines is NFS.  [URL="https://help.ubuntu.com/community/SettingUpNFSHowTo"]
Here[/URL] is a help page for setting up NFS - or a more basic version [here]("http://ubuntuforums.org/showthread.php?t=249889").

---

### Post by superprash2003 on 2009-07-03
first make sure that all machines are able to ping each other via ip.. after which you can go ahead with NFS,SAMBA etc

---

