---
title: "Many database problems"
date: 2010-08-10
forum: Mythbuntu
---

### Post by Colonelguf on 2010-08-10
I am having multiple problems and I think they are all database related. A few days ago I ran mythfilldatabase, and while it was running the power went out. When the computer started back up, I got the invalid database password error. I searched the forum and found a way to reset and get things running. Now the backend doesn't start automatically when I boot. I have to open a terminal and start it manually. The computer is accessing the hard drive continually, and accessing the internet continually. The worst part is that my recordings are not being expired anymore. My recordings drive has been full for a long time, and myth always deleted old files to keep 5 gig free. Now the drive fills up and liveTV won't work because there is nowhere to buffer. I can manually delete some recordings from livetv or recordings and it works again until it fills up. Can anyone give me some direction on fixing this?
Thanks

---

### Post by nickrout on 2010-08-12
```
sudo /etc/cron.weekly/mythtv-database
```

will try and fix your database.

---

### Post by Colonelguf on 2010-08-13
Thanks, nickrout. I ran the command and haven't figured out if it helped. I still have to manually start the backend, but I haven't run out of disk space so far. The help is appreciated.

---

### Post by Colonelguf on 2010-08-14
I stopped having the full disk problem, but the next time i rebooted couldn't log in to the database again. this time sudo dpkg-reconfigure mythtv-database is not working.
Will search for solution.
Ran sudo dpkg-reconfigure mythtv-common and that fixed it. Rebooted and had the same problem. Ran the 2 commands and deleted extra copies of mysql.txt and got it going again. So I guess the problem is solved until the next boot. I am thinking about reinstalling, but that sounds like a hassle.

---

