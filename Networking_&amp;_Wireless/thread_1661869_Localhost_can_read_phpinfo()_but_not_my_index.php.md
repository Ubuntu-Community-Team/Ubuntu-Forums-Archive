---
title: "Localhost can read phpinfo() but not my index.php ?"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by rolfhorror on 2011-01-07
I'm new to Ubuntu and linux (began summer 2010).
Installed apache2 and php5, got the message **"It works!"** and **phpinfo()** displays the info page from withing the my folder. But when i put my index.php and rest of the files in www/mysite/ I only get a blank page displaying nothing, as if my php scripts wont parse. If I create a plain html "hello world" doc it displays that..
I've used this guide before [COLOR=Blue][http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)[/COLOR]
and got it to work last time some months ago, but this time around after clean ubuntu reinstall it's showing nothing, remember I struggled with some permission things last time doing **[COLOR=DarkGreen]sudo chmod a+rwx /var/www/* [/COLOR]**[COLOR=DarkGreen][COLOR=Black]and same for subfolders css and images.
but now nothing happens, no errors or nothing.
I didnt have to do enything else last time, no php.ini or nothing, it just worked, after I set permissions to get css and images to display correctly.
Tried to put my files in www alone but dont work either (also cannot delete the default index.html in the www folder). Tried to restart apache2 and the computer, but no luck.
My site also works online from other servers, so this is a local problem.
Someone have any thoughts ?
thx!
[/COLOR][/COLOR]

---

### Post by rolfhorror on 2011-01-07
Followed the guide below and it's now working, all I had to do in addition to guide was to give permission to image folder for the site to use images.
sudo chmod a+rwx /var/www/img/*

[http://www.andyhawthorne.net/2010/10/setting-up-a-lamp-server-on-ubuntu-10-10/](http://www.andyhawthorne.net/2010/10/setting-up-a-lamp-server-on-ubuntu-10-10/)


hope that no more tweaking is needed, and that this works for future installs too...
fingers crossed.
:-)

---

### Post by rolfhorror on 2011-01-08
..now I wonder.. how safe is sudo chmod a+rwx /var/www/*
and sudo chmod a+rwx /var/www/img/*
I know it means all users can read, write and execute, but
is there any security issues with this if it's on public server ?

Anyone ?

sorry for my newbieness on this subject, but when doing all things sudo I feel I'm giving permissions here, there and everywhere.

---

### Post by CharlesA on 2011-01-08
You are effectively giving everyone read/write access, which is a bad idea.

At most you'd need it set at 775 (rwxrwxr-x) for directories
664 (rw-rw-r--) for files.

---

