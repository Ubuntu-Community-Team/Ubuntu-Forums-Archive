---
title: "Can't get online with WG311"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by Trinity1976 on 2010-06-20
I've recently ran a fresh install of Ubuntu 9.10 after having a failed attempt at upgrading to the new version. However, now I can't get online. My old version as it turns out was a i386 version. I made a fresh CD with the AMD64 version and have installed that but my normal method for getting online no longer works. I've downloaded the AMD64 versions of the files I thought I needed and tried running them as follows:

> sudo dpkg -i ndiswrapper-common_1.53-2ubuntu1_all.deb
sudo dpkg -i ndiswrapper-utils-1.9_1.53-2ubuntu1_amd64.deb
sudo dpkg -i ndisgtk_0.8.4-1_amd64.debHowever, when I get to the last of these I get the following error message:

>                                   [FONT=DejaVu Sans, sans-serif](Reading database ... 113494 files and directories currently installed.) [/FONT] 
 [FONT=DejaVu Sans, sans-serif]Preparing to replace ndisgtk 0.8.4-1 (using ndisgtk_0.8.4-1_amd64.deb) ... [/FONT] 
 [FONT=DejaVu Sans, sans-serif]Unpacking replacement ndisgtk ... [/FONT] 
 [FONT=DejaVu Sans, sans-serif]dpkg: dependency problems prevent configuration of ndisgtk: [/FONT] 
  [FONT=DejaVu Sans, sans-serif]ndisgtk depends on menu; however: [/FONT] 
   [FONT=DejaVu Sans, sans-serif]Package menu is not installed. [/FONT] 
 [FONT=DejaVu Sans, sans-serif]dpkg: error processing ndisgtk (--install): [/FONT] 
  [FONT=DejaVu Sans, sans-serif]dependency problems - leaving unconfigured [/FONT] 
 [FONT=DejaVu Sans, sans-serif]Processing triggers for desktop-file-utils ... [/FONT] 
 [FONT=DejaVu Sans, sans-serif]Processing triggers for hicolor-icon-theme ... [/FONT] 
 [FONT=DejaVu Sans, sans-serif]Processing triggers for man-db ... [/FONT] 
 [FONT=DejaVu Sans, sans-serif]Errors were encountered while processing: [/FONT] 
  [FONT=DejaVu Sans, sans-serif]ndisgtk [/FONT] 
 At the moment the only way I can get online is by using the old CD with the i386 version of 9.10 on it, but this CD, although I can run it live, I cannot do a full install from it, otherwise I'd just revert to that as the i386 versions of the ndiswrapper packages work fine.

Any ideas?

---

