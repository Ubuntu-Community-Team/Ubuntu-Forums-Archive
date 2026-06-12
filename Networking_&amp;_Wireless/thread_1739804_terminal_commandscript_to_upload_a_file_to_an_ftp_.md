---
title: "terminal command/script to upload a file to an ftp server without user input"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by oldmankit on 2011-04-26
Hello,

I've got used to using the ftp command from the terminal, which is useful, especially with macros.  But it requires user input, and what I want to do now is upload a specific file to a server, once I've finished working with it every day.  It's the same file every day.  II would like to be able to do this semi-automatically: I just give the command and it connects to the server and uploads the file.  

(I will probably want to encrypt the file before uploading it.)

I don't know how I could use ftp without  any user input: I want it to be automatic.  

But I'm sure there is someone here who does know!

---

### Post by yopnono on 2011-04-26
use the script ftp-upload

---

### Post by yopnono on 2011-04-26
IE: I use this script and cron.

> 
#!/bin/sh
# Make backup of user files
# To upload to an FTP you need the script ftp-upload and rar
#
# ftp.domain.com = 12.34.56.78
#
# Host name
n1=`uname -n`

# Date format
d1=`date +%F`

# User folder dir
f1=/home/mike

# Temp dir
f2=/tmp/backup

# Password for the .RAR archive
p1=PASSWORD

# FTP password
p2=PASSWORD

# FTP username
u1=USERNAME

# FTP IP
ip1=12.34.56.78

# Host
host1=ftp.domain.com

# Remove temp folders just in case
rm -fr "$f1"/.backup
rm -fr "$f2"

# Create temp backup folders
mkdir "$f2"
mkdir "$f1"/.backup

# Folders/files to copy
# cp -fR "$f1"/.mozilla/ "$f2"
cp -fR "$f1"/cbt "$f2"
# cp -fR "$f1"/Privat "$f2"
# cp -fR "$f1"/.gnupg "$f2"
# cp -fR "$f1"/.evolution "$f2"
cp -fR "$f1"/.Privat_encfs "$f2" 
# cp -fR "$f1"/backup "$f2"

# Remove the cache and plugin files from mozilla profile folder.
# rm -r "$f2"/.mozilla/firefox/*.default/Cache/
# rm -r "$f2"/.mozilla/plugins/*


# Compress and set password
# zip -r9P "$p1" "$f1"/.backup/backup_"$d1" "$f2"
rar a -r -p"$p1" "$f1"/.backup/backup_private_"$n1"_"$d1" "$f2"
# tar -jcf  "$f1"/.backup/backup_""$n1_"$d1".tar.bz2 "$f2"

# Upload to FTP using ftp-upload script
ftp-upload --passive -u "$u1" --password "$p2" -h "$host1" -d /backup "$f1"/.backup/*

# Remove temp folders
rm -fr "$f1"/.backup
rm -fr "$f2"

exit 0


---

### Post by DaithiF on 2011-04-26
Hi, 
ftp can read commands from standard input, see example here: [http://willcode4beer.com/tips.jsp?set=bashftp](http://willcode4beer.com/tips.jsp?set=bashftp)

---

### Post by oldmankit on 2011-04-27
I didn't know ftp could read commands from standard input like that.  Cool!

In the end I went for ftp-upload because it looked easy.  It was.

I have a little script that copies the file to a local archive directory where it is given a date to identify it, then uses gpg to encrypt the file to a temporary directory, then uses ftp-upload to put it where it needs to go.

Thanks for the help.
```
#!/bin/sh
current_date=`date +%Y_%m_%d__%k:%M`
hostname="..."
username="..."
password="..."
directory="~/..."
unencrypted_filename="file.lyx"
encrypted_filename="$current_date".gpg
archive_name="$current_date"-file.lyx

cd $directory
#local backup
cp $unencrypted_filename archive/"$current_date".lyx
echo "making a local backup"

#encrypt file
gpg --batch --yes -r my_user_name --output tmp/"$encrypted_filename" -e $unencrypted_filename

#upload encrypted file
echo "uploading encrypted file to server"
ftp-upload --passive -u "$username" --password "$password" -h $hostname tmp/*gpg

#clean tmp directory
rm tmp/*.gpg
echo "operation complete"
exit 0

```

---

### Post by gr0ck on 2011-09-19
OK here is a real simple one. 

using your basic system and ftp command. Due to many servers requiring passive commands do not forget to ftp -p 

You'll need to edit a .netrc file with the following format:

machine    machine.address.com
login username
password passwordformachine

the .netrc file goes in your home directory.

OK now for the cool part. 

In your bash script put the following:
###########################
ftp -p <<**
open machine.address.com
bin
put yourfilename
bye
**
###########################
That should do it.  If you are in the same directory as yourfilename it will upload. 

You can put all sorts of commands before the ftp -p <<** ** and many after.

---

