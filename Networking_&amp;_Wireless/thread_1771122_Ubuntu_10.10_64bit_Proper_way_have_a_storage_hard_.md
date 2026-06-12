---
title: "Ubuntu 10.10 64bit Proper way have a storage hard drive always accessible &amp; shared?"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by xekon on 2011-05-30
If I goto MainMenu>Places>Home Folder
create a directory myvids
drop a few videos in their
right click on the myvids folder and select "sharing options" 
check the "share this folder" & "guest access" boxes

Then my other computers can access the folder and file.  **YAY! SUCCESS!**

**NOW, I have added in an internal 1TB hard drive** and formatted it to ext4, it has a folder full of videos, the folder is labeled "video"

This drive is not directly mounted. I have to goto MainMenu>Places>Computer

From there I can double click into the drive I can then access the files. this also places an icon on my desktop meaning it is now mounted I believe.

So if I then go into that drive and right click on the "video" folder and select "sharing options" 
check the "share this folder" & "guest access" boxes.

It acts as if it has worked, the folder gets those neat little sharing arrows on it and everything! wooohooo! oh wait! nope, it didn't work!

I try to access it from my HTPC or other computers in the house and it don't work, the strange thing is, my other computers in the house see the share folder when they browse my shares, but when they go to access the share it **says cannot access, network path was not found.**

I would assume the proper thing to do would first be to set it up so that the drive is mounted on boot. but after reading through some posts it seems like a number of people are having trouble with this so I would prefer for somebody that knows what they are doing to help me out or point me to a guide/wiki/post that explains the proper way to do this under Ubuntu 10.10.

Anyone that can help, I definitely appreciate it, thank you so much.

---

### Post by dandnsmith on 2011-05-30
I don't know the 'proper' way to do the mounting, as I learned all this stuff using command lines with Unix before linux got going.

How I do it is to edit fstab to insert extra line(s) for filesystems I want, and specify there whether to mount (and check integrity) at boot.

I recommend reading the man pages for fstab, and looking at /etc/fstab to see what is currently there.

If you have problems, post the details of what you've tried, and how it doesn't work, and somone will be able to take it from there.

---

### Post by xekon on 2011-05-30
I added the line to the bottom of my fstab:

```
/dev/sda1 /mnt/bkup1 ext4 defaults 0 0
```

Now when I browse those files it does not create a icon on my desktop, this is because it is already mounted. I now goto MainMenu>Places>Computer

then browse to File System>mnt>bkup1

I also dragged the folder to the left pane where documents,pictures,music,videos are so now I have a quick shortcut.

This however did not fix the problem like I was hoping for accessing these files from my HTPC or other windows computers. Is there a flag or option that needs to be set/changed on my fstab or is the problem something else entirely.

---

### Post by dandnsmith on 2011-05-31
Not entirely sure where it lies, as it could be a combination of factors.
Provided you created the share for /mnt/bkp1 the same way as you did for that videos test, then you need to look at permissions and ownership for the mount points and compare them.
I'd have mounted the bkp1 with r or rw for all (as a quick guess, without knowing how you categorise the various users).
I use samba for sharing across my local network with windows PCs, so have configured /etc/samba/smb.conf - I'm not sure whether the method of sharing you describe configures this or not, as I only ever used it for a quick test.

---

### Post by xekon on 2011-05-31
yes, I created the share the same way for the folder in my home folder and for the folder on the bkup1 terabyte drive.

I just compared the permissions of the two folders and they are the same.

When I specified defaults on column4 in the fstab file that includes rw from what I read in the fstab wiki.

I think you might be onto something with trying to share through another means though, I really don't know what method is used when you share a folder by right clicking on it and selecting "sharing options" to share it. I assumed it uses samba as well but i'm not sure.

---

### Post by xekon on 2011-05-31
You were right about the permissions. the problem is that when you right click on a folder click properties and view the permissions tab there is a dropdown list for groups.
Originally my username was in the groups dropdown. I changed the groups dropdown to "sambashare" and then the dropdown below that I set to "read"

I now have full access to everything on this drive. Consider this issue resolved and Thank you so much for your help I appreciate it.

---

### Post by dandnsmith on 2011-05-31
Glad to hear you've achieved your desired aim.

---

### Post by xekon on 2011-06-01
**EDIT: GOT IT WORKING**

Well, the first drive I put in that has the 'videos' folder is still accessible. all is well.

I decided to add in a second storage drive. I followed the same procedure as last time for sharing, the new share shows up but when you try to access it, it says the network path not found again!

here is the bottom of my fstab (both are 1TB hard drives, bkup2 is the one I just added):
```
/dev/sda1 /mnt/bkup1 ext4 defaults 0 0
/dev/sdb1 /mnt/bkup2 ext4 defaults 0 0
```

Now to check the permissions incase the gui was playing tricks on me I used the command line ls -l:
top line is the working one:
```

drwxr-xr-x 3 xekon sambashare  4096 2011-05-31 14:18 videos
drwxr-xr-x  8 xekon sambashare  4096 2011-05-31 13:59 videos2

```

As far as I can tell the permissions are the same, atleast for the first column. The only difference is the working one has a 3 in column2 and nonworking has a 8. How would I change that 8 to a 3? for the nonworking on.

**EDIT: GOT IT WORKING**

I guess my brain was just thinking windows mode too much or something. Apparently the parent folder of the folder you are trying to share which is in my case the mount point, also has to have the group sambashare set to read access. so ontop of setting permissions for videos2 I had to set permission for bkup2. I must have done this to the first share as I was tinkering around with permission without realizing it.

---

