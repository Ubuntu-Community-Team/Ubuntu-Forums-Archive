---
title: "Here is a fancy script to find duplicate videos."
date: 2009-03-29
forum: Multimedia Software
---

### Post by xxsludgexx on 2009-03-29
Let's say you have 3 videos, all of which are the same video content, but one is a .mov, one is a .avi and one is a .wmv? Let's say they are different resolutions and aspect ratios.

A md5/sha compare won't do much good, you could check the movie times/frame rates and do some comparisons, but you know it all gets butchered  when re-encoded. So here's my fancy method that works pretty well.

It requires mplayer, imagemagick, sort, uniq, find, md5sum, grep and perl, and some perl modules.

It basically does this: it grabs the first 1000 (user definable) frames of the movies in question, re-sizes them to 8x8 and converts them to simple black and white images. Not gray scale, but either full black, or full white pixels. This is called a threshold.

[This is the effect. I'm referring to.]("http://www.insidegraphics.com/digital_art/images/photoshop_layers_green.jpg")

What you are left with are a bunch of images that look like little checkerboards. My idea (I don't know how original this idea is but who cares) was this: 

[B]Those checker boards should match up often with another video that has the same content. And videos that are not the same content, shouldn't match up, at least not much.
[/B]

Pseudo-code:
I render out 1000 frames, starting from the 1st frame (you can start later in, but key frames become an issue and can cause time sync to be lost between potentially similar videos). I then delete the first 300 of those frames (I have blank screens and fades in's at the start so I skip a couple seconds in. Similar concept people use when making video thumbnails. Skip a little ways in.) I then convert them to those threshold'd images. I then calculate md5 hashes of these uncompressed bmp images. Two identical bmp files will have the same md5 hash as oppose to two jpegs of various compression levels. I then do some sorting and uniq'n and it tells me how many frames from one video, matched that in another video. I would love for someone to add on to this in some way. Let me know if anyone can make it better. =)

I release this code under the GPLv2.
 

Example Output:
```

sludge@ttzztt:/$ ~/scripts/viddupes3.pl
Cleaning up directories...
Rendering 1000 frame(s), skipping the first 300. (700 end result)
/mnt/Seagate/akira.the.dog.wmv
/mnt/Seagate/akira.the.dog.mp4
/mnt/Seagate/meowser.the.cat.wmv
/mnt/Seagate/meowser.the.cat.avi
Calculating hash table...
Here come the delicious dupes:
/mnt/Seagate/akira.the.dog.wmv.count
        63.14% match with /mnt/Seagate/akira.the.dog.mp4

/mnt/Seagate/meowser.the.cat.wmv.count
        63.29% match with  /mnt/Seagate/meowser.the.cat.avi

```
akira.the.dog.mp4 is about a 200meg mp4 640x480
akira.the.dog.wmv is about 30 megs and is about half that rez.
similar type of thing with the other cat files.

This code could use a bit of cleanup, but I'm a nerd, and wanted to share it somewhere. 
I cowboy code on my weekend projects like this, so don't bad mouth my variable names and indenting too much. =)
CHECK MY CODE COMMENTS BEFORE YOU RUN THIS.

```

#!/usr/bin/perl
use File::Path;

my $ofh = select STDOUT; #Make stdout hot
$| = 1;
select STDOUT;

$getimages = 1000; #render out 1000 images
$deletefirst = 300; #delete the first 300
$totalimages = $getimages - $deletefirst; 
$minmatch = 2; #might use this later (not used now)

$searchdir = "/mnt/Seagate/"; #directory to scan
$basedir = "/tmp/hashchecker/"; #working directory, this directory will get clobbered, make it something uniq in /tmp/

print "Cleaning up directories...\n";
rmtree($basedir); #see, I told you.

print "Rendering $getimages frame(s), skipping the first $deletefirst. ($totalimages end result)\n";

@videofiles=`find "$searchdir" -type f -printf "%p\n" | grep -Ei "\.(mp4|flv|wmv|mov|avi|mpeg|mpg|m4v|mkv|divx|asf)"`;
foreach $i (@videofiles)
{
 chomp $i;
 print "$i";
 @filename = split(/\//,$i);
 $imgdir = $basedir . "/$filename[-1]";
 mkpath($imgdir);
 $data=`cd "$imgdir"; mplayer -really-quiet -vo png -frames $getimages -ao null "$i" 2>&1`;
 @data=`find "$imgdir" -type f -name "*.png" | sort`;
 for ($deletecount=0; $deletecount < $deletefirst; $deletecount++)
 {
   chomp $data[$deletecount];
   unlink $data[$deletecount];
 }
 $data=`mogrify -resize 10x10! -threshold 50% -format bmp "$imgdir/*"`;
 $data=`find "$imgdir" -type f -name "*.png" -delete`;
 print "\n";
}
print "Calculating hash table...\n";
@md5table=`find "$basedir" -type f -name "*.bmp" -exec md5sum "{}" \\; | sort | uniq -D -w32`;
foreach $x (@md5table)
{
 chomp $x;
 $x =~ m/^([0-9a-f]{32})/i;
 $md5=$1;
 $x =~ m/^[0-9a-f]{32}[ \t]*(.*)/i;
 $fullpath=$1;
 @filename = split(/\//,$x);
 open (MYFILE, ">>$basedir/$md5.md5") or die "couldnt open file\n";
 print MYFILE "$fullpath\n";
 close (MYFILE);
}

@hashfiles=`find "$basedir" -type f -name "*.md5"`;
foreach $i (@hashfiles)
{
 chomp $i;
 @uniqfiles=`sort "$i" | uniq`;
 $uniqsize=@uniqfiles;
 if ($uniqsize > 1)
 {
   $firstpass = 1;
   foreach $x (@uniqfiles)
   {
     chomp $x;
     @filename=split(/\//,$x);
     if ($firstpass == 1)
     {
       $outfile=$filename[-2];
       $firstpass=0;
     }
     else
     {
       if ($outfile ne $filename[-2])
       {
         open (COUNTFILE, ">>$basedir/$outfile.count") or die "$outfile -> couldnt open file\n";
         print COUNTFILE "$filename[-2]\n";
         close (COUNTFILE);
       }
     }
   }

 }
}
print "Here come the delicious dupes:\n";
@hashfiles=`find "$basedir" -type f -name "*.count"`;
foreach $i (@hashfiles)
{
 chomp $i;
 print "$i\n";
 @uniqfiles=`sort "$i" | uniq -c`;
 foreach $x (@uniqfiles)
 {
    chomp $x;
    $x =~ m/^[ \t]*([0-9]{1,50})/i;
    $percent = $1/$totalimages*100;
    $x =~ m/^[ \t]*[0-9]{1,50}(.*)/i;
    $filename=$1;
    printf "\t%.2f% match with %s\n",$percent,$filename;
 }
 print "\n";

}
exit;


```
Now that it works, I now have the task of coding it better and cleaner, and use less unix utils.
:guitar:

Here's a bash version I wrote kind of as psuedo-code. It works too.
```

#!/bin/bash
IFS=$'\n'

rm -rf ./Thumbs/

rm -rf ./Hashes/
mkdir ./Hashes/

rm -rf ./Counts/
mkdir ./Counts/

echo -n "Rendering movies to bitmaps..."
for i in $( find . -type f )
do
 echo -n "."
 mplayer -really-quiet -vo png -frames 1000 -ao null "$i" &> /dev/null
 mkdir -p "./Thumbs/$i/"
 mv *.png "./Thumbs/$i/"
 mogrify -resize 10x10! -threshold 50% -format bmp "./Thumbs/$i/*"
 find ./Thumbs/$i/ -type f -name "*.png" -delete
done
echo " Done"

for i in $( find ./Thumbs/ -type f -name "*.bmp"); do md5sum "$i"; done | sort | uniq -D -w32 > /tmp/info.txt

echo -n "Generating comparative hash table..."
for i in $( cat /tmp/info.txt )
do
 md5=`echo $i | grep -Eio "^[a-f0-9]{32}"`
 curdir=`echo $i | awk -F"/" '{print $3}'`
 echo "$curdir" >> "./Hashes/$md5"
done
echo " Done"

echo -n "Finding what might be dupes..."
for i in $( find ./Hashes/ -type f )
do
 uniqcount=`uniq "$i" | wc -l`
 if [ $uniqcount -gt 1 ]
 then
   firstrun=1
   for x in $( uniq "$i" )
   do
    if [ $firstrun -eq 1 ]
    then
      firstfile="$x"
      firstrun=0
    else
      echo "$x" >> "./Counts/$firstfile"
    fi
   done
 fi
done
echo " Done."

echo "-----------------------------"
echo "Here they are:"
echo -e "-----------------------------\n"
for i in $( find ./Counts/ -type f)
do
 echo -en "\n"
 echo "$i:" | sed "s/^.\/Counts\///g"

 for x in $( uniq -c "$i" | sed "s/^[ \t]*//g" | grep -Ei "^[0-9]{1,4}" )
 do
   percent=`echo "$x" | sed "s/^[ \t]*//g" | grep -Eio "^[0-9]{1,4}"`
   percentf=`echo "scale=4; $percent/1000*100" | bc -l | sed "s/00$/%/g"`
   echo "$x" | sed -r "s/^([0-9]{1,3})/$percentf match with:\t/g;s/^/\t/g"
 done
done
echo -en "\n\n"

```

Yet another improved, and faster version with hash tables

```

#!/usr/bin/perl
use File::Path;
use File::Basename;
use Term::ANSIColor;
use File::Temp qw/ tempdir /;
use Getopt::Long;
GetOptions('path=s' => \$searchdir);
die "No path defined" unless defined $searchdir;

my $ofh = select STDOUT; $| = 1; select STDOUT;
$renderfirst = 2000;
$basedir = tempdir ( DIR => "/tmp/" );

sub banner { print colored ['red'],"--------> "; print color 'green'; printf '%-50s',@_; print colored ['red']," <--------"; print color 'reset'; print "\n";}

banner "Running Vid Dupes on $searchdir";

############################################
# Rendering video to small images time     #
############################################
banner "Rendering video...";
@videofiles=`find "$searchdir" -type f -printf "%p\n" | grep -Ei "\.(mp4|flv|wmv|mov|avi|mpeg|mpg|m4v|mkv|divx|asf)"`;
$numfiles = @videofiles;
$count = 1;
foreach $i (@videofiles)
{
  chomp $i;
  $dir = dirname($i);
  $file = basename($i);
  print color 'cyan';
  printf "%4s of %-4s",$count,$numfiles;
  print "\t$i\n"; $count += 1; print color 'reset';
  $imgdir = $basedir . $dir . "/" . $file;
  mkpath($imgdir);
  $data=`ffmpeg -i "$i" -s "24x24" -vframes $renderfirst -f image2 "$imgdir/image%05d.bmp" 2>&1`;
  $data=`mogrify -threshold 30% "$imgdir/*"`;
}

###########################
# Md5 calc'n time         #
###########################

banner "Calculating md5 hashes...";
@md5table=`find "$basedir" -type f -name "*.bmp" -exec md5sum "{}" \\; | sort | uniq -D -w32`;
foreach $x (@md5table)
{
  chomp $x;  $x =~ m/^([0-9a-f]{32})/i;  $md5=$1;
  $x =~ m/^[0-9a-f]{32}[ \t]*(.*)\/image.*bmp/i;  $fullpath=$1;  @filename = split(/\//,$x);
  open (MYFILE, ">>$basedir/$md5.md5") or die "couldnt open file\n";
  print MYFILE "$fullpath\n";
  close (MYFILE);
}

###################################
# Hash sorting time               #
###################################

banner "Sorting through the hashes...";

@hashfiles=`find "$basedir" -type f -name "*.md5"`;

foreach $i (@hashfiles)
{
  chomp $i;
  @uniqfiles=`sort "$i" | uniq -c | sed "s/^[\t ]*//g"`;
  $uniqsize=@uniqfiles;
  if ($uniqsize > 1)
  {
    $firstfilenamefound=0;
    foreach $x (@uniqfiles)
    {
       chomp $x; $x =~ m/^([0-9]{1,10})[ \t]{1,2}(.*)/i; $count = $1; $filename=$2;
       if ($firstfilenamefound == 0) { $filename =~ s/$basedir/\//g; $output = $filename; $firstfilenamefound=1; }
       else
       {
          $filename =~ s/$basedir/\//g;
          if (!defined $hasharray{"$output\n\t$filename"} ) { $hasharray{"$output\n\t$filename"}  = 0 };
          $hasharray{"$output\n\t$filename"}  += $count;
       }
    }
  }
}

############################
# Outputing dupes time     #
############################
banner "Report of dupes";
print "\n";
while (($key,$value) = each %hasharray) {
   $newvalue = ($value * 100.0) / $renderfirst;
   printf("%.1f\%\t%s\n\n",$newvalue,$key);
}

banner "Cleaning up...";
rmtree($basedir);

exit;

```
I had some significant flaws in logic in the previous versions. This one is aces.

```

#!/usr/bin/perl
use File::Path;
use File::Basename;
use Digest::MD5  qw(md5 md5_hex md5_base64);
use Term::ANSIColor;
use File::Temp qw/ tempdir /;
use Getopt::Long;
use File::Find;

GetOptions('path=s' => \$searchdir,'report=s' => \$report);
die "No path defined" unless defined $searchdir;
my $ofh = select STDOUT; $| = 1; select STDOUT;

$renderfirst = 2500;
$threshold = 5;

$basedir = tempdir ( DIR => "/mnt/RAID/tmp/" );

sub banner { print colored ['red'],"--------> "; print color 'green'; printf '%-96s',@_; print colored ['red']," <--------"; print color 'reset'; print "\n";}
sub wanted {
  if ((-f $File::Find::name) && ($File::Find::name =~ m/\.bmp$/i))
  {
    $filename = $File::Find::name; $filename =~ s/^$basedir//g; $filename =~ s/^$searchdir//g; $filename =~ s/\/image.*bmp$//g;
    open(FILE, $File::Find::name); binmode(FILE); $md5 = Digest::MD5->new->addfile(*FILE)->hexdigest; close(FILE);
    open (MYFILE, ">>$basedir/$md5.md5") or die "couldnt open file\n"; print MYFILE "$filename\n"; close (MYFILE);
    unlink($filename);
  }
}

################################################
# Rendering video, thresholding, and hashing   #
################################################
banner "Rendering video from $searchdir -> $basedir";

@videofiles=`find "$searchdir" -type f -printf "%p\n" | grep -Ei "\.(mp4|flv|wmv|mov|avi|mpeg|mpg|m4v|mkv|divx|asf)"`;
$numfiles = @videofiles; $count = 1; chomp(@videofiles);
foreach $i (@videofiles)
{
  $dir = dirname($i); $file = basename($i);
  print color 'cyan'; printf "%4s of %-6s",$count,$numfiles; print "$i\t"; $count++; print color 'reset';
  $imgdir = $basedir . $dir . "/" . $file; mkpath($imgdir);
  $data=`ffmpeg -i "$i" -s "64x64" -vframes $renderfirst -f image2 "$imgdir/imageA%05d.bmp" 2>&1`; print ".";
  $data=`mogrify -resize 8x8! -threshold 25% "$imgdir/*"`; print ".";
  find(\&wanted, $imgdir); print "."; rmtree($imgdir); print " Done\n";
}

###################################
# Hash sorting time               #
###################################

banner "Sorting through the hashes...";

@hashfiles=`find "$basedir" -maxdepth 1 -type f -iname "*.md5"`; chomp(@hashfiles);
foreach $i (@hashfiles)
{
  @uniqfiles=`sort "$i" | uniq -c | sed "s/^[\t ]*//g"`; chomp(@uniqfiles); $uniqsize=@uniqfiles;
  if ($uniqsize > 1)
  {
    #print "$uniqsize File(s) in array:\n";
    for ($skip = 0; $skip < $uniqsize; $skip++)
    {
      $uniqfiles[$skip] =~ m/^([0-9]{1,10})[ \t]{1,2}(.*)/i; $outputcount=$1; $output=$2; #print "\t $skip -> $output\n";
      for ($lcv = $skip; $lcv < $uniqsize; $lcv++)
      {
         $uniqfiles[$lcv] =~ m/^([0-9]{1,10})[ \t]{1,2}(.*)/i; $count = $1; $filename=$2;
         if ($lcv != $skip)
         {
            if ($count >= $outputcount) { $newcount = $outputcount } else { $newcount = $count }
            #print "\t\t+$outputcount +$count = $newcount\t$filename\t";
            if ($output gt $filename)
            {
              #print "gt\n";
              if (!defined $hasharray{"$output|$filename"} )   { $hasharray{"$output|$filename"} = 0 }
              if (defined $hasharray{"$output|$filename"} )   { $hasharray{"$output|$filename"} += $newcount }
            }
            if ($output lt $filename)
            {
              #print "lt\n";
              if (!defined $hasharray{"$filename|$output"} )   { $hasharray{"$filename|$output"} = 0 }
              if (defined $hasharray{"$filename|$output"} )   { $hasharray{"$filename|$output"} += $newcount }
            }
         }
      }
    }
  }
}
rmtree($basedir);

############################
# Outputing dupes time     #
############################
banner "Report of dupes in $searchdir"; print "\n";

sub by_value { $hasharray{$a} <=> $hasharray{$b}; }
if (defined $report) { open (REPORTFILE, ">",$report) or die "couldnt open file\n"; }
foreach $key (sort by_value keys %hasharray) {
   $value = $hasharray{$key};
   $newvalue = ($value * 100.0) / $renderfirst;
   if ($newvalue >= $threshold)
   {
      $keyout = $key; $keyout =~ s/\|/\n\t/g;
      printf("%.1f\%\t%s\n\n",$newvalue,$keyout);
      if (defined $report) { printf REPORTFILE "%.1f\%\t%s\n",$newvalue,$keyout; }
   }

}
if (defined $report) { close (REPORTFILE); }

exit;

```

---

### Post by spoonefl1 on 2011-07-19
I just started trying this, but I get an error:

No path defined at viddupes.pl line 11.

Where do I set the path? In the script, I think it is $searchdir, but should I just add a line with that in it? I tried just putting a path on the command line when I launched the script, but that failed the same way.

I'm using the version from the bottom of your post, and perl version 5.10.1, if that helps.

Sorry if this was a stupid question, but I'm not too familiar with scripting in general.

---

