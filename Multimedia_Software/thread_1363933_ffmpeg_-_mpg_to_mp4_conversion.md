---
title: "ffmpeg - mpg to mp4 conversion"
date: 2009-12-25
forum: Multimedia Software
---

### Post by scorpias on 2009-12-25
If anyone is interest I created a perl script that will convert any mpg files in a directory automatically using ubuntu 8.10 Server


#! /usr/bin/perl -wl
use strict;
use warnings;

my$file;
my $dir = "/media/";
opendir(BIN, $dir) or die "Can't open $dir: $!";
my $newfile;
my $origfile;

while( defined ($file = readdir BIN) ) {
chomp ($file);
 my $filex;
 my @parts = split (/\./,$file);
 $filex = $parts[1];
 pop @parts;
 my $file_no_ext = join '.', @parts;
 
 $newfile = "\"".$dir.$file_no_ext . ".mp4"."\"";
 $origfile = "\"".$dir.$file."\"";
my $runcommand = "ffmpeg -i $origfile -target ntsc-vcd $newfile";

if ($filex eq "mpg")  
{
system($runcommand);

}

}
closedir(BIN);

---

### Post by scorpias on 2009-12-25
use mp4ize instead of just the ffmpeg commands it is so much easier - 

[http://thomer.com/howtos/ipod_video.html](http://thomer.com/howtos/ipod_video.html)

you don't have to figure out any video aspects sizes,

Here is my script to loop through a directory calling mp4ize - 

#! /usr/bin/perl -wl
use strict;
use warnings;

my$file;
my $dir = "/media/";
my $newdir ;
opendir(BIN, $dir) or die "Can't open $dir: $!";
my $newfile;
my $origfile;

while( defined ($file = readdir BIN) ) {
chomp ($file);
 my $filex;
 my @parts = split (/\./,$file);
 $filex = $parts[1];
 pop @parts;
 my $file_no_ext = join '.', @parts;
 
 $newfile = "\"".$dir.$file_no_ext . ".mp4"."\"";
 $origfile = "\"".$dir.$file."\"";
 $newdir = "\"".$dir."mp4ize"."\"";
#my $runcommand = "ffmpeg -i $origfile -target ntsc-vcd $newfile";

my $runcommand = "$newdir $origfile";
print "$runcommand\n";

if ($filex eq "mpg")  
{
system($runcommand);

}

}
closedir(BIN);

---

