---
title: "On another user account, the NTFS drive is not shown or accesible"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-11-12
I created a new user.
They can not use the NTFS partition sda1
I can use the partition from my ubuntu user account

screen shot shows gparted listing partition and file manager showing it not available.

fstab does not show any sda1 ntfs drives, but I should not have to make any changes! if it works in my user account.
hurdle, hurdles

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=4c1f632a-f05d-41e3-bc3e-ba9036e8e0b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9c858c14-1d67-4665-bb53-6818dc055c15 none            swap    sw              0       0
#sda5 home partition
#UUID=0db1fb5a-0727-4347-bfa7-a551d8db6632   /home         ext4    nodev,nosuid       0       2
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by dannyboy79 on 2012-11-12
the new user is most likely NOT in the admin group as your first user is which is then able to mount and use the NTFS partition.

here's a great little write up for having multiple users use an NTFS partition.

[http://askubuntu.com/questions/54321/how-do-i-give-multiple-users-access-to-a-windows-ntfs-partition](http://askubuntu.com/questions/54321/how-do-i-give-multiple-users-access-to-a-windows-ntfs-partition)

---

### Post by sdowney717 on 2012-11-12
"Put both users in a group together"
What group and how to do this?

Thanks then why does the user have all priveleges like me, yet still cant access the NTFS drive?
The gui shows all sorts of various options. Intuitively you think if they are all checked they should have same priveleges?
I am scott who can see NTFS drive, the new user is tricia and she cant see the NTFS drive.

---

### Post by Morbius1 on 2012-11-12
I'm confused - which is a normal state for me these days.

You are showing network shares in your screenshot. Does this have anything to do with this:
> [movies] 
path = /media/26E82022E81FEEB5/movies     
writeable = yes 
;browseable = yes     
guest ok = yesIt looks to me like that mount point ( /media/26E82022E81FEEB5 ) is an ntfs partition that you are mounting as you need it rather than through fstab. That's fine but when you do that it mounts with you as owner and permissions of 700 meaning only you can access it.

So you can either add an entry in fstab to have this mount with permissions allowing guest to access it or you can make the remote guest appear to be you. For example, change the share definition to this:
> [movies] 
path = /media/26E82022E81FEEB5/movies     
writeable = yes 
;browseable = yes  
[COLOR=Blue]**force user = scott   **[/COLOR]
guest ok = yesThen restart samba:
```
sudo service smbd restart
```Now when the remote guest tries to access that share she will be converted to scott and be allowed in.

Am I assuming too much of a connection to your earlier post here: [http://ubuntuforums.org/showthread.php?t=2082924](http://ubuntuforums.org/showthread.php?t=2082924)

---

### Post by sdowney717 on 2012-11-12
those network shares many are on the NTFS drive. If you click when she is logged on with her new account, they are not accesible.
They are on my account and are from the win7 Pc
So yes and no on your question. Tricia wants to use a new user account directly on my Ubuntu PC. she can not see the NTFS drive filled with pictures.

I went looking thru group settings and see this has none checked.
ADM, ADMIN tricia tom scott is checked

---

### Post by sdowney717 on 2012-11-12
> So you can either add an entry in fstab to have this mount with permissions 

yes that is fine, so what would I put into fstab?
Is the problem say I am still logged in on the PC, then I switch user to tricia ? So if I log out, then tricia user could mount like me?

---

### Post by dannyboy79 on 2012-11-12
> **sdowney717 said:**
> "Put both users in a group together"
What group and how to do this?

Thanks then why does the user have all priveleges like me, yet still cant access the NTFS drive?
The gui shows all sorts of various options. Intuitively you think if they are all checked they should have same priveleges?
I am scott who can see NTFS drive, the new user is tricia and she cant see the NTFS drive.
if you read the link i presented you would have seen lower down it shows how to create a new group etc etc.

> **sdowney717 said:**
> yes that is fine, so what would I put into fstab?
Is the problem say I am still logged in on the PC, then I switch user to tricia ? So if I log out, then tricia user could mount like me?
you will also see in the same link what to enter for the fstab. PLEASE READ THE LINK.

---

### Post by Morbius1 on 2012-11-12
>  Is the problem say I am still logged in on the PC, then I switch user to  tricia ? So if I log out, then tricia user could mount like me?     Correct.

If you want to have this internal partition automount then the line in fstab would look something like this:
```
UUID=26E82022E81FEEB5 /media/26E82022E81FEEB5 ntfs defaults,nls=utf8,umask=000,windows_names 0 0
```Here's the tricky part:

[1] If you have this partition currently mounted unmount it.

[2] Then create the permanent mount point:
```
sudo mkdir /media/26E82022E81FEEB5
```[3] Then add the line to fstab and save the file.

[4] Then run the following command to have it mount without a reboot:
```
sudo mount -a
```

---

### Post by dannyboy79 on 2012-11-12
> **Morbius1 said:**
> 
If you want to have this internal partition automount then the line in fstab would look something like this:
```
UUID=26E82022E81FEEB5 /media/26E82022E81FEEB5 ntfs defaults,nls=utf8,umask=000,windows_names 0 0
```
I seriously doubt the 26Eblahblah is the UUID, it's more then likely the volume name.
TO find out the UUID use this command
```
blkid -o value -s UUID
``` 
(use sudo if you must)
As I already stated, just read ALL the info in the link I provided

---

### Post by Morbius1 on 2012-11-12
> I seriously doubt the 26Eblahblah is the UUID, it's more then likely the volume name.
I'm fairly certain it is. It has the right length and syntax ( ie., no dashes ) and if he is in fact mounting it through Nautilus when he needs it it will mount to the UUID [COLOR=Blue]**if it has no volume label**[/COLOR].

And always run blkid this way to get a more accurate output:
```
sudo blkid -c /dev/null
```

---

### Post by sdowney717 on 2012-11-12
made a winhdd group with group id = 1003 and all three are members.
Logged out and in after doing several things listed here but still dont see it available in the file manager

I will keep trying!

> tricia@scott-P5QC:~$ sudo blkid -o value -s UUID
[sudo] password for tricia: 
26E82022E81FEEB5
0db1fb5a-0727-4347-bfa7-a551d8db6632
4c1f632a-f05d-41e3-bc3e-ba9036e8e0b1
9c858c14-1d67-4665-bb53-6818dc055c15
tricia@scott-P5QC:~$ 




fstab with a new line
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=4c1f632a-f05d-41e3-bc3e-ba9036e8e0b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9c858c14-1d67-4665-bb53-6818dc055c15 none            swap    sw              0       0
#sda5 home partition
#UUID=0db1fb5a-0727-4347-bfa7-a551d8db6632   /home         ext4    nodev,nosuid       0       2
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=26E82022E81FEEB5 /media/win ntfs rw,auto,user,exec,nls=utf8,dmask=007,fmask=117,gid=1003,uid=1000 0 2

---

### Post by sdowney717 on 2012-11-12
Ok I substitute the bad line for this one

> UUID=26E82022E81FEEB5 /media/26E82022E81FEEB5 ntfs defaults,nls=utf8,umask=000,windows_names 0 0


I tried then to unmount and it said it was 'inhibited'
so could not do the additional suggested commands
At that point I just shut down the PC
rebooted 

And logged in with tricia, the NTFS volume is accessible!

So I switched users to scott and the NTFS volume is accessible!
:P
So it is working! Very nice. And I wish this was automated and did not have to figure it out. 

So thanks again for the help!

Since i added a winhdd new group and put all three users into it, is that not needed? If so , then why did I do that?

---

### Post by dannyboy79 on 2012-11-12
nevermind, it appears you got it sorted out

---

### Post by Morbius1 on 2012-11-12
>  Since i added a winhdd new group and put all three users into it, is that not needed? If so , then why did I do that?I can't explain that line of logic but with the line you added to fstab it's not needed.

I tried to fix 2 problems at the same time and I should have explained what I was suggesting. The option "umask=000" will make the mounted partition have permissions of 777. This not only allows the other local user to access the contents of that partition but the samba "guests" that are accessing it remotely.

I also had you create a mount point at /media/uuid-number which I wouldn't do personally but you already had a number of samba shares set up with that path and didn't want you to redo your samba settings.

---

