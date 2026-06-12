---
title: "SSH In Ubuntu 10"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by Matthew24 on 2011-05-07
Hi all,
 
I installed openssh and putty. How can I gain access to a server to try  out ssh? Can I gain access to one of my PCs at home? When I try to type  in a workstation's internal ip address, it won't let me. 
 
Any input is appreciated!

---

### Post by Toz on 2011-05-07
If you installed openssh-server and putty on the same computer, then you can test by entering localhost in the "Host Name (or IP Address" field. This will create a connection to yourself. Good enough for testing.

If you want to connect to another machine, that other machine will need to be running the openssh-server as well.

---

### Post by mikewhatever on 2011-05-07
Just checked the packages, and there is no 'openssh' in any of the recent Ubuntu releases. Do make sure you install 'openssh-server' on the computer you want remote access to.

Let's assume you've installed openssh-server on computer A with a local IP - 192.168.1.100, and your username on that computer is matthew. Now, from another computer on the same LAN open a terminal window:
```
shh matthew@192.168.1.100
```

You should see a password prompt for matthew, and after typing the password, you should be remotely logged in to A. If you want to access A from a Windows computer, use Putty.

---

### Post by Paddy Landau on 2011-05-07
Incidentally, you don't need PuTTY.

You can open a terminal and use the [FONT=Courier New]ssh[/FONT] command. Use [FONT=Courier New]man ssh[/FONT] to find out the syntax. The basic syntax is
[FONT=Courier New]ssh -l [username] [host][/FONT]

---

### Post by Matthew24 on 2011-05-08
Okay awesome!

Thanks for all of the replies. 

Can I access internal ips [ie 192.168.1.x] and external server ips with ssh?

Also, if I'm sshed into a linux server once I install ssh on it, is there a way I can get a GUI for it? Or like an emulated one to help me out? Would I have to install a gui on the server itself? Is this detrimental towards server performance?

thanks for all of the help!

---

### Post by Paddy Landau on 2011-05-09
> **Matthew24 said:**
> Can I access internal ips [ie 192.168.1.x] and external server ips with ssh?
Well, if you can access it with PuTTY, then you can with SSH. As far as I understand, PuTTY is just a front-end for SSH.

> **Matthew24 said:**
> ... if I'm sshed into a linux server ... can get a GUI for it?
Try [xnest]("apt:xnest"). I've not done it myself, but you can get [xnest instructions]("http://www.youtube.com/watch?v=BSYmajttVDw") from YouTube. There may be other ways, but I don't know much about this.

---

### Post by Matthew24 on 2011-05-09
Okay, thank you I'll check it out.

---

### Post by YesWeCan on 2011-05-09
Here's how it works.

ssh is a means to get a terminal, displayed locally, of a remote server. It can also be used to make a remote server's port appear locally, or vice-versa. The server has to be running some sort of ssh server program and the client has to have some sort of ssh client program.

Ubuntu and most linux (maybe all) have ssh client pre-installed. In Ubuntu you have to add the ssh server doing what mikewhatever said. The ssh server has configurations at /etc/ssh/sshd_config which you can edit: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring).

Windows has no ssh capability. So you can use putty as an ssh client program. For making an ssh server on Windows you need something such as cygwin, which is hugely complex compared to putty.

To get a remote desktop the server has to be running a remote desktop program. There are loads of these. With linux you have a choice of viewing the actual desktop the server is running at the server's monitor, or you can instantiate a separate desktop. Unlike Windows, linux can spawn loads of independent desktops simultaneously and across multiple users. Windows is not a proper multi-tasking OS and can only run one desktop.

For my Ubuntu server I run xtightvnc. This spawns new desktops for remote access. You can also use Ubuntu's built-in remote desktop which gives remote access to your locally displayed desktop (useful for remote assistance). On a Ubuntu client I use vinagre (built in) as the VNC viewer. Windows has a built-in remote desktop server and I think it is different from VNC so in Ubuntu client you need to use something like rdesktop to see it. If you want to see an xtightvnc Ubuntu served desktop on Windows you can install TightVNC Viewer in Windows: [http://www.tightvnc.com/](http://www.tightvnc.com/)

You will have to fill in the details yourself but I hope this gives you some good leads.

---

### Post by Paddy Landau on 2011-05-09
Thank you for that excellent summary, YesWeCan.

I understand the difference between using VNC and xnest is that VNC views the desktop on the remote computer (so the remote computer does the GUI work and bandwidth is spent sending the screen); whereas xnest creates the desktop on the local computer (so the local computer does the GUI work and no bandwidth is spent sending the screen).

Please correct me if I'm mistaken.

---

### Post by YesWeCan on 2011-05-09
> **Paddy Landau said:**
> I understand the difference between using VNC and xnest is that VNC views the desktop on the remote computer (so the remote computer does the GUI work and bandwidth is spent sending the screen); whereas xnest creates the desktop on the local computer (so the local computer does the GUI work and no bandwidth is spent sending the screen).
Sorry, I am not familiar with xnest. Some info: [http://www.realvnc.com/pipermail/vnc-list/2000-January/011375.html](http://www.realvnc.com/pipermail/vnc-list/2000-January/011375.html)
VNC is quite fast in my experience. Of course, only cleverly compressed screen changes and keyboard and mouse events are transmitted.

---

### Post by Paddy Landau on 2011-05-09
I'm aware of VNC, and indeed of TightVNC, which is better compressed.

I like the idea of xnest, because it will work well even over a slow connection. If I'm right, that is.

---

