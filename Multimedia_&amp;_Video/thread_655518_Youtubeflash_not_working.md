---
title: "Youtube/flash not working"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by nintendorulz55 on 2008-01-01
Hi all, im new to the forums, and to ubuntu all together. i just switched from windows xp, and i have to say, it is truly better. but anyway, on to my situation, i go to youtube, but when i look up a video it says i dont have flash, so i click the install plugin button that appears. it all seems to install well, but i try again, and it doesnt work. so i try to install again, but it says it has already been installed. any ideas??? thanks in advance.

---

### Post by jonberling on 2008-01-01
I just had the same problem, so I tried to install flash using synaptic, but it said there were md5 checksum errors and would not install.

The solution that did work though was to go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN)
 and download option 1) the tar.gz.

After it's downloaded, extract it, and then run flashplayer-installer (in terminal, if it asks; and with firefox closed). 

HTH,
Jonathan

---

### Post by nintendorulz55 on 2008-01-01
> **jonberling said:**
> I just had the same problem, so I tried to install flash using synaptic, but it said there were md5 checksum errors and would not install.

The solution that did work though was to go to [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN)
 and download option 1) the tar.gz.

After it's downloaded, extract it, and then run flashplayer-installer (in terminal, if it asks; and with firefox closed). 

HTH,
Jonathan

ok, i just tried that, it tells me there is an error while extracting files. this is the command line error:

tar: /tmp/install_flash_player_9_linux.tar.gz: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: install_flash_player_9_linux/flashplayer-installer: Not found in archive
tar: Error exit delayed from previous errors

---

### Post by jonberling on 2008-01-01
When you downloaded the file, did you use the option to "Save to Disk"?

---

### Post by wolfen69 on 2008-01-01
here [http://rapidshare.com/files/80562619/flashplugin-nonfree_9.0.115.0ubuntu2_7.10prevu1_i386.deb.html](http://rapidshare.com/files/80562619/flashplugin-nonfree_9.0.115.0ubuntu2_7.10prevu1_i386.deb.html)  
is a link for the .deb flash file. just double click it.

---

### Post by nintendorulz55 on 2008-01-01
> **wolfen69 said:**
> here [http://rapidshare.com/files/80562619/flashplugin-nonfree_9.0.115.0ubuntu2_7.10prevu1_i386.deb.html](http://rapidshare.com/files/80562619/flashplugin-nonfree_9.0.115.0ubuntu2_7.10prevu1_i386.deb.html)  
is a link for the .deb flash file. just double click it.

THANK YOU

---

