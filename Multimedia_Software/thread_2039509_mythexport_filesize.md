---
title: "mythexport filesize"
date: 2012-08-09
forum: Multimedia Software
---

### Post by DanBender on 2012-08-09
I'm trying to find the best settings for using mythexport to watch recorded shows on my iPhone. The system works, but I'm noticing a quirk with respect to file sizes...they're the same!

I've modified the [PortableH264HighRes]("http://www.baablogic.net/mythexport/configs/12.04/PortableH264HighRes.pm") configuration to output 640x480 4:3 and 320x240, also 4:3:

640x480:
```
#!/usr/bin/perl 

package H264640x480;

use ExportBase;

our @ISA = qw(ExportBase);

my $description = "Standard Definition (640x480) Portable H264 Settings.";
my $devices = "iPhone";
my $notes = "Requires AAC, <a href=\"https://help.ubuntu.com/community/Medibuntu\">activate Medibuntu</a>";
my $version = "1.0";

sub new{
    my $class = shift;
    my $self = $class->SUPER::new(shift, shift, $description, $devices, $notes, $version);
    bless $self, $class;
    return $self;
}

sub export{
    my( $self ) = @_;

    system("avconv -i \'$self->{_inputFile}\' -y -pass 1 -an -vcodec libx264 -pre:v libx264-medium_firstpass -pre:v libx264-ipod640 -b 1500k -bt 1000k -threads 0 -s 640x480 -aspect 4:3 -f ipod '/dev/null' && avconv -i \'$self->{_inputFile}\' -y -pass 2 -vcodec libx264 -preset medium -pre:v libx264-ipod640 -b 1500k -bt 1000k -threads 0 -s 640x480 -acodec libfaac -ab 192k -ar 48000 -ac 2 -aspect 4:3 -f ipod \'$self->{_outputFile}$self->{_extension}\'")

}

1;
```320x240:
```
#!/usr/bin/perl 

package H264320x240;

use ExportBase;

our @ISA = qw(ExportBase);

my $description = "Low Resolution (320x240) Portable H264 Settings.";
my $devices = "iPhone";
my $notes = "Requires AAC, <a href=\"https://help.ubuntu.com/community/Medibuntu\">activate Medibuntu</a>";
my $version = "1.0";

sub new{
    my $class = shift;
    my $self = $class->SUPER::new(shift, shift, $description, $devices, $notes, $version);
    bless $self, $class;
    return $self;
}

sub export{
    my( $self ) = @_;

    system("avconv -i \'$self->{_inputFile}\' -y -pass 1 -an -vcodec libx264 -pre:v libx264-medium_firstpass -pre:v libx264-ipod320 -b 1500k -bt 1000k -threads 0 -s 320x240 -aspect 4:3 -f ipod '/dev/null' && avconv -i \'$self->{_inputFile}\' -y -pass 2 -vcodec libx264 -preset medium -pre:v libx264-ipod320 -b 1500k -bt 1000k -threads 0 -s 320x240 -acodec libfaac -ab 192k -ar 48000 -ac 2 -aspect 4:3 -f ipod \'$self->{_outputFile}$self->{_extension}\'")

}

1;
```The 320x240 is less clear than the 640x480 output, as one would expect, but it still looks pretty good. The 640x480 actually has some odd artifacts in it that look like bad interlacing during movement.

The thing that's most odd, though is the size of the output files. I exported the exact same recording in using both configurations. For this 30-minute program, the 640x480 file was 366,787 kB. The 320x240 one was...364,483 kB?! That's pretty much the same size! I would have expected the smaller output to be roughly one-third the filesize, having only one-fourth the pixels and all.

Does anything in the codes I posted jump out at anyone as to why the filesizes would be so similar? My first thought is maybe the smaller-resolution file is at a much higher bitrate, since all the options besides the resolution are exactly the same. But there's nothing obvious that matches the bitrate option described in the documentation on [ffmpeg.org]("http://ffmpeg.org/ffmpeg.html"), at least after a very quick look through it. And the PortableH264LowRes configuration supplied appears to be using the same options other than the resolution as well.

Any pointers would be great! I'm also posting this to the mythtvtalk boards, and I'll make sure any response gets there gets parroted here and vice versa.

Thank you in advance!

-Dan

---

