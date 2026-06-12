---
title: "Video Thumbnail Creation, Perl script"
date: 2010-10-08
forum: Mythbuntu
---

### Post by scudderwagg on 2010-10-08
Hey guys, I have been trying to automatically create thumbnails for a bunch of videos (i.e. home movies so there's no cover art to download).  I was trying to use the script available here:
[http://www.mythtv.org/wiki/Generatevideothumbs.pl]("http://www.mythtv.org/wiki/Generatevideothumbs.pl")

I had used this before, maybe 2 years ago, under Mythbuntu 8.10 and it worked fine.  Now I've upgraded to 10.04 and it's not working.  When I try to run it gives me an error message:
Ln 36 use: not found

Looking at line 36 from the script it says
```
Use DBI;
```

Now the wiki page says the following at the top:
Script needs to be updated to use Perl bindings for database credentials.

Unfortunately I'm a bit of noob and while I've googled around to try to figure out what to do, I don't really know enough about Perl to know what to do to update the script properly.  Any help would be greatly appreciated.

Script Code:
```
#!/usr/bin/perl

# generatevideothumbs.pl

# this script will loop through all videos in videometadata,
# capture a screenshot for each, move each screenshot to the
# COVERPATH dir, and update each row in videometadata with
# the appropriate information. Only rows with coverfile=
# 'No Cover' are processed. A percentage of the length
# of each video is used for the capture position to account
# for clips of widely varying lengths.

# This script is mostly based on a bash script posted to the mythtv-users
# mailing list by damonkeiman-at-hotmail-dot-com; viewable at:
# <http://www.gossamer-threads.com/lists/mythtv/users/273113#273113>.
# I had trouble getting it to work as-is (it kept losing parts of the output
# from the first mysql query), and wound up rewriting it in Perl to get it to
# work.

# Portions written by me are
# Copyright (C) 2007 David Miller <dave@justdave.net>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# The full text of the GNU General Public License can be viewed at
# <http://www.gnu.org/licenses/>.

use DBI;

if (getpwuid($>) ne "mythtv") {
  print STDERR "You must run this script as the mythtv user.\n";
  exit 1;
};

# set some defaults
my %config = (
  DBHostName => 'localhost',
  DBUserName => 'mythtv',
  DBName     => 'mythconverg',
  DBPassword => '',
);

# read in the real ones
open MYSQLDATA, "<", "/etc/mythtv/mysql.txt";
while (my $line = <MYSQLDATA>) {
  if ($line =~ /^(DB\S+)=(.*)\s*$/) {
    $config{$1} = $2;
  }
}
close MYSQLDATA;

# intialize variables
my $OUTPATH='/tmp';
my $COVERPATH='/home/mythtv/.mythtv/MythVideo';
my $FRAME='00000002.jpg';
my $SKIPOFFSET='35';

my $dsn = "DBI:mysql:host=" . $config{DBHostName} . ":database=" . $config{DBName};
my $dbh = DBI->connect($dsn, $config{DBUserName}, $config{DBPassword});

my $sth = $dbh->prepare("SELECT intid, filename FROM videometadata WHERE coverfile='No Cover'");
$sth->execute();
while (my ($ID, $FILE) = $sth->fetchrow_array()) {
  print "MYSQLRESULT: id=$ID, file=$FILE\n";

  # if video is mpeg, use ffmpeg12 codec to avoid pixelation
  my @VC = ();
  if ($FILE =~ /.*\.mp[e]*g/) {
    @VC=("-vc","ffmpeg12");
  }

  # if video is a .iso or a .img, add dvd:\\1 -dvd-device
  my @dvd = ();
  if ($FILE =~ /\.(iso|img)$/i) {
    @dvd=("dvd://1", "-dvd-device");
  }

  # use mplayer to get length of video in seconds
  my $length=`echo -n q | mplayer -vo null -nosound -identify -ac null -vc null "$FILE" | egrep "^(ID_LENGTH=)" | cut -d '=' -f 2`;

  if (!$length) {
    print "mplayer was unable to get the $FILE length.\n";
    next;
  }

  my $SKIP = int(($length * $SKIPOFFSET) / 100);
  print "calculated skip seconds: $SKIP\n";

  # command to get jpeg from video
  system("mplayer","-really-quiet","-ac","null","-noframedrop","-ss",$SKIP,"-vo","jpeg:quality=50:outdir=$OUTPATH","-frames","2",@VC,"-nosound",@dvd,$FILE);

  # move jpeg from outpath to coverpath
  print "mv $OUTPATH/$FRAME $COVERPATH/intid.$ID.jpg\n";
  if (0 != system("mv", "$OUTPATH/$FRAME", "$COVERPATH/intid.$ID.jpg")) {
    print "Move failed. Will not update videometadata table...\n";
    unlink "$OUTPATH/$FRAME";
  }
  else {
    # SQL to update table with cover image path
    my $usth = $dbh->prepare("UPDATE videometadata SET coverfile='$COVERPATH/intid.$ID.jpg' WHERE intid=$ID LIMIT 1");
    $usth->execute();
  }
}
```

---

### Post by ian dobson on 2010-10-08
Hi,

Maybe have a look at the script from my website, you can just use system("mythbackend --generate-preview --infile " . @$XXX[2] . " > /dev/null"); to generate a preview file.

My script can actually create thumbnails if they're missing, you just need to enable the code.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-10-09
Hi,

OK I've just read you post again and you want to create thumbs for videos, not recordings, so my script won't help you much.

If your only missing DBI then install it:-
sudo apt-get install  libdbi-perl

Regards
Ian Dobson

---

### Post by ian dobson on 2010-10-09
Hi,

OK I've played about with the script abit, it now seems to work on my frontend. I've also fixed afew bugs in the mkv/h264 coding.

So here's the script:-
```
#!/usr/bin/perl

# generatevideothumbs.pl

# this script will loop through all videos in videometadata,
# capture a screenshot for each, move each screenshot to the
# COVERPATH dir, and update each row in videometadata with
# the appropriate information. Only rows with coverfile=
# 'No Cover' are processed. A percentage of the length
# of each video is used for the capture position to account
# for clips of widely varying lengths.

# This script is mostly based on a bash script posted to the mythtv-users
# mailing list by damonkeiman-at-hotmail-dot-com; viewable at:
# <http://www.gossamer-threads.com/lists/mythtv/users/273113#273113>.
# I had trouble getting it to work as-is (it kept losing parts of the output
# from the first mysql query), and wound up rewriting it in Perl to get it to
# work.

# Portions written by me are
# Copyright (C) 2007 David Miller <dave@justdave.net>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# The full text of the GNU General Public License can be viewed at
# <http://www.gnu.org/licenses/>.

use DBI;

if (getpwuid($>) ne "mythtv") {
  print STDERR "You must run this script as the mythtv user.\n";
  exit 1;
};

# set some defaults
my %config = (
  DBHostName => 'localhost',
  DBUserName => 'mythtv',
  DBName     => 'mythconverg',
  DBPassword => '',
);

# read in the real ones
open MYSQLDATA, "<", "/etc/mythtv/mysql.txt";
while (my $line = <MYSQLDATA>) {
  if ($line =~ /^(DB\S+)=(.*)\s*$/) {
    $config{$1} = $2;
  }
}
close MYSQLDATA;

# intialize variables
my $OUTPATH='/tmp';
my $COVERPATH='/home/mythtv/.mythtv/MythVideo';
my $FRAME='00000002.jpg';
my $SKIPOFFSET='35';

my $dsn = "DBI:mysql:host=" . $config{DBHostName} . ":database=" . $config{DBName};
my $dbh = DBI->connect($dsn, $config{DBUserName}, $config{DBPassword});

my $sth = $dbh->prepare("SELECT intid, filename FROM videometadata WHERE coverfile='No Cover' or coverfile=''");
$sth->execute();
while (my ($ID, $FILE) = $sth->fetchrow_array()) {
  print "MYSQLRESULT: id=$ID, file=$FILE\n";

  # if video is mpeg, use ffmpeg12 codec to avoid pixelation
  my @VC = ();
  if ($FILE =~ /.*\.mp[e]*g/) {
    @VC=("-vc","ffmpeg12");
  }

  # if video is a .iso or a .img, add dvd:\\1 -dvd-device
  my @dvd = ();
  if ($FILE =~ /\.(iso|img)$/i) {
    @dvd=("dvd://1", "-dvd-device");
  }

  # use mplayer to get length of video in seconds
  my $length=`echo -n q | mplayer -vo null -nosound -identify -ac null -vc null -nocorrect-pts "$FILE" | egrep "^(ID_LENGTH=)" | cut -d '=' -f 2`;

  if (!$length) {
    print "mplayer was unable to get the $FILE length.\n";
    next;
  }

  my $SKIP = int(($length * $SKIPOFFSET) / 100);
  print "calculated skip seconds: $SKIP\n";

  # command to get jpeg from video
  system("mplayer","-really-quiet","-ac","null","-noframedrop","-nocorrect-pts","-ss",$SKIP,"-vo","jpeg:quality=50:outdir=$OUTPATH","-frames","2",@VC,"-nosound",@dvd,$FILE);

  # move jpeg from outpath to coverpath
  print "mv $OUTPATH/$FRAME $COVERPATH/intid.$ID.jpg\n";
  if (0 != system("mv", "$OUTPATH/$FRAME", "$COVERPATH/intid.$ID.jpg")) {
    print "Move failed. Will not update videometadata table...\n";
    unlink "$OUTPATH/$FRAME";
  }
  else {
    # SQL to update table with cover image path
    my $usth = $dbh->prepare("UPDATE videometadata SET coverfile='$COVERPATH/intid.$ID.jpg' WHERE intid=$ID LIMIT 1");
    $usth->execute();
  }
}


```

Regards
Ian Dobson

---

### Post by scudderwagg on 2010-10-29
Well, I've had a little more success now, but I've hit another problem getting this to work.  When I run it, I get the following for every file:

MYSQLRESULT: id=452, file=/home/scudder/Videos/xyz.avi
mplayer: could not open config files /home/mythtv/.lircrc and /etc/lirc//lirc/lircrc
mplayer: No such file or directory
Failed to read LIRC config file ~/.lircrc.
File not found: '/home/scudder/Videos/xyz.avi'
Failed to open /home/scudder/Videos/xyz.avi.
mplayer was unable to get the /home/scudder/Videos/xyz.avi length.

I tried copying over the .lirc directory from my user home to the mythtv home directory but I still get the same thing.  Any help is greatly appreciated.

---

### Post by ian dobson on 2010-10-30
Hi,

The .lirc error messages are nothing to worry about, it just means the mplayer can't use the remote control, which we don't need anyway in this case.

The error your seeing is that mplayer can decode the length of the avi file, which it uses to calculate the offset for the thumb nail.

It could be that the avi file is unreadable or mplayer just can find the length. I'll see what's possible.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-10-30
Hi,

Does the file /home/scudder/Videos/xyz.avi actually exist and what permissions does it have? Does the mythtv user have read permissions?

Regards
Ian Dobson

---

### Post by scudderwagg on 2010-10-30
Ian, thanks for your patience and help.  It was a permissions issue and I got everything to work now.  Much easier to know what each video is now.  Thanks again.

---

### Post by ian dobson on 2010-10-31
Hi,

No problems, I like helping people.

By the way I've updated to script abit so the mplayer lirc errors aren't echoed to the terminal and spaces in the file names are correctly handled:-

```
MYSQLRESULT: id=40, file=/mnt/video/mythtv/video/marc/MKV/Unthinkable.Multi.720P.BluRay.x264-Heman-wWw.Extreme-Down.Com.mkv
calculated skip seconds: 2039
mv /tmp/00000002.jpg /home/mythtv/.mythtv/MythVideo/intid.40.jpg
MYSQLRESULT: id=41, file=/mnt/video/mythtv/video/marc/MKV/Wanted 2008 MULTi 1080p Bluray x264 DTS-SoSo.mkv
calculated skip seconds: 2307
mv /tmp/00000002.jpg /home/mythtv/.mythtv/MythVideo/intid.41.jpg
MYSQLRESULT: id=42, file=/mnt/video/mythtv/video/marc/MKV/X-Men.Origins.Wolverine.VOSTFR 720p.BluRay.x264.REPACK-METiS.mkv
calculated skip seconds: 2255
mv /tmp/00000002.jpg /home/mythtv/.mythtv/MythVideo/intid.42.jpg
MYSQLRESULT: id=43, file=/mnt/video/mythtv/video/marc/MKV/fhd-dorian.gray.720p.mkv
calculated skip seconds: 2358
mv /tmp/00000002.jpg /home/mythtv/.mythtv/MythVideo/intid.43.jpg
MYSQLRESULT: id=44, file=/mnt/video/mythtv/video/marc/MKV/ninhd-robinhood-720.mkv
calculated skip seconds: 3272
mv /tmp/00000002.jpg /home/mythtv/.mythtv/MythVideo/intid.44.jpg
MYSQLRESULT: id=45, file=/mnt/video/mythtv/video/marc/MKV/xpendables.2010.720p.VOSTFR.BRip.AC3.x264-ReMz.mkv
calculated skip seconds: 2083
mv /tmp/00000002.jpg /home/mythtv/.mythtv/MythVideo/intid.45.jpg
```

Here's the script
```


#!/usr/bin/perl

# generatevideothumbs.pl

# this script will loop through all videos in videometadata,
# capture a screenshot for each, move each screenshot to the
# COVERPATH dir, and update each row in videometadata with
# the appropriate information. Only rows with coverfile=
# 'No Cover' are processed. A percentage of the length
# of each video is used for the capture position to account
# for clips of widely varying lengths.

# This script is mostly based on a bash script posted to the mythtv-users
# mailing list by damonkeiman-at-hotmail-dot-com; viewable at:
# <http://www.gossamer-threads.com/lists/mythtv/users/273113#273113>.
# I had trouble getting it to work as-is (it kept losing parts of the output
# from the first mysql query), and wound up rewriting it in Perl to get it to
# work.

# Portions written by me are
# Copyright (C) 2007 David Miller <dave@justdave.net>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# The full text of the GNU General Public License can be viewed at
# <http://www.gnu.org/licenses/>.

use DBI;

if (getpwuid($>) ne "mythtv") {
  print STDERR "You must run this script as the mythtv user.\n";
  exit 1;
};

# set some defaults
my %config = (
  DBHostName => 'localhost',
  DBUserName => 'mythtv',
  DBName     => 'mythconverg',
  DBPassword => '',
);

# read in the real ones
open MYSQLDATA, "<", "/etc/mythtv/mysql.txt";
while (my $line = <MYSQLDATA>) {
  if ($line =~ /^(DB\S+)=(.*)\s*$/) {
    $config{$1} = $2;
  }
}
close MYSQLDATA;

# intialize variables
my $OUTPATH='/tmp';
my $COVERPATH='/home/mythtv/.mythtv/MythVideo';
my $FRAME='00000002.jpg';
my $SKIPOFFSET='35';

my $dsn = "DBI:mysql:host=" . $config{DBHostName} . ":database=" . $config{DBName};
my $dbh = DBI->connect($dsn, $config{DBUserName}, $config{DBPassword});

my $sth = $dbh->prepare("SELECT intid, filename FROM videometadata WHERE coverfile='No Cover' or coverfile=''");
$sth->execute();
while (my ($ID, $FILE) = $sth->fetchrow_array()) {
  print "MYSQLRESULT: id=$ID, file=$FILE\n";

  # if video is mpeg, use ffmpeg12 codec to avoid pixelation
  my @VC = ();
  if ($FILE =~ /.*\.mp[e]*g/) {
    @VC=("-vc","ffmpeg12");
  }

  # if video is a .iso or a .img, add dvd:\\1 -dvd-device
  my @dvd = ();
  if ($FILE =~ /\.(iso|img)$/i) {
    @dvd=("dvd://1", "-dvd-device");
  }

  # use mplayer to get length of video in seconds
  my $length=`echo -n q | mplayer -vo null -nosound -identify -ac null -vc null -nocorrect-pts "$FILE" 2>&1 | egrep "^(ID_LENGTH=)" | cut -d '=' -f 2`;

  if (!$length) {
    print "mplayer was unable to get the $FILE length,trying a default value.\n";
    $length=1000;
  }

  my $SKIP = int(($length * $SKIPOFFSET) / 100);
  print "calculated skip seconds: $SKIP\n";

  # command to get jpeg from video
###  system("mplayer","-really-quiet","-ac","null","-noframedrop","-nocorrect-pts","-ss",$SKIP,"-vo","jpeg:quality=50:outdir=$OUTPATH","-frames","2",@VC,"-nosound",@dvd,$FILE,">> /dev/null","2>&1");
  $command="mplayer -really-quiet -ac null -noframedrop -nocorrect-pts -ss $SKIP -vo jpeg:quality=50:outdir=$OUTPATH -frames 2 @VC -nosound @dvd \"$FILE\"";
  $result=`$command  2>&1`;
#   print "$command\n";
  # move jpeg from outpath to coverpath
  print "mv $OUTPATH/$FRAME $COVERPATH/intid.$ID.jpg\n";
  if (0 != system("mv", "$OUTPATH/$FRAME", "$COVERPATH/intid.$ID.jpg")) {
    print "Move failed. Will not update videometadata table...\n";
    unlink "$OUTPATH/$FRAME";
  }
  else {
    # SQL to update table with cover image path
    my $usth = $dbh->prepare("UPDATE videometadata SET coverfile='$COVERPATH/intid.$ID.jpg' WHERE intid=$ID LIMIT 1");
    $usth->execute();
  }
}


```

Regards
Ian Dobson

---

### Post by CasparSeb on 2010-11-03
Thank you very much. it works like a charme.. :)

---

### Post by spyda46 on 2011-10-04
Hi Guys

I wonder if anyone could help me on this, i have tried everything to get this working.

When i run the script (the latest one posted by Ian on 			October 31st, 2010) I get the following errors

mythtv@buntu:/home/james/Desktop$ ./script9
MYSQLRESULT: id=2, file=eggbean.avi
mplayer was unable to get the eggbean.avi length,trying a default value.
calculated skip seconds: 350
mv /tmp/00000002.jpg /home/mythtv/.mythtv/MythVideo/intid.2.jpg
mv: cannot stat `/tmp/00000002.jpg': No such file or directory
Move failed. Will not update videometadata table...
MYSQLRESULT: id=16, file=Family.Guy.avi
mplayer was unable to get the Family.Guy.avi length,trying a default value.
calculated skip seconds: 350
mv /tmp/00000002.jpg /home/mythtv/.mythtv/MythVideo/intid.16.jpg
mv: cannot stat `/tmp/00000002.jpg': No such file or directory
Move failed. Will not update videometadata table...

I have the correct permissions on the folders 

mythtv@buntu:/home/james/Desktop$ ls -all /home/mythtv/.mythtv/MythVideo
total 8
drwxr-xr-x 2 mythtv root   4096 2011-10-03 19:22 .
drwxr-xr-x 6 mythtv mythtv 4096 2011-10-03 19:22 ..


It looks like Mplayer is not creating the jpegs from the files i have

Could anyone help me please i am going crazy trying to figure this out 

:)

