---
title: "No UPnP I believe the hard drive is full"
date: 2012-08-01
forum: Mythbuntu
---

### Post by jccubs on 2012-08-01
Turned on the TV and wanted to change the settings on a recording.  Got the message that the backend wasn't responding. Is it on.  I believe that was the message or at least it was something like that.  I tried to restart the computer and then it asked me to choose my language.  Then went to a 2 page menu that already had a password entered.  I left everything like it was but could not continue so i changed the password to my password and the same result. I did a search and found the similar problem but from 2008.  I believe my hard drive may be full, but I am very much a novice with this and cannot even locate the recordings using the file manager in Mythbuntu.  Any help with this situation is greatly appreciated.

---

### Post by nickrout on 2012-08-02
> **jccubs said:**
> Turned on the TV and wanted to change the settings on a recording.  Got the message that the backend wasn't responding. Is it on.  I believe that was the message or at least it was something like that.  I tried to restart the computer and then it asked me to choose my language.  Then went to a 2 page menu that already had a password entered.  I left everything like it was but could not continue so i changed the password to my password and the same result. I did a search and found the similar problem but from 2008.  I believe my hard drive may be full, but I am very much a novice with this and cannot even locate the recordings using the file manager in Mythbuntu.  Any help with this situation is greatly appreciated.

A default mythbuntu install places recordings in /var/lib/mythtv/recordings.

To see if your drive is full ```
df
``` (short for 'disk free'). If you want it in more usable units, ```
df -H
```

Deleting even 1 recording will possibly make your drive usable again.

---

### Post by jccubs on 2012-08-02
OK, that seems to be it i got 0% free and 100% used.  So how can I delete something using the terminal.  I really do not know much about this system.  It has worked well for me for 3 years now, but when a problem arises I am clueless.
 
Thank you in advance for any help.

---

