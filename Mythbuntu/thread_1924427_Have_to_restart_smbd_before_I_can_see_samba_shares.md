---
title: "Have to restart smbd before I can see samba shares"
date: 2012-02-12
forum: Mythbuntu
---

### Post by AdirondackJim on 2012-02-12
Hey everyone,

I just installed Mythbuntu 11.10.  I have this quirky issue where my Windows PC won't see the samba server's shared folders until I log into the server and do a sudo restart smbd.  I have to do this every time I boot Mythbuntu.

Anyone know what's up with that?


Thanks,


Jim

---

### Post by nickrout on 2012-02-13
samba starting before network?

samba starting before the target disks are mounted?

Look in your samba or daemon logs?

---

### Post by AdirondackJim on 2012-02-15
I looked in /var/log for logs that would tell me when things get mounted and run, but I don't see anything relevant.  It's been a while since I've looked at log files--I thought syslog was it.  I looked at syslog and I only see /dev/sda1 getting mounted (root), but not my other partition.  What log files are you referring to?

In case it helps, here's output from smbd log:
[2012/02/15 18:59:30,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2012/02/15 18:59:30.165968,  0] printing/print_cups.c:109(cups_connect)
  Unable to connect to CUPS server localhost:631 - No such file or directory
[2012/02/15 18:59:30.166072,  0] printing/print_cups.c:468(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2012/02/15 18:59:30.166328,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2012/02/15 18:59:30.172862,  0] smbd/server.c:501(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2012/02/15 18:59:30.172934,  0] smbd/server.c:501(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2012/02/15 19:02:30.264829,  0] printing/print_cups.c:109(cups_connect)
  Unable to connect to CUPS server localhost:631 - No such file or directory
