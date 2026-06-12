---
title: "MythTV-Database reconfigure required... help"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by goldencj on 2007-12-27
"MythTV-Database reconfigure required

The mythtv-database package was upgraded or installed, but was unable to contact a MySQL server. . If you were in the process of dist-upgrading, this is normal as mysql-server  is stopped for a portion of the upgrade. . If this is a fresh package installation, verify that mysql-server is installed and running.  Once you have verified the server is running, you can reconfigure  the package by running 'sudo dpkg-reconfigure mythtv-database'. . If your root password or location of the MySQL server are non standard, you can also update them via 'sudo dpkg-reconfigure mythtv-database'."

How do I verify the mysql-server is installed and running?

---

### Post by goldencj on 2007-12-30
tlc@tlc-desktop:~$ ps -c mysql-server
ERROR: Unsupported option (BSD syntax)
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy
tlc@tlc-desktop:~$

This is what came up.  What does it mean?

---

