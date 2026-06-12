---
title: "Connect a laptop with 2 nics using fstab"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by DeMus on 2011-12-07
Hi,
For some time now I have connected my computers in a network using fstab and smb.conf.
In smb.conf I share those partitions/folders of the local computer I want to share (i.e. /home/DeMus), make them browseable, not read-only and writable.
In fstab I mount the shared folders of other computers
(i.e. //192.168.1.111/home /media/home cifs  rw,username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0)

One thing I have to add is this: in my router I use DHCP but with reservations regarding the addresses. I have connected the mac address of a network-card to a fixed IP-address in the router. So when a computer boots, the mac address is send to the router, looked up in a list and the connected IP-address is used for that computer. Always the same address, which makes it easy to use the mount point in fstab, plus the computers themselves still use DHCP.

So far it has always worked.

Now I also have a laptop with a wired and a wireless connection. The wired connection gets .122, the wireless connection always gets .123 at the end of the address.

Now in the other computers I wrote 2 lines in the fstab file for each shared folder in the new laptop:
//192.168.1.122/home /media/home cifs rw,username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0
//192.168.1.123/home /media/home cifs rw,username=guest,password=,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0

Although this works, I still believe there should be a neater way of doing this. I use the laptop both wired and wireless so it can use both addresses alternatively.

Who can help me with this?

---

### Post by dmizer on 2011-12-08
I think perhaps this is what you're looking for: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by DeMus on 2011-12-08
> **dmizer said:**
> I think perhaps this is what you're looking for: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Thanks for your answer, but I guess you need to be some kind of computer-wiz to understand that all. Isn't there an easier way to explain this? Your signature holds some interesting links which I saved. Will read those first.
Thanks again.

---

### Post by dmizer on 2011-12-09
It's really not so hard as it looks. After installing autofs, you should be able to get your mounts to work with the following configurations.

1) Configure your master map file in /etc/auto.master by adding a line at the end of the file like so:
```
/media/home /etc/auto.cifs
```
2) Configure your map file in /etc/auto.cifs like so (you'll have to create this file):
```
wired -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8 ://192.168.1.122/home
wireless -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8 ://192.168.1.123/home
```
3) Restart autofs
```
sudo /etc/init.d/autofs restart
```
Now you should be able to browse to /media/home/wired and the share should appear if your laptop is wired, or /media/home/wireless if you laptop is wireless. You may or may not have to create the /media/home/wired and /media/home/wireless directories.

---

### Post by DeMus on 2011-12-09
> **dmizer said:**
> It's really not so hard as it looks. After installing autofs, you should be able to get your mounts to work with the following configurations.

1) Configure your master map file in /etc/auto.master by adding a line at the end of the file like so:
```
/media/home /etc/auto.cifs
```
2) Configure your map file in /etc/auto.cifs like so (you'll have to create this file):
```
wired -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8 ://192.168.1.122/home
wireless -fstype=cifs,rw,username=guest,password=,uid=1000,iocharset=utf8 ://192.168.1.123/home
```
3) Restart autofs
```
sudo /etc/init.d/autofs restart
```
Now you should be able to browse to /media/home/wired and the share should appear if your laptop is wired, or /media/home/wireless if you laptop is wireless. You may or may not have to create the /media/home/wired and /media/home/wireless directories.

Thank you very much for your explanation. I do have a question though:
I do not quite understand which folder I put in the auto.master and the auto.cifs file. When and where do I use the local foldername and where the shared foldername?
Do I still use smb.conf to share folders?

Let's take my example:
Computer A (laptop with 2 nics):
shared folder 1 = /home/DeMus (in smb.conf shared as Home-DeMus)
shared folder 2 = /home/DeMus/Video (in smb.conf shared as Video

Mountpoint in computer B (desktop):
/home/DeMus/shares/Home-DeMus
/home/DeMus/shares/Video

What do I put in which file?

Once again thank you very much for your help. I really appreciate it.

---

### Post by redmk2 on 2011-12-09
There is another method to auto mount Samba shares.  This is with the package Gigolo.  Using Gigolo you can browse and/or bookmark your shares.  There is no need to have them listed in fstab at all.

Gigolo uses the GVFS libs (Gnome) without the need for the entire Gnome desktop.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.uvena.de/gigolo/index.html") and [**_[COLOR="Blue"]here[/COLOR]_**]("https://www.google.com/search?q=gigolo+site%3Aubuntufrums.org&btnG=Go!#sclient=psy-ab&hl=en&source=hp&q=gigolo+site:ubuntuforums.org&pbx=1&oq=gigolo+site:ubuntuforums.org&aq=f&aqi=&aql=&gs_sm=e&gs_upl=7979l7979l0l10642l1l1l0l0l0l0l284l284l2-1l1l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=5e3d974d25606803&biw=1146&bih=636") for more info.  I have this installed and it works perfectly.  I can see the shares and have bookmarked them.  All with no entries in fstab.

Edit: This means NO autofs is needed.

Edit2: Here is [**_[COLOR="Blue"]a posting[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1887469") that mentions automating the start of Gigolo.

---

### Post by DeMus on 2011-12-09
> **redmk2 said:**
> There is another method to auto mount Samba shares.  This is with the package Gigolo.  Using Gigolo you can browse and/or bookmark your shares.  There is no need to have them listed in fstab at all.

Gigolo uses the GVFS libs (Gnome) without the need for the entire Gnome desktop.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.uvena.de/gigolo/index.html") and [**_[COLOR="Blue"]here[/COLOR]_**]("https://www.google.com/search?q=gigolo+site%3Aubuntufrums.org&btnG=Go!#sclient=psy-ab&hl=en&source=hp&q=gigolo+site:ubuntuforums.org&pbx=1&oq=gigolo+site:ubuntuforums.org&aq=f&aqi=&aql=&gs_sm=e&gs_upl=7979l7979l0l10642l1l1l0l0l0l0l284l284l2-1l1l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=5e3d974d25606803&biw=1146&bih=636") for more info.  I have this installed and it works perfectly.  I can see the shares and have bookmarked them.  All with no entries in fstab.

Edit: This means NO autofs is needed.

Edit2: Here is [**_[COLOR="Blue"]a posting[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1887469") that mentions automating the start of Gigolo.

Hello redmk2,
Thank you for your answer. I looked at it and on one PC I installed the Gigolo (funny name btw), set it up and made contact with the other computer.
I then setup bookmarks (although they are called Entries in Dolphin filemanager) so I can reach them very easily. It was then that I thought do I need Gigolo? In the other PC I added the same entries in Dolphin and also without Gigolo there I could simply open the shared folders.
In both computers I do still have some entries in the smb.conf files to share the folders.
I think my problem is solved now. As said it started with your idea to use Gigolo so thank you for that.

---

### Post by DeMus on 2011-12-09
dmizer,

it took me a while but I've got it. I first couldn't get it to work and tried some other things. Then I looked in your explanation again and tried this and that. But still it didn't work. Until I saw something in the auto.master file.
You wrote I had to place a line at the end of the file, but it turns out there is some kind of eof line placed there. I didn't see that and place my line below that, placing it outside the file. When I saw what I had done it was fast and easy.
So, thank you very much for your help. I really learned something today.

---

