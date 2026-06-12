---
title: "mt-daapd stopped working on fiesty"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by piusvelte on 2007-08-15
I've done some searching on this, but nothing seems to directly relate to my issue. It probably doesn't help that I'm quite new to linux.

I'm running xubuntu fiesty fawn, and have setup some samba shares, mt-daapd for sharing music, and have been working on vnc4server so that I can run the box headless. Anyway, mt-daapd was running fine for a few days, and during another frustrating and failed attempt at getting vcn up and running, I decided to remove both vnc4server and X11vnc. I did this using:
sudo aptitude purge vnc4server
sudo aptitude purge X11vnc
I rebooted and since then, I can't seem to get mt-daapd working. The admin site is inaccessible, and my remote machines don't see the shared music anymore either. It may not be related, but I've been really thrashing about with the whole vnc problem. All of my shared folders, music and files are on another drive, so I could reinstall fiesty again if necessary.

Here are the steps that I used to setup mt-daapd:

sudo apt-get install libid3tag0
wget [http://prdownloads.sourceforge.net/m...2.4-1_i386.deb](http://prdownloads.sourceforge.net/m...2.4-1_i386.deb)
sudo dpkg -i /home/bryan/mt-daapd_0.2.4-1_i386.deb
sudo nano /etc/mt-daapd.conf

# change the following lines:
mp3_dir /mnt/hde1/share/music
servername Lin02 music

# restart
sudo /etc/init.d/mt-daapd restart

# webadmin
[http://localhost:3689](http://localhost:3689)
username: admin
password: mt-daapd

###
I keep pretty detailed notes, for cases such as this, so if anyone would like to know more about what I've been trying with vnc, (vnc4server, vnc4server/edgy, -extensions XFIXES), please let me know.

Thanks in advance for any help and sorry for such a long first post.

---

### Post by piusvelte on 2007-08-20
I've decided to reinstall xubuntu, so I'll see where that takes me.

---

