---
title: "Create html list of recordings"
date: 2008-11-19
forum: Mythbuntu
---

### Post by zagor on 2008-11-19
Hi all,

I need to give the list of my recordings and videos to a friend, with the description, if possible.
A simple list of the filnames is not useful, given the nasty filenames of mythtv.
I can certeinly use 
```
mythrename.pl --link
```
but I won;t have the show description.

The best would be to have a html file in the fashion of the mythweb plugin: a list of recordings, with an image (linked to the file) and the description and possibly a "delete" botton

Very nice would also be to improve the above by having a script or a plugin which will allow to: 
1. select videos/recordings
2. copy selected files to a DVD or external HD or path
3. create in the target folder a html file as above, with link to the file (so to open it easily) and delete botton (so to remove the file once watched).

Anybody has a suggestion on how to do this? Anybody volunteers to create such a script/plugin? Or simply knows similar scripts already available?

I'm very poor in scripting and programming (VERY poor!!) so I really can't do it by myself....

Thanks

---

### Post by ian dobson on 2008-11-19
Hi,

Wrote this a while back, it sends me an email with a list of all programs recorded yesterday, maybe it'll be a good starting point.

```

#!/usr/bin/perl
#
# Send email with a list of recordings from yesterday
#
#

use DBI;
use Net::SMTP;
my $TransCodeLink='http://mail.planet-ian.com/mythweb/tv/detail/';
my $MailServer="mail.planet-ian.com";
my $MailTo='i.dobson@planet-ian.com';
my $MailFrom='MythTV@planet-ian.com';

  my ($SQLUser, $SQLPassword, $hostname,$SQLServer)=PrepSQLRead();

  my @result=SQLQuery("SELECT title,subtitle,description,chanid,UNIX_TIMESTAMP(starttime),basename 
                       from recorded 
                       where starttime >= DATE_SUB(CURRENT_DATE(), INTERVAL 1 DAY) 
                       and starttime < CURRENT_DATE()");
  $smtp = Net::SMTP->new("$MailServer",
                    Hello => "$MailServer",
                    Timeout => 60);
  $smtp->mail($MailFrom);
  $smtp->to($MailTo);
  $smtp->data();
  $smtp->datasend("From: $MailFrom\n");
  $smtp->datasend("To: $MailTo\n");
  $smtp->datasend("Subject: MythTV recordings from yesterday\n");
  $smtp->datasend("\n");
  
  for my $XXX (@result){
  	 $smtp->datasend("@$XXX[0] - @$XXX[1] \n@$XXX[2]\n");
  	 if (index (@$XXX[5], ".mpg") > 0 ) {
    	 if ( $TransCodeLink ne "") {
  	 	   $smtp->datasend("Transcode Recording - $TransCodeLink@$XXX[3]\/@$XXX[4]?job=1\n");
       }
  	 }
  	 $smtp->datasend("\n\n\n");
  }
  $smtp->datasend;
  $smtp->quit;


exit;

#Perform  SQL query returns an array of arrays
sub SQLQuery {
   my  ($QUERY) = @_;
   my @data;
   my $dbh = DBI->connect_cached("DBI:mysql:$SQLDBName:$SQLServer", $SQLUser, $SQLPassword)
     or die "Couldn't connect to database: " . DBI->errstr;
   my $table_data = $dbh->prepare($QUERY) or die "Couldn't prepare statement: " . $dbh->errstr;
   $table_data->execute or die "Couldn't execute statement: " . $table_data->errstr;
   $SQLCount++;
   while ( @row = $table_data->fetchrow_array )  {
      push @data,[@row] ;
   }
   if ($data[0]) {
      return @data;
   } else {
      return 0;
   }
}

#Try and read MythTV configuration parameters from mysql.txt (This could be in several places)
sub PrepSQLRead {
   my $hostname = `hostname`;
   chomp($hostname);

# Read the mysql.txt file in use by MythTV. Could be in a couple places, so try the usual suspects
   my $found = 0;
   my @mysql = ('/usr/local/share/mythtv/mysql.txt',
      '/usr/share/mythtv/mysql.txt',
      '/etc/mythtv/mysql.txt',
      '/usr/local/etc/mythtv/mysql.txt',
      "$ENV{HOME}/.mythtv/mysql.txt",
      'mysql.txt'
     );
   foreach my $file (@mysql) {
      next unless (-e $file);
      $found = 1;
      open(CONF, $file) or die "Unable to open $file:  $!\n\n";
      while (my $line = <CONF>) {

         # Cleanup
         next if ($line =~ /^\s*#/);
         $line =~ s/^str //;
         chomp($line);

         # Split off the var=val pairs
         my ($var, $val) = split(/\=/, $line, 2);
         next unless ($var && $var =~ /\w/);
         if ($var eq 'DBHostName') {
            $SQLServer = $val;
         }
         elsif ($var eq 'DBUserName') {
            $SQLUser = $val;
         }
         elsif ($var eq 'DBName') {
            $SQLDBName = $val;
         }
         elsif ($var eq 'DBPassword') {
            $SQLPassword = $val;
         }

         # Hostname override
         elsif ($var eq 'LocalHostName') {
            $hostname = $val;
         }
      }
      close CONF;
   }
   die "Unable to locate mysql.txt:  $!\n\n" unless ($found && $SQLServer);
   return ($SQLUser, $SQLPassword, $hostname,$SQLServer);
}

```

