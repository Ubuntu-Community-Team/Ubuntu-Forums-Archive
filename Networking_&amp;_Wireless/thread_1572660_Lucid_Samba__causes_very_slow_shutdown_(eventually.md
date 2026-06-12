---
title: "Lucid: Samba  causes very slow shutdown (eventually by timeout)"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by dblaisde on 2010-09-11
Samba doesn't seem to disconnect on shutdown except by timing out, causing a loooong Lucid shutdown. (I can disconnect manually before shutdown by unmounting the Samba shares, and shutdown is then very fast.) Apparently Network Manager is somehow involved. I've installed a NM shutdown Samba script which works for the first user account, but not for the second user account (which was created and then put into the admin group).

---

### Post by huck416 on 2010-09-25
I'm curious to know what your script is. I am having the same problem and I've tried a couple things but none of my scripts would work as they required sudo to run and I couldn't find how to run a sudo script automatically on shutdown. I have only one user account so I'm hoping your script will solve my problem. Thx

---

### Post by maino82 on 2010-10-08
I have the same issue and would also be interested in seeing your script/process. Right now my solution is to manually umount everything before shutdown, which isn't really much of a solution.

---

### Post by luca.marinosci@gmail.com on 2010-10-28
Hi v'body,

I have the same issue since...well since i've moved from winzozz to ubu (9.04).

Currently i'm on the perfect 10 and i still have the issue and i can confirm that is strictly latched to wireless.

A little bit of my pc background:

Asus G1s, dual core 2GHZ, 3gb ram, ubuntu 10.10 64bit, wireless/bluetooth non switchable by hardware button (only by sysop), samba shares are mounted from fstab (with security policy too), can't rem the kernel but everything is up to date.

If i keep the connection on cable and the wless off it switches off in less than 10 seconds (*_SIMPLY AMAZING_*).
Not the same if we're on wless..seems like the network manager is shut down when the user is logged out(or a little bunch of msecs before). I've put a log file when the GDM execute the PostSession (/etc/GDM/PostSession/Default) to check whenever is going through but i'm still thinking about any kind of solution (already tried to put umount /path/to/mounted/share but hasn't worked as expected).

...don't metion rcX.d 'cause is totally unuseful...the wless is shut down before we reach those levels (0 or 6). Haven't tried thou the other levels...mmh...tonight i'm goin' to (i'm at work right now) put a new log onto the rc missing levels (guess 2--5) and see if there is any operation at shutdown time (if i can rem well won't)...muuumble...
[B]
Any suggestion guys? I'm opened up to any kind of solutions....[/B]

---

### Post by m2xtreme on 2011-01-30
I believe I have found a solution!  Rather than mounting samba shares through /etc/fstab you should use gigolo (sudo apt-get install gigolo).  Gigolo will periodically check for the configured samba shares (I think the default is 60 seconds?) and if found will automatically mount them via nautilus.

How is this helpful?  Because when nautilus mounts shares they are mounted to a hidden folder in your home folder: /$HOME/.gvfs/"share_name at server_name"

After mounting the samba shares via nautilus you can check the exact path names by

 > cd  /$HOME/.gvfs/Now if you want to link that hidden location to somewhere else it is as simple as

      > ln -s  /$HOME/.gvfs/"share_name at server_name" /link/to/locationI hate when files have spaces in them since it tends to make things more confusing/break things in Linux but I had trouble renaming the newly made link names via terminal.  Luckily I was able to change them by "gksudo nautilius" and doing it that way.

Hope this helps.  Let me know if you need clarification with anything.

Special thanks to Moribius1 for the mounting locations, originally posted here: [http://ubuntuforums.org/showthread.php?t=1535268&highlight=slow+shutdown+samba+fstab](http://ubuntuforums.org/showthread.php?t=1535268&highlight=slow+shutdown+samba+fstab) 

[LEFT] 

    

[/LEFT]

---

