---
title: "Mythtv Settings entered in Database Configuration 2/2 will not SAVE ??"
date: 2009-10-28
forum: Mythbuntu
---

### Post by Quazza on 2009-10-28
Hi There,

I am trying to get Wakeonlan to work between my mythbuntu frontend and Arch mythbackend, something odd is happening with the mythtv settings, from the Mythtv menu when I go to setup - setup - General -next - next

[B]Database Configuration 2/2
[/B] 

I enter the below info

```
Enable Database Server Wakeup -> checked
Reconnect time -> 50
Retry attempt -> 10
Wake command -> /home/jase/.mythtv/scripts/wol <MAC Address>
```

I then click next through the rest of the menus and finally click finish.

Once I go back in to check the settings I now see nothing entered and the check box for enable Database Server Wakeup is actually unchecked?  

I have been and done this again and again different ways and still it will not save the settings I enter, what is going on?

Cheers Quazza :D

---

### Post by Neon Dusk on 2009-10-28
What's the permissions of your mysql.txt file?
```

ls -l /etc/mythtv/mysql.txt

```

---

### Post by Quazza on 2009-10-28
> **Neon Dusk said:**
> What's the permissions of your mysql.txt file?
```

ls -l /etc/mythtv/mysql.txt

```

Hi Neon Dusk,

The permissions are as per below, oh and the mythtv folder is located in my home folder as a hidden directory and I am using Arch Linux.

```
dad : /home/dad > cd /home/dad/.mythtv
dad : /home/dad/.mythtv > ls -l
total 32K
drwxr-xr-x 2 dad  users 4.0K 2009-10-27 01:40 channels/
-rw-r--r-- 1 root root   420 2009-07-13 10:17 config.xml
-rw-r--r-- 1 root root  1.1K 2009-07-05 13:02 mysql.txt
-rw-r--r-- 1 dad  users 1.1K 2009-10-29 12:25 mysql.txt~
drwxr-xr-x 2 dad  users 4.0K 2009-08-29 23:00 mythbackup/
drwxr-xr-x 2 dad  users 4.0K 2009-10-27 15:49 osdcache/
drwxr-xr-x 2 dad  users 4.0K 2009-07-05 22:55 scripts/
drwxr-xr-x 3 dad  users 4.0K 2009-10-26 22:22 themecache/
dad : /home/dad/.mythtv > 
```


Also its not all settings that won't save only the settings on the Database Configuration 2/2  page

Thanks for taking the time and I hope I can get this fixed.

Cheers

Quazza :D

---

### Post by Neon Dusk on 2009-10-29
Can you try channging to permissions of the mysql.txt file so that everyone can write to it :-
```

chmod a+w mysql.txt

```

---

### Post by Quazza on 2009-10-29
Hi Neon dusk,

I did what you advised and it appears to still have the same permissions as before?

```
[root@archbuntu .mythtv]# chmod a+w mysql.txt
[root@archbuntu .mythtv]# ls -l
total 32
drwxr-xr-x 2 dad  users 4096 2009-10-27 01:40 channels
-rw-r--r-- 1 root root   420 2009-07-13 10:17 config.xml
-rw-rw-rw- 1 root root  1122 2009-07-05 13:02 mysql.txt
-rw-r--r-- 1 dad  users 1122 2009-10-29 12:25 mysql.txt~
drwxr-xr-x 2 dad  users 4096 2009-08-29 23:00 mythbackup
drwxr-xr-x 2 dad  users 4096 2009-10-27 15:49 osdcache
drwxr-xr-x 2 dad  users 4096 2009-07-05 22:55 scripts
drwxr-xr-x 3 dad  users 4096 2009-10-26 22:22 themecache
```

Cheers  Quazza :D

---

### Post by Neon Dusk on 2009-10-29
```

-rw-rw-rw- 1 root root  1122 2009-07-05 13:02 mysql.txt

```

That shows that everone has write access - there's a 'w' in the owner, group & other columns. Is the configuration info still not saving?

---

### Post by Quazza on 2009-10-29
Yeah mate I did a couple more tests and its definately not saving.

Very strange.

Oh one thing I forgot to ask the other mysql.txt file should that one have the same permissions?
```

-rw-r--r-- 1 dad  users 1122 2009-10-29 12:25 mysql.txt~
```


