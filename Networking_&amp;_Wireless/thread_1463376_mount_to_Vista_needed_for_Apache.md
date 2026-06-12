---
title: "mount to Vista needed for Apache"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by tconrad on 2010-04-26
I have a problem where I'm using Ubuntu linux to mount a Windows Vista machine's USB drive and access it on the web using Apache.

I did have the USB drive plugged into the Linux machine directly and that was working via the web.

FollowSymLinks is on in httpd.conf


$ ls -ld /mnt
drwxr-xr-x 3 root root 4096 2010-04-26 20:06 /mnt

$ ls -ld /mnt/music
drwxr-xr-x 1 root root 16384 2010-04-26 20:06 /mnt/music

I have a soft link to the mount:

$ ls -l Music
lrwxrwxrwx 1 user1 httpd 10 2010-04-26 19:23 Music -> /mnt/music

The mount line in fstb
//192.99.99.99/My\040Music /mnt/music cifs ro,user,credentials=/etc/cifspw 0 0

Credentials:
$ ls -l /etc/cifspw
-rw------- 1 root root 30 2010-04-26 19:20 /etc/cifspw

The mount works and I can see the files (see above) from my regular linux user account.

If I make a test file in /mnt and soft link to that, I can see it on the web.  So it's just the mount to the vista machine that seems to be a problem.  It's supposed to be a simple read-only mount and the apache login should (I think) be able to see the same generic root access permissions.

log from apache:
[Mon Apr 26 20:39:42 2010] [error] [client 99.99.99.99] Symbolic link not allowed or link target not accessible: /home/user1/pub_html/Music, referer: [https://xx.xx.xx/~user1/music.html]("https://xx.xx.xx/%7Euser1/music.html")

The credentials have a login and password that matches a special read-only account on Vista.  I can see the files on the system from Linux, but not via the web.  As mentioned above, a different link to the same /mnt area works fine via the web.  I've tried several different mount options with no success.

Any ideas?

Thanks,
Tim

---

### Post by tconrad on 2010-07-19
I'm still lost - any ideas???

Thanks,
Tim

---

### Post by tconrad on 2010-07-19
Here is a new data point - I don't think I knew this before.  If I put in an explicit path to a file on the remote drive, I can access it via the web.  But it's being able to browse the external drive that isn't working.

---

### Post by tconrad on 2010-07-19
[CENTER]
[LEFT]While not the best solution, I worked around this by using a cgi file lister.   Every thing works nicely now.   Better would be to change the apache settings (which?) that control this.

I also needed to modify the cgi file lister so that it only lists files in the directories that I allow (not the whole system).   It translates the file list to an html path (and calls itself with a new path for directories).  It's something that I hacked up from a simpler script I found on the web once.

Tim

[/LEFT]
[/CENTER]

---

