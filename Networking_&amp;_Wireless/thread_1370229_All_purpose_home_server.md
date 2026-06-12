---
title: "All purpose home server"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by thekingof7 on 2010-01-02
Hi guys, 
      I'll cut to the chase, I currently have a large amount of a assorted computer components laying around (who doesnt?). I've assembled a decent machine and I was hoping to setup some sort of headless server. I'm fairly proficient regarding the usage of unix environments, but I've always been lacking in networking skills. This server will act as a simple file server for my house. (preferably ftp seeing as samba was confusing to me.) I also would hope to be able to run torrentflux and have some sort of tunneling program setup to allow me ssh access outside of the house. And finally some sort of free domain name service for ease of usage would be great.
 Sorry to ramble but essentially what I need is a current, accurate, and somewhat "lead you by the hand" friendly guide. I've already used the usual methods of obtaining said information, but the guides I've come across seem to be either to vague or vastly out of date. Any recommendations or advice.
It would be greatly appreciated. Thanks for everyone's time. :guitar:

---

### Post by 10nitro on 2010-01-02
> **thekingof7 said:**
> This server will act as a simple file server for my house. (preferably ftp seeing as samba was confusing to me.)
I actually recommend NFS (Network File System), although there seems to be this conspiracy to replace it with CIFS (probably because it works with Windows (backwards compatible with SMB, Windows file sharing (Samba if a free software implementation of SMB/CIFS)).  In Ubuntu, setting up a CIFS share server-end is crazy easy.  Right-click on the folder, select `Sharing Options'.

> **thekingof7 said:**
> I also would hope to be able to run torrentflux
torrentflux is in the Ubuntu repos, but the included-by-default Transmission also has a nice web interface.(Edit->preferences->web(tab)->enable web interface)

> **thekingof7 said:**
> and have some sort of tunneling program setup to allow me ssh access outside of the house.This is basic port forwarding.  This should probably be done on the gateway, usually a router.  Most routers make this really easy to configure.  Or, if you manage to set up the server as the gateway, you can do this with the program iptables (though I can't help you actually doing it).  This will work something like:
your.internet_addr:1001 -> sever:22
your.internet_addr:1002 -> bedroom:22
your.internet.addr:1003 -> laptop:22

Note that this is affected by your physical network setup:

With a router:
```

           Internet
               |
             Router
             / | \
    .-------'  |  `-------.
   |           |           |
server      bedroom     laptop

```
with the server as the gateway (requires 2 NICs, or a NIC with 2 ports):
```

           Internet
               |
             server
               |
             Switch
             /   \
    .-------'     `-------.
   |                       |
bedroom                  laptop

```                

> **thekingof7 said:**
> And finally some sort of free domain name service for ease of usage would be great.
You mean like domain-name registration?  You can occasionally find something for free with a weird top-level domain (`.co.nr'), but for the most part you will have to pay for this. [https://www.godaddy.com/](https://www.godaddy.com/) seems pretty good.  If your Internet connection has a dynamic IP, this will be difficult, because your IP will periodically change, so your domain-name settings will need to change.  I've seen programs to do this, but can't help you much myself.

Given the ease of configuring the first 2 with Ubuntu desktop, I recommend installing the desktop version of Ubuntu, and disabling the X server in init -- plus, you can get any GUI utilities you need on the server via ssh, always convenient.

---

### Post by thekingof7 on 2010-01-02
Thanks for the info, but are there any guides that deal with what you just talked about. My setup would be the first example (router). And you recommend NFS, would that be windows compatible? Basically I'd like to make this as easy as possible for the rest of the family. Drag and drop, so all they have to do is either open up a webpage to upload, or winscp. And one more stupid question, why is there a 22 behind server bedroom, etc?

---

### Post by illy123 on 2010-01-02
> **thekingof7 said:**
> Thanks for the info, but are there any guides that deal with what you just talked about. My setup would be the first example (router). And you recommend NFS, would that be windows compatible? Basically I'd like to make this as easy as possible for the rest of the family. Drag and drop, so all they have to do is either open up a webpage to upload, or winscp. And one more stupid question, why is there a 22 behind server bedroom, etc?

22 Is the port OpenSSH listens on by default.

---

### Post by thekingof7 on 2010-01-02
Could anyone explain the iptables concept to me a little further?
Is that bit about "your.internet_addr:1002 -> bedroom:22" how it would look in a config file? Or is that how it would show up in a the search bar of a browser.

---

### Post by mike_yung on 2010-01-02
I suggest installing the Ubuntu server edition.  The installation guide is at the link below.
[https://help.ubuntu.com/9.10/serverguide/C/installation.html](https://help.ubuntu.com/9.10/serverguide/C/installation.html).  You will need a monitor & keyboard for this step.

When you get to the installation steps dealing with the package tasks choose OpenSSH server, Samba (on the assumption that your laptop & bedroom PC are running Windows), & the LAMP (ready-made Linux/Apache/MySQL/PHP server) which you will need for TorrentFlux.

Don't install the BIND services, at this would only be appropriate if you were using the router-less network topology described in the 2nd post.

The OpenSSH server will work right out of the box, but if you wish to tweak the default settings refer to the 9.10 "Ubuntu Server Guide".  [https://help.ubuntu.com/9.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.10/serverguide/C/openssh-server.html)

Once the installation's done & SSH server are configured, install a ssh client on the computer you will be using to maintain your headless server.  Again, assuming your laptop &/or bedroom computer runs on Windows, your options are PuTTY ([http://www.chiark.greenend.org.uk/~sgtatham/putty]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty")) or Microsoft's tools ([http://www.suacommunity.com/forum/Default.aspx](http://www.suacommunity.com/forum/Default.aspx)).

Once you've got your SSH client working you are almost ready to disconnect the monitor.  Before you do so be sure to restart, go into your BIOS menu to ensure your PC will start with no keyboard & monitor, save & exist, then reboot.  When it starts, make sure you can log in remotely.

If you can, enter the command ```
sudo shutdown -h now
``` loose the screen & connect your headless server in the basement, garage or wherever then power it up.

if you can not, make sure the OpenSSH service is configured to start on boot.

Once your headless server is running away happily in the background move on to configuring out of the house access.  This is done by telling your router to forward external requests to port 22 to the server on your home LAN.  

> And one more stupid question, why is there a 22 behind server bedroom, etc? Port 22, is the port the your server's OpenSSH service will be waiting for requests on.  That's a very good questions by the way.

Once your router is configured you can access your server from outside the house by pointing your SSH client to the IP address your ISP gives to your router.

The default Samba service will not work right out of the box, but is almost ready to go.  It needs to told which folders to share & how to handle usernames, passwords, etc.  To configure Samba this edit /etc/samba/smb.conf according to the 9.10 "Ubuntu Server Guide"  [https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html).  When it's ready to go run the command ```
 sudu /etc/init.d/samba restart
```.  Samba is the name of the program which provides the SMB file-sharing service to your Windows computers.  When it's working you will see a network drive files can be dragged & dropped to & from.

I have no first hand experience with LDAP (ready-made Linux/Apache/MySQL/PHP server), or TorrentFlux but can provide some links.  

Refer to the 9.10 server guide for LDAP [https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/9.10/serverguide/C/openldap-server.html), and the Community docs for TorrentFlux [https://help.ubuntu.com/community/TorrentFlux](https://help.ubuntu.com/community/TorrentFlux).

Post a reply if you have any questions or get stuck along the way.

---

### Post by van_Zeller on 2010-01-09
Hello,

Sorry to steal hijack this thread, but I am having similar, although not the same doubts, and I figured i might as well ask here instead of opening another thread. Let me know if this is inappropriate.

So I'm trying to access my computer from anywhere. I can ssh home at this point (for this I set up a dyndns account, free and simple) and told my router to handle the ip changes alone (really simple). Then I did port forwarding (no problems here). At this point I can access my computer as if I were in front of it using a console.

What I want now is to transfer files, obviously. I have the ftp server running, but I am having problems configuring the rest. My goal is to have an ftp server where only my user can log (using my username and password) and to then be able to transfer files back. Can anybody help me here? Any help is very appreciated.

van_Zeller

---

### Post by Leppie on 2010-01-09
> **thekingof7 said:**
> And you recommend NFS, would that be windows compatible?
you can download the Windows Services for Unix v.3.5 from Microsoft: [http://www.microsoft.com/downloads/details.aspx?FamilyID=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en)

---

### Post by Neezer on 2010-01-12
> **van_Zeller said:**
> Hello,

Sorry to steal hijack this thread, but I am having similar, although not the same doubts, and I figured i might as well ask here instead of opening another thread. Let me know if this is inappropriate.

So I'm trying to access my computer from anywhere. I can ssh home at this point (for this I set up a dyndns account, free and simple) and told my router to handle the ip changes alone (really simple). Then I did port forwarding (no problems here). At this point I can access my computer as if I were in front of it using a console.

What I want now is to transfer files, obviously. I have the ftp server running, but I am having problems configuring the rest. My goal is to have an ftp server where only my user can log (using my username and password) and to then be able to transfer files back. Can anybody help me here? Any help is very appreciated.

van_Zeller


Not sure if it is appropriate or not, but I'll see if I can lend a hand. It depends what your setup is for machines? I have a server and a laptop with Ubuntu 9.10 on them. I used ssh for the remote file access, and it was a LOT easier than I expected it to be.

I already had the ssh connection up and running from remote sites though. once you have that going, it is a snap to set up.

I just went to Places -> Connect to Server. When the box came up the top option is a drop down menu. I chose ssh. The next box down is options for a server. Here put in your external IP address of the server. (to get this go to whatismyip.com or some similar site. Also note that unless you are paying a premium, this ip address can and will change. this discussion is for a separate thread). Once you put your server IP address in, the next box down is the port. the default port is 22. My preference is to change the port. The reason is that there are a lot of people that snoop around for open port 22 on systems and use it to try to hack into a system. I know this isn't a replacement for using a secure ssh system (I use a RSA key to ensure security on port 2222). But the number of probes on my machine gets reduced drastically if I use port 2222 instead of 22 for my ssh needs.

The next one is folder. I use /home/nathan for my folder, but you could put anything you like in there....if you want to be more specific, you could put /home/user/Music and set one up for music, and then /home/user/Pictures for you pictures...It doesn't really matter...you could even put / in there and share everything in the filesystem. (This last option is probably not recommended by security professionals, but I really have no clue about that).

I hope that helps. Also, you will need to port forward on your router. basically when you set up prort forwarding, a signal from your remote computer comes to the router (via your external ip from whatismyip.com) with instructions to go to port 22 (or 2222 or whatever you want). the router sees the request for that port and forwards it to an INTERNAL ip address specified. here you will put the IP address of your server. that way all signals on port 22 get directed to your server. Your server then authenticates the signal via password (not recommended), or key (recommended).  

In order for this to work, you will need to set up your server on a static IP address (internally).

I hope this helps, and just post back if you have any additional questions.

---

### Post by changingstate on 2010-01-12
Just a small addition, as I've not seen anyone else post it. If you're on a dynamic IP, you can still get a domain name and for free, too. I'm using [http://www.dyndns.com/](http://www.dyndns.com/) but other Dynamic DNS services are available.

---

### Post by gtr32 on 2010-01-12
If you are doing a headless server, you might find Webmin to be of great help.

[http://www.webmin.com/index.html](http://www.webmin.com/index.html)

Debian package:
[http://prdownloads.sourceforge.net/webadmin/webmin_1.500_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.500_all.deb)

---

