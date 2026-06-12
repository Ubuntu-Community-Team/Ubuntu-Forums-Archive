---
title: "How to tell Transmission to save to a network share?"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by stevefrench88 on 2009-09-26
Hi There, 

I have several network shares setup on my local network. I would like to point Transmission to one of these shares, however it does display these shares in the "Destination folder" menu.

Can anyone help, or at least know if this is possible with Transmission on Ubuntu?

I running Ubuntu 9.04, and Transmission 1.51.

Thanks!

---

### Post by Charles Kerr on 2009-09-27
I don't understand the question?

You can tell Transmission where to save new downloads by specifying a different Destination folder in the dialog that pops up when you add a torrent.  You can also set the default in Edit > Preferences.

If you're wanting to tell Transmission about torrents that you've already downloaded and that are on the network share, you can do that in 1.7x (but not 1.5x) via the "Set Location" menu button.

---

### Post by stevefrench88 on 2009-09-27
I know how to tell transmission to point to where I want it to save the downloaded files. However, I am not able to point it towards my network shares (even though they are mounted).  In the "Destiination Folder" dropdown menu (under Edit > Preferences), I choose "Other". I get the options shown in the attached screen shot.  None of the locations are my network shares. Even if I copy and paste the destination of a network folder into the "Location" bar, it errors with "destination file/folder not found".

I've even tried creating a launcher on my desktop to a folder on my network, but it won't accept the launcher as a destination either.

---

### Post by Rasputin507 on 2010-03-25
The quick and dirty version is as follows:

- Show hidden files by pressing ctrl+h.
- Browse to username/.gvfs, you'll see your network shares listed there.  If you don't see them, then they aren't mounted.  If you don't see .gvfs, and a lot of other .foldername listed, then press ctrl+h.

The above method will need to be performed each time you start Ubuntu.  If there is a particular share that you want to connect to every time, then you can edit /etc/fstab according to the directions provided below.  Thanks to uidb4056 for these.

"You have to edit /etc/fstab as root 
 
Code: 
 
sudo gedit /etc/fstab 
 
and add this line: 
 
Code: 
 
//computername/sharename /home/username/foldertomountname smbfs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 
 
You need also create if not exists or edit the file .smbcredentials 
 
Code: 
 
sudo gedit /root/.smbcredentials 
 
and add two lines as: 
 
username=yourusername 
password=yourpassword 
 
Save it and then test you can mount using from terminal 
 
Code: 
 
sudo mount -a 
 
If it works then you will have mounted every time you boot. For sure there can be another ways but this is running for me."

---

### Post by stevefrench88 on 2010-03-25
Thank you so much!  Navigating to the share through the username/.gvfs worked perfectly!!!

Thanks again!

---

### Post by stevefrench88 on 2010-04-02
An update:

Following the first set of instructions, I am successfully able to point Transmission to my network drive via the home/username/.gvfs folder - however as mentioned, I have to repeat these steps after every reboot.

So I've attempted to permanently mount the drive using the code provided in the second set of instructions, but it doesn't seem to be working for me for some reason.

This is what I've entered into /etc/fstab:
//johns-airport-extreme.local/1.5tb_wd /home/johnadmin/.gvfs smbfs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=077 0 0

I've also edited /root/.smbcredentials using my un&pw for the computer (which is the admin account btw).

When I try to mount the folder via Terminal, (sudo mount -a), I get the following error:
johnadmin@johns-laptop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //johns-airport-extreme.local/1.5tb_wd,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


The filesystem of my network drive is the Mac fs, HFS+.  Is that why I am getting the error?

Thanks again for any assistance!

---

### Post by stevefrench88 on 2010-04-04
Solved my issue, so I'll point out what I was doing wrong here for any other "newbs" like me!

1) I didn't have smbfs installed (sudo apt-get install smbfs)

2) I was was misunderstanding what i should be filling out in this code:

/computername/sharename /home/username/foldertomountname smbfs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 

....so here's a breakdown:

/computername/sharename  = the path to the share you want to mount on startup

/home/username/foldertomountname  = create a new folder ("foldertomountname") in your home      directory (on the system that you want the share to mount in at startup)... i guess some local data is written/stored here for the share you are mounting?

Also, make sure the credentials entered into .smbcredentials are obviously the credentials required (if any) to connect to the share.

With those changes, it is working perfectly now.

---

### Post by manco1911 on 2011-08-09
only if i had come across this thread earlier today.. jeje
thanks for the breakdoen stevefrench88. 

Now the mountpoint is working.. on to the transmission install.. will update. 
Did you have any issues downloading to the network folder? Anything on permissions or the sort?

---

