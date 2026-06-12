---
title: "Cannot log into Ubuntu box from XPpro"
date: 2006-05-28
forum: Networking &amp; Wireless
---

### Post by smoothunit on 2006-05-28
Hi,
Hoping someone can shed me a little light on a problem im having regarding my network settings, specifically getting my xp box to browse my shared file in Ubuntu.

I've installed samba and set up a share OK.
I've also mapped my windows shared folder to Ubuntu (works a treat).
I can Ping both machines from Ubuntu and XP.

My XP machine can view my Ubuntu network place workgroup, but here lies the problem.
After many searches on this forum and others, I am still yet to be able to log into the ubuntu (from XP) after entering the correct credentials. 
ie. smoothunit \home\smoothunit\shares 

I've read in this forum that you both xp and ubuntu should share the same user name, or by changing the SMB user name to correspond with my xp box (currently Administrator), would this help and if so how would i go about doing so.

Your help on this topic would be greatly appreciated and i look forward to your answers.

Thanks again,

Alex.

---

### Post by Irony on 2006-05-28
Your smb username will be whatever username you log onto ubuntu with - for example my username is irony so that is also my smb username.

However you have to set up an smb password for each username;

[PHP]sudo smbpasswd -a username

sudo /etc/init.d/samba restart[/PHP]

When you go to Network Places you should see the link to your shared folder. Click on it and sign on with your username and smb password. You will also see your home folder. If you don't want to see your home folder then make another user for your ubuntu machine (even if you are the only actual user for your machine you will thus end up with 2 logins) and set a smb password for that user.

When you sign on with the other user you will see the shared folder (assuming it has the necessary permissions) and the home folder of the other user (there won't be anything in it though).

If you can't see the shared folder in Network Places click the folder icon to see the tree view on the left and navigate to microsoft network client (something like that) and see if its there - if so put a shortcut to it.

If you still can't see anything perhaps your XP firewall software needs to be configured to allow your home network.

---

### Post by smoothunit on 2006-05-29
Sorry I took soo long to get back.

All i can say is thankyou.

followed the above commands and presto, first go.
after 2 days of post trawling an trying the above in no specific order
all seems to be fine.

thanks again,

Now if only i could return the favour...........

---

