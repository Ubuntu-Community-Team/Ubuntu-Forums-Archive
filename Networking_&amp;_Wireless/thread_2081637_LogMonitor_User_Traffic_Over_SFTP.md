---
title: "Log/Monitor User Traffic Over SFTP"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by cheflo on 2012-11-07
Hello,
I'm using Ubuntu Server 12.04 to set up a server via OpenSSH that I use to share pics with my friends via SFTP. I have them chrooted to a common directory and in /var/log/auth.log I can see everyone who opens a connection to the server, which is great. I can also monitor current network traffic with iftop.

However, I cannot view which file a specific user is downloading. I would like to log the files being downloaded by each user, so that I can see how much different users are using my server. Is it possible to obtain this data and could I get it in a file looking something like this:

USER...CONNECTION........FILE......START....END......AVG.SPEED
alex.......sftp.........pic5.jpg....02:03....02:05......15Mbit/s
john.......sftp.........folder1.....04:00....04:55......1Mbit/s

Any feedback is greatly welcome since I'm going mad trying to achieve this with rsyslog right now.

---

### Post by Lars Noodén on 2012-11-07
Try setting the log level to INFO.  The filenames will be logged to auth.log

```

Subsystem       sftp    /usr/libexec/openssh/sftp-server -l INFO

```

Or

```

Subsystem       sftp    internal-sftp -l INFO

```

Be aware that this severely violates user privacy.

Alternately, you can use -f to change the log facility from AUTH to something else and then capture the logs in a different file.

---

### Post by Lars Noodén on 2012-11-07
When you are logging at log level INFO, you can sort out the traffic by adding a file /etc/rsyslog.d/60-sftp-server.conf with the following content.

```

:syslogtag,startswith,"sftp-server" /var/log/sftp-server.log

```

That will get you the files that were successfully transfered into their own log file, while still leaving auth.log untouched.  

If you want all sftp traffic, including login status, logged to the separate file, then you should change the log facility of sftp-server / internal-sftp to LOCAL0 or something like that.  

```

Subsystem sftp internal-sftp -f LOCAL0 -l INFO

```

Then the rsyslog configuration file should read like this.

```

local0.*                       /var/log/sftp-server.log

```

I notice that sftp-server doesn't seem to log filenames from attempts to upload or download files that don't exist.

---

### Post by cheflo on 2012-11-07
Thank you for your prompt response Lars!
You suggestions worked perfectly for non-chrooted SFTP users, but didn't worked for my chrooted users. However, it led me on the right track in contrasting the differences between logging for non-chroot and chroot.

So, after a minor trip to hell and back, understanding the different procedures of  adding sockets in syslogd/rsyslogd, as well the logging structures in centOS/debian, I **FINALLY** got this to **WORK**. A lot of help came from this thread  [http://kb.monitorware.com/log-sftp-chroot-with-rssh-t10497.html](http://kb.monitorware.com/log-sftp-chroot-with-rssh-t10497.html) and here is what my setup looks like:

In /etc/ssh/sshd_config
```
Subsystem sftp internal-sftp -f LOCAL7 -l INFO
Match group sftpusers
        ChrootDirectory /SFTP
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp -f LOCAL7 -l INFO
```

Then I created /etc/rsyslog.d/60-sftp.conf and added the following three commands.```

# Create an additional socket for some of the sshd chrooted users.
$AddUnixListenSocket /SFTP/dev/log

# Parse the data logged at level INFO and facility LOCAL7 into /var/log/sftp.log
local7.info /var/log/sftp.log

# Report logins and logoffs
:syslogtag,startswith,"sftp-server" /var/log/sftp.log
```

Finally, I created the directory specified in 60-sftp.conf, which for me was /SFTP/dev (basically, there needs to be a "dev" directory at the root level of the chroot)

Now, when someone logs in to my chroot and transfer files, a file called "log" is created by rsyslog in /SFTP/dev and the information from this file is parsed into /var/log/sftp.log where I can read it. To see who did what, I use two commands.
```
cat /var/log/sftp.log | grep [username]
# Among other things, this returns a number that I use in the next command
cat /var/log/sftp.log | grep [number] | grep -w -e close -e remove
```

Phew! Thats one day of frustration, but with a happy ending! \\:D/ Thanks again!

(The only thing still a mystery is the prefixes for the files in rsyslog.d/. Are these (10,50,60) just to get the files processed in the correct order? I know the GRUB config has the same setup, since a few distro updates back.)

---

### Post by Lars Noodén on 2012-11-08
Glad it's working.  I missed the part about chroot.

These two lines in rsyslog's configuration file might be redundant.  It is probably necessary to have only one.  Having two means getting double entries.

```

# Parse the data logged at level INFO and facility LOCAL7 into /var/log/sftp.log
local7.info /var/log/sftp.log

# Report logins and logoffs
:syslogtag,startswith,"sftp-server" /var/log/sftp.log

```

---

### Post by cheflo on 2012-11-08
For me that's not the case. The first line reports reading and writing of files by my chrooted users and the second line only reports their logins and logoffs. When I leave one of them out, the respective information is not shown in /var/logs/sftp.log.

---

### Post by teledyn on 2013-08-06
Thanks so much for this, I think the source of my own woes may have been the chroot environment, although the recipe I followed asked that the chroot be set to %h, which is the sftp user's home directory, and that to me makes more sense, but then does that mean my dev must be in each home directory?

and I'm also not quite following the magic happening here:

> **cheflo said:**
> Now, when someone logs in to my chroot and transfer files, a file called "log" is created by rsyslog in /SFTP/dev and the information from this file is parsed into /var/log/sftp.log where I can read it. 

do you do anything to get that socket dev put into the legible log?  Is that what the pattern-match and local7 lines will do in this situation?

---

### Post by Joe_Carroll on 2014-02-07
teledyn, did you ever get logging working for chrooted users? I've configured our system with %h also and I'm having trouble with this. I've created separate dev directories and sockets for both users concerned. Logging works fine for non-chrooted users.

---

### Post by Joe_Carroll on 2014-02-07
Ah, now I spotted my problem: I forgot to update the [COLOR=#000000][FONT=Ubuntu Mono]ForceCommand[/FONT][/COLOR] directive for the chrooted group :-) Thanks a million to cheflo for documenting this solution clearly here.

---

