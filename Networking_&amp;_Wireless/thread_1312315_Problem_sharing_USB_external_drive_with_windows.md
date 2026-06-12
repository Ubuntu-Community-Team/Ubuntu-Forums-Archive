---
title: "Problem sharing USB external drive with windows"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by fistuks on 2009-11-03
Hello,

I'm an Ubuntu user for about 3 years now.
Until the karmic update i used my ubuntu machine as file server with other computers(mostly windows and macs) and it worked perfect.

I only had to change/add the smb.conf with:

security = user
usershare owner only = false 

In the Authentication section.

Since i upgraded (Actually i made a fresh install) i can access the external drives share only from a mac but not from windows.
(Shares on the home directory of the ubuntu machine I can access from windows)

Any clues?

---

### Post by fistuks on 2009-11-03
Any one?
I checked the samba log of the windows machine and that's the output:

[2009/11/03 16:04:16,  0] param/loadparm.c:8546(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/maxtor failed. Permission denied
[2009/11/03 16:04:16,  0] param/loadparm.c:8546(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/maxtor failed. Permission denied
[2009/11/03 16:04:16,  0] smbd/service.c:190(set_current_service)
  chdir (/media/maxtor) failed
[2009/11/03 16:04:16,  0] smbd/service.c:190(set_current_service)
  chdir (/media/maxtor) failed
[2009/11/03 16:04:16,  0] smbd/service.c:190(set_current_service)
  chdir (/media/maxtor) failed
[2009/11/03 16:04:16,  0] smbd/service.c:190(set_current_service)
  chdir (/media/maxtor) failed
[2009/11/03 16:04:16,  0] smbd/service.c:190(set_current_service)
  chdir (/media/maxtor) failed
[2009/11/03 16:04:16,  0] smbd/service.c:190(set_current_service)
  chdir (/media/maxtor) failed
[2009/11/03 16:04:16,  0] smbd/service.c:190(set_current_service)
  chdir (/media/maxtor) failed
[2009/11/03 16:04:16,  0] smbd/service.c:190(set_current_service)
  chdir (/media/maxtor) failed

---