---

### Post by spyda46 on 2011-10-04
Just to add when i run the command to generate the jpeg below it works but not when run in the script

james@buntu:/var/lib/mythtv/coverart$ mplayer -really-quiet -ac null -noframedrop -nocorrect-pts -ss 350 -vo jpeg:quality=50:outdir=/tmp -frames 2 @VC -nosound @dvd /var/lib/mythtv/videos/Family.Guy.avi
mplayer: could not connect to socket
mplayer: No such file or directory
james@buntu:/var/lib/mythtv/coverart$

---

### Post by spyda46 on 2011-10-04
Is this to do with mplayer? when i run the command manually for length i get errors

mplayer -vo null -nosound -identify -ac null -vc null -nocorrect-pts /var/lib/mythtv/videos/Family.Guy.2010.Its.A.Trap.DVDRip.XviD.avi
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory

Any ideas on how fix this ?

Thanks

---

### Post by ian dobson on 2011-10-04
> **spyda46 said:**
> Is this to do with mplayer? when i run the command manually for length i get errors

mplayer -vo null -nosound -identify -ac null -vc null -nocorrect-pts /var/lib/mythtv/videos/Family.Guy.2010.Its.A.Trap.DVDRip.XviD.avi
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory

Any ideas on how fix this ?

Thanks

