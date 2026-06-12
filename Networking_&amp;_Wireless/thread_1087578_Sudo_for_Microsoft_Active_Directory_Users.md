---
title: "Sudo for Microsoft Active Directory Users"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by khanhnq2984 on 2009-03-05
Hi all,
I'm newbie.
I have a problem with Ubuntu 8.10: When I joined Ubuntu to Microsoft AD by likewise-open, the user domain can't use sudo -i command. It's notice: "DOMAIN\user is not in the sudoers file. This incident will be reported".
I used vi to insert a row "DOMAIN\user ALL=(ALL) ALL" to the sudoers file. But it not run.
Plz help me!
Thanks alot!:)

---

### Post by Yashiro on 2009-03-05
Replace DOMAIN\user with your name, and use visudo to edit the sudoers file maybe?

I believe someone else had this problem this week. Do a search.

---

### Post by khanhnq2984 on 2009-03-05
I want some domain user can use [COLOR="Red"]sudo[/COLOR] command.
And I used visudo to edit the sudoers file, but when I inserted command
**DOMAIN\User01 ALL=(ALL)ALL** to add domain user User01 in the suders file. The user User01 still can't use sudo -i command. Any body show me how-to?
Anyway, thank Yashiro alot :)

---

### Post by Yashiro on 2009-03-05
Try just the account name without domain\ attached?
Or make a real account on the machine with the same name?

I can't help a great deal as I don't have my old network around to test.

---

### Post by khanhnq2984 on 2009-03-06
Thanks Yashiro
I'm sorry, I show you what i want:
I have a acount user01, this account can't use sudo command.
If I want to use sudo command, I must use the other account (user02)
But when I'm using user01, I want to use sodu command but I don't want to logoff then logon by user02.
How can I do? Can you show me the how-to? Thanks alot :)

---

### Post by Yashiro on 2009-03-07
You just log in as the other user.

Use 'su' not sudo. *su - otheruser*
Then you can use sudo from that account.

---

### Post by khanhnq2984 on 2009-03-08
Thanks you very much Yashiro! I'm done :)

---

### Post by Yashiro on 2009-03-09
:)

---

