---
title: "IREXEC have no function in daemon mode"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by TheConsultant on 2007-07-23
Hi @all

with XUBUNTU (mythbuntu) Gutsy Gibbon 07/10 - IREXEC will not work well.

Test this with following ~/.lircrc:
[b]
begin
   prog    = irexec
   button = ok
   config = echo "Psst, this a secret!"
end
[/b]

If you start irexec with * irexec & ~/.lircrc * and press the ok button of your remote control, IREXEC will show * Psst, this is a secret! * in a console.

If you start IREXEC with * irexec -d ~/.lircrc *, irexec will not shown any text in the console.
It's the same, if you with mythbuntu change the .lircrc to:
[b]
begin
   prog    = irexec
   button = power
   config = /bin/sudo /sbin/shutdown -h now
end
[/b]

Any suggestions?

Regards

Martin

---

### Post by dysphasi on 2007-10-30
*bump* 

Can anyone help?...I've got exactly the same problem, irexec works fine if not run in daemon mode, but with the -d switch it loads, but none of the key configurations set in .lircrc work.

---

### Post by dysphasi on 2007-10-30
...hmmm, if I run:
```
sudo irexec -d
```
from the terminal it works....only thing is, this is next to useless for a startup process. 

What's going on here?

---

