---
title: "Cinelerra Error in Edgy"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by aust_paul on 2007-04-02
Excuse my Linux n00b-ness.

I teach at a Multimedia college and would like to get my students acquainted with Cinelerra CV. I have it successfully running on Ubuntu Edgy Eft 6.10 but I get this error when I start Cinelerra:

[FONT="Courier New"]void MWindow::init_shm():WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff" > /proc/sys/kernel/shmmax[/FONT]

I can do as the message instructs and all works fine, however when I restart Ubuntu next time I get the error again.

I don’t want students to be root… is there anyway I can add this command to some sort of start-up script so it’s like this all the time and I don’t have to run this command every time I start Cinelerra?

Any help greatly appreciated!

---

### Post by avpx on 2007-04-03
Though this may not be a multimedia question, [http://ubuntuforums.org/showthread.php?t=6963](http://ubuntuforums.org/showthread.php?t=6963) may help.

Cheers!
Nick

---

### Post by kr152ta on 2007-04-21
Add the following to your /etc/sysctl.conf:

# make cinelerra happy 
kernel.shmmax = 2147483647

krisz

---

### Post by aust_paul on 2007-04-29
Excuse me for taking so long to get back to you. Thanks. That worked an absolute treat. Cheers!

---

