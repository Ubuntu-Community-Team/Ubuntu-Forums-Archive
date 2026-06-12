---
title: "Build a Basic Ubuntu LAN?"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by Bartender on 2009-09-01
I hope LAN is the right term...:)

I've googled around this morning, looked in Community Docs, etc.  Maybe this is such a basic task that there's very little discussion?

I have an Ubuntu laptop, an Ubuntu desktop with a wireless card that works, and a WRT54G router.  I'd like to build a wired network, then a wireless network.  Stuck with dial-up at home so networking has never been a priority.  But I'd like to at least see two Linux PC's work together.

Anyone know a good link that walks thru the basics?

---

### Post by dmizer on 2009-09-01
Plug (or connect wirelessly) all computers into your router.

You now have a LAN. LAN means Local Area Network. A "network" is simply a group of computers connected together (in your case, by a router).

Having a LAN doesn't really do much for your computers though unless you enable some network services like file sharing, printer sharing, or any number of other LAN services. So, what would you like to do with your LAN?

---

### Post by Bartender on 2009-09-01
Well, that shows you how much I don't know about networking...

I'd like to be able to do basic file sharing, I guess.  Dinked around with the 3 components (two PC's and router) since first post.  Able to ping each other, but that's about it.  
Tried remote desktop.  The desktop PC is running Mint Gloria and doesn't seem to have the Terminal Server Client.  The Ubuntu laptop does, but "VNC" is grayed out when I went into TSC.  At the library right now with broadband, trying to find "vnc" package if there is such a thing

---

### Post by dmizer on 2009-09-01
VNC should be installed by default, you just need to enable it. You can enable it by going to system > preferences > remote desktop.

Then you can access it by typing the following in the command line:
```
vncviewer [COLOR="Red"]vnc.computer.ip.address[/COLOR]
```
Replace [COLOR="Red"]vnc.computer.ip.address[/COLOR] with the actual IP address.

For file sharing, first thing is to configure shares. You can configure a share by right clicking on a folder (for example, the Public folder) and selecting "share options". Make sure that all three boxes are checked.

Then, you can browse to the share from another computer by going to: places -> connect to server. Switch to "Windows share", and enter the other computer's IP address in the "server" field", and the name of the share in the "share" folder (in the above example, the name of the share would be "Public"). You can create a bookmark if you like, then click connect.

---

### Post by Bartender on 2009-09-01
Hi, dmizer!
You're up, and I'm winding down for the day.  Found several posts that mentioned "VNC greyed out" in Terminal Server Client.  Had to run this

```
sudo apt-get install xtightvncviewer
```

That fixed the VNC greyed out problem.  

I'm back home behind our crummy dial-up connection.  Just read your latest post.

Found the Public folder and right-clicked.  Tried to check the first box and got an error message - "Sharing service is not installed".  Then it wants to install the Windows networks sharing service.  #$(*&@ dial-up has made it such a pain to do anything in Linux.  Looks like it wants to install samba.

Will try again when I can find some broadband.  Thanks for the tip about configuring shares.

---

### Post by Bartender on 2009-09-07
Took laptop to library and installed samba, smbfs, openssh-server and ssh.  Made an AptonCD and used it to install those programs to the desktop at home, which is stuck behind dial-up connection.

Using the WRT54G router in between, the laptop pings the desktop and vice versa.  Both PC's running 9.04.  The laptop's updated, the desktop is a fresh install but no upgrades because of dial-up.

_OpenSSH_
On laptop: Using "Connect to Server" (SSH) the laptop sees everything on the desktop PC.  The desktop fails to connect to the laptop.  Times out.

_Samba_
I used the command to start Samba in case it wasn't running. 
The laptop gets no further than the Windows Network icon before I get the dreaded "Failed to retrieve share list.." message.
The desktop goes further.  It opens to WORKGROUP, then shows both PC's, then I get the same error message.

I searched some of the threads and will try disabling firewall.

Giver doesn't seem to do anything either but I'm not clear on how it works.

Oh, yeah, I set up a couple of folders on each PC as "Shared".

_STATUS REPORT_
I disabled ufw on both machines and that got me partway there.  The laptop got past Windows Network to WORKGROUP, then showed the desktop PC but not itself.  The desktop PC showed itself but not the laptop.  Edited /etc/hosts file, adding the desktop IP address to the laptop's file and vice versa.  Now they're sharing in Samba!
BTW, someone mentioned a neat little diagnostic trick that sounded very odd to me but it worked.  I was trying to find the laptop PC, which was at 192.168.1.100.  Opened Firefox (!) on the desktop and typed in "smb://192.168.1.100".  Firefox showed me the two shared folders on the laptop!  I assume this only works if you have installed samba.

Now I gotta figure out what to do about the firewall.  Don't want to leave it disabled.

---

### Post by Cardale on 2009-09-07
what firewall are you using?

---

### Post by Bartender on 2009-09-07
Just the firewall that's enabled in a basic Ubuntu install.  ufw, I think?  I hadn't done anything with Linux firewalls before beginning this networking project, and don't really understand the subject very well.  Have read several posts from guys who said they turned off ufw and aren't worried about it.

I haven't installed gufw but will get that next time I'm in town with the laptop.

I'm open for any ideas on setting up firewall so that it does its job without impeding file sharing between PC's on the LAN or WLAN.

---

