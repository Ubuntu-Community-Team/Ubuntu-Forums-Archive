---
title: "Multimedia/USB Permissions Solution"
date: 2010-09-10
forum: Multimedia Software
---

### Post by Luxx on 2010-09-10
I have had considerable problems with getting my computer to recognize my USB drive and my CD/DVD ROM drive. I have tried every possible solution I could find and finally found one SIMPLE solution that actually worked. I thought perhaps sharing this would save someone the 2 years of grief I have been having with both of these issues.

For some reason Windows changed the permissions on my USB drives EVERY time I used them in a Windows computer. That's just not playing nice, and in my predjudice I like to imagine it may be by design. The only way I could fix this was to format the USB drives in Windows. Ouch. Sorry, I know that's not the best news, and it hasn't happened that way for everyone.

What got the USB drive and the CD/DVD ROM to be consistently usable in Ubuntu was to enter them in fstab, pointing USB to mnt folder instead of media folder to avoid confusion:

Open fstab in Terminal (Applications, Accessories, Terminal)```
gksudo gedit /etc/fstab
```
Then add the drives to the bottom of the file```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sr0       /mnt/usbfloppy   udf,iso9660 user,noauto,exec,utf8 0       0
```Save and close.

Go back to Terminal. To allow permissions, change the mode of the mount points:
```
sudo chmod 777 /media
```
```
sudo chmod 777 /mnt
```

(777 is the code for read, write and delete for all users as opposed to the usual default code 755 which restricts permissions to read only except root.)

---

