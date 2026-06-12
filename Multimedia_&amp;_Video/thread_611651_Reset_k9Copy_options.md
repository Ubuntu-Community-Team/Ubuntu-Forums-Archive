---
title: "Reset k9Copy options?"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by raistlin_kell on 2007-11-13
When i invoke k9Copy on my HP NC6220 laptop running a new Kubuntu Gutsy 7.10 install it crashes to the desktop after i set k9Copy to use OpenGL for the display output* stupid me*.

Does anyone know how i can remove/reset the K9Copy options back to default before i altered the preferences?

[COLOR="Red"]Backtrace from running as normal user[/COLOR]
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
***no debug line repeated about 40 times***
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1234229568 (LWP 6840)]
(no debugging symbols found).
***no debug line repeated about 40 times***
(no debugging symbols found)
[KCrash handler]
#6  0x00000000 in ?? ()
#7  0x080663e6 in ?? ()
#8  0x00000000 in ?? ()

[COLOR="Red"Error output from Konsole when running "sudo k9copy"[/COLOR]
Error: "/tmp/kde-user" is owned by uid 1000 instead of uid 0.
libGL.so: cannot open shared object file: No such file or directory
***libGL.so error line repeated about 12 times***
libGL.so: cannot open shared object file: No such file or directory
KCrash: Application 'k9copy' crashing...

---

### Post by mcduck on 2007-11-13
It has probably made a hidden file/directory inside your home to store your settings. Remove that and all settings are reset to defaults.

---

### Post by raistlin_kell on 2007-11-13
checked for hidden directories looking for anything with .k9 or similar and nothing presented unfortunately. I also had a looksee in the .kde folder thinking there might be something in there. I also checked the /tmp/k9copy folder but that was also blank... After that, i did some research here on the ubuntu forums, then decided it was time to post!

---

### Post by ingo on 2007-11-14
~/.kde/share/config/

There are a couple of k9copy files in there

---

