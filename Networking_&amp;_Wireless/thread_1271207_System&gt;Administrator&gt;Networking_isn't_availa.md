---
title: "System&gt;Administrator&gt;Networking isn't available"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by sibot13 on 2009-09-20
I just installed Ubuntu this weekend using Wubi and love it. But I'm having some issues setting up my network options. I was trying to rename the host name. 

After searching the net I found this can be done in System >  Administrator > Networking but that menu option isn't available. 

I found I could open the network settings dialog if I ran the command sudo network-admin but when I run that command it says command not found.

How do I enable these options? Are they just not available because I'm using wubi? I also installed the KDE desktop but I've been using GNOME so I don't know if that has anything to do with it. 

I'm also having an issue where the other server names in my network aren't resolving using any of the network tools. I have a Windows Home Server box and I wanted to remote desktop in but it says the host name not found. If I use the IP address it works fine and I'm able to browse to the server from Places > Network.

Thank you. Any help will be very much appreciated.

---

### Post by SteveDee on 2009-09-21
The Network tool you mention can be installed via System > Administration > Synaptic Package Manager. Just search for "gnome-network-admin" and install.
Also read this: [https://help.ubuntu.com/community/NetworkAdmin](https://help.ubuntu.com/community/NetworkAdmin)

---

### Post by sibot13 on 2009-09-21
Thank you very much. I thought I searched for that package but didn't find it.

---

### Post by ianp5a on 2010-10-31
Thanks for that. That fixed it for me.
It didn't install Network for me in 10.10 be default either.
I had no clue what to do or what to search for.
I wonder why it is not always installed?

TIP: Install Ailurus the Gnome Tweak tool. It allows you to change the host name easily too.

---

