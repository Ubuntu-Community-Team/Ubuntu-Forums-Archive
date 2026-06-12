---
title: "Access problem to a samba shared folder with password"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by ario on 2010-05-31
I have created a shared folder via nautilus. I can not access it, because it asks me for user name and password again and again. I'm sure both username and password are exactly right. But I can not access the folder.
Only when I check "Allow guest user access" it will allow me to access my data, Which is not secure enough for me.
Anyone has idea how can I solve this problem?
Thanks for your attention guys.

---

### Post by ario on 2010-06-27
Bump!

---

### Post by Morbius1 on 2010-06-27
Two different usernames and passwords are involved. A linux one and a samba one. Did you create a samba user / password?

For example:
```
sudo smbpasswd -a morbius
```Assuming there is a local user named morbius on the system with the share, the above command will add AND enable a morbius samba user.

---

### Post by ario on 2010-07-27
> **Morbius1 said:**
> Two different usernames and passwords are involved. A linux one and a samba one. Did you create a samba user / password?

For example:
```
sudo smbpasswd -a morbius
```Assuming there is a local user named morbius on the system with the share, the above command will add AND enable a morbius samba user.

Thanks man! It solved my problem. God bless you!
By the way I wish there was a GUI for doing this without asking it in a forum and then getting a magic command to solve the problem. This is why some people can't leave windows and join us in Linux community.

---

### Post by ario on 2010-07-27
But can samba be hacked trough another windows or linux computer? Are my files safe?

---

### Post by P4man on 2010-07-27
you can do all that through the GUI (just install the samba config program from ubuntu software center). its just so much easier to give CLI instructions. just one short command that you can copy paste, language and dekstop environment independent. Explaining the same using the GUI would take 10x as long and would require making assumptions about your DE, installed language etc.

> 
But can samba be hacked trough another windows or linux computer? Are my files safe? 

Define safe. Just about anything can be hacked if its worth spending infinite resources on; but samba is really old and stable there will be no glaring security flaws in it. Whether you will be able to configure it so its secure is something else.

---

### Post by ario on 2010-10-02
Thanks man. I installed samba-config-samba and it worked:)

---

