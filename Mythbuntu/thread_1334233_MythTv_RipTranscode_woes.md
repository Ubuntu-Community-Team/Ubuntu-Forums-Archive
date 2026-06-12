---
title: "MythTv Rip/Transcode woes"
date: 2009-11-22
forum: Mythbuntu
---

### Post by dotnick on 2009-11-22
When I go to the DVD Import screen, MythTv recognizes there is a DVD inserted, but when I press the "Begin Ripping" button, nothing happens.  I've checked my /var/log/mythtv/mythbackend.log and /var/log/mythtv/mtd.log, but there seems to be nothing there.  The mtd.log simply shows a socket was opened, but nothing more.

I have added my storage folders in mythtv-setup, so I do not believe that is the cause.  I am able to write to the temp directory also, so I do not believe its a permissions issue (at least not there).

---

### Post by dagreatk on 2009-11-23
I have the exact same issue mythbuntu 9.10.I even looked through the general video settings to find that my dvd drive was incorrect but that still didnt correct the issue. anyone help would be greatly appreciated.

---

### Post by kja999 on 2009-11-23
> **dagreatk said:**
> I have the exact same issue mythbuntu 9.10.I even looked through the general video settings to find that my dvd drive was incorrect but that still didnt correct the issue. anyone help would be greatly appreciated.

Not very positive I know, but I have never got the mtd to work correctly (in about 2 years).
Script handbrake and leave it there ... 

```

#!/bin/bash

#location of my vid files and Handbrake command
cd /mnt/video/mpegs/

mythshutdown --lock 

#Get the filename
filmname=$(zenity --entry --title="Enter film name" --text="Enter the title of the film : ")
filename=${filmname}".mp4"

filename=$(echo $filename | sed 's/ /_/g')

echo $filename

#Confirm ok
zenity  --question --title "Alert"   --text "Film is $filmname. Are you sure you wish to continue ?"

continue=$?

echo $continue

if [ $continue == 1 ] 
    then
    echo Requested stop
        exit 0
fi

#Do the rip
nice -n 20 ./HandBrakeCLI -i /dev/dvd -L -N eng -o "$filename" --preset="Normal"
    
mythshutdown --unlock

eject dvd
```

---

### Post by dagreatk on 2009-11-23
I figured it out and posted the ticket to mythtrac
                  I don't know whether this is just mythbuntu or whether its an issue for all distros using mythtv but I was having a problem ripping dvds, the begin ripping button was non responsive. I found out that when I ran frontend verbose this error came up. 2009-11-23 13:52:05.216 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'mythdvd.LocalRipDirectory?' AND hostname = 'Media-Center' ;" 2009-11-23 13:52:05.216 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'mythdvd.LocalRipDirectory?' AND hostname IS NULL;" 2009-11-23 13:52:05.217 MSqlQuery::exec() "SELECT data FROM settings WHERE value = 'VideoStartupDir?' AND hostname = 'Media-Center' ;" 2009-11-23 13:52:05.217 titledialog.o: I can't rip, as I have nowhere to put finished files. MythVideo? installed? 
  when I query the database no rows come up. 
  Whenever I would change my temp directory in the Media Settings->Rip Settings it would not write the changes to the database I corrected this issue by manually putting it into the database 
  UPDATE settings SET data = '/var/lib/mythdvd/temp' WHERE value = 'VideoStartupDir?' and hostname LIKE 'Media-Center'; 
  in my case the hostname is Media-Center and my directory is /var/lib/mythdvd/temp

---

### Post by dotnick on 2009-11-30
kja999:
I tried the script, and that worked fine. Is there a way to incorporate that into MythTv so I don't have to pull up a shell and can use my remote?  Maybe using the handbrake command in the spot that asks for "transcode" ?

dagreatk:
I also looked at the database oops.... even after I made sure the correct path was there (using phpMyAdmin), the button for ripping was non-responsive.

---

### Post by kja999 on 2009-12-02
In truth, I have never tried .. I have an icon on the xfce menu to the script.
Wife accepted the solution ;)

---

### Post by ahood on 2009-12-02
> **dotnick said:**
> When I go to the DVD Import screen, MythTv recognizes there is a DVD inserted, but when I press the "Begin Ripping" button, nothing happens.  I've checked my /var/log/mythtv/mythbackend.log and /var/log/mythtv/mtd.log, but there seems to be nothing there.  The mtd.log simply shows a socket was opened, but nothing more.

I have added my storage folders in mythtv-setup, so I do not believe that is the cause.  I am able to write to the temp directory also, so I do not believe its a permissions issue (at least not there).

Try a rip and then post the same days output from the mtd.log. Maybe we will see something that will lead to a solution.

Make sure that only one instance of MTD is running. Use the top command to view processes.

I have found some DVDs will not be ripped due to protection mechanism built into the DVD. Could this be the case?

I once had to update the libcss library to successfuly rip DVDs after upgrading from a previous version of Mythbuntu. 

Cheers,

---

### Post by kja999 on 2009-12-03
I got to thinking about this, and it is easy to add the script to the menu ..

Play if you are brave ...
You'll need to have knocked up a custom menu first. In /usr/share/mythtv/themes. 
copy folder defaultmenu to a new folder name and edit the menu file you want to add it to I.e. mainmenu.xml for example; add the below code

```

   <button>
        <type>DVD</type>
        <text>Import a DVD</text>
        <description>Run the import program</description>
        <action>EXEC <path to your script></action>
    </button>


```

Then in appearance settings you should find the name of your new theme folder .. use that and your edited menu's will appear.

---

### Post by apdt on 2010-01-01
> **dotnick said:**
> I have added my storage folders in mythtv-setup, so I do not believe that is the cause.  I am able to write to the temp directory also, so I do not believe its a permissions issue (at least not there).

That may be the issue.  I couldn't get importing working when using storage groups.  I had to go into the frontend setup and set 'Directories that hold videos' (in Utilities/Setup -> Setup -> Media Settings -> Videos Settings -> General Settings) to the same path as the directory in the storage group, and then it all started working.  You'll also need to mount it over the network if the frontend and backend are on different machines.

It would seem that the DVD import feature doesn't use Storage groups yet (but hey, they do say that storage groups in MythVideo is incomplete - see [http://www.mythtv.org/wiki/MythVideo#Storage_Groups]("http://www.mythtv.org/wiki/MythVideo#Storage_Groups"))

---

### Post by dotnick on 2010-01-01
That seems to have fixed it for me as well.  I hope that all new installs have this field filled in automatically to avoid this problem.  Even a script that would go through an existing database and "reset" everything to default values while not losing the existing video/recording/music listings would be helpful.

Thanks

---

