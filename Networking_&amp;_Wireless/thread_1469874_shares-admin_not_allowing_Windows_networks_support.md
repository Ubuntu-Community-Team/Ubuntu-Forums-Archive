---
title: "shares-admin not allowing Windows networks support?"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by daanbrg on 2010-05-02
Dear Xubuntu-ers,

I'm trying to set up a little home server here, using Xubuntu 10.04 on an IBM NetVista 6341-75G (very old desktop computer, but it does the job).
At first, I couldn't find the "Shared Folders" option in the "System"-menu, so I decided to install *samba* and *smbfs* by myself - but since I didn't have any experience with those at all, I decided to investigate what the terminal command for the "Shared Folders" panel was.
I found it (sudo shares-admin) and as usual, it asked me to install Unix networks support and Windows networks support. I clicked *Install services* and it went downloading & installing.

But when it finished, it didn't start working, it started from the beginning again - it again asked me to install NFS and SMB.
I tried rebooting, removing SMB, then rebooting and then re-installing via shares-admin, but no avail.
[COLOR="Red"]**[update]** I just re-installed Xubuntu completely (first wiped the hard drive, then did a clean install) and the glitch is still there. Seems to be a bug. I will report this on Launchpad, but if you have the answer to my question, please still let me know. Thanks! **[/update]**[/COLOR]

[COLOR="Blue"]**[update 2]** [Click here to see the Launchpad report I cooked up.]("https://bugs.launchpad.net/ubuntu/+bug/574046") **[/update 2]**[/COLOR]

Can someone in the community help me out with this one?

Thanks in advance!
- Daan Berg

---

### Post by garybrlow on 2010-05-04
I was actually wondering where shares-admin went and after a few days of Googling I found your post. I actually though I was the only one having this problem.  
 

 I think its an outstanding bug. This used to work out of the box before but it seems that development is not going to continue on the direction of shares-admin since the next update of XFCE 4.8 (hopefully this june according to the xfce website) especially thunar will have network shares built in. This might be the reason for excluding shares-admin from the system menu but still exists for transition purposes.
 

 Shared-folders will actually install the needed files and programs but because of the bug it will only allow you to create the workgroup name which will be written/saved to the SAMBA configuration file located in "/etc/samba/samba.conf". Sharing actual folders does not seem to work. To share folders you have manually write and save the configuration to samba.conf. You can use and edit the CDROM example in that files to create your own read only configuration setting. For more configuration setting visit the official samba site at [http://www.samba.org]("http://www.samba.org/").
 

 Meanwhile to fill in the gap of actually browsing the network shares in thunar until 4.8, a combination of Gigolo and gvfs-fuse will do the trick. Access the shares via Gigolo and gvfs-fuse will open the share in thunar. Installation of gvs-fuse is required,after that a restart and then browse away. File operations depend on sharing permission settings via Samba. This is actually the next best thing to native file-share browsing as provided by gnome or kde.


Cheers!
:biggrin:

---

### Post by daanbrg on 2010-05-04
Well, I already fixed it by myself - I decided to pull the Windows XP Home Edition-cd out of it's sleeve. But, as a matter of fact, this slow piece of sh*t runs faster on Xubuntu than it does on Windows XP.
So, I'd love to have it running Xubuntu, but it's too late already :P

Thanks for the suggestions though! I wanted it to be a read/write thing anyway - your suggestion of read-only Samba wouldn't work then.

---

### Post by garybrlow on 2010-05-05
you can set read only to no to have read/write functionality.  ;) you're welcome.

---

