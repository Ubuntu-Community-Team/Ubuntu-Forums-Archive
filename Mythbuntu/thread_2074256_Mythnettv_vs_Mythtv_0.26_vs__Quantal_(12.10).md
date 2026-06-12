---
title: "Mythnettv vs Mythtv 0.26 vs  Quantal (12.10)"
date: 2012-10-21
forum: Mythbuntu
---

### Post by Kheops_74 on 2012-10-21
Hi,

    Anybody use mythnettv to grab video from the Internet to feed Mythtv? Since i upgrade to Quantal(12.10) and MythTV 0.26. I get this error when the "mythnettv update" command is launched:

Failed to update [http://NAMEOFTHEFEED/:](http://NAMEOFTHEFEED/:) _object has no attribute 'date'_

Anybody know if something is different between 0.25 and 0.26 at the Database level?

What is this date?

---

### Post by Kheops_74 on 2012-10-21
I discover a new version of Mythnettv there : [https://github.com/managementboy/mntv](https://github.com/managementboy/mntv). Look interesting but i'm not able to make it work.

Here the error:

Traceback (most recent call last):
  File "./mythnettv", line 25, in <module>
    import database
  File "/home/k/mntv/database.py", line 12, in <module>
    import program
  File "/home/k/mntv/program.py", line 24, in <module>
    import mythnettvcore
  File "/home/k/mntv/mythnettvcore.py", line 16, in <module>
    import proxyhandler
  File "/home/k/mntv/proxyhandler.py", line 15, in <module>
    import utility
  File "/home/k/mntv/utility.py", line 129, in <module>
    from pyparsing import *
ImportError: No module named pyparsing

Any idea what pyparsing is?

Anyone use ths tool? dDo you have an "how to" install ?

---

### Post by Kheops_74 on 2012-10-21
An other interesting information on the official MythTV wiki : [http://www.mythtv.org/wiki/MythNettv](http://www.mythtv.org/wiki/MythNettv)

+Todo: Script needs to be updated to use_ Python bindings_ for database credentials.

What it means???

---

### Post by Kheops_74 on 2012-10-21
I continue to search. The script from here [https://github.com/managementboy/mntv](https://github.com/managementboy/mntv) seems the key. I solve the pyparsing error. I had to install more Python script from Synaptic. Each time i launched "./mythnettv update" a new error message appear with a new script name. Any way, i don't have error massage anymore. I have to test it a little more.

---

### Post by Kheops_74 on 2012-10-21
I have a new error message with the command "./mythnettv download 100", It download the file but it doesn't import the video in MythTV

Importing video 128be5526d65aeaf36ab6d4df5a743fe...
Download Error: 'inetref'
Traceback (most recent call last):
  File "/home/k/mntv/mythnettvcore.py", line 123, in DownloadAndImport
    prog.Import(out=out)
  File "/home/k/mntv/program.py", line 797, in Import
    tmp_recorded[u'inetref'] = row['inetref']
KeyError: 'inetref'

---

### Post by Kheops_74 on 2012-10-21
OK found it. The new version seems to need something in the field inetref of the table mythnettv_subscription. Mine was NULL since the beginning. I put something (ex. 100 or 101) in the field. Don't know why it crash the script in this version. Anyways.

---

### Post by Kheops_74 on 2012-10-22
Last error i hope. This one happen when i try to download a Youtube video.



Download Error: [Errno 2] No such file or directory
Traceback (most recent call last):
  File "/home/k/mntv/mythnettvcore.py", line 121, in DownloadAndImport
    out=out) == True:
  File "/home/k/mntv/program.py", line 481, in Download
    total = streamingsites.Download('YouTube', youtubeid, datadir)
  File "/home/k/mntv/plugins/streamingsites.py", line 27, in Download
    download = subprocess.Popen(['/usr/bin/youtube-dl', identifier], stdout=subprocess.PIPE)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1259, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

---

### Post by Kheops_74 on 2012-10-22
Solve the previous error by reinstalling youtube-dl package.

Here a new error. The downloaded video is an mp4 but the script try to copy a FLV. Any idea?

No video metadata could be detectedImporting video 7205ea2877ca683c0fca7aaefa869d49...
Problem: moving /var/lib/mythtv/mythnettv/<type 'file'>.flv did not work, please check file permissions.
 Will copy instead.Download Error: [Errno 2] No such file or directory: "/var/lib/mythtv/mythnettv/<type 'file'>.flv"
Traceback (most recent call last):
  File "/home/k/mntv/mythnettvcore.py", line 123, in DownloadAndImport
    prog.Import(out=out)
  File "/home/k/mntv/program.py", line 713, in Import
    '%s/%s' %(videodir, dest_file))
  File "/usr/lib/python2.7/shutil.py", line 119, in copy
    copyfile(src, dst)
  File "/usr/lib/python2.7/shutil.py", line 82, in copyfile
    with open(src, 'rb') as fsrc:
IOError: [Errno 2] No such file or directory: "/var/lib/mythtv/mythnettv/<type 'file'>.flv"
No video metadata could be detectedImporting video 7205ea2877ca683c0fca7aaefa869d49...
Problem: moving /var/lib/mythtv/mythnettv/<type ''file''>.flv did not work, please check file permissions.
 Will copy instead.Couldn't straggling 7205ea2877ca683c0fca7aaefa869d49, removing it from the queue
  Error: [Errno 2] No such file or directory: "/var/lib/mythtv/mythnettv/<type ''file''>.flv"

---

### Post by Kheops_74 on 2012-10-22
The programmer post a new version on github : [https://github.com/managementboy/mntv](https://github.com/managementboy/mntv). I reinstall it and it seems to solve the YouTube issue. Look everything work just fine. Time will say.

---

### Post by rayperkins on 2012-11-02
I am trying to get mythnettv going on a new install of mythbuntu 12.04.1.  I follwed the README and on first run it seems to execute ok, I just specify the --datadir option.

On subsequent runs, --help works but anything else gives me a 1060 error about a duplicate column (mythnettv_programs.mime_type).

Any ideas?  I have searched high and low and have not found anything on point.  I am not sure why the script would be trying to re-create table columns anytime it runs.




ray@myth:~/managementboy-mntv-b3ada26$ ./mythnettv subscribe "http://www.ted.com/talks/rss" "TEDTalks" "yourchanid" "ttvdbid"
Updating tables
Traceback (most recent call last):
  File "./mythnettv", line 778, in <module>
    main(sys.argv)
  File "./mythnettv", line 244, in main
    db = database.MythNetTvDatabase()
  File "/home/ray/managementboy-mntv-b3ada26/database.py", line 58, in __init__
    self.CheckSchema()
  File "/home/ray/managementboy-mntv-b3ada26/database.py", line 175, in CheckSchema
    self.UpdateTables()
  File "/home/ray/managementboy-mntv-b3ada26/database.py", line 514, in UpdateTables
    self.db_connection.query('alter table mythnettv_programs '
_mysql_exceptions.OperationalError: (1060, "Duplicate column name 'mime_type'")
ray@myth:~/managementboy-mntv-b3ada26$

---

### Post by Kheops_74 on 2012-11-02
I'm not an expert. I looked at the code in [https://github.com/managementboy/mntv/blob/master/database.py](https://github.com/managementboy/mntv/blob/master/database.py)

line 514 is:

 if self.version == '7':
      # Start tracking the MIME type of videos, this helps with bittorrent
      self.Log('Upgrading schema from 7 to 8')
      self.db_connection.query('alter table mythnettv_programs '
                               'add column mime_type text, '
                               'add column tmp_name varchar(255);')
      self.version = '8'

Look like it want to upgrade your database. When i did my update to 12.10, i update mythtv to 0.26 also. I know that it upgrade the MySQL database. Maybe the script is tested with MythTV 0.26, i don't know. Here it work great with Ubuntu 12.10 and MythTv 0.26.

K

---

### Post by Kheops_74 on 2012-11-02
BTW, here the table structure of the table mythnettv_programs in my MySQL server.

Table Structure

Field Type Null Key Default Extra

guid text YES NULL
url text YES NULL
title text YES NULL
subtitle text YES NULL
description text YES NULL
date datetime YES NULL
unparsed_date text YES NULL
parsed_date text YES NULL
download_started int(11) YES NULL
download_finished int(11) YES NULL
imported int(11) YES NULL
transfered int(11) YES NULL
size int(11) YES NULL
filename text YES NULL
mime_type text YES NULL
tmp_name varchar(255) YES NULL
inactive tinyint(4) YES NULL
attempts tinyint(4) YES NULL
failed tinyint(4) YES NULL
last_attempt datetime YES NULL
inetref text YES NULL

---

### Post by trogod on 2012-11-08
I think I have the same problem.  I posted about this on the MythNetTV mailing list and the github site:

[email]Mythnettv@lists.stillhq.com[/email]
[http://lists.stillhq.com/listinfo.cgi/mythnettv-stillhq.com](http://lists.stillhq.com/listinfo.cgi/mythnettv-stillhq.com)

[https://github.com/managementboy/mntv/issues/2](https://github.com/managementboy/mntv/issues/2)

The response was

[INDENT]I think I have figured it out. It seems that the "new" version of mysql in 12.10 Ubuntu defaults to innodb when creating a new table. The mythnettv scripts needed it to be myisam. Well, long story short, I have updated the database part to explicitly create myisam tables for mythnettv and it seems to work. 
[/INDENT]

I haven't tried it out, yet, but I wanted to report back here

---

### Post by rayperkins on 2012-11-25
I have tried this and the latest update works.

Thanks to Elkin Fricke for fixing this quickly.

---

