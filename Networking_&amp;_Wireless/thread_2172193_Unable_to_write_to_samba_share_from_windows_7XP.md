---
title: "Unable to write to samba share from windows 7/XP"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by biggyk on 2013-09-03
Testing a samba share that I set up on my Server 12.04 box. I can see it and open it on the windows machines but when I tried to drag and drop a txt file in the folder it said I do not have permisson. Being on a home network, im not worried about logins so I made it public.
The purpose of setting up a share is to transfer movies I have converted and place them in the folder that mediatomb or Plex will be using.

I know im so close but cant figure this out. Anyways heres what i put it the smb.conf

[Share]
   comment = test share
   path = /home/share
   read only = no
   browseable = yes
   guest ok = yes
   create mask = 0755

is there an issue with using the home folder? Eventually when im ready the real share folder I want to use will be on another drive. Im just trying to teach myself before hand.

Thanks

---

### Post by Morbius1 on 2013-09-03
This is the 3rd plex topic in as many days - if I only knew what plex was I might be better at answering this question.
> [Share]
   comment = test share
   path = /home/share
   read only = no
   browseable = yes
   guest ok = yes
   create mask = 0755
What are the permissions of the target folder:
```
ls -dl /home/share
```
You have a share that allows write by anyone but samba cannot override Linux permissions on the shared folder itself.

If you just created the folder and then shared it the permissions might be something like this:
> drwxr-xr-x
The only person who has write access is the owner of the directory and it's probably root so the guest will never gain write access.

One way is to change permissions to drwxrwxrwx by doing this:
```
sudo chmod 777 /home/share
```

---

### Post by biggyk on 2013-09-03
Plex is a upnp media server/client application that is similar to mediatomb, ps3 media server, windows media sharing ect.



Also, before I set it to guest ok, when I used the windows machine it would ask me for my login but the domain was my windows computer name (Mike-PC)  so it would never log me in. Do you know why it does that?

---

