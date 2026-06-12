---
title: "cant see computer in network after upgrage to 10.04"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by fragileandys on 2010-06-10
recently upgraded to 10.04 from 9.10 can i cant see my computer in the network on either my computer or my windows machines using samba

Ive followed the instructions at both:

[http://macpablodesigns.wordpress.com/2010/05/01/enable-personal-file-sharing-in-ubuntu-10-04/](http://macpablodesigns.wordpress.com/2010/05/01/enable-personal-file-sharing-in-ubuntu-10-04/)

~and~

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Filesharing](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Filesharing)

neither work for me.

I have my shares configured using both the samba GUI and ive edited the smb.conf file, ive supplied a password to my smb user name.  not sure what the next step would be.

---

### Post by garvinrick4 on 2010-06-10
Set up a Workgroup in Windows. Must have a user password in Windows. Will be able to see any machine and device that is booted up. 10.04 comes with samba installed, do believe in 9.10 you have to install samba.

---

### Post by fragileandys on 2010-06-12
I have this ubuntu machine and 2 other computers running win 7 in my house. 

I am able to see both of those windows computers, and am able to connect to them.

They cannot see my computer on the network, nor can I see my own computer from the places -> network window

any other suggestions?

---

### Post by fragileandys on 2010-06-13
said "ef" it and did a fresh install of 10.04 and it works fine now

---

