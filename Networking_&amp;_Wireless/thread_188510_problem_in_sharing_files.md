---
title: "problem in sharing files"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by anurag_gupta on 2006-06-04
i hav a PC with mandriva\Xp Dual boot and Toshiba L20-P340 laptop with breezy\XP dual boot.
i connect them using a cross cable

when i connect my laptop(XP) with dektop(mandriva) threre is no problem i can connect ,share internet and files from both sides easily. 
BUT 
when i connect PC(XP) and Laptop(ubuntu) then it doesn't works.
i can ping,telnet to Xp and vice-versa. but whenever i try viewing shared folders(on my laptop(ubuntu)) XP asks for authentication. but it doesn't accepts any password.
when i try viewing windows folders from ubuntu sometimes it shows and sometimes it doesn't.

plz help

---

### Post by Iowan on 2006-06-05
How is Samba set up on the Ubuntu laptop?

---

### Post by anurag_gupta on 2006-06-06
what do u mean by"How is Samba Setup on ubuntu"

it's there from the time i installed ubuntu.

---

### Post by Jason_25 on 2006-06-06
[QUOTE=anurag_gupta]what do u mean by"How is Samba Setup on ubuntu"

it's there from the time i installed ubuntu.[/QUOTE]
He means exactly what he says.  What does your samba configuration look like?  smb.conf, added users, etc...

---

### Post by Iowan on 2006-06-06
Sorry, question was a little blunt/brief.  I probably could have better asked: What does the /etc/samba/smb.conf file look like on the Ubuntu laptop. Perhaps yours did, but my Ubuntu did not automatically install Samba - especially the server side.  Samba will need to have users added to the smbpasswd file (well, depending on security settings - which will show in the smb.conf file).

---

