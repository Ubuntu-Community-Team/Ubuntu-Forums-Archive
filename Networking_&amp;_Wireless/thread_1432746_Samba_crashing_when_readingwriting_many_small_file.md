---
title: "Samba crashing when reading/writing many small files"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by palmboy5 on 2010-03-18
Short version: 
Samba seems to crash and come back after some seconds if I copy a lot of small files in a short period of time over the network. How do I fix it?

Long version: 
I have Ubuntu 9.10 Server 64bit running on a D945GCLF2 board sharing two 1TB ext4 formatted HDDs to my Windows PCs using samba. I've been having an issue with reading or writing files through samba. It happens during copying operations or checksumming, anything that reads or writes MANY small files in a small amount of time. I am pretty sure the problem has to do with my server because the server has run on two different LANs in different homes and will crash from activity with any of several other PCs. There is no crashing if I access the files through SSH, although when I do that the max transfer speed is less than 1MB/s.

When I induce the crashing, there is absolutely no output to the server terminal.

As an easy access example of something that will crash samba, extracting [Cinebench R11.5]("http://www.maxon.net/index.php?id=162") to the server will do the job. It always fails.

How can I fix this please?:x

---

### Post by palmboy5 on 2010-03-18
Bump!

---

### Post by jrssystemsnet on 2010-03-19
So when you say "crash", you really mean "freeze", not "crash" then, right?  If it comes back on its own without you doing anything, that's not a crash.

I'm not saying that to pick on you, I'm saying it because it's an important distinction. :)

Try changing the default I/O scheduler for your drives to **deadline** and see if that helps.  You can do this on the fly like this:

```
echo deadline > /sys/block/sdX/queue/scheduler
```

Do once for each of your active drives, **including your system drive and both shared drives**, replacing "sdX" with the actual devicename for the drive as found under /dev/.  If your "two shared drives" are actually a RAID1 array, then don't use their raw devicenames as individual drives, use the devicename of the RAID1 - ex. md0, not sdb & sdc or whatever.

