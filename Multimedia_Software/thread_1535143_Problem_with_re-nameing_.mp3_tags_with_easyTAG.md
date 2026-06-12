---
title: "Problem with re-nameing .mp3 tags with easyTAG"
date: 2010-07-20
forum: Multimedia Software
---

### Post by Poadrim on 2010-07-20
Hello, i start a new thread since my standing problem is with the tag it self and not Rhythmbox itself.

I have tried now basically 4hours straight to fix this, but it won't go at all. I can change "file name", "Title", "Year" and "Genre" in both easyTAG and the file it self. But it won't change the file with "artist", "track #" and "album" to the file, it shows that the file is altered in easyTAG but the file is not changed.

Made any sense? :confused:

---

### Post by ron999 on 2010-07-20
Hi
I think that EasyTAG is setting one type of ID3 tag and Rhythmbox is reading a different type of ID3 tag.
This problem has been discussed before. Here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1514708]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1514708")

---

### Post by Shompol on 2010-07-20
I wrote a perl script to pull ID3 tag from file name and insert it in the tag. This being perl, you don't need to compile it, just run.

It translates filename artist-name.mp3 to ID3 tag. Feel free to modify to suit your tagging needs.

<code>
#/bin/perl -w
use strict;
use MP3::ID3v1Tag;

my $destpath="G:/music/new";
opendir(INDIR, $destpath) or die("Cannot open directory: $!");
my @listing = readdir(INDIR);
my @mp3list;
foreach (@listing)
{
    push @mp3list, $_ if /\.mp3$/;
}

foreach (@mp3list)
{
    my $newname = $_;
    $newname =~ s/ (\w)/ \U$1/g;
    $newname =~ s/^(\w)/\U$1/g;
    $newname =~ s/ The / the /g;
    $newname =~ s/ A / a /g;

    if ($newname ne $_)
    {
    print "OLD $_  NEW $newname\n";
    #rename old new
    rename "$destpath/$_", "$destpath/$newname";
    }

    my $song = $newname;
    $song =~ s/.mp3$//;

    my $artist = $song;
    $artist =~ s/ *-.*$//;
    $artist =~ s/ +/ /g;

    my $title = $song;
    $title =~ s/^.*?-//;
    $title =~ s/^ *//;
    $title =~ s/ *$//;
    $title =~ s/ +/ /g;
    
    my $mp3_file = new MP3::ID3v1Tag("$destpath/$newname");
    $mp3_file->set_title($title);
    $mp3_file->set_artist($artist);
    $mp3_file->print_tag();
    $mp3_file->save();
}
</code>

---

### Post by Poadrim on 2010-07-22
Thanks for the help guys! Much appreciated! ;)

---

