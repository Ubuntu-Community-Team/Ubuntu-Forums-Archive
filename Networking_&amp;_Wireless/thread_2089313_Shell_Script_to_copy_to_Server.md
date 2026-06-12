---
title: "Shell Script to copy to Server"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by Hank_The_Dog on 2012-11-28
Ok, the more I research this, the harder it seems.

Here is all I want

*A shell script that moves all the contents of a local folder, to my server...*

I have a samba share, and open-ssh set up on the server..

I would like this script to be automatic and require no user input..

I feel like this should be easy, but the more I look, the more complex it becomes..


Any help would be greatly appreciated

---

### Post by gerowen on 2012-11-28
As long as you haven't disabled it in the SSH config on the server, SSH also supports "SFTP", which is basically just FTP over SSH.  If you set up a particular SFTP folder to be automounted to an easy to find folder, you could just script the copy of files to the folder that the server is mounted on.

---

### Post by Hank_The_Dog on 2012-11-28
Thanks for the response,

I use SFTP to access my server from work. 

any tips on auto mounting in Kubuntu 12.04? Never done it before..

Would  I just use the cp command?

---

### Post by agillator on 2012-11-28
What OS are you running on each? I assume one is windows since you are using samba. If both happen to be linux you solution is simple - an rsync job scheduled by cron. If one is windows then sftp may be your best answer. Again, I would see about setting up a cron job. If you need more details, give us some specifics.

---

### Post by Hank_The_Dog on 2012-11-29
@Ag,

I like the way you roll, I have been meaning to learn cron for some time... 

Here are my specs.. 

**Local:**
*LinuxMint 13 Maya*

**Server:**
*Ubuntu 10.10*

Here is a little more detailed explanation of what I would like to accomplish..


[LIST=1]
[*]A script of some sort (assuming a shell script is best) needs to be called (either from another source, or double click)
[*]This script should be automatic and require no user input
[*]Move* contents of /local/dir to //server/dir
[*]*Now the local folder should be empty, and the server folder should contain it's old contents
[*]This is not a timed event, it should be dependent on the user/outside source to call it
[/LIST]
Any tips or tuts would be great!

---

### Post by ahallubuntu on 2012-11-29
use rsync to do the copy via ssh:

```
rsync -av /my/local/folder/ user@remotemachine:/my/remote/folder/
```

rsync copies the folder but ONLY the changes.  If /my/local/folder's contents changed only slightly, only a tiny bit is copied.

You should find that works very easily, except that it will prompt you for user's password on "remotemachine" (replace with your IP address or a machine name).  To avoid being prompted for a password, you generate authorized keys on one machine and copy them to the right place on the other.  There are numerous tutorials on how to do that.  Here's just one:

[http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/](http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/)

---

### Post by agillator on 2012-11-29
Note: all commands are in a terminal, by the way.

The above gives you the correct and most simple command for rsync. By the way, learn to use rsync, it is one of the beautiful and most useful/powerful programs. However, onwards . . . .

You really don't need a script for what you have described. All you need is to program a cron job. First, check the manual pages for cron and crontab. Then look at your current crontab file (if you have one). The format is pretty well described in there. You can see your file with the command crontab -l. If you don't see anything or it tells you there is none, then try sudo crontab -l. That should give you root's and there should be a few entries there. 

With that orientation behind you, it is time to do it for real. I am assuming you have read permission for the necessary directory or directories on the source machine, and write permission on the destination machine. We are going to keep this VERY simple, by the way. To set up your job for the same time, say 12:30 a.m. every day, enter crontab -e. You may have to pick an editor if you have never done this before. I use vim. you are free to use one of the others listed. Install if/as necessary. 

With the editor open go to the end of the file and add a line. First, you need five fields for the schedule in the order of minute, hour,  day of the month, month, and day of the week. For our simple example enter 30 0 * * * (those are spaces between the numbers and asterisks, although tabs are ok). The asterisks mean 'every'.

Now, enter a tab (although space(s) will work) and the command you wish executed. Hint: enter full paths, don't rely on the PATH environment variable.

Close your editing session. Now, every day at 12:30 in the morning (local time) your command will be run. If you check your system log you should see it there when it runs. You can also have an email sent if you wish; see the man page.

You did not need a script because you were only running one command. If you were doing more than that you would have needed a script, of course, and would have used the command to run the script. 

Good luck. Watch out for Murphy. Get used to cron because it can do some pretty neat stuff for you.

---

### Post by agillator on 2012-11-29
I overlooked your 'this is not a timed event'. Oops. 

If you do not want to do it automatically at a certain time, the technically you do not need a script although a script will make it easier.

Open an editor. Enter #!/bin/bash on the first line. That assumes you use bash. If not, try #!/bin/sh which should work. 

On the next line enter the rsync command.

Close the edit session. Change the permissions so the file is executable as you wish and put it somewhere on your PATH.

If you call the script joe (i.e. the file name is joe) all your user has to do is enter joe on a command line and BINGO, just like magic it gets done. But why not get the user out of the picture completely if you can?

---

### Post by Hank_The_Dog on 2012-11-30
> **ahallubuntu said:**
> use rsync to do the copy via ssh:

```
rsync -av /my/local/folder/ user@remotemachine:/my/remote/folder/
```rsync copies the folder but ONLY the changes.  If /my/local/folder's contents changed only slightly, only a tiny bit is copied.

You should find that works very easily, except that it will prompt you for user's password on "remotemachine" (replace with your IP address or a machine name).  To avoid being prompted for a password, you generate authorized keys on one machine and copy them to the right place on the other.  There are numerous tutorials on how to do that.  Here's just one:

[http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/](http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/)



SOLVED! 

Thanks for the tip, you have answered my current dilemma! (And quite possibly opened up another few thousand) SO THANK YOU!

rsync  works like a charm, ssh is a lot smoother in the terminal, and the authorized keys tutorial you recommended couldn't have been easier..

Now, I can automatically back up my local dir at the click of a button, or whenever a torrent gets done downloading :popcorn:

Thanks again!

---

### Post by ahallubuntu on 2012-11-30
rsync is an awesome little tool - can't imagine living without it now.

Here's something else to consider in the future: "rdiff-backup" (google for more info) .  It is basically rsync but with incremental backup.  That is, if you run it yesterday, accidentally delete a file today, then run the rdiff-backup tomorrow, you can find the deleted file (or any day's version of that file if you change it every day) in your backup.  On the downside, it does take more disk space on your backup disk.

---

