---
title: "Access password protected shares on LAN"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by Tigger_2009 on 2009-05-26
Took a while to find this one but it allows normal access to password protected shares using Nautilus without needing any command line work around. Still need to install Samba and smbfs as normal to see the network (check Nautilus sees the network correctly by adding a non-password protected share as a temporary test).

Open a terminal window then type the following

** sudo nano /etc/samba/smb.conf**

Then add the following lines to the file: 

 [global]
[B] # THE LANMAN FIX
client lanman auth = yes
client ntlmv2 auth = no[/B]

Note: I put these at the end of the [global] section.

Save the changes then either re-boot or restart Samba

Now when asked for the username and password the share is mounted correctly ;)

PS - trashed Ubuntu a few times trying different fixes before finding this !!!

---

### Post by dunbrokin on 2009-10-31
I cannot access other computers on my LAN via Network (cannot mount) however if I go Computer/Go/Location and enter the IP address, I can access the folders. However the public folders ask for a password....but I have not set a password for any of them....How do I get around this password problem?

---

### Post by hombibi on 2010-01-26
Thank you!!! I have been searching for this solution such a long time ..

---

### Post by CCK on 2011-03-21
For me on karmic amd64.

I add the following line to the global section of smb.conf

client use spnego = no 

This allowed me to connect to windows 7 shares and printer with my choice of password protected or not.

:)

---

### Post by mastia on 2011-03-28
Brilliant, I can finally access my ReadyNas server. Many thanks!

---

