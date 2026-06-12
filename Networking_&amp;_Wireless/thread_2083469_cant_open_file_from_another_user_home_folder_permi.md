---
title: "cant open file from another user home folder permission issue"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-11-12
Tricia when logged in on her user account cant open these pictures owned by me (scott)

So how can I release these to this user name?

also the shared folders which are working on the win7 pc, she cant view them in her ubuntu user account named tricia

first one is off the 539gb partition
second is from the shared network icon

---

### Post by papibe on 2012-11-12
Hi sdowney717.

You need to add read permission to allow her to see the files, and execute permission to the folder so she can 'cd' into them.

As scott:
```
chmod a+x ~/Kristin\ wedding/*

chmod -R a+r ~/Kristin\ wedding/*
```
If you have more subdirectories under those we can see, you would have to repeat the 2nd command for every level of the tree. An alternative would be:
```
find ~/Kristin\ wedding -type d -exec chmod a+x '{}' \;
```

A simpler solution (not exactly perfect but practical), would be to just add both permissions to all the tree:
```
chmod -R a+rx ~/Kristin\ wedding/
```
Hope that helps. Let us know how it goes.
Regards.

---

### Post by sdowney717 on 2012-11-12
thanks, I logged in as me and looked at the permissions before doing any changes. It already says others have access so why would it say that if she cant open it?

---

### Post by papibe on 2012-11-12
'Kristin wedding' doesn't seem to be the problem, as she can see the content of that directory.

Try checking the permissions of 'a&k's decorations' for instance, or other directory under 'Kristin wedding'.

Let us know how it goes.
Regards.

---

### Post by sdowney717 on 2012-11-12
yikes, how to get using terminal to another partition? The 539gb one has these folders under a user named scott from long ago. I still apparently own them logged in on another partition with the same user name.

here is a permission shot of one of the files in a subfolder of that folder. Looks like permissions would be ok?

---

### Post by sdowney717 on 2012-11-12
ok found out you can get the name from /media
now stuck on a space name folder.
> scott@scott-P5QC:~$ cd ..
scott@scott-P5QC:/home$ cd ..
scott@scott-P5QC:/$ cd /media/0db1fb5a-0727-4347-bfa7-a551d8db6632 
scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632$ ls
BootInfo  boot-sav  home  lost+found
scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632$ cd home
scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632/home$ cd scott
scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632/home/scott$ cd Kristin wedding
bash: cd: Kristin: No such file or directory
scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632/home/scott$ cd Kristin%20 wedding
bash: cd: Kristin%20: No such file or directory
scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632/home/scott$ 


---

### Post by papibe on 2012-11-12
The files look OK. Read only would work.

However, check the permissions on the directory itself, that is,  while in 'Kristin wedding', right click on  'a&k's decorations'. The directory should have 'Access files' for others.

Regards.

P.S.: try:
```
cd 'Kristin wedding'
```

---

### Post by sdowney717 on 2012-11-12
ok I am in the folder and showing the subfolders
(to get thru a space use a '\' character in front of the space)
what next?

> scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632/home/scott/Kristin wedding$ ls
a&k's decorations    a&k's rehersal              Alex&Kristen
a&k's getting ready  a&k's wedding photos&extra  kristin's portraits
scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632/home/scott/Kristin wedding$ 

I checked subs, they all have suitable permissions

---

### Post by papibe on 2012-11-12
Run these 2 commands:
```
chmod -R a+r *

find -type d -exec chmod a+x '{}' \;
```

---

### Post by sdowney717 on 2012-11-12
ok done will log in as her and see 
> scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632/home/scott/Kristin wedding$ chmod -R a+r *
scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632/home/scott/Kristin wedding$ find -type d -exec chmod a+x '{}' \;
scott@scott-P5QC:/media/0db1fb5a-0727-4347-bfa7-a551d8db6632/home/scott/Kristin wedding$ 



Success!, that works. She can see and open the files

what do these commands do exactly?
So why cant the gui do this?

---

### Post by papibe on 2012-11-12
> **sdowney717 said:**
> Success!, that works. She can see and open the files
:D Glad you sorted it out.

> **sdowney717 said:**
> what do these commands do exactly?

This command:
```
chmod -R a+r *
```
add read permission to all files and directories recursively to all the tree below it.

This other one:
```
find -type d -exec chmod a+x '{}' \;
```
finds all directories under it, and for each one found runs the command chmod... That last one adds execution permission to the directory, so a user can double click and enter the directory.

> **sdowney717 said:**
> So why cant the gui do this?
It can be done using the GUI. But it is a bit more complicated for me to explain it, and it takes longer for you to execute it ;-).

Best Regards.

---

### Post by sdowney717 on 2012-11-12
> It can be done using the GUI. But it is a bit more complicated for me to explain it, and it takes longer for you to execute it

Go ahead if you have time and tell me as I would like to know.

---

### Post by sdowney717 on 2012-11-12
oddly the images of the files show a lock type symbol. In an entirely different folder, one which is ok for her viewing, which I did nothing with, one which is higher on the tree , there is no lock showing.

---

### Post by papibe on 2012-11-12
I believe the lock is showing because the files are read-only.

Regards.

---

### Post by sdowney717 on 2012-11-13
no, that cant be. Check this. These jack pictures have no lock symbol.
They are in another folder in that partition
and are shown as read only.

the user 'scott' has shared the Kristin wedding folder onto the network neighborhood so a win7 pc could view them. Will that cause the lock symbol to appear?

---

