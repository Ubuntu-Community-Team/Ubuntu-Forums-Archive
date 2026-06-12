---
title: "ran out of space on &quot;system&quot; partition - HELP"
date: 2010-05-05
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-05-05
I have been using myth for a while without any major issue but just today I went to update my 9.10 (myth 0.22) system and found out that the system partition is full (well 30mb free space).  Clearly this is BAD, what has happened?  Is there some form of massive log file etc i can delete, where should i start (im not that familiar with linux to start randomly deleting large files!). 

The myth recording partition is about 220gb with the install being 30gb but surly that should be enough space??  I am planning on upgrading to 10.04 at some point but didnt really want to do a full reinstall (as i have lirc, squeezebox, mediatomb etc all working nicely now).

Any ideas please?

---

### Post by oldfred on 2010-05-05
Are you running a backup that defaulted to a system directory?

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by ian dobson on 2010-05-05
Hi,

maybe try an apt-get clean, apt-get autoclean, apt-get purge
this usually saves 200-300Mb on my server.

Then maybe delete some log files in /var/log. You can delete all the .gz .0 .1 files also have a look in  /var/log/mythtv there could also be log files you can delete.


Regards
Ian Dobson

---

### Post by LowSky on 2010-05-05
MythTV uses the /var/lib/Recordings (I think that is right) folder for the default, which would be in the root or (system as you call it) partition. Make sure its not full of recordings.

you can also set myth to keep a certain amount of space free as well. I set mine to keep an additional 10GB free for "just in case"

---

### Post by geekyhawkes on 2010-05-05
Thanks, some how i ended up with a 6.7gb mediatomb log file!  Ive stopped mediatomb for now while i work out what is going on there!

---

### Post by ian dobson on 2010-05-05
Hi,

Linux has a tool logrotate that should create compressed copies of your log files, saving disk space.

Maybe you could configure log rotate to handle your mediatomb log files. Have a look in /etc/logrotate.d for examples of configuration scripts.

Regards
Ian Dobson

---

### Post by buntunoob on 2010-05-07
Check ther log and see what the error/error's are.
How are you starting mediatomb?, if your starting it in debug mode it'll output A LOT of info, I'm not sure if it would be 16 gb but that might depend onlast logrotation(without debug the logs are like 42k a week for me).

---

