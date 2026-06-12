---
title: "Permanent mount of windows shares"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by SteveHillier on 2011-08-26
I want to take nothing away from the good people who have put up threads on this topic before.  They have done good work and it has been very helpful.
I do however want to put up a few ideas that I used to overcome problems I found.

Coming as I have from a world of Windows (started with MS-DOS in 1983) there is a foreign concept of a 'mount point'.  (Indeed the concept of needing to logically mount disks was lost in Windows World and only dimly remembered from my RSX-11M days.  Windows does this for you but just doesn't say anything about it.)
There is really nothing difficult about this but the terminology is new to recent migrants from Windows.
**For our current purpose simply create a new folder (directory) somewhere convenient to you** and give it name that means something to you.
I created a folder called 'common' under my home documents directory using the gui.  So I now have a folder called /home/%username%/Documents/common.  You can create this folder anywhere you like but as a Windows user you are used to 'My Computer', 'My Documents' etc so put it somewhere easy for you.
Create as many of these as you need - one for each share you want to link to.

Now - following the work of others I now edit the fstab file
```
sudo gedit /etc/fstab
```
I entered a line 
```
//192.168.0.200/Common  /home/%username%/Documents/common  smbfs  uid=%username%,credentials=/home/%username%/fred
```
First the server name.  I have used the IP of my server because I have an unresolved issue with my local DNS but you should be able to type in the name of your server itself.
Next I have put in the sharename respecting the case of the letters in the name.  [Windows doesn't care - Linux does!]

Next the mount point.  As I said earlier this is simply the full path of the folder I created in my Documents folder.  Again respect the case of the path.

The file system.  I suppose I should specify cifs but this is where I am at this moment.  It doesn't seem to matter much as the volumes are mounted with cifs anyway - just would be tidier the proper way (and of course it might matter more in the future).

The user id.  Ultimately I will change this to be group id but again this where I am at the moment and on a machine that is going to used by the same person each time that is not a problem.  My machine will have other users able to log on later on so the group id is the better solution.

Finally the credentials file.  Boy, did I have big problems here.  Having resolved mount point issues I had a run of 'Credentials File is corrupt' error messages.  After checking several times I did something weird.  Or at least it seemed so to me.
When I created this file, and following my Windows heritage for text files of this sort I had made sure I had pressed enter on the last line (after the password).  I deleted this and behold no error in the file.  [COLOR="Purple"]Some of you make think this is obvious but I have spent years in Windows World making sure there IS a newline on the last line just to make sure Windows reads and actions the last line in the file.[/COLOR]
**So when creating your credentials file DO NOT PRESS ENTER at the end of the password line.**

Just to say that while testing all of this I did add the switch to make the mount command verbose.  So for those you are having problems use
```
sudo mount -av
```
instead of the 
```
sudo mount -a
```
recommended in most of the threads elsewhere.  You will now see what is going on in the background.

I hope this little supplement to all the good work done by others help out a little.

---

