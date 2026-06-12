---
title: "My Password fails when trying to access shared folders"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Indubitableness on 2008-12-06
Hey guys. I ran into a problem that I can't find any answers to on google.
I am running two machines with ubuntu, my computer is purely ubuntu, and my sister's computer is an XP/Ubuntu dual boot. Both running hardy.

 I have a problem with shared folders, everytime i try to access shared folders on my machine from my sister's computer it asks me for my password and fails when i type it in. I know it's the right password, i use it all the time, so i'm not sure why it's happening, but when i access shared folders on my sister's computer from my own, it works every time.

  I'm not sure why this is, it doesn't matter if her computer is running in XP or in ubuntu, i can access my folders just fine from my own machine, and like i said, i'm only running ubuntu on my machine (because F windows, that's why) and it just refuses to acknowledge that my password is correct.

 I don't even know where to begin looking for a solution to this, if anyone knows what's going on, let me know.

 a little more information, i'm accessing my shares (or trying to) using nautilus and the "smb://192...." (after installing samba)

 Using my IP address is the only way i've been able to get these computers to talk to each other, and even though rebecca's IP address jumps around from time to time, it's worked well enough for me so far.

 Is there maybe a different, linux specific protocol i should be using? or does it even matter?


  Thanks in advance for any help guys.

---

### Post by ktrnka on 2008-12-06
From the sound of it, it seems that you have not added your (linux) user to samba. You can add it and set your samba password like so:

```
sudo smbpasswd -a USERNAME
```

It will then prompt you to create a password.

Also, could you please post your /etc/samba/smb.conf file for further help if the above does not work.

---

### Post by superprash2003 on 2008-12-06
after creating the samba user mentioned above , you need to add it to the /etc/samba/smbusers file . For reference Step 5 [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by LeadFingers on 2008-12-07
If you want you can set the sharing options so you don't need a password.
In the sharing options check Guest access.

---

