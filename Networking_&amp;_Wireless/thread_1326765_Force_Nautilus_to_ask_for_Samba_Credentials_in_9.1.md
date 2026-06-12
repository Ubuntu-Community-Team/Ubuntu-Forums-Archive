---
title: "Force Nautilus to ask for Samba Credentials in 9.10"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by BandD on 2009-11-14
Is there a way to force Nautilus to ask for Samba credentials when trying to access a samba share?  

I have a NAS (Dlink DNS-323) that has several users on it whose files' permissions are all set to be read only by that user.  In Jaunty, when trying to connect to the NAS I was always prompted for a username and password.  But in Karmic I'm not, and thus I'm not able to view the files I need to view.

I haven't been able to find any threads or bug reports that deal specifically with my problem.  I'm not sure if this is a Nautilus problem, a gvfs problem, or a samba problem.  

Any help would be greatly appreciated!

---

### Post by dno on 2009-11-14
There must be a bug, I have a similar type issue with Karmic.  Users try to log onto the NAS and get prompted for the ID & password and then when they enter it, nothing happens but the prompt comes back.  I can ping and log into the administrator via https, but no connection from cifs of smbfs. Other users from winbloze and 8.04 LTS log in with no issues.

---

### Post by BandD on 2009-11-15
@ dno:

I remember having a similar paroblem when trying to connect to my NAS unber 9.04 and was able to trace it down to a depricated version of samba running on the NAS and having to change some setting in my 9.04 smb.conf file (though for the life of me I can't remember what it was nor can I find the thread again!)  But it had something to do with a change in smaba authentication or some such.  The newer version was much more secure, but it wasn't backwards compatible with the older versions.  Sorry I can't be of more help there.

The problem I'm having is a little different.  Nautilus isn't bringing up the prompt for a id or password at all.  It's just signing me in a "guest" I imagine.  So I can access the samba share and files that don't have such restricted permissions.  But some of the files I need to access have very restrictive permissions and I can only read and write to/from them as a specific user.  

I'll try later today to type in the nautilus address bar something like smb://username@ip-address-of-samba-share and see if I can get in as the specified user that way.  But it seems to me that it would be nice to have the option to use a different user than the 9.10 user you are currently logged in as.  Like in Finder in OSX...it defualts as guest, but you can click to specify connecting as a different user.

Still, if anyone knows of a way to force Nautilus to ask for credentials when accessing a samba share EVERY time I would be very greatful!

---

### Post by BandD on 2009-11-15
@ dno:

here's the thread I was talking about in my last post 
[http://ubuntuforums.org/showthread.php?t=873385]("http://ubuntuforums.org/showthread.php?t=873385")

It's a quick edit to your smb.conf file that MIGHT do the trick depending on how old the version of Samba is on your NAS.

---

### Post by dmizer on 2009-11-15
Have you tried mounting the share via /etc/fstab? If you mount in /etc/fstab, this will probably be a permanant fix for you. In /etc/fstab, you can specify the credentials used to log into the share so it will use those credentials every time you connect.

For more information, see the 2nd link in my sig.

---

### Post by BandD on 2009-11-16
It's a share I only occasionally need to connect to (anywhere between 3-10 times a month) via samba.  I do weekly backups via rsync.  Sometimes I just feel like viewing things graphically, but more than that, I like to have more than one way into the NAS (if I insall a new version of Ubuntu for instance, and forget to put the id_rsa file in my new .ssh directory).

I tried out the smb://user@IP-Address-of-NAS and that did the trick.  So I can live with that.  Though I did have to weaken the ubuntu machine's smb.conf authentication as mentioned earlier.  I'm currently looking into updating the samba version on the NAS.

One other oddity is the way Nautilus lists the samba shares on my two laptops.  One laptop has plain old Ubuntu 9.10 installed and the other has Netbook Remix 9.10 installed.  When I click on Network in Nautilus on the NBR machine I see all the samba shares listed in the network:/// directory.  But on the plain Ubuntu machine It lists one of the shares only, then when I click on WORKGROUP I see the remaining shares.  Why would this be?

---

### Post by dno on 2009-11-16
DMIZER.

That did the trick.  Thanks!  I updated my nas, but it didn't seem to matter.  I did try to edit /etc/fstab and I received the same error.  I will reinstall this weekend because I tried so many things to get this working.  See if that makes a difference.

---

