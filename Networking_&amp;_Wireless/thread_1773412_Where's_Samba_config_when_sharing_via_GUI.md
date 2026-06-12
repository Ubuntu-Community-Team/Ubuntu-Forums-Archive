---
title: "Where's Samba config when sharing via GUI"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by Lexus45 on 2011-06-02
Hi all.

I can't understand what Samba config file is used when the shares are created via Ubuntu GUI ?

[LIST]
[*]**/etc/samba/smb.conf** seems to be unchanged
[*]when I do '**ps aux | grep smbd**' - I don't see any parametres either, which indicate to the config files, used by **smbd**
[/LIST]

Best regards, Alexey

---

### Post by dandnsmith on 2011-06-02
If smb.conf is unchanged AND smbd isn't running (nor nmbd), you can safely bet you're not using SAMBA.
You've answered one of my questions - which won't help you.

What other places can you see the files from (eg PCs running Ubuntu, other linux, Windows ...)?

I use SAMBA for sharing files with multiple Windows PCs

---

### Post by capscrew on 2011-06-03
> **Lexus45 said:**
> Hi all.

I can't understand what Samba config file is used when the shares are created via Ubuntu GUI ?

[LIST]
[*]**/etc/samba/smb.conf** seems to be unchanged
[*]when I do '**ps aux | grep smbd**' - I don't see any parametres either, which indicate to the config files, used by **smbd**
[/LIST]

Best regards, Alexey

Answering your questions in the order asked:
[LIST]
[*]The smb.conf file is not used when creating shares with the Nautilus GUI
[*]The parameters are not part of what ps looks at
[*]The shares are located at: /var/lib/samba/usershares
[/LIST]

Nautilus creates these usershare files and stores them where Gnome wants them, not where Samba would put them.

---

### Post by Lexus45 on 2011-06-06
Thanks for help, friends.

---

