---
title: "duplicity ftp help needed"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by jlparsons on 2011-12-14
Hi folks, scripting newbie here, probably doing something face-palmingly obviously wrong...

I'm trying to write a script to instruct duplicity to backup to my NAS FTP drive.  I'm then going to cron it so it backs up incrementally every few hours in the background as root.  I'm using the instructions [>>here<<]("https://help.ubuntu.com/community/DuplicityBackupHowto") Problem is I can't get the thing to access my ftp drive.  This is what I've got:[INDENT]```
export PASSPHRASE="mypassphrase"
export FTP_PASSWORD="myftp"
duplicity /home/"directorytobebackedup" ftp://"username"@192.168.0.4/"myfolder"
unset PASSPHRASE
unset FTP_PASSWORD
```[/INDENT]Items "in quotes" are replacements obviously.  On the log file I find this:[INDENT]failed with code 3 (attempt #1)
Error is:
Remote host has closed the connection.
ncftpput "Backupdirectory"/duplicity-full.20111214T152750Z.vol1.difftar.gpg: could not send file to remote host.

[/INDENT]Help!!

---

### Post by Lars Noodén on 2011-12-14
[rsync](https://help.ubuntu.com/community/rsync) is probably a better tool for the job.  Can you connect with SSH or SFTP?

---

### Post by jonobr on 2011-12-14
+1 on rsync , its perfect for the job and gives you a lot more flexibility in handling then FTP ( not to mention security)

ON the actual problem, 

could it be that the port 20 is blocked?

Port 21 and 20 are used for ftp 
21 is control (login, password, cd ls etc)
where as 20 is data.

So if you had 21 open and 20 blocked you would be able to login 
list change directory etc but not transfer

Best way to test is to do it by hand

open a terminal

```
ftp <ipaddress> 
```
supply credentials

```
bin
hash 
prompt 
```

do the above commands work?

If the do

```
mget *
```

Do you get a lot of ##############
showing the transfer or does it kick you?

---

### Post by jlparsons on 2011-12-14
Thanks mate.  Results;

```
james@parsons-desktop ~ $ ftp 192.168.0.4
Connected to 192.168.0.4.
220---------- Welcome to Pure-FTPd [TLS] ----------
220-You are user number 1 of 10 allowed.
220-Local time is now 03:31. Server port: 21.
220-This is a private system - No anonymous login
220 You will be disconnected after 15 minutes of inactivity.
Name (192.168.0.4:james): admin
331 User admin OK. Password required
Password:
230 OK. Current restricted directory is /
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> bin
200 TYPE is now 8-bit binary
ftp> hash
Hash mark printing on (1024 bytes/hash mark).
ftp> prompt
Interactive mode off.
ftp> 
```

---

### Post by jonobr on 2011-12-14
Ok,

so control looks ok,

what about moving a file?

mget * or mget file_i_want_to_move

---

### Post by jlparsons on 2011-12-14
Yup, i can mget, i can also up/download via ftp as a folder in nautilus and I can view my ftp files/folders in firefox at [ftp://username@192.168.0.4](ftp://username@192.168.0.4).  To make matters even more confoozing, deja-dup uploads to the server fine, and that (so i believe) uses duplicity....

I'm thinking there must be something wrong with the script I'm using?

---

### Post by jonobr on 2011-12-14
so it looks like ftp data is ok,

That returns you to the script....

What I would do is look for a log file
and open it.
Eg with vsftp  you could

```
 sudo tail -f /var/log/vsftpd.log 
```

This will open the log and print out the latest output,

Run the script and see what pops out...

( just want to reiterate that rsync is soooo much simpler,
one command line that you put put in a cron job)

---

### Post by jlparsons on 2011-12-14
I've set up the job to use a log, this is what comes out;
```

