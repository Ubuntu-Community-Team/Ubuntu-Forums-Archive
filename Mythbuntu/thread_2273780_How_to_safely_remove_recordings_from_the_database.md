---
title: "How to safely remove recordings from the database"
date: 2015-04-15
forum: Mythbuntu
---

### Post by GreatBeach on 2015-04-15
Hello all, brand new fan and noob here.

I want to create my own script for converting recorded video from MythTV.   My plan is to query the database and pull out relevant information for the recording, then covert the video and save the file into my Plex Media Server folders.     After the conversion is complete, I will delete the source file and remove the record from the database...

My question is this; what tables should I be concerned with, in the 'mythconverg' database, to remove a recording event?     I see the 'recorded' and 'recordedprogram' tables... but are there more tables to be concerned with?     I'm not looking for the SQL code, just what tables are used so that I can safely remove the event and not break MythTV.   :)

Thanks in advance!

---

### Post by khPWXxF on 2015-04-16
You can use the removerecorded call of the services API for this.  It is in the wiki.  The parameters to be used in the call are discussed here

[https://forum.mythtv.org/viewtopic.php?f=33&t=478](https://forum.mythtv.org/viewtopic.php?f=33&t=478)

If you want a perl example just ask.
Hth
Phil

---

### Post by GreatBeach on 2015-04-16
Thanks Phil!   This was just what I was looking for.

---

### Post by GreatBeach on 2015-04-17
I tried to make the API work but it failed.  Each time I would receive "401Invalid Action".   While browsing around I found a Perl script that I was able to modify and it seems to work well.

---

### Post by khPWXxF on 2015-04-17
Was it this?
[https://www.mythtv.org/wiki/Perl_API_examples](https://www.mythtv.org/wiki/Perl_API_examples)
I forgot I put removerecorded as the example.

You have seen that removerecorded has a limited shelf life.  See
[https://www.mythtv.org/wiki/DVR_Service#RemoveRecorded](https://www.mythtv.org/wiki/DVR_Service#RemoveRecorded)
but I am not sure yet how one can tell within a program which version of api calls is supported.
Phil

---

### Post by GreatBeach on 2015-04-17
The Perl example I found was here: [http://www.taz.net.au/mythtv-tools/](http://www.taz.net.au/mythtv-tools/)

I adjusted 'myth-delete-recording.pl' so that I could feed it the file name of the recording I wanted to remove from the database.   The script removes the recording from the database and also removes the associated files from the directory.  There is probably a better way but for now this will work.

Adjusted script (delete-recording.pl):

```
#! /usr/bin/perl -w

# verify command line argument was given
if (@ARGV == 0) {
  print "\nUsage: delete-recording.pl <recorded file name>\n";
  exit;
}

# set recording directory and setup removal job
$RecordingPath = "/var/lib/mythtv/recordings/";
$BaseName = $ARGV[0];
$FilePath = $RecordingPath . $BaseName;

# verify filename given exists
unless (-e $FilePath) {
  print "\nFile not found: $FilePath\n";
  exit;
}

# process request
use MythTV;

$Myth = new MythTV();

print "Removing the following recording: $BaseName\n" ;
my $file = $Myth->new_recording($BaseName);
$Myth->backend_command(['FORCE_DELETE_RECORDING', $file->to_string()], '0');
```

---

