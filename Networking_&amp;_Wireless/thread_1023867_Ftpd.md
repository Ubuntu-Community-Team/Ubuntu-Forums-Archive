---
title: "Ftpd"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by pshown on 2008-12-28
I have installed the ftpd server client. I cannot find it in application, system admin preferences etc. I want to set up a server to share my music collection. Can anyone help?

---

### Post by albinootje on 2008-12-28
> **pshown said:**
> I have installed the ftpd server client. I cannot find it in application, system admin preferences etc. I want to set up a server to share my music collection. Can anyone help?

Can you give the exact package name ?
There's proftpd, vsftpd, pure-ftpd and more.
```

dpkg -l|grep ftpd

```
They don't come with a GUI, but there are some admin GUI for it, e.g. :
[http://www.howtoforge.com/proftpd_web_interface_gui_tools](http://www.howtoforge.com/proftpd_web_interface_gui_tools)

Do you want to share this over a local network or over the internet ?
Do you want others to be able to upload ?

If you need this to go via the internet then there are easier and better ways to provide your music to yourself and others.

For example with :
[http://www.gnu.org/software/gnump3d/](http://www.gnu.org/software/gnump3d/)
[http://ampache.org/](http://ampache.org/)
[http://www.pancake.org/zina](http://www.pancake.org/zina)

---

### Post by pshown on 2008-12-28
albinootje,
I do want to make my Music collection available to friends and family over the internet. Out of the list of applications you provided, do you use one of them?
Also, I am new to Ubuntu/Linux as a whole so I am not proficient at installation of .tar.gz file types. Any additional info would be a big help.

---

### Post by albinootje on 2008-12-28
> **pshown said:**
> albinootje,
I do want to make my Music collection available to friends and family over the internet. Out of the list of applications you provided, do you use one of them?
Also, I am new to Ubuntu/Linux as a whole so I am not proficient at installation of .tar.gz file types. Any additional info would be a big help.

I've played with gnump3d some time ago, I have used ampache some time ago, and I like the webpage of Zina.

Here's some howtos for gnump3 :
[http://ubuntuforums.org/showthread.php?t=214621&highlight=gnump3](http://ubuntuforums.org/showthread.php?t=214621&highlight=gnump3)
[http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html](http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html)
[http://geek-tale.blogspot.com/2006/02/gnump3d-mini-howto.html](http://geek-tale.blogspot.com/2006/02/gnump3d-mini-howto.html)

gnump3 is available for hardy, but not for intrepid for some reason
[http://packages.ubuntu.com/search?keywords=gnump3](http://packages.ubuntu.com/search?keywords=gnump3)

Read also this bit from comment #9 
> 
Actually you don't have to install Apache in order to run gnump3d, it will automatically serve a web interface.


---

### Post by pshown on 2008-12-28
Thank you albinootje. Looks like I some work to do. I am sure that I will be able to set up gnump3 with the tutorials.

---

### Post by pshown on 2009-01-02
albinootje,
It looks like gnump2d is a good aplication to share my music if people who just want to listen to music. I have some friens and famiily members that would be more intrested in being able to actually download my files. Do you have any ideas what I can use?

---

### Post by albinootje on 2009-01-02
> **pshown said:**
> albinootje,
It looks like gnump2d is a good aplication to share my music if people who just want to listen to music. I have some friens and famiily members that would be more intrested in being able to actually download my files. Do you have any ideas what I can use?

You can apache as web-server for that.
```

sudo apt-get install apache2

```
Or see here for a howto with screenshots :
[http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06](http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06)
Make sure to skip the php, phpmyadmin, and mysql parts, unless you need that for something else.

To protect some of your webpages with passwords, see here :
[http://ubuntu-tutorials.com/2007/10/06/limiting-access-to-websitesdirectories-with-htaccess/](http://ubuntu-tutorials.com/2007/10/06/limiting-access-to-websitesdirectories-with-htaccess/)

---

