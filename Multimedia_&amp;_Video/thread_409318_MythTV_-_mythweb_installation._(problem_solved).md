---
title: "MythTV - mythweb installation. (problem solved)"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by CarloMagno on 2007-04-14
Well, I've had a hard time trying to set-up MythTV in a server backend - client frontend configuration. My last problem has been with mythweb refusing to load and complaining about not having php enabled for my server (I had php5 and php4 installed). 

I am running Edgy with the latest updates and I have followed the instructions given in:

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Desktop#head-375892e27a7292018db6fca65e0baedf06f6f577](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Desktop#head-375892e27a7292018db6fca65e0baedf06f6f577)

even the last part relating to phpmyadmin and mythweb troubleshooting.

The solution to my problem was in these pages:

[http://www.gossamer-threads.com/lists/mythtv/users/247547](http://www.gossamer-threads.com/lists/mythtv/users/247547)
[http://www.jnewcastle.com/blog/2007/03/18/installing-mythtv-on-ubuntu-edgy/](http://www.jnewcastle.com/blog/2007/03/18/installing-mythtv-on-ubuntu-edgy/)

As I am quite new to linux and apache I had to interpret those threads as best as I could but I finally found the solution. I edited the following files:

sudo gedit /etc/php4/apache2/php.ini
sudo gedit /etc/php5/apache2/php.ini

and I inserted the following lines in the section containing "Dynamic Extensions":

extension=mysql.so
extension=myth.so

After that we have to restart the apache server:

sudo /etc/init.d/apache2 restart

And now I am able to access mythweb though my server: [http://localhost/mythweb](http://localhost/mythweb)
Please, if anyone knows something more about this files and can explain what happens and the reason for these changes please feel free to comment, I would appreciate any info. Hope this helps anyone

---

### Post by jboehm on 2007-04-28
Thanks! Great how to for feisty fawn!!

---

