---
title: "chmod problems"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Tsquad on 2009-11-14
I just my ftp server up and running on ubuntu 9.10 using proftpd. I made a user on ubuntu named ftpuser for log in reasons so everyone doesnt have my root pw. anyway, iv been trying to figure out how to use chmod to make it so when connected to my ftp server as ftpuser, the user does not see the entire contents of my servers hard drive. I would like to designate a dir for ftp use and make the rest of the HD invisable to the user ftpuser. any help is appreciated. thanks.


ALSO: ftpuser is not my main account on this server, i have an account named taylor(my name) that i set all this up on. And i just want the other ftpuser to be used for ftp server login only.

---

### Post by Tsquad on 2009-11-15
Anyone? im having alot of trouble finding a solution to this.

---

### Post by puppywhacker on 2009-11-15
Proftpd has a configuration option in /etc/proftpd.conf that will limit access only to the home directory. Cant remember the name, but that is where google helps

---

### Post by Tsquad on 2009-11-16
> **puppywhacker said:**
> Proftpd has a configuration option in /etc/proftpd.conf that will limit access only to the home directory. Cant remember the name, but that is where google helps

I have done google. The problem is that my /etc/proftpd.conf file is blank, my config file is located in /etc/proftpd/proftpd.conf and it looks a little different than all the proftpd.conf files iv been seeing on the web. That part that they all have that you are talking about is not in my proftpd.conf file. I have been thinking its due to all these websites based on 8.4 and 8.10, and im on 9.10

---

### Post by puppywhacker on 2009-11-16
yes the correct configuration file is /etc/proftpd/proftpd.conf. According to the Proftpd FAQ [http://www.proftpd.org/docs/faq/linked/faq-ch5.html#AEN524](http://www.proftpd.org/docs/faq/linked/faq-ch5.html#AEN524) 

It explains that you can uncomment the configuration block "anonymous" which is limited to a certain directory. Or if you run proftpd as root and than create a chroot jail where users get their own little private space where they are trapped.

---

### Post by Tsquad on 2009-11-16
> **puppywhacker said:**
> yes the correct configuration file is /etc/proftpd/proftpd.conf. According to the Proftpd FAQ [http://www.proftpd.org/docs/faq/linked/faq-ch5.html#AEN524](http://www.proftpd.org/docs/faq/linked/faq-ch5.html#AEN524) 

It explains that you can uncomment the configuration block "anonymous" which is limited to a certain directory. Or if you run proftpd as root and than create a chroot jail where users get their own little private space where they are trapped.

Thank you for the link. Tho it was very confusing to me. Im unsure how to "uncomment" things. And if i only have one user that i want to limit access for, i would have to use the jail method right? I just want one user(ftpuser) to beable to access one folder(one i designate) and that user will beable to make/delete folders and add/delete files to those folders.

---

### Post by puppywhacker on 2009-11-17
Hi,

uncommenting is done by removing #-hash sign and restarting the proftpd server (sudo /etc/init.d/proftpd restart)

This time I checked on my own ubuntu and I added a DefaultRoot to lock a user "temp" in one directory and another has access to the whole tree. So you can assign a DefaultRoot to chroot one specific user in a specific directory. In below example that would be bob, stuck in his home directory, unable to break out of his tree.

[http://articles.techrepublic.com.com/5100-10878_11-5031101.html](http://articles.techrepublic.com.com/5100-10878_11-5031101.html)

ProFTPD to chroot that home directory. This prevents users from moving outside their home directory tree. In any other FTP environment that doesn't chroot the home directory upon login, users can change to directories like /etc or /usr/bin. When you tell ProFTPD to chroot the home directory, the user will be placed in / instead of /home/username when they connect, and /home/username will be treated as an absolute root directory. If the user then tries to change to /etc, ProFTPD will attempt to change to /home/username/etc. Although this should not be the complete basis for FTP security (it can be circumvented), it is usually enough for the average FTP site. Trying to break out of a chroot environment via FTP is time consuming and difficult. To enable this feature, use:

DefaultRoot / bob
DefaultRoot /home/public temp

---

### Post by Tsquad on 2009-11-17
wow, this is turning out to be way harder than i had thought. Through the process of doing what many different guides told me to do in order to get this working, i can no longer log in with the ftpuser account i had made. Id like to start fresh over but im unsure how to do that(uninstall and reinstall pro ftpd?) Then the flury of linux terms that i dont know seeing as am 4-5 days new to linux. I also cant help but think that my pro ftpd version is newer/different than the one in all of the guides designed for ubuntu 8.x.

If i posted my proftpd.conf file, would you maby beable to help me more, so you can see what im seeing? I dont know what your knowledge of proftp is.

Edit: in the end i just started over with 8.10 due to the mass's of solved issues and guides on the net that a noob like myself wont have any software missmatch issues with.

---