Quazza

---

### Post by Neon Dusk on 2009-10-29
> **Quazza said:**
> Yeah mate I did a couple more tests and its definately not saving.

Very strange.

Oh one thing I forgot to ask the other mysql.txt file should that one have the same permissions?
```

-rw-r--r-- 1 dad  users 1122 2009-10-29 12:25 mysql.txt~
```


Quazza

I'm not sure why you have a mysql.txt~ file I've not seen this in ubuntu. You could try changing the permissions on that file as well. Do you have any other mysql.txt files?

```

locate mysql.txt

```

---

### Post by SiHa on 2009-10-29
[QUOTE=Quazza]```
-rw-r--r-- 1 dad  users 1122 2009-10-29 12:25 mysql.txt~
```[/QUOTE]

I think you've probably just used 'gedit' to edit mysql.txt at some point? When you do this gedit will automatically save a backup of the original file with the '~' suffix.

Also, I notice that your ownership is root:root, on mine it's mythtv:mythtv.

Perhaps you could try to change it?```
sudo chown dad:users mysql.txt
```

And finally if that doesn't work, my mysql.txt actually resides in **/etc/mythtv**, and the one in **/home/mythbox/.mythtv** is a symlink to it. Perhaps, Myth is trying to save to a copy in **/etc/mythtv**? If you wanted to try that setup:

```
cd /home/dad/.mythtv
cp mysql.txt mysql.bak
sudo mv mysql.txt /etc/mythtv
ln -s /etc/mythtv/mysql.txt /home/dad/.mythtv/mysql.txt
```Note that the **ln -s** requires full pathnames for both arguments, regardless of what the current working directory is.


Note, I've backed the file up to mysql.bak first. If something goes horribly wrong, you can just copy it back, and remove the others.```
sudo rm /etc/mythtv/mysql.txt /home/dad/.mythtv/mysql.txt
cd /home/dad/.mythtv
mv mysql.bak mysql.txt
```

---

### Post by Neon Dusk on 2009-10-29
@Quazza

Can you run 'mythfrontend -v important' from a terminal window try and change the settings then quit?

In the terminal window you should see something like 'Could not open settings file /home/dad/.mythtv/mysql.txt for writing'

---

### Post by Quazza on 2009-10-29
Hi Neon Dusk and SiHa,

I did the ```
sudo chown dad:users mysql.txt
```

and then tried to set the settings again and it still didn't work, also I did the   ```
mythfrontend -v important
```
with the output from that below and it appears to not be able to write to the file on my frontend??  as I run a seperate backend frontend..

```
2009-10-30 09:38:00.051 No theme dir: /home/jase/.mythtv/themes/blootube-wide
2009-10-30 09:40:25.370 Could not open settings file /home/jase/.mythtv/mysql.txt for writing
2009-10-30 09:40:25.370 Could not open settings file /home/jase/.mythtv/mysql.txt for writing
jase@mythtv-frontend:~/Desktop$ 
```

So should I go on with what you have suggested SiHa or is there something else I should do now? 

Thanks heaps for the help so far.

Cheers Quazza :D

---

### Post by Neon Dusk on 2009-10-29
Ok I think we've been looking at the backend instead of the frontend.
On the frontend does 
```

ls -l /home/jase/.mythtv/mysql.txt

```
show that /home/jase/.mythtv/mysql.txt is a link to /etc/mythtv/mysql.txt?

If it does then run
```

ls -l /etc/mythtv/mysql.txt

```

If that indicates that owner and group are set to root then you need to change it to mythtv

i.e. if it returns
-rw-rw---- 1 **root** **root** 1118 2009-10-29 23:13 /etc/mythtv/mysql.txt

then run
```

sudo chown mythtv:mythtv /etc/mythtv/mysql.txt

```

---

### Post by Quazza on 2009-10-29
Hi Neon Dusk,

I tried several different fixes and even invested the help of a mate at work who is a bit of a Unix buff and we just deleted the symbolic link that was in the .mythtv folder and then copied the mysql.txt file from /etc/mythtv to the .mythtv folder and it now works.

Still trying to work out why it was happening that way but anyway all good now and thanks you so much for yours and SiHa's help as this has been annoying me for quite sometime.

I guess we can mark this as solved

Cheers Quazza :D

---

