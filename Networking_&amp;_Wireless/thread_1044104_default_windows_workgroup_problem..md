---
title: "default windows workgroup problem."
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by K_V_B on 2009-01-19
Hello all,

I have an ubuntu 8.10 desktop, that is connected to the corporate network, which is predomantly a windows environment.
I can browse windows shares using Nautilus without any problem. I just enter a smb:// url in the address bar, and nautilus prompts me for workgroup, username and password. That works well.
The problem is when I try to open certain documents directly from the share. When I double click on a word document OpenOffice is started. However, the files is not downloaded, OpenOffice gets passed an smb:// url of the document and tries to open it. This causes a new dialog to appear, prompting me again for username and password. However, in this dialog I cannot change the workgroup name, which is set to "WORKGROUP". 
So somewhere in my system the default workgroup used by the smb client libraries used by OpenOffice or Gnome, or whatever that prompted me has a default workgroup name set. I need to change this default workgroup name.
I've chaned it in the /etc/samba/smb.conf file, but this did not have any effect. 
So where do I change the default workgroup used when a program like OpenOffice tries to open an smb:// url?

---

### Post by bruno.vitorino on 2009-02-27
I'm having exactly the same problem as you, and tried the same solution with no luck.

---

### Post by Iowan on 2009-02-27
One potential option might be to [mount]("http://ubuntuforums.org/showthread.php?t=288534") the share.  Perhaps it would provide a more permanent "link".

---

