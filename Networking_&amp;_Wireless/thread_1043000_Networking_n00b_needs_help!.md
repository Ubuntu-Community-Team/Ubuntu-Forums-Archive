---
title: "Networking n00b needs help!"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by Neodude112320 on 2009-01-18
Right,I Have 2 Computers (Laptop,Desktop).Now my desktop is running XP Pro SP3 and my Laptop is running Ubuntu 8.10.

Now i want to be able to files and my printer from my desktop to my laptop.Now i have *NO* Idea how to do this,They both connect wirelessly to my router,and i can ping them both no problems.

Any help would be GREAT!

---

### Post by theozzlives on 2009-01-18
```
sudo apt-get install samba
```
```
gksudo gedit /etc/samba/smb.conf
```
Look for the line that says workgroup=WORKGROUP and change the one in caps to your Windows workgroup name.Save & exit.
```
sudo /etc/init.d/samba restart
```
setup your shares in Windows and Ubuntu.

---

### Post by Neodude112320 on 2009-01-18
Done!

Now,How do i setup shares :)

---

### Post by theozzlives on 2009-01-18
in Ubuntu, right-click on a folder you want to share and go to sharing options. In Windows, right click on the folder (or the whole drive) and go to sharing/security (make sure you have file/print sharing enabled in Windows).

Ubuntu you can access the shares by going to Places>Network. In Windows it's My Network Places.

On both, just right click on your printer and go to share.

---

### Post by Neodude112320 on 2009-01-18
Excellent! It Works...

...Kinda



I Can acsess my shares on my windows machine no problem and transfeer files into my shares through that,but my laptop doesnt see my windows machine at all? It's in the correct Workgroup and i have checked everything....


Any Suggestions?

---

### Post by Iowan on 2009-01-18
Not a permanent fix, but...> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

