---
title: "[SOLVED] Kopete issue"
date: 2008-08-01
forum: Multimedia Software
---

### Post by vijaychandilya on 2008-08-01
I am trying to use Kopete to video chat with a webcam. I use a Gnome desktop and Kopete will not run. Running Kopete from the command line gives the following output:

kopete: WARNING: KTempFile: Error trying to create /home/ubuntu/.kde/tmp-laptop2/startkdeinitlockXXXXXX.tmp: Permission denied
kopete: WARNING: KTempFile: Error trying to create /home/ubuntu/.kde/tmp-laptop2/startkdeinitlockXXXXXX.tmp: Permission denied
kopete: WARNING: KTempFile: Error trying to create /home/ubuntu/.kde/tmp-laptop2/startkdeinitlockXXXXXX.tmp: Permission denied
kopete: WARNING: KTempFile: Error trying to create /home/ubuntu/.kde/tmp-laptop2/startkdeinitlockXXXXXX.tmp: Permission denied
kopete: WARNING: KTempFile: Error trying to create /home/ubuntu/.kde/tmp-laptop2/startkdeinitlockXXXXXX.tmp: Permission denied
kopete: WARNING: KTempFile: Error trying to create /home/ubuntu/.kde/tmp-laptop2/startkdeinitlockXXXXXX.tmp: Permission denied
kdeinit: Aborting. No write access to '/home/ubuntu/.ICEauthority'.
kopete: ERROR: KUniqueApplication: Can't setup DCOP communication.

Can someone please tell me what the problem is?

Regards,
Vijay

---

### Post by y@w on 2008-08-01
Check that you can browse to the directory listed (/home/ubuntu/.kde/tmp-laptop2/) and write files there.

---

### Post by vijaychandilya on 2008-08-01
I can write to the directory you specify. I also changed permissions on .ICEAuthority, but now the error it gives me is as follows:

ubuntu@laptop2:~$ kopete
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/ubuntu/.kde/socket-laptop2/kdeinit__0'
kopete: ERROR: KUniqueApplication: Can't setup DCOP communication.

Thanks for your help!

---

### Post by y@w on 2008-08-01
Does this help?

[http://ubuntuforums.org/archive/index.php/t-487106.html](http://ubuntuforums.org/archive/index.php/t-487106.html)

---

### Post by vijaychandilya on 2008-08-01
> **y@w said:**
> Does this help?

[http://ubuntuforums.org/archive/index.php/t-487106.html](http://ubuntuforums.org/archive/index.php/t-487106.html)

That helps, thanks! I can start Kopete now

---

