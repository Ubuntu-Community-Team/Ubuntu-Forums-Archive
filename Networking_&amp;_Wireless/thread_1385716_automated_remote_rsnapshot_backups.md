---
title: "automated remote rsnapshot backups"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by acy76 on 2010-01-19
I've been working the bugs out of my backup server the past couple of days, and want to document/share the major pieces that stumped me.

I found the answers in various threads, both here and on other sites, but nothing that brought it all together in one place.

If you're new to rsnapshot, read the [**[COLOR="DarkOrange"]how-to[/COLOR]**]("http://rsnapshot.org/howto/") and [**[COLOR="DarkOrange"]man page[/COLOR]**]("http://rsnapshot.org/rsnapshot.html") on the [**[COLOR="DarkOrange"]official site[/COLOR]**]("http://rsnapshot.org/") first. It's a great little backup utility, and the basic settings and operations are described in those documents (and beyond the scope of this post).

[COLOR="Blue"]++++++++++++++[/COLOR]

My network includes a central file server running Ubuntu Server and sharing files via Samba. I want to be able to take automated snapshots of this file server on another machine on my LAN, so I am protected from hardware failure, accidental deletion or accidental modification of files. This backup server also runs Ubuntu Server (x86, version 9.10).

It is only necessary to install rsnapshot on the backup server, as the software "pulls" files from the file server. The rsnapshot package is not required on the file server. **The user that will be used to log into the file server over ssh will, of course, need sufficient permission to access all the files to be backed up.**

[COLOR="Blue"]++++++++++++++[/COLOR]

The first step is to install rsnapshot from the repositories:

```
sudo apt-get install rsnapshot
```

Since we will be automating the process using cron, we need to be sure cron can send us status messages. Ubuntu does not automatically install a mail package - if your system does not have one, I recommend mailx. There has been some discussion about cron not operating correctly without a default mailer installed; see [[COLOR="DarkOrange"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=500687&highlight=rsnapshot") for more information.

```
sudo apt-get install mailx
```

During installation, mailx will prompt you for the type of mail server you're running. For my purposes, the "local" option fit perfectly. If you need additional features, choose accordingly.

You will also need the openssh and rsync packages; these may already be installed on your server (they were on mine), but add them if not.

[COLOR="Blue"]++++++++++++++[/COLOR]

The next step is to generate a passphrase-less key so that ssh connections can be made between the two machines without user intervention. **_Note that this may pose a security risk in certain situations, so be sure this solution is right for you before proceeding._** Read more about ways to secure and restrict public/private key ssh logins [[COLOR="DarkOrange"]here[/COLOR]]("http://troy.jdmz.net/rsnapshot/").

Generate DSA key pair. Be sure to hit enter when asked for the passphrase (and target directory, assuming you're in your home directory already):

```
ssh-keygen -t dsa
```

I used DSA based on a tutorial I was following, and the fact that I am not too concerned about security when sharing keys on my home LAN. For a discussion of RSA vs. DSA algorithms, see [[COLOR="DarkOrange"]here[/COLOR]]("http://www.linuxforums.org/forum/linux-security/3515-rsa-versus-dsa.html") and choose accordingly.

Send the key to the file server as the user who will be logging in to perform the backups (again, assumes you are in your home directory):

```
scp .ssh/id_dsa.pub *user@computer*:~/.ssh
```

Log into the file server as the user who will be logging in to perform the backups and add the key to the list of authorized keys:
```

ssh *user@computer*

cd .ssh

cat id_dsa.pub >> authorized_keys2

rm -rf id_dsa.pub
```

Test this by logging out and logging in (via ssh) again; this time, you should not need a password. Type "yes" if asked whether or not to add the machine to the list of known hosts.

[COLOR="Blue"]++++++++++++++[/COLOR]

Now configure rsnapshot. The official howto and man page (linked at the beginning) explain the options for backing up your data and how to edit the configuration file.

**IMPORTANT CONFIGURATION NOTES:**

Edit the file using your favorite editor:

```
sudo nano /etc/rsnapshot.conf
```

Be sure to uncomment the lines specifying the paths to the cp, ssh, rsync, etc. commands.

Also be sure to add an -i argument to ssh telling it which key to pass (the one we generated earlier) to the file server; by default, it will pass root's key (which probably doesn't exist) because we will be running the automated backups from the root crontab. More on this can be found [[COLOR="DarkOrange"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1059461&highlight=rsnapshot"), particularly post #4. An example:

```
ssh_args        -i /home/username/.ssh/id_dsa
```

**Note that the config file expects <tabs> and not <spaces> in all places *except* in the argument strings, so in the example above, tabs should be used between "ssh_args" and "-i", but everything after "-i" is a space. If you use tabs, the config file will be syntactically legal but it won't pass the arguments correctly to ssh.**

Edit the other options as your needs dictate. My config file (with commented sections removed for clarity and personal information removed for privacy) is listed below:

```
config_version  1.2

snapshot_root   /var/snapshots/

cmd_cp          /bin/cp

cmd_rm          /bin/rm

cmd_rsync       /usr/bin/rsync

cmd_ssh         /usr/bin/ssh

cmd_logger      /usr/bin/logger

cmd_du          /usr/bin/du

interval        hourly  6
interval        daily   7
interval        weekly  4
interval        monthly 12

verbose         2

loglevel        3

logfile         /var/log/rsnapshot

lockfile        /var/run/rsnapshot.pid

ssh_args        -i /home/user/.ssh/id_dsa

du_args         -csh

exclude         /var/somedir/someotherdir/dir*/

backup  user@fileserver:/var/somedir/someotherdir/             data/
backup  user@fileserver:/var/somedir/differentdir/             data/
```

Test the config file for syntactical errors:

```
sudo rsnapshot configtest
```

[COLOR="Blue"]++++++++++++++[/COLOR]

The final step is to add the backup jobs to the root crontab. 

Open it for editing:

```
sudo crontab -e
```

Add the jobs according to your needs. The man page has a good example crontab to copy, **but be sure to adjust the path to rsnapshot for Ubuntu use** (it's in /usr/bin not /usr/local/bin). Tip of the hat for this solution goes to [[COLOR="DarkOrange"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8685932#post8685932").

Attached is a copy of the crontab I use:

```
0 */4 * * * /usr/bin/rsnapshot hourly
00 06 * * * /usr/bin/rsnapshot daily
00 05 * * 7 /usr/bin/rsnapshot weekly
30 04 1 * * /usr/bin/rsnapshot monthly
```

[COLOR="Blue"]++++++++++++++[/COLOR]

Test the backup system by initiating the lowest-level backup (in my case, hourly. Note that if you expect to move lots of data, you may want to do a manual run before adding the jobs to cron to avoid scheduled backups being skipped because the first one is still running.

```
sudo rsnapshot hourly
```

Check the log to see whether it completed:

```
cat /var/log/rsnapshot
```

You can also check the snapshot root (/var/snapshots/ in my case) to be sure the files were backed up correctly. If there were any issues with the cron jobs, cron should send you an email, which you can check by entering 'mail' on the command line.

[COLOR="Blue"]++++++++++++++[/COLOR]

I hope this was helpful. Setting this up for the first time can be a frustrating experience, as I know all too well. If I missed something, please let me know - I tried to cover it all from memory.

---

