---
title: "VNC Round 2--Let's Try This Again"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by JohnnySage50307 on 2009-07-08
Alright, I'll state the problem/symptoms again because somehow my last thread just died...
 
I had recently installed Jaunty (v9.04) and have been slowly converting it into a workhorse-server for some projects I'm working on and as a common machine for some students of mine to work on. To date, I have SSH, FTP, and Apache HTTPD up and running perfectly along with a registered DNS name. Being as some of my students desire to learn OpenGL, a working VNC server will be required.
 
I installed TightVNC server using "sudo apt-get tightvncserver" through Terminal. Also, while reading up on what ports I ought to have opened (since this is the first server I'm really setting up alone), I opened TCP and UDP ports listening on 5900. After correcting the links (i.e. ensuring 'vncserver' links to 'tightvncserver' etc.), I began to run "vncserver" and suplied a password. On my laptop (running Windows Vista [ugh, long story]), I opened Tight VNC Viewer and began to run it like normal: I suplied my server's URL with the alocated port (since I'm the only one VNC-ing, it's always been :1 thusfar). It opens the window alowing me to view the desktop.
 
Mouse functions work perfectly, however this is where the fun begins... The keyboard is scrambled. For instance the 5-key is now the backspace key and the s-key is now 'b'. On a different thread, I was advised to deactivate 'compiz', which apparently meant turning off the desktop visual effects. When I went to do this, I discovered that I already had no desktop effects running, therefore I can conclude this is not the case.
 
For 4-lettered-words and giggles, I went to Tight's website and downloaded the package to install, believing somehow I had a corupt installation (somehow? Anything's possible at this point I guess). When I run the "./configure" program, it returns with error claiming I do not have X installed on my machine. While I'm more than happy to persue this avenue, I discovered from X.org's website that downloading X is not a simple endevour: it's a group of individual packages which each need to be installed in some order?.. Needless to say, but X.org's site is far from user-friendly.
 
So, given my plight, any sugestions? Thank you in advance to everyone who helps me out!!

---

### Post by JohnnySage50307 on 2009-07-11
Ok, according to a friend of mine, the issue might be that I need to configure Xserver. Does anyone have a clue where I'd go for that and how I'd do it?

---

### Post by JohnnySage50307 on 2009-07-12
Alright, I just wiped everything out and started over again.   Installed vnc4server this time, and everything seems to be working great...only issue is I can't support multiple vnc connections at the same time for some odd reason.  Oh well, I'll figure that one out soon enough.

---

### Post by RGPerson on 2009-07-12
Do you have Compiz running? I've heard that could be my problem.  But I can't figure out how to remove it.  

But I'd also like a working vnc server.  How did you get yours installed?  I can't see what my mouse and keyboard are doing when I'm VNCed. I can use them but the display will not update.

Gabrielle

---

### Post by JohnnySage50307 on 2009-07-12
Someone mentioned the Compiz thing to me before, but I didn't have that enabled.  I did get vncserver working finally, but I had to basically start from the beginning again.  Assuming you are starting from scratch, here's what you can do:

[B]Within your Router (192.169.1.1):
[/B]On your machine, make sure you enable VNC connections.  This usually requires a TCP connection for ports 5550, 5900, and 5901.

**From Terminal:**
Do "sudo apt-get vnc4server".  That will install (what I've found) a working vncserver on your machine.  You will need to make a hard link for it by typing "sudo ln vnc4server vncserver".  I also had to create a hard link for Xvnc by typing "sudo ln Xvnc4 Xvnc"...for some reason it installs its own version of Xvnc, but doesn't search for it by what they called it!  Weirdness!!

As a precaution, be careful of your remote desktop privlages.  I found a security issue with mine that I could just open a remote desktop without a password.  I fixed it by setting it and restarting.

---

### Post by RGPerson on 2009-07-12
> **JohnnySage50307 said:**
> Someone mentioned the Compiz thing to me before, but I didn't have that enabled.  I did get vncserver working finally, but I had to basically start from the beginning again.  Assuming you are starting from scratch, here's what you can do:

[B]Within your Router (192.169.1.1):
[/B]On your machine, make sure you enable VNC connections.  This usually requires a TCP connection for ports 5550, 5900, and 5901.

**From Terminal:**
Do "sudo apt-get vnc4server".  That will install (what I've found) a working vncserver on your machine.  You will need to make a hard link for it by typing "sudo ln vnc4server vncserver".  I also had to create a hard link for Xvnc by typing "sudo ln Xvnc4 Xvnc"...for some reason it installs its own version of Xvnc, but doesn't search for it by what they called it!  Weirdness!!

As a precaution, be careful of your remote desktop privlages.  I found a security issue with mine that I could just open a remote desktop without a password.  I fixed it by setting it and restarting.

Thanks. I'll try that if I have anymore problems. I did finally get rid of Compiz and that seems to have fixed the issue. I can now see what I click!

Gabrielle

---

