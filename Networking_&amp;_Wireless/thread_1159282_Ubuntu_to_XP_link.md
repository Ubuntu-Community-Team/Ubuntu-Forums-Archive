---
title: "Ubuntu to XP link"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by sqrooup on 2009-05-14
I have a desktop, it used to run windoze XP, it now runs Jaunty.
I also have a laptop, it runs XP.
When the desktop ran XP I had set up a file sharing (2 way) network, allowing file sharing between the "shared documents" directories of both PCs, and printer sharing (the printer is connected to the desktop).
Due to a mishap I lost the XP hard drive, and made a permanent switch to Ubuntu.
I have experimented; the network works, but only one way, the desktop can see the laptop's "shared documents" directory, but the laptop comes up with "folder empty", also it will not print (in fact if I need to print any document on the laptop, I need to access it from the desktop).

Is there anything I can do so that I can print, or view desktop files, from the laptop?

---

### Post by pastalavista on 2009-05-14
You need to install Samba on your 'buntu box. It's in Synaptic or you can do it in terminal: ```
sudo apt-get install samba
```

---

### Post by sqrooup on 2009-05-14
Thanks

---

### Post by timbim on 2009-05-14
If samba can allow ubuntu to see windows files, why can't ubuntu do it natively?  Why hasn't support for it been implemented?

---

### Post by Iowan on 2009-05-14
From the example given above, you can see that it does.  Ubuntu (desktop)was able to see the XP (laptop) shares.  Samba client comes pre-installed on most Ubuntu releases. It's when you want to go the other way that you need to install the "server" package.

---

