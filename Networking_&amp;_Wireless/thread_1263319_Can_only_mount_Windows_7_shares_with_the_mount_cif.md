---
title: "Can only mount Windows 7 shares with the mount cifs command"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by scottfreeze on 2009-09-10
Hi all,

I have been searching all over the forums for the answer to this question, and I'm still perplexed.  Here's my situation.  I'm trying to mount a password-protected windows 7 share from Jaunty.  I've followed all the suggestions here:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Despite making all those changes, I cannot connect to the Windows 7 share in any of the following ways:
1.  SMB4K browser doesn't work - the Windows PC is visible in my workgroup but no shares show up when I click it.

2.  SMB4K "mount manually" doesn't work with using either the computer name or the IP address - in both cases gives message "mount error(13):  Permission denied".

3.  Trying to browse Places - Network - Workgroup doesn't work either... again, the Windows PC is visible, but when I double click it I get a username/domain/password dialog box that does not accept any username/domain/password combination (including the username and password that end up working in the mount cifs method below).  The password dialog just keeps popping back up.

4.  Using Places - Connect to Server does not work using either the computer name or the IP address.  Same result as number 3... doesn't accept User/domain/pass combinations.

The only thing that works for me is to use the Terminal and run the following command:
sudo mount -t cifs //computer_name/server /home/username/share -o username=xxxx,password=xxxxx,iocharset=utf8,file_mode=0777,dir_mode=0777

One last piece of info (in case it's relevant) - I can connect with no problems to a non-password protected Windows XP share by any of the above methods, so it's something specific to either needing a password or Windows 7.

My question is quite simply... why do none of the other methods to mount/browse the Windows 7 file share work, but the CIFS method does?  And what do I need to do to get the GUI based methods to work?

Sorry for the long post, thanks for the help!
Freeze

---

### Post by agro666 on 2009-11-02
This is exactly the same issue I have now.  I can mount with the CIFS method, but smbclient, smbmount or Places -> Network   doesn't work.

Did you get a resolution?  Thanks!

---

