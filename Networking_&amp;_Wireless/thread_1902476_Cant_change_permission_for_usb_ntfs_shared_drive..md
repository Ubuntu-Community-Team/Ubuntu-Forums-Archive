---
title: "Cant change permission for usb ntfs shared drive."
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by darksniperx on 2011-12-30
Hi,

I have used:

```
sudo gedit /etc/fstab
```

and added the following line:

```
UUID=B9709709D876CB78 /media/windows ntfs-3g auto,uid=1000,gid=1000,umask=0022 0 0
```

I dont remember the line i have used to get the uuid.

Then went to /media folder and shared windows folder, but in permission for that folder, under others, it wont let me change folder access from "Access Files" to "Create and Delete Files"

In order for me to access the shared folder on windows machine i had to restart ubuntu computer otherwise i had permission error.

After restart when i wont to see /media/windows the folder did not have the 2 arrows showing that the folder was shared.

How can i find setting that indicate that my /media/windows folder is shared as backup ( since that is how i named in sharing setting ) and add permission to other for delete and create folder and files.

Thank you!

---

### Post by darksniperx on 2012-01-01
Anyone,

Did i do something wrong with fstab? Just need the change the permission for others, from read only to full.

---

### Post by Morbius1 on 2012-01-01
[1] Unmount the partition:
```
sudo umount /media/windows
```[2] Change **umask=0022** to [COLOR=Blue]**umask=0000**[/COLOR] in fstab:
```
 UUID=B9709709D876CB78 /media/windows ntfs-3g auto,uid=1000,gid=1000,umask=0000 0 0
```[3] Save fstab and run the following command to test for errors and mount the partition without requiring a reboot:
```
sudo mount -a
```Note: a "2" in umask turns off write. A "0" turns off nothing.

---

### Post by darksniperx on 2012-01-01
Hey,

Thank you very much, the sharing works perfectly now :)

Is there a command or somewhere in ubuntu that i can go to find everything that is being shared at the moment and change settings.

After i restart ubuntu the icon on the shared folder disappears with the indication that the folder is shared.

When I was testing out sharing I shared bunch of folders, but after restart i cant turn off the sharing on those folders, since there is no indication.

Thank you!

---

### Post by Morbius1 on 2012-01-01
You know you've used the term "share" several times in this topic and I'm not sure what you mean by "share"

If you are talking about Samba sharing it depends on how you created the samba share - there are two methods to do that:

[1] Classic Samba shares - have the share in smb.conf and one way to see them all is to run this command:
```
testparm -s
```[2] Samba Usershares - created from Nautilus

You can see all your shares with this command:
```
net usershare info --long
```

---

### Post by darksniperx on 2012-01-01
Here is how i shared the folder.

I right click on the folder, choose "Sharing options" then select "Share this folder", "Allow other to create and delete","Guest Access", then click "Create Share".

```

net usershare info --long

```

Shows my shared folders. How do i edit this info?

---

### Post by Morbius1 on 2012-01-01
> **darksniperx said:**
> Here is how i shared the folder.

I right click on the folder, choose "Sharing options" then select "Share this folder", "Allow other to create and delete","Guest Access", then click "Create Share".

```

net usershare info --long

```Shows my shared folders. How do i edit this info?
The same way you created it - through nautilus.

---

### Post by darksniperx on 2012-01-01
The folders that i shared though nautilus, don't appear shared. If i right click on them and choose sharing options, it is asking me to share them again.

---

### Post by Morbius1 on 2012-01-02
I have never experienced that problem. There was a bug a few versions ago that a shared folders icon would not show it being shared after a reboot but that did not alter the fact that it was still shared.

"net usershare info --long" should always show you the state of all the shares you created through Nautilus. If it shows the folder as being shared and Nautilus doesn't and you want to change how it's shared just share it again through Nautilus.

---

### Post by darksniperx on 2012-01-02
the folders are shared, thats not an issue. 

The issue, is when i would like unshare a folder. I dont have the option to do that.

I can see all of my shared folders with "net usershare info --long" But if i want to undo sharing i cant. If i go to the same folder and share it again, then it will appear appear twice.

---

### Post by Morbius1 on 2012-01-02
If it appears twice in net userhare info then there is something defiantly wrong with your system or with the package that enables you to share it through Nautilus.

* You might want to reinstall the package:
```
sudo apt-get --reinstall install nautilus-share
```
* If that doesn't fix it then the only thing I can think of is that you shared it once as a normal user and again as root. Remove both shares at the source: **/var/lib/samba/usershares**

---

### Post by darksniperx on 2012-01-02
Thank you!

Once i have instantiated your command, the arrows indicating sharing reappeared :) So as the settings in folder :)

The path showed me all of my shares, and i was able to delete all of the broken ones :)

Thank you everyone that helped me to overcome my troubles with sharing nfs drives to windows network :)

---

