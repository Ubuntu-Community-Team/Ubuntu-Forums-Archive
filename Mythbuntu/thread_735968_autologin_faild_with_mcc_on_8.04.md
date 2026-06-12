---
title: "autologin faild with mcc on 8.04"
date: 2008-03-26
forum: Mythbuntu
---

### Post by TheConsultant on 2008-03-26
Hi @all.

I have instaledl mythbuntu 8.04 beta. At the section "artwork and login" I have activated the "start automatic login..." check box for the installed user. But the autostart doesn't work. :(

How can I start up mythwelcome as a shell instead the xfce desktop?

Best regards

Martin

---

### Post by laga on 2008-03-26
> **TheConsultant said:**
> Hi @all.

I have instaledl mythbuntu 8.04 beta. At the section "artwork and login" I have activated the "start automatic login..." check box for the installed user. But the autostart doesn't work. :(


Can you please post /etc/gdm/gdm-cdd.conf and maybe the gdm log file from /var/log/gdm/? Make sure you're not posting anything confidential..

---

### Post by TheConsultant on 2008-03-26
Hello Laga.

I attached the files with this thread.

Thanks in common

Maritn

---

### Post by TheConsultant on 2008-03-26
Hi there.

I have solved this issue with the following workaround:


[LIST]
[*]Write into the home dir a *.xsession* file.
[*]Write the following into the new file:*/usr/bin/mythwelcome *(or */usr/bin/mythfrontend* if you not want to use mythwelcome)
[*]Close the Editor and save the file.
[*]Logout.
[*]Login and choose the "Session" button
[*]You have to choice the "xsession start" radio button.
[*]Start to Login.
[*]In the upcoming dialog say "Default".
[/LIST]

Thats it.:popcorn:

Best regards 2all

Martin

---

