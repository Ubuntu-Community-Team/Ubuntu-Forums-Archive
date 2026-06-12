---
title: "Remote Support on Ubuntu"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by karimruan on 2009-10-31
I found a similar thread, but only one post. Anyway, I used to offer remote desktop support on windows. Now, I only run ubuntu. Is there a package similar to TeamView(er?) that I can use? Preferably a DEB.

Any help is appreciated!

---

### Post by nowin4me on 2009-10-31
Aparntly it run under WINE.

Or you can use your browser.> Web Connector - use TeamViewer via web browser: Through the newly developed web client you can now control remote computers via a web browser. The remote control works with Adobe Flash 9. Thanks to that TeamViewer 4 does not require Active X or any other security-critical components. Therefore, the web client is the perfect solution for environments in which no executables are allowed to be run or installed, for remote access on the road and for working from Linux machines. The TeamViewer Web Connector is included in TeamViewer Premium.

---

### Post by mlentink on 2009-10-31
The Web Cionnector is a feature of the windows version of Team Viewer, if I read that message correctly. Probably works with IE only?

Perhaps: [http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)

---

### Post by cariboo on 2009-10-31
There is remote desktop and the terminal server client installed by default in Ubuntu. I haven't used the remote desktop for a couple of releases, so I don't know how well it works, but the terminal server client works quite well connecting to windows desktops.

Have a look at vnc, it is in the repositories. If you do use vnc create a really strong password as it servers as an entry point for crackers.

I running Xubuntu at the moment, so I'm not exactly sure what the menu selection is.

---

### Post by toupeiro on 2009-10-31
I would recommend VNC, which has variants that support HTTP. 

Fact of the matter is, however, that most people have router based firewalls, so you have to have port forwarding working for any RDP-like client.  I've done this to help my nephew in Texas with an ubuntu machine before.

---

### Post by mlentink on 2009-10-31
+1 for vnc

Afaik teamviewer is based on NX which apparently is a bit faster.

But the OP could have a very workable solution with [Ultra VNC  SC. ]("http://www.uvnc.com/addons/singleclick.html")which seems to do everything teamviewer does on windows. Haven't used it myself yet, though

---

### Post by karimruan on 2009-10-31
Hey I checked out the link for ultra VNC and it only seems to have a win32 and x64 installer. Am I supposed to wine it, or am i missing the *nix installer?

---

### Post by jgolightly on 2009-10-31
If you're connecting:

FROM an Ubuntu machine TO a machine running UltraVNC: use vinagre, which is preinstalled with Ubuntu

FROM an Ubuntu machine TO a machine running Ubuntu: Go to System > Preferences > Remote Desktop and configure the VNC connection settings.  Then just use vinagre to connect to the Ubuntu machine.

---

### Post by karimruan on 2009-11-01
what about connecting to a windows machine? That is what I support.

---

### Post by mlentink on 2009-11-03
The windows user would download the little sc program from your site, which in effect takes care of a reverse connection to circumvent their firewall.
You can support them using vinagre.

---

### Post by karimruan on 2009-11-05
My solution: 

Logmein (web based, haven't tested it) and the teamviewer web client. I run xp in virtual box, so I guess now I am okay. At least I don't have windows on it's own partition!

Still a single boot system! Thanks for all of your help!

Maybe now you can check out my other thread about running xubuntu on an e1400.

---

### Post by Tony Ricena on 2009-11-06
> **karimruan said:**
> what about connecting to a windows machine? That is what I support.

Terminal Server Client FTW :)  use rdpv5 for xp and newer, rdp for win 2000 and older

---

