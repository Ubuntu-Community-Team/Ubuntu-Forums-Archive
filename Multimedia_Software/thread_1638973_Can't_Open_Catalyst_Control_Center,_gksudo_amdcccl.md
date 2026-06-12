---
title: "Can't Open Catalyst Control Center, gksudo amdcccle"
date: 2010-12-06
forum: Multimedia Software
---

### Post by ricky222 on 2010-12-06
Hi, I just tried EnvyNG to update my ATI display drivers, it installed the same version as I had previously but now I can't open the Catalyst Control Center with my usual command:

gksudo amdcccle

I get this error:

Parse error on line 31 of section Module in file /etc/X11/xorg.conf    "Disable" is not a valid keyword in this section.
tc/X11/xorg.confParse error on line 31 of section Module in file /etc/X11/xorg.conf
    "Disable" is not a valid keyword in this section.

I tried this but it did not work:

                 To fix this bug run, in a terminal:
 sudo gedit /usr/share/applications/amdccclesu.desktop
 Then, in gedit, replace "amdxdg-su -c amdcccle" with "gksudo amdcccle".
 This should be the default, instead of a command that doesn't even exist.

        
                                                                                                                                    
Thanks

---

