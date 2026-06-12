---
title: "Sharing files between two ubuntu computers"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by GaryRixon on 2010-08-14
Right, I would like to be able to share files with another member of my family over our home wireless network. I have ran the command avahi-browse -a but it on returns my computer. Any help would be greatly appreciated. 

Thanks in advance

---

### Post by AlphaLexman on 2010-08-14
I believe the easiest way is to use 'samba.' The client side is installed by default in ubuntu. That's you, the client. To access files on another computer, it must have 'samba-server' installed (not by default), and if that computer is running ubuntu, and they want files from your computer, you will also have to install samba-server. This method allows a user to use the GUI via Places -> Network, to navigate the computers on the network. Another option, which works more from the command line, but IMO is more powerful is 'ssh'.

---