Regards
Ian Dobson

---

### Post by zagor on 2008-11-20
Thanks, I'll give it a spin and try to adjust to my needs.

---

### Post by dmfrey on 2008-11-20
I setup some scripts to transcode select recordings for my nokia n800.  Once they are complete, they are dropped into a directory that I expose through apache.  There is a php file in that produces a RSS feed for me to use with my podcast client on my nokia n800 for automatic delivery to the unit.

Would something like this work for you?  I can post it later when I get home if you like.

---

### Post by ian dobson on 2008-11-21
Hi,

I had afew minutes free yesterday and wrote this:-

```

#!/usr/bin/perl
#
# Make a list of all recordings to a HTML table
#
# This is the only variable you need to change it points to the HTML file to be created
my $HTMLFile='/data/tmp/HTMLLinks.html';

use DBI;

  my ($SQLUser, $SQLPassword, $hostname,$SQLServer)=PrepSQLRead();
  my @result=SQLQuery("SELECT title,subtitle,description,chanid,starttime,basename from recorded ");

  open (HTMLFILE ,">$HTMLFile");
  print HTMLFILE <<EOM;
<!doctype html public "-//w3c//dtd html 4.0 transitional//en">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
<title>MythTV Listings</title>
</head>
<body bgcolor="#CCCC99">
<table>
EOM

  for my $XXX (@result){
     print HTMLFILE <<EOM;
       <tr><td>@$XXX[0]</td><td>@$XXX[1]</td><td>@$XXX[2]</td></tr>
EOM
  }
  print HTMLFILE <<EOM;
</table>
</html>
EOM
close (HTMLFILE);
exit;


#Subs and functions from here on
#Perform  SQL query returns an array of arrays
sub SQLQuery {
   my  ($QUERY) = @_;
   my @data;
   my $dbh = DBI->connect_cached("DBI:mysql:$SQLDBName:$SQLServer", $SQLUser, $SQLPassword)
     or die "Couldn't connect to database: " . DBI->errstr;
   my $table_data = $dbh->prepare($QUERY) or die "Couldn't prepare statement: " . $dbh->errstr;
   $table_data->execute or die "Couldn't execute statement: " . $table_data->errstr;
   $SQLCount++;
   while ( @row = $table_data->fetchrow_array )  {
      push @data,[@row] ;
   }
   if ($data[0]) {
      return @data;
   } else {
      return 0;
   }
}

#Try and read MythTV configuration parameters from mysql.txt (This could be in several places)
sub PrepSQLRead {
   my $hostname = `hostname`;
   chomp($hostname);

# Read the mysql.txt file in use by MythTV. Could be in a couple places, so try the usual suspects
   my $found = 0;
   my @mysql = ('/usr/local/share/mythtv/mysql.txt',
      '/usr/share/mythtv/mysql.txt',
      '/etc/mythtv/mysql.txt',
      '/usr/local/etc/mythtv/mysql.txt',
      "$ENV{HOME}/.mythtv/mysql.txt",
      'mysql.txt'
     );
   foreach my $file (@mysql) {
      next unless (-e $file);
      $found = 1;
      open(CONF, $file) or die "Unable to open $file:  $!\n\n";
      while (my $line = <CONF>) {

         # Cleanup
         next if ($line =~ /^\s*#/);
         $line =~ s/^str //;
         chomp($line);

         # Split off the var=val pairs
         my ($var, $val) = split(/\=/, $line, 2);
         next unless ($var && $var =~ /\w/);
         if ($var eq 'DBHostName') {
            $SQLServer = $val;
         }
         elsif ($var eq 'DBUserName') {
            $SQLUser = $val;
         }
         elsif ($var eq 'DBName') {
            $SQLDBName = $val;
         }
         elsif ($var eq 'DBPassword') {
            $SQLPassword = $val;
         }

         # Hostname override
         elsif ($var eq 'LocalHostName') {
            $hostname = $val;
         }
      }
      close CONF;
   }
   die "Unable to locate mysql.txt:  $!\n\n" unless ($found && $SQLServer);
   return ($SQLUser, $SQLPassword, $hostname,$SQLServer);
}

```