failed with code 3 (attempt #1)
Error is:
Remote host has closed the connection.
ncftpput "Backupdirectory"/duplicity-full.20111214T152750Z.vol1.difftar.gpg: could not send file to remote host.
```I thought duplicity was itself just a way to use rsync with gpg encryption?  Can rsync do so on its own?  My intention was to put the above script in cron once working.

Haven't tried the full url ie;
```

ftp://james:password@192.168.0.4:21/backup
```

---

### Post by jonobr on 2011-12-14
any chance try chcnging

```
ftp://"username"@192.168.0.4/"myfolder"
```
to
```
ftp://"username"@192.168.0.4/"myfolder"/*
```
or maybe 
> ftp://"username"@192.168.0.4/"myfolder/"

---

### Post by jonobr on 2011-12-14
Also rsync is used for file sync and can be done across ssh.

It can be used to compare whats at the source and desitnation and either overwirte whats there,
only copy whats different,
compress, delete what was transferred and so on.

Im not really all that familiar with duplicity (you found me out :-( )

After a bit of research..... Its a sad day you dont learn something new

> About Duplicity Encrypted Backup

Duplicity is a stable Debian package used for Encrypted backup using rsync algorithm. The benefits of duplicity are as follows:

    Encryption using GPG
    Differential Backups - Takes an inital full-backup, and from then on - only the files which have changed, saving bandwith and high disk usage.
    Can be done over ftp or scp - Some backup servers only allow ftp on a shared server. As a result files need to be encrypted. 

The idea of putting the words FTP and and secure in the one sentence seems kind of alien to me. :-0

---

### Post by jlparsons on 2011-12-14
Just tried every permutation of the above suggestions.... same error.  I'm perplexed!  How does deja-dup work but duplicity doesn't?

---

### Post by jonobr on 2011-12-14
Is there a firewall in place such as ufw or iptables that may be blocking return?

I was assuming port 21 and 20, but it could be using something else..

---

### Post by jlparsons on 2011-12-14
> **jonobr said:**
> 
The idea of putting the words FTP and and secure in the one sentence seems kind of alien to me. :-0

Agreed!  But then as long as it's encrypted and it's only going across my LAN (or nowhere, as is currently the case) I'm fine with it.

---

### Post by jonobr on 2011-12-14
agreed

Did you try checking firewalls, eg ```
sudo ufw disable
``` and try that?

---

### Post by jlparsons on 2011-12-14
no ufw, no firewall.

---

### Post by jonobr on 2011-12-14
Im running out of arrows here.

does running a 
```
tcpdump -i any -vvv -s 1600 port 20
```
show anything when you do the transfer?

---

### Post by jlparsons on 2011-12-14
Yes, it picks up ftp traffic and I've found residual (tiny) gpg files at the source, it seems like the connection is getting cut just after the transfer starts.

I'm all out of arrows and considering throwing rocks!  It's so frustrating... all other ftp functions, check.  Deja dup (which is based on duplicity), check.  Duplicity, fail. Doh.

---

### Post by jonobr on 2011-12-14
Are you using wireless or some other connection which may be flakey?

Can you ftp over the full file the way we did at the start?

---

### Post by jlparsons on 2011-12-14
I'm on wireless yes.  FTP large files working fine.  My router is a sky one though, and this could be an issue.  But then wouldn't I expect other ftp issues if that were the case?

---

### Post by jonobr on 2011-12-14
Did you try checking the version an searching for know issues on Launchpad. It appears your kungfu is strong....

---

### Post by jonobr on 2011-12-14
You know what , if the file is moved with FTP but not (or partially) with duplicity implication would be that your box is okfor one, it should be ok for the other.

All i can recommend is to try the tcpdump and see if something is shown up

---

### Post by jonobr on 2011-12-14
I noticed reports of people having trouble copying when they had partials files.

Could you clean out your partials and try another copy,(although I think this may be an excercise in futility)


Cheers

---

### Post by jlparsons on 2011-12-14
You're right, i'm clutching at straws at this point, which is one step from rocks.  My money says it's got to be a bug, have looked for existing reports but can't find... will check again.  I'll try it with a different router tomorrow then if that fails I think I'll conclude it's something to do with the ncftput instruction (which is where it always seems to go bang) and think about a bug report.  Who knows, maybe a duplicity blackbelt will lurk by at some time and let us know what deja-dup is doing that duplicity is not.

Thanks for your assistance Fr Jack, very much appreciated!

---

### Post by jlparsons on 2011-12-14
> **jonobr said:**
> I noticed reports of people having trouble copying when they had partials files.

Could you clean out your partials and try another copy,(although I think this may be an excercise in futility)


Cheers


Thanks, tried that but no joy.  :(

---

### Post by jlparsons on 2011-12-17
Inelegant solution found, shall post here in case anyone else has this issue;

```
export PASSPHRASE="mypassphrase" 
duplicity /home/directorytobebackedup file://home/james/localincrementalbackup
lftp -u username,password -e "mirror --reverse --only-newer /home/james/localincrementalbackup /ftpbackupdirectory" ftp://serveraddress/
unset PASSPHRASE
```This does the incremental backup to a home directory then dumps that directory to the ftp server as a mirror, only uploading files if newer.

So, almost solved, but not actually solved.

As to the problem with duplicity itself, I'm convinced there's either a bug in ncftpput (as every other ftp option I'm trying works fine) or ncftpput has a problem with my sky router.  But I've been wrong before!

---