### Post by jccubs on 2012-08-02
Had a friend help me set this up.  I have this computer networked so I can use Samba? to see the files.  I tried to delete it from another computer but it said disk is full or write protected.  I can double click the file and see it using windows media player (no sound, but I can tell which files are which so I will know what to delete.  When I typed df -H it looks as if my files are located in /var/lib.  so if I can get to there and delete a few I may be back in business.  As far as the screen that asks what language and then the second page asking for a password, can I input whatever password I want there?  Thanks again.

---

### Post by nickrout on 2012-08-03
> **jccubs said:**
> Had a friend help me set this up.  I have this computer networked so I can use Samba? to see the files.  I tried to delete it from another computer but it said disk is full or write protected.  I can double click the file and see it using windows media player (no sound, but I can tell which files are which so I will know what to delete.  When I typed df -H it looks as if my files are located in /var/lib.  so if I can get to there and delete a few I may be back in business.  As far as the screen that asks what language and then the second page asking for a password, can I input whatever password I want there?  Thanks again.

```
cd /var/lib/mythtv/recordings
ls -S|head 

```

Change Directory to /var/lib/mythtv/recordings
list files, sort by filesize, pipe through head (head prints the first few lines of the input, so it lists the largest files in the directory)

```
rm {filename}
```

where {filename} is the largest file there.

---

### Post by jccubs on 2012-08-03
so then do i type del and then the file name? Sorry I really am a novice at this terminal stuff.  Wait,is the rm short for remove?

---

### Post by anonymousdog on 2012-08-03
Yes

---

### Post by jccubs on 2012-08-03
so everytime I type cd /var/lib/mythtv/recordings i get the message:
No such file or directory
 
my terminal prompt is :
[EMAIL="jc@JC-Myth:~$"]jc@JC-Myth:~$[/EMAIL]
 
does that make aifference?

---

### Post by jccubs on 2012-08-03
OK, OK.  I believe I have deleted (removed) a few files that should get me in the clear.  So when I try to start the backend I get the same message telling me to pick my language.  I select english and the next page is asking for Hostname (it has localhost in the blank), Database name, user, and password.  Can I name these whatever I want or do they have to be whatever they were before so I do not lose my recordings or at least the way to get to the recordings.  Sorry I'm so much trouble here!

---

### Post by Lester_Burnham on 2012-08-04
Hi,

I think you're starting the frontend if it's asking those questions.
If the backend is on the same machine, use localhost.
The user/password details need to be for the backend. Type nano ~/.mythtv/mysql.txt into a terminal and you will find the other details in there. Alt+x to get out of the terminal.

If it doesn't connect, restart MySQL and mythbackend.
If still no go, start mythbackend in a terminal, to see what is going on.

Lester

---

### Post by jccubs on 2012-08-04
Alright, I typed nano ~/.mythtv/mysql.txt and got the information.  I tried again but the information on those 2 screens (when starting the frontend) was exactly the same.  I changed the info just to see what happens and then retyped nano....... and those changed to what I had entered.  after trying to start it the message simply said "cannot"  if I try to start the backend it wants to know if I want to run mythfill database.  It cannot run that either.  I do not know how to start the backend in a terminal.  This is really too confusing for a problem that would seem quite common (letting the hard drive completely fill up).  Again, my most sincerest thanks for those helping me.

---

### Post by nickrout on 2012-08-04
> **jccubs said:**
> Alright, I typed nano ~/.mythtv/mysql.txt and got the information.  I tried again but the information on those 2 screens (when starting the frontend) was exactly the same.  I changed the info just to see what happens and then retyped nano....... and those changed to what I had entered.  after trying to start it the message simply said "cannot"  if I try to start the backend it wants to know if I want to run mythfill database.  It cannot run that either.  I do not know how to start the backend in a terminal.  This is really too confusing for a problem that would seem quite common (letting the hard drive completely fill up).  Again, my most sincerest thanks for those helping me.

You seem very confused about what you are doing.

mythtv will never fill your hard drive, it keeps a portion of your hard drive free for you, but something else may have filled it.

is mythbackend running?

```
ps ax|grep mythback
```will tell you. If not, run it```
sudo service mythtv-backend start
```

then check again with the ps command. If it is not running then STOP and come back here. The logs are in /var/log/mythtv and you will need to look at the log and see if there are any clues as to what is going wrong.

Now if the backend is running you need to start mythfrontend and when it asks for the password you need to put in the one that is set in the database, I hope you can remember it. If you have hopelessly forgotten it then run in a terminal:
```
sudo dpkg-reconfigure mythtv-common
``` and set a known password (user is mythtv).

---

### Post by jccubs on 2012-08-06
I have been out of town for a couple days and I wanted to try again.  I decided to start at the beginning of the post.  First I want to thank everyone for taking the time to respond to my post!!  OK, so I typed df -H and here are my results:

Filesystem                Size      Used     Avail     Use%   Mounted on
/dev/sda1                    12G       11G         501M     96%      /
none                               521M    267k       521M       1%       /dev
none                               525M        0             525M       0%      /dev/shm
none                               525M     320k       525M       1%      /var/run
none                               525M        0            525M      0%      /var/lock
none                               525M        0             525M       0%      /lib/init/rw
/dev/sda6                  988G     918G        70G      93%     /var/lib

the 96% and the 93% used to be 100% but I was able to delete some programs to get them down.  Once it is working again I plan on deleting quite a few more.

---

### Post by jccubs on 2012-08-06
Ok Lester posted to get the other details and I have those.  It still doesn't connect.  Lester posted to restart MySQL.  I do not know how to do that.  I really suck at this so you'll have to spell it out for me.  Same for starting mythbackend.  then I can get a terminal, but wouldn't know how to start the backend in a terminal.  I'm going to keep trying here and If I get any further I will post immediately.

---

### Post by jccubs on 2012-08-06
OK, tried to type ps ax and then there is a line vertically in your post.  I don't know if that was a lower case "L" or what?  anyway I typed in only ps ax and got this

jc@JC-Myth:~$ ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     1:25 /sbin/init
    2 ?        S      0:00 [kthreadd]
    3 ?        S      0:00 [migration/0]
    4 ?        S      0:02 [ksoftirqd/0]
    5 ?        S      0:00 [watchdog/0]
    6 ?        S      0:01 [events/0]
    7 ?        S      0:00 [cpuset]
    8 ?        S      0:00 [khelper]
    9 ?        S      0:00 [netns]
   10 ?        S      0:00 [async/mgr]
   11 ?        S      0:00 [pm]
   12 ?        S      0:00 [sync_supers]
   13 ?        S      0:00 [bdi-default]
   14 ?        S      0:00 [kintegrityd/0]
   15 ?        S      0:02 [kblockd/0]
   16 ?        S      0:00 [kacpid]
   17 ?        S      0:00 [kacpi_notify]
   18 ?        S      0:00 [kacpi_hotplug]
   19 ?        S      0:32 [ata/0]
   20 ?        S      0:00 [ata_aux]
   21 ?        S      0:00 [ksuspend_usbd]
   22 ?        S      0:00 [khubd]
   23 ?        S      0:00 [kseriod]
   24 ?        S      0:00 [kmmcd]
   27 ?        S      0:00 [khungtaskd]
   28 ?        S      0:17 [kswapd0]
   29 ?        SN     0:00 [ksmd]
   30 ?        S      0:00 [aio/0]
   31 ?        S      0:00 [ecryptfs-kthrea]
   32 ?        S      0:00 [crypto/0]
   36 ?        S      0:00 [kstriped]
   37 ?        S      0:00 [kmpathd/0]
   38 ?        S      0:00 [kmpath_handlerd]
   39 ?        S      0:00 [ksnapd]
   40 ?        S      2:13 [kondemand/0]
   41 ?        S      0:00 [kconservative/0]
  255 ?        S      1:04 [scsi_eh_0]
  256 ?        S      0:00 [scsi_eh_1]
  262 ?        S      0:00 [usbhid_resumer]
  264 ?        S      0:00 [scsi_eh_2]
  265 ?        S      0:00 [scsi_eh_3]
  266 ?        S      0:00 [scsi_eh_4]
  267 ?        S      0:00 [scsi_eh_5]
  288 ?        S      0:10 [kjournald]
  327 ?        S      0:02 [flush-8:0]
  347 ?        S      0:00 upstart-udev-bridge --daemon
  351 ?        S<s    0:00 udevd --daemon
  535 ?        S<     0:00 udevd --daemon
  536 ?        S<     0:00 udevd --daemon
  600 ?        S      0:00 [kpsmoused]
  683 ?        S<s    0:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --device
  689 ?        S      0:00 [xfs_mru_cache]
  690 ?        S      0:00 [xfslogd/0]
  691 ?        S      0:00 [xfsdatad/0]
  692 ?        S      0:00 [xfsconvertd/0]
  693 ?        S      0:01 [xfsbufd]
  708 ?        S      0:01 [xfsaild]
  719 ?        S      0:00 [hd-audio0]
  747 ?        S      0:00 [xfssyncd]
  783 ?        Ss     0:00 /usr/sbin/sshd -D
  785 ?        Ss     0:00 smbd -F
  793 ?        Sl     0:24 rsyslogd -c4
  800 ?        Ss     0:01 dbus-daemon --system --fork
  806 ?        Ssl    0:00 gdm-binary
  823 ?        S      0:00 smbd -F
  825 ?        Sl     0:00 /usr/sbin/console-kit-daemon --no-daemon
  892 ?        Sl     0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome
  894 ?        Ssl    0:00 NetworkManager
  896 ?        S      0:00 /usr/sbin/modem-manager
  899 ?        S      0:00 /sbin/wpa_supplicant -u -s
  900 ?        S      0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp
  904 tty7     Ss+  302:35 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-fo
  937 tty4     Ss+    0:00 /sbin/getty -8 38400 tty4
  942 tty5     Ss+    0:00 /sbin/getty -8 38400 tty5
  955 tty2     Ss+    0:00 /sbin/getty -8 38400 tty2
  956 tty3     Ss+    0:00 /sbin/getty -8 38400 tty3
  959 tty6     Ss+    0:00 /sbin/getty -8 38400 tty6
  960 ?        Ss     0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
  964 ?        Ss     0:00 cron
  965 ?        Ss     0:00 atd
 1042 ?        Ssl    2:10 /usr/sbin/mysqld
 1145 ?        Ss     0:02 nmbd -D
 1151 ?        Ss     0:05 /usr/sbin/apache2 -k start
 1203 ?        Ss     0:07 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 105:108
 1268 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session
 1293 tty1     Ss+    0:00 /sbin/getty -8 38400 tty1
 1310 ?        Sl     0:00 /usr/lib/gdm/gdm-session-worker
 1313 ?        S      0:00 /usr/lib/upower/upowerd
 1318 ?        S      0:00 /usr/lib/policykit-1/polkitd
 1345 ?        Ssl    0:02 /usr/sbin/hald
 1346 ?        S      0:00 hald-runner
 1436 ?        S      0:00 hald-addon-input: Listening on /dev/input/event3 /dev
 1467 ?        S      0:43 hald-addon-storage: polling /dev/sr0 (every 2 sec)
 1481 ?        S      0:00 /usr/lib/hal/hald-addon-cpufreq
 1496 ?        S      0:00 hald-addon-acpi: listening on acpid socket /var/run/a
 1657 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
 1679 ?        Ss     0:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xser
 1706 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 1709 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/share/m
 1710 ?        Ss     0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address
 1714 ?        Ssl    0:00 /usr/bin/mtd -d
 1730 ?        S      0:02 xscreensaver -no-splash
 1734 ?        S      0:00 /usr/bin/xfce4-session
 1736 ?        S      0:00 /usr/lib/xfconfd
 1742 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2
 1743 ?        S      0:00 xfsettingsd
 1745 ?        S      0:02 xfwm4
 1747 ?        S      0:09 xfce4-panel
 1749 ?        Sl     0:24 Thunar --daemon
 1751 ?        S      0:06 xfdesktop
 1779 ?        S      0:00 /usr/lib/gamin/gam_server
 1784 ?        Ss     0:02 gnome-power-manager
 1786 ?        Ss     0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authenticatio
 1790 ?        Ss     0:00 bluetooth-applet
 1794 ?        Ss     0:00 nm-applet --sm-disable
 1796 ?        Ss     0:12 update-notifier
 1797 ?        S      0:00 xfce4-settings-helper
 1799 ?        Sl     0:07 /usr/lib/udisks/udisks-daemon
 1800 ?        S      0:23 udisks-daemon: polling /dev/sr0
 1801 ?        Sl     0:00 /usr/lib/xfce4/panel-plugins/xfce4-menu-plugin socket
 1803 ?        S      0:00 /usr/lib/gvfs/gvfsd
26489 ?        S      0:00 /usr/sbin/apache2 -k start
26490 ?        S      0:00 /usr/sbin/apache2 -k start
26491 ?        S      0:00 /usr/sbin/apache2 -k start
26492 ?        S      0:00 /usr/sbin/apache2 -k start
26493 ?        S      0:00 /usr/sbin/apache2 -k start
27845 ?        Rsl    0:00 xfce4-terminal
27847 ?        S      0:00 gnome-pty-helper
27848 pts/0    Ss     0:00 bash
28119 ?        Ssl    1:33 /usr/lib/firefox/firefox
29272 ?        Ss     0:00 /bin/sh -e /proc/self/fd/11
29273 ?        Sl     0:00 /usr/bin/mythbackend --logfile /var/log/mythtv/mythba
29278 pts/0    R+     0:00 ps ax

Then I typed sudo service mythtv-backend start and after entering my password it said:
Job is already running:mythtv-backend.

---

### Post by jccubs on 2012-08-06
Tried to start the frontend again and got the same questions.  Language I said English.

*Hostname I put localhost

ping test server is checked

Port is empty

Database name is JC-Myth

user is mythtv

password is known (I use the same one for almost everything)

Page 2

ues custom identifier for frontend preferences is not checked

Enable Database server wake up is not checked

I click Finish and the next screen just says:

cannot and when I click it I go back to the hostname page.

---

### Post by Lester_Burnham on 2012-08-07
Hi,

The sda1 patition is a bit on the small side.
Why did you change the database name :).You sure it's not mythconverg still?
Anyway, to start the backend in a terminal first you need to stop it 
```
sudo service mythbackend stop
```
To start in a terminal
```
sudo mythbackend
```
Now you will see any errors in the terminal if the backend can't start or has issues. When you close the terminal the backend will be stopped.

To start mysql
```
sudo service mysql start
```

To check databases in mysql 
mysql -u mythtv -p
enter mysql password for mythtv
show databases;
to exit mysql type quit

I'm no expert at mysql, just googling what I'm trying to find out. Which is, if your database really is called JC-Myth.
Lester

---

### Post by jccubs on 2012-08-07
The screen saver that comes on automatically when there is nothing going on for a while (I'm 100% sure you are quite farmiliar with screen savers).  Well it says JC-Myth generic.  I will try it with that first and then back to the default if that does not work.

---

### Post by tgm4883 on 2012-08-07
> **jccubs said:**
> The screen saver that comes on automatically when there is nothing going on for a while (I'm 100% sure you are quite farmiliar with screen savers).  Well it says JC-Myth generic.  I will try it with that first and then back to the default if that does not work.

That would be the machine name, not the database name. Your database is likely 'mythconverg'

---

### Post by tgm4883 on 2012-08-07
So I just read back a few posts. I'm assuming that the frontend and backend are on the same machine since you are using localhost. Looks like you are using incorrect settings when the frontend asks.

Your database name is likely mythconverg, not jc-myth.

Your username is mythtv

Your password is likely wrong. You need to look in /etc/mythtv/mysql.txt  (this file will actually have the username, password, dbname, and dbhost)

If it doesn't connect after that, then you need to try

```
mysql -u mythtv -p mythconverg
```

When that prompts you for a password, use the one from mysql.txt.

---

### Post by jccubs on 2012-08-07
tried this and got the following:

jc@JC-Myth:~$ sudo mythbackend
2012-08-07 21:27:58.059 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2012-08-07 21:27:58.060 Using runtime prefix = /usr
2012-08-07 21:27:58.060 Using configuration directory = /home/jc/.mythtv
2012-08-07 21:27:58.060 Empty LocalHostName.
2012-08-07 21:27:58.060 Using localhost value of JC-Myth
2012-08-07 21:27:58.069 New DB connection, total: 1
2012-08-07 21:27:58.077 Unable to connect to database!
2012-08-07 21:27:58.077 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

---

### Post by jccubs on 2012-08-07
then typed in this and got the following:

jc@JC-Myth:~$ /etc/mythtv/mysql.txt
bash: /etc/mythtv/mysql.txt: Permission denied
jc@JC-Myth:~$

---

### Post by Lester_Burnham on 2012-08-07
Hi, 

Try using the way I showed you previously, as it's a shortcut or symlink to that file anyway.
```
nano ~/.mythtv/mysql.txt
```

Remember, if you can't find a file etc. just navigate through the folders using thunar file manager or list the directory from the command line..

Then fix the settings in the backend and see if it starts this time. Hopefully the password in that file is correct.

Lester

---

### Post by jccubs on 2012-08-08
got this:

DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=chicago
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv every time.
# NO TWO HOSTS MAY USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here
                               [ Read 39 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by nickrout on 2012-08-08
> **jccubs said:**
> then typed in this and got the following:

jc@JC-Myth:~$ /etc/mythtv/mysql.txt
bash: /etc/mythtv/mysql.txt: Permission denied
jc@JC-Myth:~$

yes because /etc/mythtv/mysql.txt is NOT a command it is a FILE containing setup information for mythtv Specifically the database connection details. If you want to READ a file use the cat command, like```
cat /etc/mythtv/msql.txt
```

If it scrolls past too quick pipe it through less, eg```
cat /etc/mythtv/mysql.txt | less
```. use the space bar to scroll through, q to exit (quit).

The | symbol is the pipe symbol, on my keyboard it is <shift>+\ but it varies by keyboard.

If the password does not work you need to use the command I have already given to reset it to something known. ```
sudo dpkg-reconfigure mythtv-common
```

---

### Post by jccubs on 2012-08-08
OK, I type in sudo dpkg-reconfigure mythtv-common.  I go through the screens and enter a new password.  I try to run the frontend and the same screen comes up.  It already has all the information including the new password that I entered in the reconfigure, but will still not work.  After I click finish on page 2 i get a scteen that only has "cannot" right in the middle of the screen with "OK" as the only thing to click.  once I click OK it takes me back to page 1.  I don't have a problem doing whatever it takes to get back up and running including reloading everything, but would prefer to keep my saved recordings.  I'm not good at this as you can all tell, but I will try to do whatever I am told.  The pipe symbol for me is works also  | .

---

### Post by jccubs on 2012-08-08
also did the following:

jc@JC-Myth:~$ ps ax|grep mythback
 5847 ?        Sl     0:00 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --user mythtv
 5853 pts/0    S+     0:00 grep mythback


also:

jc@JC-Myth:~$ sudo service mythtv-backend start
start: Job is already running: mythtv-backend

---

### Post by Lester_Burnham on 2012-08-09
Hi, 

So what do you get when you stop the backend and run it in a terminal? Does it connect to mysql ok?
You need to make sure of that before moving on.

Lester

---

### Post by tgm4883 on 2012-08-09
<Zinn> If you are having problems connecting to your mysql database, perform the following to reconfigure it: [1] sudo dpkg-reconfigure mysql-server-5.5 (pay attention to the root password you set, you will need it later)  [2] sudo dpkg-reconfigure mythtv-database [3] sudo dpkg-reconfigure mythtv-common

---

### Post by jccubs on 2012-08-09
OK tried step #1 snd got this:

jc@JC-Myth:~$ sudo dpkg-reconfigure mysql-server-5.5
Package `mysql-server-5.5' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql-server-5.5 is not installed
jc@JC-Myth:~$

---

### Post by tgm4883 on 2012-08-10
> **jccubs said:**
> OK tried step #1 snd got this:

jc@JC-Myth:~$ sudo dpkg-reconfigure mysql-server-5.5
Package `mysql-server-5.5' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql-server-5.5 is not installed
jc@JC-Myth:~$

Which version of Mythbuntu are you on

---

### Post by jccubs on 2012-08-10
I don't knkow how to check what version of myth I am running.

---

### Post by jccubs on 2012-08-10
I believe I posted about what it says when I try to run the backend from a terminal.

---

### Post by jccubs on 2012-08-10
did the following:

jc@JC-Myth:~$ sudo service mythtv-backend stop
[sudo] password for jc: 
mythtv-backend stop/waiting
jc@JC-Myth:~$ sudo service mythtv-backend start
mythtv-backend start/running, process 29035
jc@JC-Myth:~$

---

### Post by tgm4883 on 2012-08-11
> **jccubs said:**
> did the following:

jc@JC-Myth:~$ sudo service mythtv-backend stop
[sudo] password for jc: 
mythtv-backend stop/waiting
jc@JC-Myth:~$ sudo service mythtv-backend start
mythtv-backend start/running, process 29035
jc@JC-Myth:~$

Post the output of

```
lsb_release -a
```

---

### Post by nickrout on 2012-08-11
> **jccubs said:**
> I don't knkow how to check what version of myth I am running.

You weren't asked what version of mythtv you were using. You were asked what version of mythbuntu.

---

### Post by Lester_Burnham on 2012-08-11
> **jccubs said:**
> I believe I posted about what it says when I try to run the backend from a terminal.

The purpose of that was to try and see if you were still not able to connect to the database after you reconfigured database passwords etc.

A google search would've shown what you need to do to find what version of mythbuntu you are running.
You're not even trying to help yourself on simple things. If you keep following that path, you won't learn anything.

Lester

---

### Post by jccubs on 2012-08-11
I did the google search and there are tons of listings to tell which version of Ubuntu you are running but none (that I could find) that would show me how to tell which version of Mythbuntu I am running.  I have done a TON of google searches to try to resolve this.  I certainly can reload everything and have no problem doing that, but I would like to save my recordings.  I certainly do not wish to be a burden on anyone.

---

### Post by jccubs on 2012-08-11
When I go to Update Manager and click settings at the bottom of the window the click Other Software it says cdrom"[Mythbuntu 9.04_Jaunty Jackalope_-Release i386 (2009 it )J/jaunth main restricted universe - don't know if that is what you are looking for.  I have been running all updates since it was installed with no problems.

---

### Post by jccubs on 2012-08-11
jc@JC-Myth:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid

---

### Post by nickrout on 2012-08-12
> **jccubs said:**
> jc@JC-Myth:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid

Then I think your mysql version is 5.1. Adjust the commands given previously accordingly.

Also tab completeion should work to produce the full package name.

---

### Post by tgm4883 on 2012-08-12
> **nickrout said:**
> Then I think your mysql version is 5.1. Adjust the commands given previously accordingly.

Also tab completeion should work to produce the full package name.

Yep, he'll just need to use the same commands I posted earlier and adjust for 5.1 instead of 5.5

---

### Post by jccubs on 2012-08-12
Thank you!Thank you!Thank you!Thank you!Thank you!Thank you!Thank you!Thank you!Thank you!Thank you!Thank you!Thank you! 1000 times thank you.  It all seems to be working now.  I will mark this as solved, but if there is a way to avoid this or anything please feel free to let me know.  Once again thank you for your patience and help in this matter!!!!!

---

