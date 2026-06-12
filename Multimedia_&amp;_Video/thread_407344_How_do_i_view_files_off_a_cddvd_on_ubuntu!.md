---
title: "How do i view files off a cd/dvd on ubuntu!"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by hydroxph on 2007-04-12
I have a dvd data disc that contains music and i cant seem to view any of the files on the disc through ubuntu! does anyone know how or know a program that lets u?

[IMG]http://i29.photobucket.com/albums/c291/hydroxph/GIFZ/Screenshot.png[/IMG]

---

### Post by Jonam on 2007-04-12
Simply right click on the DVD icon on your desktop and select "Browse Folder" from the menu.

Jonam

---

### Post by hydroxph on 2007-04-12
i did that and it opens up that menu.

---

### Post by RomeReactor on 2007-04-12
Hi. If it opens in the Nautilus burning application, the disc is being recognized as blank. Are you sure it contains data?

---

### Post by hydroxph on 2007-04-12
yes im sure it has data,

---

### Post by RomeReactor on 2007-04-12
With the DVD is in the drive try navigating to it on the terminal:

```
cd /media

ls
```

change to the media **ls** lists; probably **cdrom**, and see if it shows the files.

---

### Post by hydroxph on 2007-04-13
[IMG]http://i29.photobucket.com/albums/c291/hydroxph/GIFZ/Screensho2t.png[/IMG]

---

### Post by RomeReactor on 2007-04-13
Once you're in the **media** folder, type **ls** again to list its contents. If nothing comes up, then the system is unable to read any information contained within. If you can, check the disc on another computer.

---

### Post by Jonam on 2007-04-13
Just a guess - do you have the dvd libraries installed - libdvdnav4 and libdvdread3 along with libdvdcss2? Check Synaptic package manager if you are unsure.

Jonam

---

### Post by hydroxph on 2007-04-13
yea i installed them and i still cant view the files on the cd, i can veiw the files on the cd on windows.

---

### Post by eggdeng on 2007-04-13
I think RomeReactor didn't quite finish explaining, so perhaps it would be an idea to go through it again. Start with 

```
cd /media/cdrom0
```

then

```
ls -a
```

If you get nothing, substitute cdrom1 for cdrom0 and repeat. Is it just this DVD you can't read, all DVDs or DVDs & CDs?

---

### Post by hydroxph on 2007-04-14
yea i can read cds but not dvds, :(

---

### Post by eggdeng on 2007-04-14
Try putting a CD in the drive and then type the command ```
mount
``` in a terminal. This will tell you which devices are mounted and to which folders. You should see a line something like this
```
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=eggdeng)
```
In my case, this means my DVD device is /dev/hda and the dvd is mounted to the /media/cdrom0 folder. 
Now try the same with a DVD and post the results for both attempts.

---

### Post by hydroxph on 2007-04-14
```
hydroxph@hydroxph-desktop:~$ /dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=hydroxph)
bash: syntax error near unexpected token `('
hydroxph@hydroxph-desktop:~$ 

```

---

### Post by Jonam on 2007-04-15
You might want to look at the system log by typing:

dmesg | tail

to see if there are any problems with the DVD drive. Post the output.

I have had issues reading DVDs when I have had the DVD-RW and a CD-RW drive on the same IDE bus. With one configuration, I was not able to see the DVDs and have had to revert to using a particular setup to allow me to use both drives, the penalty being burning speed on the DVD-RW.

Jonam

---

### Post by ronocdh on 2007-04-15
Perhaps this is a mounting issue, but I assume OP is able to read CDs via the same physical drive as the DVDs (s)he's trying to mount. Could it be a format issue? As a data disc, it could be formatted to something weird... e.g., recently in OS X I burned a data disc as HFS+ and it couldn't be read on Windows.

Although Linux has read of NTFS by default. =( Still, any chance it's due to formatting?? How was it burned?

---

### Post by eggdeng on 2007-04-15
> **hydroxph said:**
> ```
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=hydroxph)
bash: syntax error near unexpected token `('

```

I'm guessing, but the syntax error referred to might be in your /etc/fstab. In particular the line which refers to the dvd device (hda) should read 
```
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Sure you have tried 
```
ls -a /media/cdrom0
```

If that gives no output, try

```
sudo mount /dev/hda /media/cdrom0
```

and then the previous command again.

---

### Post by hydroxph on 2007-04-15
> **ronocdh said:**
> Perhaps this is a mounting issue, but I assume OP is able to read CDs via the same physical drive as the DVDs (s)he's trying to mount. Could it be a format issue? As a data disc, it could be formatted to something weird... e.g., recently in OS X I burned a data disc as HFS+ and it couldn't be read on Windows.

Although Linux has read of NTFS by default. =( Still, any chance it's due to formatting?? How was it burned?

[COLOR="Green"]it was burned on windows with nero! it is ntfs format, i guess i cant read dvd datas on ubuntu..[/COLOR]


> **eggdeng said:**
> I'm guessing, but the syntax error referred to might be in your /etc/fstab. In particular the line which refers to the dvd device (hda) should read 
```
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Sure you have tried 
```
ls -a /media/cdrom0
```

If that gives no output, try

```
sudo mount /dev/hda /media/cdrom0
```

and then the previous command again.

[COLOR="Green"]still nothing [/COLOR]:(

---

### Post by Jonam on 2007-04-15
I am wondering whether Nero closed the session when the DVD was burnt. I have had instances with data CDs (containing photos) that were created in Windows in which the session was not closed and only Windows could read the disc. Inserting the disc into a multi-format DVD player to view the photos would result in the disc appearing empty or unreadable.

Can Linux read other DVDs or is this problem only with the one you have burnt? Are you able to burn another in Nero to find out if Nero is closing the session properly?

Jonam

---

### Post by hydroxph on 2007-04-15
it does this will all my dvds that i burnt. and they work on windows :(

---

### Post by Jonam on 2007-04-15
Check that Nero is closing the session on these disks. Also see what happens if you burn a DVD in Linux and then try and read it.

Have you tried reading/ playing any commercial (ie movie) disks in Ubuntu?

Jonam

---

### Post by hydroxph on 2007-04-16
i dotn have a dvd burning on my pc that is running ubuntu

---

### Post by Jonam on 2007-04-17
OK. Then you still have a couple of options:

1. Boot your Windows machine off an Ubuntu Live CD and see if you can read the DVDs you made in Windows. This will at least let you know if Ubuntu or Nero is the problem or the hardware in your Ubuntu machine.

2. As said previously, try inserting a standard DVD movie disk in your Ubuntu machine and see if you can read the files on the disk. This will either confirm Nero is the problem or something in the Ubuntu machine.

3. Boot the Ubuntu machine with a Live CD and then try reading DVD disks. This should let you know if something is wrong with the Ubuntu installation on the hard disk of your Ubuntu machine.

I can't really think of much else so I hope that the above helps you find the problem.

Jonam

---

### Post by hydroxph on 2007-04-24
yea i guess its the burning session on nero cuz i tried a dvd video the other day and it worked perfectly.

---

