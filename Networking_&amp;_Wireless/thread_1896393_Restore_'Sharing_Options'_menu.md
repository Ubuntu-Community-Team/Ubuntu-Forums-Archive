---
title: "Restore 'Sharing Options' menu"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by Unterseeboot_234 on 2011-12-16
Background:
Oneiric 64-bit on AMD64
I tried to set up Samba for a LAN to other Ubuntu machines. That process begins with navigation to the folder you want to share, right-click, pick Sharing Options in the context menu. If you don't have Samba, Ubuntu will offer to install it. However, there are many dependencies missing for the GUI that is supposed to come up to begin tweaking Samba. The GUI loads and quits in a split second.

Search on the forums and on the web and I a-l-m-o-s-t got Samba working after installing pyNeighborhood. There is much info out there that is out-of-date and advice to use the terminal in root mode. The resulting file-permissions were beyond repair. I thought I could delete Samba, reinstall and come back with pyNeighborhood to configure Samba.

However I have lost the Context-menu 'Sharing Options' menu item.

[**[COLOR="Blue"]link to Desktop Sharing Option[/COLOR]**]("http://www.liberiangeek.net/2011/11/a-quick-way-to-share-folders-in-ubuntu-11-10-oneiric-ocelot/")

To get back File/Folder Sharing Options is there any way to fix that menu short of re-installing Oneiric and not having to re-install a lot of custom-built software?

---

### Post by Unterseeboot_234 on 2011-12-16
Firstly, do **[COLOR="Red"][SIZE="3"]NOT [/SIZE][/COLOR]**install a package called swat. Some of the help advice on the Samba configuration says to install that package. swat is out-of-date and Synaptic in the description says swat can lock some LAN users out forever from the Samba server.

I restored my Context-menu 'Sharing Options' by using Synaptic, searching for Samba and noting a package called 'natulius-share'. I installed that and package 'gadmin-samba'. Synaptic also wanted to install 'menu'.

The restored menu item Sharing Option is out of order in comparison to a fresh-install Oneiric after I re-installed natilus-share. This menu-item is vital to the set-up of Samba working with your network clients. That is the vision of how Samba will interface with Oneiric.

Because I had glade, py-samba, gtk, system-config-samba already installed due to all the other advice trying to get Samba going, the GTK gui works like it should. It fires up as a logon user from a menu item 'Samba', In the background it writes the sudo (root) configuration changes.

So, confusion there. The Natilus menu item, its label is 'Samba', but it fires up the gadmin-samba GUI. Samba and its config file are independent of gadmin-samba. Samba is a lib, not a GUI.

I'll leave this post open to put my thinking into practice. (The rest of our computers are cold at the moment.) I'll see if I can share and if so, close this link as solved.

Please give me any comments...

---

### Post by Unterseeboot_234 on 2011-12-17
Okay, with 3 AMD64 computers running Oneiric64, configured to allow a anonymous visitors and with USB wi-fi dongles, I was able to swap files in Samba shares using gadminsamba and also see a printer hooked up to an XP box. 

In Ubuntu traditional Desktop [menu] > Other > Samba >> fires up gadminisamba. That software will tweak config.samba with a normal user logon.

I did not really need pyNeighborhood, but I could use it if I studied it more. pyNeighborhood is a little bit more confusing concerning whether you need to be a /root or a /user and if you want cifs or samba configuration.

gadminsamba, at least with Ubuntu64 Oneiric, is initially missing glade, gtk2 and some python; thus the GUI refuses to 'validate' as we say in Java programming. The GUI does not pause and wait for a Close [x] action.

Trying to get to config.samba with /root manipulation is chancy at best. I had bad luck. I almost lost my Ubuntu Oneiric install but was able get gadminsamba back and I already had the dependencies ready to go for the GUI with a clean config.samba file.

---

