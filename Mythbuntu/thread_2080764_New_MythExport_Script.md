---
title: "New MythExport Script"
date: 2012-11-04
forum: Mythbuntu
---

### Post by lionsnob on 2012-11-04
Hi all -

I wrote a perl script that does one thing: it changes the podcastName column in the mythexport table to be the same as the title column.

Why would you want to do this?  As far as I can tell, there is no way to create different podcasts for different shows.  This will create a single podcast for each show.

To use, copy and paste this text ```

#!/usr/bin/perl
use strict;
use warnings;
use DBI;

my $username='mythtv';
my $pass='your_mythconverg_pw';
my $db='mythconverg';
my $host='mythbackend_ip';
my $dbh = DBI->connect( "dbi:mysql:$db:host=$host", $username, $pass, { 'PrintError' => 1, 'RaiseError' => 1 } );
my $sql='update mythexport set podcastName = title';
#my $sql_arg=1;
my $sql_handle=$dbh->prepare($sql);
#$sql_handle->execute($sql_arg);
$sql_handle->execute();
#my @data;
#while (@data=$sql_handle->fetchrow_array()) {
#print join("\n",@data)
#}

``` into a text file named ```
setMythExportPodcast.pl
``` and place it into /usr/local/bin .  Change the IP and password to match your install.  Make it executable by running ```
sudo chmod +x /usr/local/bin/setMythExportPodcast.pl
``` and create a file named ```
setMythExportPodcast
``` in ```
/etc/cron.d/
``` with the following text ```
#
# Regular cron jobs for the setMythExportPodcast.pl script
#
*/1 * * * *  root	perl /usr/local/bin/setMythExportPodcast.pl

```The */1 means it will execute every minute.  Change the 1 to an appropriate value for you.

---

