---
title: "FTP Help: Automate removal of matching files"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by Jzak on 2011-02-18
Hello,
  I am trying to do more things in ubuntu, and need some help with this one.
I have an FTP server I work with on a consistent basis that I access my work orders from.
When I am done with the order I have to send the completed file back with the same name to a different folder on the ftp server.
The problem I am running into is removing the original order from the order folder. As of right now I have to do it all by hand and need to find a way to automate this function.
I have to keep the working orders on the server downloading all of them and doing this on my HD is not an option.

What I want to do is have a script or function that will look in a particular folder and delete all the ones that match it on the server.
Is this possible? Is there a program already created that will do this?
I have not used FTP in ubuntu as of yet so I am asking this as a total noob
Thank you

---

### Post by cjhabs on 2011-02-18
> **Jzak said:**
> Hello,
  I am trying to do more things in ubuntu, and need some help with this one.
I have an FTP server I work with on a consistent basis that I access my work orders from.
When I am done with the order I have to send the completed file back with the same name to a different folder on the ftp server.
The problem I am running into is removing the original order from the order folder. As of right now I have to do it all by hand and need to find a way to automate this function.
I have to keep the working orders on the server downloading all of them and doing this on my HD is not an option.

What I want to do is have a script or function that will look in a particular folder and delete all the ones that match it on the server.
Is this possible? Is there a program already created that will do this?
I have not used FTP in ubuntu as of yet so I am asking this as a total noob
Thank you

You can use curlftpfs to mount the ftp folder to your local system and then treat it like any other file system:

sudo curlftpfs url.com /media/my_ftp -o user=ftpuser:ftppassword -o allow_other -o uid=1000 -o nonempty

---

### Post by Jzak on 2011-02-18
Thats actually a really good idea... I will look into that however that raises a whole bunch of other questions as well as the way I store my files.
All I really want is some type of script or function that will look into a directory on my HD and delete any matching files on the ftp server. 
Is there a way to do that?

---

### Post by cjhabs on 2011-02-19
> **Jzak said:**
> Thats actually a really good idea... I will look into that however that raises a whole bunch of other questions as well as the way I store my files.
All I really want is some type of script or function that will look into a directory on my HD and delete any matching files on the ftp server. 
Is there a way to do that?

Once you mount the filesystem, you can use rsync with the [FONT=monospace]"[/FONT]--remove-sent-files" option or the "mirror" option - depends which direction you want the deletion. This solution would use rsync to actually do the file copy also - otherwise you would need to write a script.

---

### Post by Jzak on 2011-02-20
Ok I am understanding this, however I am having issues figuring out the proper commands for rsync.
I was able to get curlftpfs working and mounted the ftp server.
I am now trying to work with rsync but not having any success.
I am doing test runs trying to find out if I can do this on my system and the --remove-sent-files is not doing its job
I am using this....
[PHP]rsync --progress --remove-sent-files /home/o0ljzakl0o/all /home/o0ljzakl0o/nlftp/Requests
[/PHP]

and it is not removing the like files.
What am I doing wrong? Again I am a noob to many things linux.
I have been reading the commands and do not understand why the files are not deleting. Am I using the correct command or would a different one work?

---

### Post by cjhabs on 2011-02-20
My bad - that should be --remove-source-files
If you run "man rsync" it will tell you all about the command options.

---

