---
title: "Networking (file &amp; printer sharing) 3 home computers"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by vchapman on 2010-06-26
I have 3 home computers. Two of them are dual boot Windows and Ubuntu. The third runs only Ubuntu. I want to share files and two printers among the three machines. What is the best approach to doing this.

TIA

---

### Post by matt-fender on 2010-06-26
> **vchapman said:**
> I have 3 home computers. Two of them are dual boot Windows and Ubuntu. The third runs only Ubuntu. I want to share files and two printers among the three machines. What is the best approach to doing this.

TIA

I think Samba does this?

---

### Post by Morbius1 on 2010-06-26
Since you have Windows and Linux in your network it makes sense to use Samba first ( for your file sharing - you can use CUPS for the printers ) . There are two completely different methods of Samba file sharing in Ubuntu but lets try the simplest first. It's called Samba Nautilus-share.

Let's create a very simple guest share on one of your linux boxes:

To use Samba Nautilus-share:
Open Nautilus ( your Home folder )
Right click on a folder you own, like say ... Documents
Select "Sharing Options"
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

Now see if your other machines can access the share. If you've been good all year and the samba gods are happy it will work instantly. If not ...

---

### Post by jrela2000 on 2010-06-26
> **Morbius1 said:**
> Since you have Windows and Linux in your network it makes sense to use Samba first ( for your file sharing - you can use CUPS for the printers ) . There are two completely different methods of Samba file sharing in Ubuntu but lets try the simplest first. It's called Samba Nautilus-share.

Let's create a very simple guest share on one of your linux boxes:

To use Samba Nautilus-share:
Open Nautilus ( your Home folder )
Right click on a folder you own, like say ... Documents
Select "Sharing Options"
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

Now see if your other machines can access the share. If you've been good all year and the samba gods are happy it will work instantly. If not ...


Those Gods are not happy with me.

When I hit "Modify Share" a window pops up and says that Natilus needs to change permissions for the folder.  I agree to it, but then I look at the permissions, they are unchanged and I can't change them manually.  The permissions for other people instantly change back.

---

### Post by Morbius1 on 2010-06-26
**vchapman, **My apologies. Had I been smart enough to read the complete heading of this thread I would have clearly noted that you are using lubuntu. As there is no Nautilus in lubuntu then what I wrote was useless. I don't know if there is a Nautilus-share equivalent in lubuntu. I would suggest that you install the following package:
> system-config-samba**jrela2000**, you might want to start your own thread. What you are describing sounds like you are trying to share a partition that is formatted in FAT32 or NTFS. It will work but linux can't change the permissions on a windows filesystem. The quickest way to fix this is to add a line to your smb.conf file:

From a Terminal:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
force user = morbius
```*[COLOR=Blue]Change morbius to your own login user name.[/COLOR]*
Save the file, exit gedit, and back in the terminal type:
```
sudo service smbd restart
```If that doesn't fix it for you then please start your own post. We are both guilty of hijacking this thread.:wink:

---