[2012/02/15 19:02:30.264997,  0] printing/print_cups.c:468(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2012/02/15 19:02:30.265233,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 1902 -- ignoring

<this is where I restart smbd>

[2012/02/15 19:05:37,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2012/02/15 19:05:37.620043,  0] printing/print_cups.c:109(cups_connect)
  Unable to connect to CUPS server localhost:631 - No such file or directory
[2012/02/15 19:05:37.620193,  0] printing/print_cups.c:468(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2012/02/15 19:05:37.620438,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option


Btw, this is a fresh install--I haven't touched much--modified smb.conf & hosts.allow files and mythtv stuff.

Thanks,
Jim

---

### Post by AdirondackJim on 2012-02-20
OK, I can NOT find any log file that timestamps when filesystems are mounted.  However, in my travels, I found this in a samba log that had __ffff:... (gumby is the Windows PC that doesn't see the shares):

[2012/02/20 15:44:29.608818,  0] lib/util_sock.c:1514(matchname)
  matchname: host name/address mismatch: ::ffff:192.168.0.2 != gumby
[2012/02/20 15:44:29.608877,  0] lib/util_sock.c:1635(get_peer_name)
  Matchname failed on gumby ::ffff:192.168.0.2
[2012/02/20 15:44:29.608909,  0] lib/access.c:413(check_access)
  Denied connection from UNKNOWN (::ffff:192.168.0.2)
[2012/02/20 15:44:29.608933,  1] smbd/process.c:2299(smbd_process)
  Connection denied from ::ffff:192.168.0.2

When I first encountered this, I disabled ipv6 by doing the following:
**gksudo gedit /etc/sysctl.conf**

Then add these four lines:
**net.ipv6.conf.all.disable_ipv6 = 1**
**net.ipv6.conf.default.disable_ipv6 = 1**
**net.ipv6.conf.lo.disable_ipv6 = 1**

Is this a clue as to what's going on?

Thanks,


Jim

---

### Post by ivanchic on 2012-02-22
I had similar issues with accessing existing Windows Network! I didn't disable ipv6 but manually configured ipv4 to match those on my Windows XP which I use sometimes (before that I had ipv4 set to 'Automatic'). First, I was unable even to ping Windows computer in the network. So I played a lot with **smb.conf** file, rebooted comp and... nothing. I was so frustrated, turned off computer and went home. Tomorrow, there were no problems accessing network shares and printers!

To sum up, you have to play with /etc/samba/smb.conf file using it to set Samba Client on your Ubuntu and shut down and again restart. In my smb.conf I changed following lines like this:

```
workgruop=WORKGROUP_NAME
wins support=yes
.....
security=user
.....
printing=cups
printcap name=cups
```

Of course, WORKGROUP_NAME should be replaced with the real name of your Windows network! Also, the fastest way to see is you can access network is to ping someone's IP address from the group.

I don't guarantee immediate success but it worked fine for me!

---

### Post by roelforg on 2012-02-22
> **ivanchic said:**
> I had similar issues with accessing existing Windows Network! I didn't disable ipv6 but manually configured ipv4 to match those on my Windows XP which I use sometimes (before that I had ipv4 set to 'Automatic'). First, I was unable even to ping Windows computer in the network. So I played a lot with **smb.conf** file, rebooted comp and... nothing. I was so frustrated, turned off computer and went home. Tomorrow, there were no problems accessing network shares and printers!

To sum up, you have to play with /etc/samba/smb.conf file using it to set Samba Client on your Ubuntu and shut down and again restart. In my smb.conf I changed following lines like this:

```
workgruop=WORKGROUP_NAME
wins support=yes
.....
security=user
.....
printing=cups
printcap name=cups
```Of course, WORKGROUP_NAME should be replaced with the real name of your Windows network! Also, the fastest way to see is you can access network is to ping someone's IP address from the group.

I don't guarantee immediate success but it worked fine for me!

How can you be sure he has CUPS installed?

---

### Post by ivanchic on 2012-02-22
As I said and I will repeat, it worked for me on Ubuntu 11.10 in my office. I guess that this is one way of solving the problem.

---

### Post by roelforg on 2012-02-22
> **ivanchic said:**
> As I said and I will repeat, it worked for me on Ubuntu 11.10 in my office. I guess that this is one way of solving the problem.
I meant:
That mode required the CUPS printing daemon to be present; as the error logs display connection problems, it leads me to suspect CUPS isn't installed.

---

### Post by ivanchic on 2012-02-22
I see! Well, I guess it will be a good idea to install CUPS ;)

---

### Post by nickrout on 2012-02-22
> **ivanchic said:**
> I see! Well, I guess it will be a good idea to install CUPS ;)

for god's sake you don't need cups to make samba work unless you want to run a cups based print server.

---

### Post by AdirondackJim on 2012-03-01
Thanks for the comments.  I don't think it's my samba configuration or CUPs because when I restart the daemon, things work ok.   But, I'll take another look at the config file and strip out anything that I absolutely don't need.  Maybe I'm using something that isn't up yet.

I started looking at Upstart (because of nickrout's response early on), but didn't get far.  The stuff in Upstart looks ok, but I can't find enough timestamped logs to verify the order of things.   I would like to find those, if anyone knows...

The ipv6 weirdness is the only interesting thing I've found so far.

---

### Post by chuckshunk on 2012-03-07
Hi, all . . .

Ubuntu newbie (well, sort of--I've been dabbling for years actually) here.  I had a very similar problem myself and just fixed it (I think), so I thought I'd post what I found.

After a reboot of my smbd server (also my workstation), I went to see what services were running using this command:

```
sudo initctl list
```This told me that while nmbd was running, smbd was in stop/waiting mode.  When I compared the upstart configuration for the two services (/etc/init/smbd.conf vs. /etc/init/nmbd.conf), the smbd.conf had this line in it:

```
start on (local-filesystems and net-device-up)

```whereas the nmbd.conf had this line in it:
```

start on (local-filesystems and net-device-up IFACE!=lo)
```When I changed the smbd.conf "start on" directive ("stanza" I think they call it??) to include the exclusion for the loopback interface and rebooted, my problem went away.

Of course, I have no idea what else I may have screwed up, but for now I'm happy.  Hope this helps someone.

---

