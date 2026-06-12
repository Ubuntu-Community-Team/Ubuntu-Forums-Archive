---
title: "Rsync with Gadmin to freenas"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by tobytennant on 2009-06-22
Hello,
I am currently trying to backup my ubuntu system to a freenas server using rsync. I am using Gadmin to configure the setup and of my laptop to use rsync with my freenas NAS. I have configured my freenas to use the Private key that Gadmin generates. I am just having a problem with it producing this error message:

'rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.5]'

Could anyone explain what this error message means. Any any suggestions to remedy it.

Thank you,
Toby Tennant

I am not sure that this is in the right area of the forum so if anyone can suggest where else to post it. I would very much apreciate it.

---

### Post by jonobr on 2009-06-23
no takers on this one eh?

I would try a couple of things,

I would try to do an rsync without the gui and see if there is anything that may indicate whats going on

eg
```
rsync -avz <hostname>:~/Desktop/mystuff .
```

I have not used gadmin for this myself but again I would remove the gui to see if there are any additional clues.

Secondly I would just check my connections using another transport protocol such as ftp or scp

```
scp myname@<remoteip>:~/Desktop/mystuff .
```

Although it seems as if not a lot is working on rsync Im thinking scp wont have a problem

---

### Post by tobytennant on 2009-06-23
Thank you for your help I tried out scp and managed to get it to transfer. Although I couldn't get rsync to complete succesfully. I get the same error when I try and use rsync as I got in gadmin.

---

### Post by jonobr on 2009-06-23
Hello


My guess would be that your rsync daemon/server is not setup correctly?

Using rsync is much better as with scp you will copy over the same stuff over and over again,
rsync will only copy over the differences between the two sides

The important thing is that you can see you network is ok, and your transport works to your freenas.
it seems specific to rsync.

So a few questions I would have is how are you using rsync how have you set it up?

If you could post results from
```

cat /etc/default/rsync
cat /etc/xinetd.d/rsync 
cat /etc/rsyncd.conf

```
This will show how you have setup your system

---

### Post by tobytennant on 2009-06-23
This is what my config files are on my ubuntu laptop I am trying to backup:

toby@toby-laptop:~$ cat /etc/default/rsync
# defaults file for rsync daemon mode

# start rsync in daemon mode from init.d script?
#  only allowed values are "true", "false", and "inetd"
#  Use "inetd" if you want to start the rsyncd from inetd,
#  all this does is prevent the init.d script from printing a message
#  about not starting rsyncd (you still need to modify inetd's config yourself).
RSYNC_ENABLE=false

# which file should be used as the configuration file for rsync.
# This file is used instead of the default /etc/rsyncd.conf
# Warning: This option has no effect if the daemon is accessed
#          using a remote shell. When using a different file for
#          rsync you might want to symlink /etc/rsyncd.conf to
#          that file.
# RSYNC_CONFIG_FILE=

# what extra options to give rsync --daemon?
#  that excludes the --daemon; that's always done in the init.d script
#  Possibilities are:
#   --address=123.45.67.89		(bind to a specific IP address)
#   --port=8730				(bind to specified port; default 873)
RSYNC_OPTS=''

# run rsyncd at a nice level?
#  the rsync daemon can impact performance due to much I/O and CPU usage,
#  so you may want to run it at a nicer priority than the default priority.
#  Allowed values are 0 - 19 inclusive; 10 is a reasonable value.
RSYNC_NICE=''

# Don't forget to create an appropriate config file,
# else the daemon will not start.
toby@toby-laptop:~$ cat /etc/xinetd.d/rsync 
cat: /etc/xinetd.d/rsync: No such file or directory
toby@toby-laptop:~$ cat /etc/rsyncd.conf
cat: /etc/rsyncd.conf: No such file or directory
toby@toby-laptop:~$

Do you need my config files for my server. I was reading on the freenas site on how to set up backup in windows. It was saying that the server needed to be setup to pull the files to the server. With the freenas box acting as a client. Am I right to have my laptop pushing the files to backup?

---