Hi,

Thats 100% a mplayer error. The script tries to find out how long the file is and then uses a "reasonable" offset to grab a picture.

Are you sure it's not a permissions problem.

Regards
Ian Dobson

---

### Post by spyda46 on 2011-10-04
Thanks,

Well i pretty sure, mythtv owns the folders and can read / write 

Not really sure where else to look

What permissions would you suggest i look into? 

I have check mythtv can read / write to /home/mythtv/.mythtv/MythVideo

everytime i run the script i get the below results, i can;t see why the 00000002.jpg file isnt created. mythtv user can create files in the tmp dir manually and it works when i run the command manually? 

mv /tmp/00000002.jpg /home/mythtv/.mythtv/MythVideo/intid.148.jpg
mv: cannot stat `/tmp/00000002.jpg': No such file or directory
Move failed. Will not update videometadata table...

---

### Post by spyda46 on 2011-10-04
I have found a solution - if i add /var/lib/mythtv/videos into the script in front of the $FILENAME for the jpeg grabber command it seems to work

---

### Post by ian dobson on 2011-10-04
Hi,

The script should be run from the video directory.

Maybe I can hack the script so that it ready the video directory from the database... let me have a think about it.


Regards
Ian Dobson

---

### Post by spyda46 on 2011-10-05
Thanks for the reply, yea afterwards i placed the script in the video folder - i still have some it can't move 

anyway thanks for your help and i would welcome a new script :)

---

### Post by ian dobson on 2011-10-05
Hi,

Strange the script should work, the SQL table videometadata/field filename seems to contain the path to the file (/mnt/video/mythtv/video/Cartoon/FileName.mkv). Ofcoarse this path must be correct. It'll be correct on the frontend that can play the videos but will be incorrect for the backend if run on a different system.

Also the coverart directory (/home/mythtv/.mythtv/MythVideo) must be correct. If it's not edit the script.

Regards
Ian Dobson

---

