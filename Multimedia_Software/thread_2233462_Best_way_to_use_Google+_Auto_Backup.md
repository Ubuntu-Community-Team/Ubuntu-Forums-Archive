---
title: "Best way to use Google+ Auto Backup"
date: 2014-07-08
forum: Multimedia Software
---

### Post by chrisps on 2014-07-08
Hi,

Having used Linux for various purposes for a long time, I have just made the switch to Ubuntu as my primary desktop. 

Like them or loath them, I use Google (specifically Google+) to share all of my photos with family (who don't use Facebook) and just to keep backups.

One issue however which I didn't forsee is that Google ended Picasa support for Linux.

I can't find much information about good replacements, but can anyone suggest something which can do a similar job to Picasa on windows, i.e. auto-backup new photos to Google+?

Through a bit of searching, I came across Shotwell which sounds like it might support it, but I don't really want to have to "import" my photos to another directory, I like my directory structure as it is!

Thanks!

Chris

---

### Post by shoham on 2015-07-05
There is a way to install `Google photos auto backup` on ubuntu (taken from [here]("http://www.reddit.com/r/linux/comments/37ptsw/any_got_the_new_google_photos_backup_desktop/"), worked for me...)


1. install google photos auto backup on windows machine(may be a virtual pc or an ordinary pc)
2. start > run > regedit
3. go to > HKEY_CURRENT_USER\Software\Google\Picasa\Picasa2\Preferences
4. then on menu > registry > export registry file.
    It should look somthing like this:  
    Windows Registry Editor Version 5.00


    [HKEY_CURRENT_USER\Software\Google\Picasa\Picasa2\Preferences]
    "GoogleOAuth"=hex:xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,\  xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx,xx
   "GoogleOAuthEmail"="youremail@gmail.com"
    "GoogleOAuthServices"="mail,lh2,cp,cp.manager,mailrelay,plus.stream.write,    plus.circles.read,plus.profiles.read,plus.me,plus.media.upload,plus.media.    readonly,plus.settings,youtube,"
    "GoogleOAuthVersion"=dword:00000005




5. install playOnLinux > go to configure > create a new 32 bit windows virtual drive, call it GooglePhotosBackup > select the new virtual drive > wine tab> task manager > new task > select the [gpautobackup_setup.exe]("https://dl.google.com/dl/picasa/gpautobackup_setup.exe") file you've downloaded from google > Install google auto backup.
6. select the new virtual drive again > registry editor , then on menu > registry > import registry file > import the registry file you created earlier.
7. general tab > "make a new shortcut from this virtual drive" button> select google photos backup.exe.


Finally, run the application and you should be logged in!

---

### Post by rbnonato on 2016-01-20
This method worked for me, but Google Photos Backup was crashing very frequently under Wine 1.6.2. I installed it under Wine 1.2.3 (using PlayOnLinux) and it hasn't crashed in a while now.

---

