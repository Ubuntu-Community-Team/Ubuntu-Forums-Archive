---
title: "How to get Ubuntu to see Windows machines???"
date: 2012-09-17
forum: Networking &amp; Wireless
---

### Post by CatMan3110 on 2012-09-17
I have 4 machines set up. 2 are running Ubuntu 12.04 LTS, 1 is running Windows 2003 server, and 1 is dual booting WinXP and Win7. 1 of the Ubuntu machines is configured to share out 2 disk volumes ("Data" and "DiskImages". My windows machines can see these shares. My other Ubuntu machine cannot. Neither of the Ubuntu machines can see any other machine on my local network (although i can sucessfully ping any of them from my shared out Ubuntu machine. I want to get it where all of my machines can see eachother and move files back and forth, as the ubuntu machines are going to be my new servers. Can anyone help me out or give me a good starting point? Any help at all would be greatly appreciated.

---

### Post by Kirk Schnable on 2012-09-18
Try grabbing the IP address of one of your Windows computers, and connecting to it as a Samba location.

(in the location bar on the file browser, type "smb://123.123.123.123" where 123.123.123.123 is the IP address of the Windows computer.

I suspect your shares will appear there.

---

### Post by CatMan3110 on 2012-09-18
I tried your suggestion in firefox, and this is what i got:

The address wasn't understood.      
       
Firefox doesn't know how to open this address, because the protocol (smb) isn't associated with any program.
        
         You might need to install other software to open this address.


So it looks like i'm missing something, but i don't know what. Any ideas?

---

### Post by Kirk Schnable on 2012-09-18
Sorry, I didn't mean the location bar in Firefox.  I meant the location bar in Nautilus.

Go to your Home folder, and do CTRL+L.  That should make the location ("/home" if you went to your home folder) an editable text box.  Type the "smb://ip-address-here/" into THAT location box.  Yeah, Firefox can't load Samba shares.

Kirk

---

