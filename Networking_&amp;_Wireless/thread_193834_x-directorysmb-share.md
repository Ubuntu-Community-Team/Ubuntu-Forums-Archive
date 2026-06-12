---
title: "x-directory/smb-share"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by Lymen on 2006-06-10
I'm having some networking problems.  I can see my home network in Unbuntu, but get an error in opening it.  I've found lots of people asking this same question on many forums but have not found an answer.  Please help if you can.

here is the error message:[COLOR="Red"]The filename "RAUN" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. [/COLOR]
[COLOR="Black"]How do I rename the file to the correct extension?
thanks![/COLOR]

---

### Post by ns2048 on 2006-06-10
Can you provide more details about your setup?

* What is 'RAUN' running (i.e., Windows, Linux/Samba)?
* Post your '/etc/samba/smb.conf'
* Output of 'smbtree'

--ns2048

---

### Post by hotch on 2006-06-29
Did you find an answer to your question? I am having the same problem, and have no idea where to go from here.

---