Regards
Ian Dobson

---

### Post by zagor on 2008-11-21
@Ian:
WOW, thanks!
I'll try it asap and post a feedback.
This solves the most urgent part: give the list to my friend.
Still open how to move the shows to another directory and create the same html

@dmfrey:
Sounds a bit too complicated to me, but maybe there's something I can use:
I can skip the transcode and just run rename, than move to a different directory and finally check if the RSS is already enough or try to integrate and adapt the script from Ian.
So yes, please, post your scripts, so I can peer through them and see if and what I can adapt.
Thanks!

---

### Post by dmfrey on 2008-11-21
I will post the script this weekend, however, I was thinking and I am not seeing why you need to do this.  You could just expose your mythweb outside your home router and you friend could just go through the mythweb interface.  Am I missing something in your intent?  You could even turn on the ability to view the recording right from the mythweb interface if all he wants to do is watch the video, it will stream right to his desktop.

---

### Post by ian dobson on 2008-11-21
Hi,

You could use perl to copy/move the files to a different directory then a simple SQL command can update the database so that the storagegroup is correct.

something like 
```

UPDATE `mythconverg`.`recorded` SET `storagegroup` = 'newgroup'

```

Note that newgroup is the storage group that points to the new directory. You could just patch this SQl command into my script using the SQLQuery function.

Regards
Ian Dobson

---

### Post by zagor on 2008-11-21
@dmfrey
Two reasons for not doing as you propose:
1. I'm not on the internet 24hours, just the few minutes needed for the xmltv script to run
2. my friend might want to keep a copy of certain shows
Obviously, I can just copy the shows he wants, after renaming in human-readable format, but wouldn't be nice (to him) to give him also the show description? Hence my request.
Also, as for the list itself, without the recordings, I've just realized that I can create a simple pdf out of the "recorded programs" page of mythweb...!! 

@ian
If I know little of html, I actually know nothing of perl....
This might be a nice exercise for me to start learning perl, but it might take long (to me).
So, I'll try to follow your suggestion and write back, even if not quickly. Hope you don't mind to check this thread every once a while just to follow my progress (if any!!!).

Thanks to both

Edit: just a sidenote: how you two are doing when you want to keep some files with their description, saving them to a different HD or DVD? Do you just keep the file (maybe transcoded) without description? Is it not a pity? Mytharchive with "native archive" will copy the file(s) and give an xml with the description, one per file, but then this is done to be re-imported into mythtv, not to be "edible" to other software or OSs...

---

### Post by dmfrey on 2008-11-21
zagor,

I don't keep them around too often.  I record some kid shows for my daughter that I keep and will be archiving them to dvd iso and storing them on my server which is mounted over nfs and stores all videos, music and photos.

I do regularly create dvd's of Hereos for a friend of mine so that he can watch it (he doesn't have any form a of cable).

Otherwise, I don't keep recordings around for any period of time.

I will periodically transcode to my Nokia n800 and do a sync with my podcast catcher so that I can easily take it with me (no need for copying to an sd card or anything like that).

Actually, an rss feed for your friend may be beneficial, as he can run a rss feed reader (or live bookmark in firefox) and rss generator can be modified to list all the episodes currently in your watch list along with program details and a link to download the file, etc.

With some minor tweaking, you could add a table to the db and a script to your jobs menu that places an entry in the table that marks a recording to be exposed on the feed so you can select which recordings you want to expose.  That would be a neat little project to attempt and i may have to try it out this weekend if i get some time.

---

### Post by zagor on 2008-11-24
> **dmfrey said:**
> 
That would be a neat little project to attempt and i may have to try it out this weekend if i get some time.

That could be great! an rss feed might actually work fine for my purpose.
Let me know if you step forward in this "neat little project"!
Thanks

---