Anyway, that suffices for testing - change the scheduler for all drives from "cfq" (the default, which really doesn't work worth a crap for workstations or small servers) to "deadline", then re-test.  If that improved your results, then you can make it permanent by editing your GRUB boot entry and adding "elevator=deadline" to the end of the kernel line - or if for some reason you don't want to mess with GRUB, you can just add those echo commands to the end of /etc/rc.local, which will accomplish the same thing.

---

### Post by palmboy5 on 2010-03-19
Hi, yes I suppose it would be a freeze then, although if something crucial like explorer.exe crashes in windows, it gets run again by itself. In that case it wouldn't be a freeze, right?

I don't seem to have permission to do what you said to do, even when using sudo..
```
vcn64ultra@Diamondville:/sys/block$ ls
loop0  loop3  loop6  ram1   ram12  ram15  ram4  ram7  sda
loop1  loop4  loop7  ram10  ram13  ram2   ram5  ram8  sdb
loop2  loop5  ram0   ram11  ram14  ram3   ram6  ram9
vcn64ultra@Diamondville:/sys/block$ echo deadline > /sys/block/sda/queue/scheduler
-bash: /sys/block/sda/queue/scheduler: Permission denied
vcn64ultra@Diamondville:/sys/block$ sudo echo deadline > /sys/block/sda/queue/scheduler
-bash: /sys/block/sda/queue/scheduler: Permission denied
vcn64ultra@Diamondville:/sys/block$

```
```
sudo nano /sys/block/sda/queue/scheduler
```
and then replacing all the contents with the word deadline and writing out seems successful but the file contents are still default if I reopen or cat the file.

What am I doing wrong? Do I have to kill any particular background programs? Thanks!

---

### Post by jrssystemsnet on 2010-03-19
> **palmboy5 said:**
> I don't seem to have permission to do what you said to do, even when using sudo..

Oh, I'm sorry! I forgot that the sudo doesn't pass through the redirection.  Do it this way:

```
echo deadline | sudo tee /sys/block/sda/queue/scheduler
```

Then you can cat the same file, and you should see [deadline] selected in square brackets, like this:

```
:~$ cat /sys/block/sda/queue/scheduler
noop anticipatory [deadline] cfq
```

Give that a shot (for all drives), then retry your test case with Samba and the small files, and let me know how it went.

---

### Post by palmboy5 on 2010-03-20
Both files already had the content as
```
noop anticipatory [deadline] cfq
``` before I ever changed them.. but I entered the commands anyway, as such
```
vcn64ultra@Diamondville:~$ echo deadline | sudo tee /sys/block/sda/queue/scheduler
[sudo] password for vcn64ultra:
deadline
vcn64ultra@Diamondville:~$ cat /sys/block/sda/queue/scheduler                   noop anticipatory [deadline] cfq
vcn64ultra@Diamondville:~$ echo deadline | sudo tee /sys/block/sdb/queue/scheduler
deadline
vcn64ultra@Diamondville:~$ cat /sys/block/sdb/queue/scheduler                   noop anticipatory [deadline] cfq
vcn64ultra@Diamondville:~$
```
The copy operations are still failing. :(

I'm going to try setting them to cfq now haha.

BTW, the OS is installed on a 4GB partition at the beginning of sda, so there are only 2 to change still.

---

### Post by jrssystemsnet on 2010-03-20
Well, fooey.  OK, let's try something different - can you do the same operation in some way WITHOUT Samba (like locally on the server) to see if the problem happens without Samba in the mix at all?

PS: CFQ is what you had to start with... and it pretty much sucks.  And it's what you'll have again next time you reboot anyway, if you didn't put anything in /etc/rc.local or change your GRUB menu. :)

---

### Post by jrssystemsnet on 2010-03-20
Also, you might want to try looking through /var/log/messages and /var/log/samba/smb.log to see if there are any ugly error messages popping up around the time that you're making your server cry. :)

---

### Post by palmboy5 on 2010-03-20
Setting the drives to cfq had the same errors.
There are no entries in /var/log/messages recent enough to have been caused by my recent error invocations. The time stamp of the most recent entry has a difference of more than 5 hours and I checked with "date" to make sure the system time was correct (it was correct).

The only files in /var/log/samba is a directory called "cores" and a bunch of files with prefix "log.". I tried the log ending with the name of the computer I was doing the test case on and eureka! Below are log entries from multiple error invocation tests.
```
[2010/03/19 22:27:28,  0] smbd/open.c:151(fd_open)
  Too many open files, unable to open more!  smbd's max open files = 1044
[2010/03/19 22:27:29,  0] smbd/open.c:151(fd_open)
  Too many open files, unable to open more!  smbd's max open files = 1044
[2010/03/19 22:34:00,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/03/19 22:34:00,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/03/19 22:47:00,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/03/19 22:47:00,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/03/19 22:51:54,  0] smbd/open.c:151(fd_open)
  Too many open files, unable to open more!  smbd's max open files = 1044
[2010/03/19 22:51:55,  0] smbd/open.c:151(fd_open)
  Too many open files, unable to open more!  smbd's max open files = 1044
[2010/03/19 22:51:56,  0] smbd/open.c:151(fd_open)
  Too many open files, unable to open more!  smbd's max open files = 1044
[2010/03/19 22:52:01,  0] lib/debug.c:663(reopen_logs)
  Unable to open new log file /var/log/samba/log.toledo: Too many open files
```
So either something isn't closing files or the limit should be increased? What do you make of this?

---

### Post by jrssystemsnet on 2010-03-20
Well that's interesting; Samba's default max open files setting is 10,000.

More likely, you're hitting the per-process file descriptor limit for the OS... which is easy enough to check.

```
you@box:~$ ulimit -n
1024
```

1024 is what my box returned, anyway.  So, try bumping 'er up.

```
you@box:~$ sudo -s
root@box:~# ulimit -n 8192
root@box:~# /etc/init.d/samba stop
root@box:~# /etc/init.d/samba start
root@box:~# exit
you@box:~$ 
```

Now, this is important: ulimit is a bash built-in, NOT a command on disk... so sudo doesn't work on it; that's why I did sudo -s to get a root shell there, and you're going to have to do the same thing.

What we did is - hopefully - set the per-process descriptor to 8192 temporarily, then stopped and started Samba, and then got you the heck back out of the root shell.  Now, try your crashy test again.  With luck, this time you will get through it OK.  (Also, with luck, you have plenty of RAM in this server.)

Did it work?  Then you'll probably want to set the per-process descriptor higher every time you run Samba.  AFAICT, this ought to do it for you... **sudo nano /etc/init.d/samba**, find this part:

```
		log_daemon_msg "Starting Samba daemons"
		# Make sure we have our PIDDIR, even if it's on a tmpfs
		install -o root -g root -m 755 -d $PIDDIR
```

And add this immediately afterward:

```

		ulimit -n 8192
		ulimit -n

```

The second ulimit -n without the argument isn't strictly necessary; all that does is spits out "8192" at you to let you know the ulimit really did get bumped up, whenver you do a **sudo /etc/init.d/samba start** in the future.

Caveat: I'm not that familiar with monkeying around with ulimit... so this SHOULD work, but not having something that breaks the limit handy, I can't really test it for sure.

Caveat2: you now have a non-standard init.d script for Samba, and future Samba upgrades may try to re-write it... so if this does fix your problem for you, you'd better document it well enough to remember how to put it back if upgrades replace the script at some point in the future.

Lemme know how this works, I'm curious. :popcorn:

---

### Post by jrssystemsnet on 2010-03-20
Oh - and if it doesn't work, add ```
max open files = 10000
``` to the [global] section of **/etc/samba/smb.conf**, do a **sudo /etc/init.d/samba restart**, and try it again... that shouldn't make any difference, since 10000 is the default, but it can't hurt to make SURE that Samba didn't somehow get its own value set weirdly for that.

---

### Post by palmboy5 on 2010-03-20
My box also returned 1024 as the default number. 
Amazingly, "ulimit -n 8192" allowed the server to get through my worst known test case of 67790 files! There must be a sweet spot at the point between 1024(1044) and 8192, in regards to the speed of closing files.. The server has only 1GB RAM but it didn't seem to have an issue.

I have modified /etc/init.d/samba as you instructed and rebooted to see that the worst case test still passes! :D Looks like the problem is solved, at least until I find something else. Thank you so much for your help!

P.S.
It's weird though, "ulimit -n" in the terminal still returns 1024..

---

### Post by jrssystemsnet on 2010-03-20
> **palmboy5 said:**
> My box also returned 1024 as the default number. 
It's weird though, "ulimit -n" in the terminal still returns 1024..That's 'cause ulimit is set per-process (though also inherited from parent process) - so what happens when your init script gets run is, the bash session running the init script has its ulimit set to 8192, then smbd and nmbd inherit that high ulimit of 8192, but your *own* shell still has the default 1024.

I think if you were to **sudo /etc/init.d/samba restart** while the system was up you'd end up with your own ulimit bumped up to 8192 as well as Samba's, but I'm not positive, and it shouldn't really make much difference. :)

Glad I could help!

---

