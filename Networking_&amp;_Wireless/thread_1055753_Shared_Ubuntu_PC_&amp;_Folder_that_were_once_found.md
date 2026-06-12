---
title: "Shared Ubuntu PC &amp; Folder that were once found in Places&gt;Network missing"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-01-31
So, basically, I formated two PCs and reinstalled Ibex.  Before applying any updates, I went ahead and created a shared folder on each PC (which of course prompts for samba or whatever to be automatically installed and the session/PC restarted).  After doing this, the shares were visible and I could easily move files back and forth.  This remained even after applying updates last night.  It even worked today, until a few hours ago.  I had not installed any firewall software or anything "special" that would modify my iptables (or so I think).  Now, on both PCs, when I click Places>Network, the only thing that appears is the "Windows Network" icon, which when you double-click on that, shows nothing.  Though I didn't have to click on that to gain access to the other PCs shares...

So...  theories?  Suggestions?  Perhaps someone knows of a good psychic with palm reading skills?

---

### Post by cariboo on 2009-01-31
What are the resuslts of the following command. Open a Applications-->accessories-->termianl and type:

```
smbclient -L<computername> -U%
```

you should see an outoput something like this:

```
smbclient -L willy -U%
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	movies          Disk      TV Shows and Movies
	music           Disk      Music library
	data            Disk      Data directory
	updates         Disk      Project Dakota
	images          Disk      iso images
	stuff           Disk      misc stuff
	IPC$            IPC       IPC Service (willy server (Samba, Ubuntu))
	HP_LaserJet_5P_LPT_parport0_HPLIP Printer   HP LaserJet 5P
	HP_LaserJet_5P_LPT_1 Printer   HP LaserJet 5P
Domain=[APLUS] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	RISKY                Windows computer
	WILLY                willy server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	APLUS                WILLY
```

You can run the above command on one computer, you don't have to run back and forth, just press the up arrow and change the computername.

If you get an error of any sort you may have to make sure you smbpasswd is valid and enabled. In the same terminal type:

```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```

Do the same on the second computer.

Jim

---

### Post by diablo75 on 2009-01-31
Here's the output from my PC:

```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (zeke-desktop server (Samba, Ubuntu))
	HP-LaserJet-6P  Printer   HP-LaserJet-6P
	sharedond       Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	KRISTINPC            kristinpc server (Samba, Ubuntu)
	ZEKE-DESKTOP         zeke-desktop server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            KRISTINPC

```

And here is the info from the second PC:

```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (kristinpc server (Samba, Ubuntu))
	HP-LaserJet-6P  Printer   HP-LaserJet-6P
	sharedonk       Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	KRISTINPC            kristinpc server (Samba, Ubuntu)
	ZEKE-DESKTOP         zeke-desktop server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            KRISTINPC

```

---

### Post by Nevon on 2009-01-31
I've got pretty much the same problem. First it was working fine, now nothing works (not even printer sharing). I've got the following computers in my network:
- loltop: my laptop running Ubuntu 8.10 and Windows XP
- lolbox: my desktop running Kubuntu 8.10 and Windows XP
- Ninas: my mother's desktop running Windows XP
- Leodatorn: my brother's desktop running Ubuntu 8.10 and Windows XP

My laptop is also connected to a printer, which should be accessible from all computers. All computers are connected via wifi. 

This set up used to work perfectly, and then right out of the blue no computer were able to find each other. At least not in Linux. I'm not sure if they were able to in Windows, at least not my two computers. I think my brother could access our mother's computer, and vice versa, when in Windows. 

The output of smbclient --list=loltop -U% is as follows:
```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (loltop server (Samba, Ubuntu))
	Deskjet-3900    Printer   HP Deskjet 3900
	tommys          Disk      
	musik           Disk      
	pictures        Disk      
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]

	Server               Comment
	---------            -------
	LOLTOP               loltop server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            LOLTOP
```

When I ran that command, both my laptop and desktop were turned on with file sharing supposedly enabled. Regardless of which computer I use, I can't see the other one on the network. smbclient --list=lolbox -U% while on my laptop gives nothing but an error message: "Connection to lolbox failed (Error NT_STATUS_BAD_NETWORK_NAME)"

---

### Post by diablo75 on 2009-01-31
I guess I can be happy that I'm not alone.
:-({|=

---

### Post by Shadow12313 on 2009-01-31
Try going into "Places > Connect to Server" and try using that.

---

### Post by diablo75 on 2009-01-31
> **Shadow12313 said:**
> Try going into "Places > Connect to Server" and try using that.

Whoa whoa whoa.  You mean I should just forget about this problem?  The bloody thing isn't doing what it's supposed to be doing.  I might as well go and install Dropbox on all my computers and just pretend Ubuntu shouldn't be expected to do something simple as share a folder publicly over a local area network.

---

### Post by Shadow12313 on 2009-01-31
> **diablo75 said:**
> Whoa whoa whoa.  You mean I should just forget about this problem?  The bloody thing isn't doing what it's supposed to be doing.  I might as well go and install Dropbox on all my computers and just pretend Ubuntu shouldn't be expected to do something simple as share a folder publicly over a local area network.

I didn't say that at all.  By the way did you try it?

---

### Post by diablo75 on 2009-01-31
What exactly are you wanting me to do?  SSH?  Windows Share?  FTP?

---

### Post by Shadow12313 on 2009-01-31
Windows Share.

---

