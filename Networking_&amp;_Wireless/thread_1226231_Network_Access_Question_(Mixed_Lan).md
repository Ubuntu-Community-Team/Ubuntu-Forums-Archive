---
title: "Network Access Question (Mixed Lan)"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by t-vercetti on 2009-07-29
hey everyone,

my 1st post in the ubuntu-forum! :-)

my issue is probably dealt with many times and i've read some tutorials and various guides so far, but sadly i haven't come up with any solution yet. ok here it goes:

in my w-lan network i have a linux mint 7 laptop, and 2 others running winxp.
from linux mint i can view the shared folders/files on the win pcs. i can read and write, so i got full access.

the other way around (using the win pcs) i can see the folders of the linux mint laptop and also open them making the files visible. the problem is, i cannot read the shared files or write anything into the folders.

to configure the workgroup, shared folders, etc. i'm editing the smb.conf file in /etc/samba.
i  set the "read only" option to "no", so i don't know why i can't read or write from the win pcs.

the only things i changed in the smb.conf file are:
1.) workgroup (they are now all in the same workgroup)
2.) i added the following lines at the end of the file:

[share]
        path = /home/my_username/Shared Files
        read only = No
        guest ok = Yes


what do i have to edit/do in order for the winpcs to access (read/write) my shared files on the linux mint laptop?


thx for your time,
vercetti.

edit: p.s. i would be grateful for a solution without having to add users, groups and passwords (unless this is impossible to avoid). a compromise would be setting a password and allowing every guest to access files after entering this password.

---

### Post by superprash2003 on 2009-07-29
try adding the following arguments instead of read only = no

available = yes
browsable = yes
writable = yes

---

### Post by t-vercetti on 2009-07-29
> **superprash2003 said:**
> try adding the following arguments instead of read only = no

available = yes
browsable = yes
writable = yes


hey thanx for your help.
i added the lines you mentioned but nothing changes...

what seems to be the problem here?

vercetti.

---

### Post by Iowan on 2009-07-29
Did you restart Samba after editing */etc/samba/smb.conf*?

---

### Post by t-vercetti on 2009-07-29
ok guys,

stop all your thoughts, i figured out most of the problem in the last minute!

in another forum someone told me to give "nautilus" a try instead of using the smb.conf file. i read in a tutorial that nautilus can only make "owned" folders/files accessible in the network. i thought this only meant the partition where linux was on and that it would not work with the fat32 partition (which i created especially for network shares and my dualboot with winxp). 
i gave nautilus a try anyway and being the linux n00b i am, i realized that i was in fact able to share folders on my fat32 partition. i also created a folder in /root/desktop in nautilus just to see if this would also work.
to my surprise both folders showed up on the winxp pc but i could only access the one on the fat32 (read and write). perfect! :-)
i was denied access to the folder on /root/desktop though, which -in my case- is ok (i only need the fat32 share to work).

so now the only thing left is how i can automatically have the fat32 mounted when i boot linux. until i mount the fat32 in linux it stays unavailable for network share.

what would be the correct line to add in /etc/fstab to have the fat32 auto-mounted?

the fat32 partition is dev/sda8 and it shows up as /media/SHARES under my computer. the folder i want to have shared is "/media/SHARES/shared files"

i found this line in a tutorial: (after personalizing it) is it what i need and how must i edit it? 

/dev/sda8 /mnt/win1 vfat users,owner,rw,umask=000 0 0 

thx for your help!

vercetti.

---

### Post by t-vercetti on 2009-07-29
ok,

got my last issue solved too:

automounting the fat32 partition was done by using a little tool named "pysdm" (gui for editing fstab). 
everything works great now!

all issues solved,
thx for your help,
vercetti.

---

