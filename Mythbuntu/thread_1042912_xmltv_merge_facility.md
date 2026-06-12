---
title: "xmltv merge facility ?"
date: 2009-01-18
forum: Mythbuntu
---

### Post by Caysho on 2009-01-18
I'm in Perth, and the commercial channels broadcast much of their SD programming on their HD channels.

I have done a configuration whereby I:
[LIST=1]
[*]grab the SD data from oztivo
[*]load it into mythtv
[*]use sed to change some channel details for the HD data
[*]load the modified "HD" data.
[*]grab the HD data from oztivo (small selection of programmes)
[*]load the HD data.
[/LIST]

I expected mythfilldatabase to simply replace programme data, but I see this does not always happen (the programme end times in the file are not always honoured). I have used the --update and --refresh-all options but there's no difference in the results.

I found a tool called [xmltvAlter.exe]("http://www.xpmediacentre.com.au/community/free-epg-discussion/26970-xmltvalter-exe-xmltv-tool.html") which has a rule to do what I am after - have a look at the mergeChannels rule in its xmltvRules.xml file. Of course its a Windows application, and I don't want to run wine if I can avoid it.

Is there a way to merge the files in linux so I don't have to rely on mythfilldatabase to get it right ?
I see there is a [mythfilldatabase --refresh-all bug]("http://svn.mythtv.org/trac/ticket/6070"), but I'm not sure this covers my case.

---

### Post by ian dobson on 2009-01-18
Hi,

I'm using 2 xmltv grabbers and just call them from cron and then feed the files into mythtv using the mythfilldatabase -file option.

Works well for me.

Here's the script I'm using note the provider supplies the xmltv data in a compressed zip file that I need to expand before using.
I've also deleted somw of the code I've added to fixup the xmltv ID's which don't quite matchup on my system.

```

#!/usr/bin/perl
use URI;
use Date::Manip;
use Archive::Zip qw(:ERROR_CODES);
use LWP::UserAgent;

#Go to correct directory
chdir '/tmp';

#Cleanup mess left from last run
print "-Remove old data.xml file if it exists...\n";
unlink('/tmp/data.xml');
unlink('/tmp/raw.xml'); 
unlink('/tmp/log.tmp');
unlink('/tmp/tvdata.zip');
sleep 1;

#Get and save the file to /tmp using %2B1 (+1) to add one hour to the times
print "-Download updated listings from www.bleb.org...\n";
my $ua = LWP::UserAgent->new(agent=>"MythTV XMLTV grabber for www.planet-ian.com");
my $request = HTTP::Request->new('GET',"http://www.bleb.org/tv/data/listings?days=0..6&format=XMLTV&channels=bbc1%2B1,bbc2%2B1,bbc3%2B1,bbc4%2B1,bbc_hd%2B1,cbbc%2B1,cbeebies%2B1,bbc1_n_ireland%2B1&format=XMLTV");
my $response = $ua->request($request, "/tmp/tvdata.zip");

sleep 1;

#Unzip it into the 3 files
if (-e "/tmp/tvdata.zip"){
  my $zip = Archive::Zip->new();
  my $status = $zip->read( '/tmp/tvdata.zip' );
  die "Read of $zipName failed\n" if $status != AZ_OK;
  $zip->extractTree();
  sleep 1;

#Call mythfilldatabase
  print "-Calling mythfilldatabase\n";
  system ('mythfilldatabase --file 2 /tmp/data.xml);
  print "----DONE----\n";
}

```

Regards
Ian Dobson

---

### Post by Caysho on 2009-01-18
I am doing the same thing with with the file option, but as I said, mythfilldatabase is not always honouring the end times.
That's why I'm after a merge facility to avoid this problem.

---

### Post by Caysho on 2009-02-02
Had another look at the files I'm merging.

mythfilldatabase does not update/modify listings if it doesn't find a start/top stime match for the merging timespan.

eg if the original file has 

```

<programme start="20090127193000 +0900" stop="20090128000000 +0900" channel="SevenHD">

```

and the file that has the updates contains
```

<programme start="20090127213000 +0900" stop="20090127223000 +0900" channel="SevenHD">
<programme start="20090127223000 +0900" stop="20090128000000 +0900" channel="SevenHD">

```

then nothing is replaced.

If the starttime of the second file's first item is changed to match the first file's item's starttime, it works.

The command line I am using is:
```

mythfilldatabase --file 1 file.xml

```

I have also done it with the --update option, but it made no difference.

Is this a bug in mythfilldatabase, or is it working as expected ?

---

### Post by Caysho on 2009-07-13
Looking at the [mythfilldatabase page]("http://www.mythtv.org/wiki/Mythfilldatabase#3._Run_mythfilldatabase_with_the_--file_flag"), the offset option was removed; this allowed the functionality I am after.

---

