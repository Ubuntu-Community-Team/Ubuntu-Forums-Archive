---
title: "Remote access -- please suggest the 'fastest' solution"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by harisund on 2006-06-29
hello

I want to access my remote PC behind a router (yes, I know how to forward ports on the router) using my laptop while on the move

I tried XDMCP and it is pretty ok. But the bad news is that the remote PC makes a connection to my laptop in port 6000. That means it ain't going to work if I am behind another router (which is the case at every place I am connected using a wireless router). So XDMCP is out of the question. Does anybody have a fix for this by any chance? 

X over SSH works super fine. But the problem is, it is too slow :( I don't like encryption, it takes away all my bandwidth. I haven't tried X over Telnet, thats coming up for the weekend. 

VNC seems to be a try-able solution. Can someone suggest which is the fastest free VNC that can be installed on Ubuntu? I really would prefer I see the whole gnome desktop session rather than open individual apps with SSH/telnet. 

What is the best / fastest option I have got? I am not looking for too much security, so if I can trade some security for speed I would be willing to do it.

---

### Post by LKRaider on 2006-06-29
The best solution nowadays is NX/FreeNX.

There are some How-To's on these forums, let me see...

FreeNX on Ubuntu help: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

FreeNX packages: [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/)

A HowTo for Breezy, but still useful: [http://ubuntuforums.org/showthread.php?t=97277](http://ubuntuforums.org/showthread.php?t=97277)

Another FreeNX thread: [http://www.ubuntuforums.org/showthread.php?t=1968](http://www.ubuntuforums.org/showthread.php?t=1968)

---

### Post by chenel on 2006-06-29
If you decide you need VNC, x11vnc (it's in the repos) is the fastest server I've found.  To use it you will have to make sure the Gnome VNC client (vino) is disabled (System->Preferences->Remote Desktop).

The best Windows client (if you need one) is UltraVNC ([ultravnc.sourceforge.net]("http://ultravnc.sourceforge.net")); the linux clients all seem to work about the same as far as I can tell, so I suggest using the one that comes with Ubuntu (Applications->Internet->Terminal Server Client).

---

### Post by fragos on 2006-06-29
Actually Ubuntu has a Remote Desktop capability based on vncviewer.  All you need do is to enable it.  I find it quite handy for using my office LAN.  Its response even on a LAN is visually slower than native attachment.  WAN network speeds will slow it down even more.  I'd experiment with whats bundled in Ubuntu before installing additional packages.  In the long run you may find file syncing with rsync or unison a better choice for some applications.  I usually use memory sticks and sync to make my data portable.  Another advantage is I can work on my data when I can't connect to the Internet as when flying.  It all depends on what you wish to accomplish.

---

### Post by harisund on 2006-06-29
Hello !

Thanks everyone for their suggestions

I am going to try out NX. I will post back how it was. Thanks LKRaider

chenel, I did use vino and wasn't satisfied with it. I will try x11vnc as you have suggested. Also, does the client you use matter? I thought only the server determined the speed. I am going to try UltraVNC now, I have been using the RealVNC server. Among the 3 VNCs (Ultra, Real and Tight) which is the best? 

fragos, the default Ubuntu remote desktop is the vino server. Yes, I do use a lot of portable data, and I prefer SSHing if only the terminal is involved (which is, in most cases). However, I do like to see the graphic desktop for some appli cations and hence the thread...

---

### Post by chenel on 2006-06-29
[QUOTE=harisund]
Also, does the client you use matter? I thought only the server determined the speed. 
[/QUOTE]
I think that the server is the lion's share of the speed, but UltraVNC's interface is very helpful and has lots of nice options that the other clients don't.

> Among the 3 VNCs (Ultra, Real and Tight) which is the best?  UltraVNC is Windows-only.  I use TightVNC's Java client for web access (x11vnc can be configured to serve a Java viewer through port 5800 + display #).  In linux, I usually make do with the Ubuntu-default Terminal Server Client (which I believe is built on RealVNC).  I've been experimenting with NX, though, and if you don't need to be able to access an already-open login session, it works worlds better.

Oh, and if you don't mind a little configuration, ditch vino and never look back.   On my machine it uses up to 70% of the processor time when active, whereas x11vnc usually uses 10-15%.

---

### Post by merlinof2 on 2007-02-27
This thread is of interest as I have to solve this issue also.
I currently have Edgy running at my house, and 2Kpro at the office.  TightVNC is installed at the office and I've forwarded a port to the system.  It works perfectly from the house to the office, even quicker than a native win to win RDP client I used to use.
NOW, I need to go from the win client (2kpro) to the Edgy machine at home with full screen control, not just ssh or telnet.
I used to do this exceptionally easy back and forth with X86 on my OS/2 machine with Slackware.  It seems a more difficult task with win involved.
Any suggestions would be greatly appreciated.

thanks in advance...
don

---

### Post by gjern on 2007-03-02
Concerning speed, NX from Nomachine via SSH is the way to go IMHO.

By the way:
If You intend to use Your Ubuntu box as a jump-server that You can log in to remote, eg. for surfing the Internet when You are on the road, I recommend to install the firefox add-on "FlashBlock" on the firefox-browser on Your Ubuntu-box.
All those flash animations that are running on a lot of commercial sites, makes surfing the internet via a remote NX-session to appear slow, because NX (or VNC or what-ever You use) constantly must update the screen.
FlashBlock stoppes all those flash animations. 
(If You never the less have an irresistably need to see an animation, just clik on it, and FlashBlock will allow it to play.)

I run a Ubuntu 6.10 as a jump-server on a 512/2048 ADSL, and with NX over SSH and with flashBlock installed on it, I can surf the internet remote through this jump-server with (allmost) the same speed as when I am at home.

---

