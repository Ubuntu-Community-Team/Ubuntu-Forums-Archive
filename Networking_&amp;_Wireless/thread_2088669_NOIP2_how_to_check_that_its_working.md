---
title: "NOIP2: how to check that its working?"
date: 2012-11-27
forum: Networking &amp; Wireless
---

### Post by alek66 on 2012-11-27
I have installed and configured, apparently correctly, how can I test it?

Is there a way to force the update for the DNS. So I check on the website?

Thanks!

---

### Post by efflandt on 2012-11-28
```
host your_full_noip_name
```

See if that points to your public IP.

TTL is apparently 60 seconds (to expire from DNS cache), but not sure how often noip2 running as a daemon contacts them to grab your public IP.  I use a Perl script as a daemon with LWP module to poll/parse the web interface of my DSL modem/router every 5 minutes and it logs to syslog hourly.  If my PPPoE IP changes, it just runs noip2 once to notify them to update and also posts the IP change to syslog.

---

### Post by alek66 on 2012-11-28
> **efflandt said:**
> ```
host your_full_noip_name
```

See if that points to your public IP.

TTL is apparently 60 seconds (to expire from DNS cache), but not sure how often noip2 running as a daemon contacts them to grab your public IP.  I use a Perl script as a daemon with LWP module to poll/parse the web interface of my DSL modem/router every 5 minutes and it logs to syslog hourly.  If my PPPoE IP changes, it just runs noip2 once to notify them to update and also posts the IP change to syslog.


Thanks, what I was looking for was more of a command line thing, to force update, and see if it is work at the moment.

I have doubts that its not working, and dont know how to debug it.

---

### Post by SlugSlug on 2012-11-28
put in a duff IP via the webpage, reboot or restart service and see if it's updated ?

---

### Post by alek66 on 2012-11-28
> **SlugSlug said:**
> put in a duff IP via the webpage, reboot or restart service and see if it's updated ?

How do I restart the noip2 service???

its not listed under service noip2 restart...

---

### Post by SlugSlug on 2012-11-28
```
sudo /etc/init.d/noip2 restart
```

if not post output of 

```
ls /etc/init.d/
```

---

### Post by alek66 on 2012-11-28
> **SlugSlug said:**
> ```
sudo /etc/init.d/noip2 restart
```

if not post output of 

```
ls /etc/init.d/
```
Hey, thanks for helping out

heres the init.d
 ```
ls /etc/init.d/
ajenti             modemmanager                 rfkill-store
alsa-restore       module-init-tools            rsync
alsa-store         munin-node                   rsyslog
anacron            mysql                        sendsigs
apache2            netatalk                     setvtrgb
apparmor           networking                   single
apport             network-interface            skeleton
atd                network-interface-container  ssh
avahi-daemon       network-interface-security   stop-bootlogd
binfmt-support     network-manager              stop-bootlogd-single
bluetooth          ntp                          subsonic
bootlogd           nullmailer                   sudo
console-setup      ondemand                     supervisor
cron               passwd                       udev
cups               plymouth                     udev-fallback-graphics
dbus               plymouth-log                 udev-finish
dmesg              plymouth-splash              udevmonitor
dns-clean          plymouth-stop                udevtrigger
friendly-recovery  plymouth-upstart-bridge      ufw
grub-common        pppd-dns                     umountfs
halt               procps                       umountnfs.sh
hddtemp            ps3mediaserver               umountroot
hostname           rc                           unattended-upgrades
hwclock            rc.local                     urandom
hwclock-save       rcS                          vnstat
irqbalance         README                       vsftpd
killprocs          reboot                       x11-common
lightdm            resolvconf                   zoneminder
lm-sensors         rfkill-restore
```


I only did this:

cd /usr/local/src/
wget [http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz](http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz)
tar xf noip-duc-linux.tar.gz
cd noip-2.1.9-1/
make install

And configured the user and password. I didnt do anything else.

---

### Post by imdw on 2012-12-15
Hallo.

Check the readme file which comes with the tarball you downloaded.

Put the script
```
 #######################################################
        #! /bin/sh
        # . /etc/rc.d/init.d/functions  # uncomment/modify for your killproc
        case "$1" in
            start)
                echo "Starting noip2."
                /usr/local/bin/noip2
            ;;
            stop)
                echo -n "Shutting down noip2."
                killproc -TERM /usr/local/bin/noip2
            ;;
            *)
                echo "Usage: $0 {start|stop}"
                exit 1
        esac
        exit 0
        #######################################################

```

in the /etc/init.d folder (call it as you want)
 than created a symbolic link in the /etc/rc6.d folder to the script

and that should work

---

### Post by alek66 on 2012-12-18
> **imdw said:**
> Hallo.

Check the readme file which comes with the tarball you downloaded.

Put the script
```
 #######################################################
        #! /bin/sh
        # . /etc/rc.d/init.d/functions  # uncomment/modify for your killproc
        case "$1" in
            start)
                echo "Starting noip2."
                /usr/local/bin/noip2
            ;;
            stop)
                echo -n "Shutting down noip2."
                killproc -TERM /usr/local/bin/noip2
            ;;
            *)
                echo "Usage: $0 {start|stop}"
                exit 1
        esac
        exit 0
        #######################################################

```

in the /etc/init.d folder (call it as you want)
 than created a symbolic link in the /etc/rc6.d folder to the script

and that should work


Hey thanks!
I did:

In /etc/init.d/
touch noip
pasted the script into that noip file created.

ln -s /etc/init.d/noip2 /etc/rc6.d/

Thats all?

---

### Post by alek66 on 2012-12-19
Guys I don't see that its working after installing everything and letting one day (after reboot)

The date now: 19/DEC/2012

NO IPs Last Update: 2012-12-17 13:04:32 PST

How can I debug to see whats wrong?

---

### Post by chuckiv on 2013-05-01
I would also like to know the answer here. Bump^^

I've been thinking... all that script does is call /usr/local/bin/noip2
And the script doesn't seem to be for ubuntu

Can't we just add the line /usr/local/bin/noip2 to /etc/rc.local ?

Check with ps -A or ps -A | grep noip2

should work

---

### Post by sourchier on 2013-05-04
I am using a script that I found online for noip. I found that script here:

[http://siripong-computer-tips.blogspot.de/2012/01/run-noip-duc-automatically-when-debian.html]("http://siripong-computer-tips.blogspot.de/2012/01/run-noip-duc-automatically-when-debian.html")

---

