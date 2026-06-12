---
title: "Rhythmbox won't import/load new tracks"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by AVH on 2008-04-04
Rhythmbox will not import new files or folders into the library,nor will it update the library to include files and folders added to the folder pointed to in Edit>Preferences>Music>Library location.

The library folder is located on the windows partition of a dual boot system, but that didn't stop it from loading the contents of this folder the first time it was pointed at it.

Attempts to import or update the library after the first time result in "Import Errors" saying the "stream is in the wrong format". All these formats were present in the folder the first time the library was created. 

Removing and re-installing Rhythmbox had no results: the original library contents showed up unchanged. Apparently, removing Rhythmbox did not remove the data base it created.

Any suggestions to get this working, anyone?

Thanks

Alan

---

### Post by Glaxed on 2008-04-09
bump, same issue on hardy

---

### Post by Glaxed on 2008-04-11
Allright, I have a fix, but it's crappy. Just saying :D.
Ok, so, create a new file and name it '**.rblaunch.sh**'.
Edit it, and write;
```

#!/bin/bash
# Please make sure to specify the correct partition to unmount/mount. Not always /dev/sda3
sudo umount /dev/sda3
echo "umount /dev/sda3"
mkdir /home/$USER/Music
sudo mount /dev/sda3 /home/$USER/Music
echo "mount /dev/sda3 /home/$USER/Music"
echo "gksudo rhythmbox"
gksudo rhythmbox
exit

```
Close the file. It should disappear at some point, that's allright, press **Ctl+H**. Now move this file to /home/$USER.
Now, open a terminal and execute;
```
$ chmod +x /home/$USER/.rblaunch.sh
```
Now, go to System-->Preferences-->Main Menu and go to Sound/Video.
Right click on Rythmbox, and pick properties.
Under command, write
> gksudo /home/$USER/.rblaunch.sh.
Now, I use gksudo so that you wont have to open this script via terminal.
I know you should avoid using gksudo with CLI applications, but it needs to be done (if there's a better way, I'd like to know about it.)
Now, run rhythmbox from the applications menu, and it should come up with root preferences (i.e none of your settings are carried over).
So specify the music folder where you mounted it, and enjoy.

---

### Post by AVH on 2008-04-11
Galxed:
Didn't work for me. Rhythmbox failed to launch at all. Not sure where I went wrong. The only change  I made was from "/dev/sda3" to "/media/sda1"  for my windows partition.

thanks
avh

---

### Post by Glaxed on 2008-04-12
**Edit: If it is under /media/x, im pretty sure its already mounted. If you have not done this, Ubuntu did. So have you tried directing Rhythmbox to load tracks from /media/sda1/home/$USER/Music? You'd need root access (perhaps necessitating a shell script, but it should work. Or you could try these steps ->.**

Sorry to doubt you, but can you post your .rblaunch.sh content?
If you're sure you've done the other steps correctly, I advise you to unmount /media/sda1, and mount it yourself. My script was supposed to do that...
Normally, Ubuntu mounts partitions in /media/disk-x..
So try
```

$ sudo umount /dev/sda1
$ sudo mount /dev/sda1 /home/$USER/Music
# or
$ sudo umount /media/sda1
$ sudo mount /media/sda1 /home/$USER/Music

```
Failing that, try and replace $USER in the script with your username. $USER is a Bash variable, so it should work, but still.

If nothing works, open a terminal, run the script, and post the output.
Oh, and check if there is a spelling mistake in the Main Menu - Launcher.

Sorry, and good luck.
You might just try Amarok, but I'm trying to stay only on GNOME libraries myself.

---

### Post by AVH on 2008-04-13
Sorry for the delay , long weekend.

Here's my.rblaunch.sh file

```
#!/bin/bash
# Please make sure to specify the correct partition to unmount/mount. Not always /dev/sda3
#sudo umount  /dev/sda3
#echo "umount /dev/sda3"
sudo umount /media/sda1
echo "umount /media/sda1"
mkdir /home/$USER/Music
#sudo mount /dev/sda3 /home/$USER/Music
#echo "mount /dev/sda3 /home/$USER/Music"
sudo mount /media/sda1/home/$USER/Music
echo "mount /media/sda1/home/$USER/Music"
echo "gksudo rhythmbox"
gksudo rhythmbox
exit
```

When I try to start from the menu nothing happens. But, when I run from the terminal it launches, but with no library. This is the output of "gksudo /home/$USER/.rblaunch.sh"

> alan@alan-u-livingroom:~$ gksudo /home/$USER/.rblaunch.sh
umount /media/sda1
mount /media/sda1/home/root/Music
gksudo rhythmbox
mount: can't find /media/sda1/home/root/Music in /etc/fstab or /etc/mtab
ory

(rhythmbox:5905): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(rhythmbox:5905): Rhythmbox-WARNING **: couldn't connect to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(rhythmbox:5905): Rhythmbox-WARNING **: Couldn't connect to system bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.



When I then try to point to the Windows music folder in preferences it only loads part of the contents with the "stream is in the wrong format" error message for the rest.

So now I have two incomplete libraries. Is there any way to wipe them out and start over?

avh

---

### Post by Glaxed on 2008-04-15
Crap.
No, don't start over... In my other post I mentioned that as you are using sudo (superuser do), all of your root preferences (your root account library etc) is used, which is non-existant... If you keep using it as root though, your preferences will be saved.
Because of this sudo/root mess, the $USER variable is throwing Rhythmbox off too.
You set your library somewhere under your home directory right?
using ```
$ sudo echo $USER
``` in a terminal wont show your username, it'll show 'root'.
This is my mistake.
I didn't know your username, so I assumed it would be allright to use $USER. Please replace it everywhere you used it with your real username. 
On the "stream is in the wrong format" error message, try installing ubuntu-restricted-extras and or more Gstreamer packages.
Post any problems you have.
- Sorry again.

---

