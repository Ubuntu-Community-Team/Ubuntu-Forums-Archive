---
title: "Alternatives to Samba for Windows Networking"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by jcobban on 2009-12-02
I am extremely frustrated with Windows SMB based networking.  Basically it is a piece of garbage even in a pure Windows environment, adding Linux into the picture doesn't make it any better.

For example at the moment I have a laptop running Windows Vista and a desktop PC running Ubuntu Karmic Koala connected on my home network.  **Occasionally** I am able to connect from the Ubuntu system to the Windows file system, but it is entirely dependent upon the Windows system bothering to wake up and identify itself.  Again this has nothing to do with the fact that I am running Ubuntu.  Even if I boot my desktop server up in Windows it **still** cannot see the laptop unless the laptop takes the time to announce itself.  I have been networking for many many years and have never found anything that I can do on a Windows system to force it to make itself available to the rest of the network.  If it doesn't do it spontaneously **nothing** can get it to do so.

Since replaced my old Win98 laptop with one running Windows Vista I have **never** been able to get it to connect to the Samba server on my Ubuntu server.  Since the other direction works occasionally I do not believe this is a problem with Ubuntu, but rather that Vista insists on changing the userid I enter, so that the logon to the Samba server is rejected.  I have repeatedly posted looking for help with that, but although lots of people have read my posts, nobody has had any suggestions of how to get around it.

So as far as I am concerned Windows SMB networking is a piece of odoriferous excrement, and I would desperately like a reliable alternative to it.

---

### Post by ipage on 2009-12-02
Are you trying to browse the network from Windows explorer?  I often find that it doesn't bother to find a server there, no matter how many times you hit F5.  But typing [\\*servername*]("file://\\servername") in the address bar will often bring it out of its stupor...

---

### Post by mikewhatever on 2009-12-02
I think NFS is an alternative, although I hope some day, there will be something relatively easy to use.

---

### Post by Iowan on 2009-12-02
Some sharing options: NFS, SSHFS, FTP. There are probably more - these are just the ones that come to mind.

---

### Post by jcobban on 2009-12-03
> **mikewhatever said:**
> I think NFS is an alternative, although I hope some day, there will be something relatively easy to use.

NFS is not supported in the "Home" versions of either Vista or Windows 7.

---

### Post by jcobban on 2009-12-03
> **ipage said:**
> Are you trying to browse the network from Windows explorer?  I often find that it doesn't bother to find a server there, no matter how many times you hit F5.  But typing [\\*servername*]("file://\\servername") in the address bar will often bring it out of its stupor...

There seems to be a fundamental weakness in the SMB design that it depends upon the other system to announce itself, rather than doing a broadcast request, either periodically or in response to a refresh request, asking other systems on the network to identify themselves.  I assume that this flaw is fundamental since neither the Windows nor the Linux implementations of SMB support take the trouble to go out and find other systems. This flaw creates timing problems where the announcement occurs at a time when the other system is not available to see it.  Your suggestion might work when there are only two systems on the net, but would be impractical in a larger network.

I also don't like that in the Ubuntu implementation of support for SMB networking the remote file systems do not appear as filesystems, the way that remote NFS systems do for example, but rather have a smb: prefix on the file names.

---

### Post by cb951303 on 2009-12-03
All the computers on my home network have static LAN IPs and when I try to navigate to a samba/windows share from Ubuntu, a "smb://IP.ADRESS" input to the nautilus location bar never failed me.
but other than that you're right. smb is a very old protocol and I remember trying to work it between 2 windows computers for hours.

---

