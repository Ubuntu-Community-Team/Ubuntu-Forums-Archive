---
title: "how to batch convert with ffmpeg?"
date: 2008-07-23
forum: Multimedia Software
---

### Post by logos34 on 2008-07-23
So I want to convert all the .m4a (apple lossless .alac) files in a folder to .wav.  How?

ffmpeg -i *.m4a ?

---

### Post by Creative2 on 2008-07-23
save this lik m4a2wav.sh then you have to give it executable permission
and the execute in a terminal ./ m4a2wav.sh

for f in *.m4a; do mplayer -ao pcm:file="${f%.m4a}.wav"  "$f"; done

or you could install fuoco tools it manage m4a to mp3 or what you want..

---

### Post by logos34 on 2008-07-23
cool, it works.  Thanks. Just had to 

sudo chmod +x 

the file first.

But I get this message (in red) for every track:
> 
user@ubuntu:~/09 Penderecki _ Orchestewerke _.m4a$ ~/./m4a2wav-mplayer.sh
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 2600+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
[COLOR=Red]mplayer: could not connect to socket
mplayer: No such file or directory[/COLOR]
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team

But it doesn't seem effect anything.

I also changed it slightly and it works with ffmpeg too:
> 
for f in *.m4a; do **ffmpeg -i "$f" **"${f%.m4a}.wav"; done

> user@ubuntu:~/03 Messiaen _ Quatuor pour la Fin d$ ~/./m4a2wav-ffmpeg.sh
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 17 2008 19:38:35, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[COLOR=DarkRed]Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '01 Quatuor pour la fin du Temps_ 1..m4a':
  Duration: 00:03:04.7, start: 0.000000, bitrate: 607 kb/s
  Stream #0.0(und): Audio: alac, 44100 Hz, stereo[/COLOR]
[COLOR=Blue]Output #0, wav, to '01 Quatuor pour la fin du Temps_ 1..wav':
  Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, 1411 kb/s[/COLOR]
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=   31823kB time=184.7 bitrate=1411.2kbits/s    
video:0kB audio:31823kB global headers:0kB muxing overhead 0.000135%


---

### Post by Creative2 on 2008-07-25
well you can convert or not?
if not :
medibuntu repository are up or not?
no?
add medibuntu repository 
yes?
i don't know 
done

xD

---

### Post by logos34 on 2008-07-25
yeah, your script converts with both mplayer and ffmeg, I was just wondering why the error message with mplayer.

---

### Post by Creative2 on 2008-07-26
i really dunno , well if your files are ok why are you  worrying :D ?

(well if i was you probably i would ask to myself the same question.. )

---

### Post by hesapotman on 2010-03-12
Well ... I had some problems with that also. I tried "Sound Converter", and it was STILL "Adding Files" after 3 hours (because I have 10,000+ music files). Totally unacceptable. So my solution was to write a Perl script. It's not the best or prettiest code in the world, but it does the job and is extensible for various audio transcoding tasks.

```

#!/usr/bin/perl

my($indir, $outdir, $informat, $overyn,
   $outformat, $codec, $bitrate,
   $channels, $sample, $overwrite) =
  (0, 0, 0, 0, 0, 0, 0, 0, 0, 0);
  
my @lines = `/usr/bin/ffmpeg -formats e`;
system "clear";
shift(@lines);
my (@wrappers, @codecs, @dec_wraps, @enc_wraps, @dec_codecs, @enc_codecs);
while($lines[0] !~ m/^codecs:/i)
{
    push(@wrappers, shift(@lines));
}
pop(@wrappers);
shift(@lines);
while((length($lines[0])) > 5)
{
    push(@codecs, shift(@lines));
}
undef(@lines);
foreach my $wrapper (@wrappers)
{
    if($wrapper =~ m/^(.{4}).{1,}$/)
    {
        my $modes = $1;
        $wrapper =~ s/^.{4}//;
        $wrapper =~ m/^(\S{1,})\s/;
        my $details = $1;
        my @detail_arr = split(/,/, $details);
        foreach my $single (@detail_arr)
        {
            if($modes =~ m/^.D/i)
            {
                push(@dec_wraps, $single);
            }
            if($modes =~ m/^..E/i)
            {
                push(@enc_wraps, $single);
            }
        }
    }
}
foreach my $codx (@codecs)
{
    if($codx =~ m/^(.{8}).{1,}$/)
    {
        my $modes = $1;
        $codx =~ s/^.{8}//;
        $codx =~ m/^(\S{1,})\s/;
        my $details = $1;
        my @detail_arr = split(/,/, $details);
        foreach my $single (@detail_arr)
        {
            if($modes =~ m/^.D/i)
            {
                push(@dec_codecs, $single);
            }
            if($modes =~ m/^..E/i)
            {
                push(@enc_codecs, $single);
            }
        }
    }
}

while(! $indir)
{
	print "Enter Source Directory (e.g. '/home/user/music')\n> ";
	chomp($indir = <STDIN>);
	$indir =~ s/\\/\//g;
	$indir =~ s/\/{1,}$//;
	if((!-e $indir) || (!-r $indir))
	{
		print "\nERROR: The Source Directory does not exist or cannot be read.\n\n";
		$indir = 0;
	}
}

while(! $outdir)
{
	print "\nEnter Destination Directory (e.g. '/home/user/converted')\n> ";
	chomp($outdir = <STDIN>);
	$outdir =~ s/\\/\//g;
	$outdir =~ s/\/{1,}$//;
	if((!-e $outdir) || (!-w $outdir))
	{
		print "ERROR: The Destination Directory does not exist or is read-only.\n";
		$outdir = 0;
	}
}

while(! $informat)
{
	print "\nEnter the Input Media Wrapper (e.g. " . join(', ', @dec_wraps) . ")\n> ";
	chomp($informat = <STDIN>);
	$informat =~ s/\.//g;
	$informat = lc($informat);
	my $found = 0;
	foreach(@dec_wraps)
	{
		if($_ eq $informat)
		{
			$found = 1;
		}
	}
	if(! $found)
	{
		print "ERROR: Your 'ffmpeg' cannot process this Input Media Wrapper.\n";
		$informat = 0;
	}
}

while(! $outformat)
{
	print "\nEnter the Output Media Wrapper (e.g. " . join(', ', @enc_wraps) . ")\n> ";
	chomp($outformat = <STDIN>);
	$outformat =~ s/\.//g;
	$outformat = lc($outformat);
	my $found = 0;
	foreach(@enc_wraps)
	{
		if($_ eq $outformat)
		{
			$found = 1;
		}
	}
	if(! $found)
	{
		print "ERROR: Your 'ffmpeg' cannot process this Output Media Wrapper.\n";
		$outformat = 0;
	}
}

while(! $codec)
{
	print "\nEnter the Output Media Codec (e.g. " . join(', ', @enc_codecs) . ")\n> ";
	chomp($codec = <STDIN>);
	$codec = lc($codec);
	my $found = 0;
	foreach(@enc_codecs)
	{
		if($_ eq $codec)
		{
			$found = 1;
		}
	}
	if(! $found)
	{
		print "ERROR: Your 'ffmpeg' cannot process this Output Media Codec.\n";
		$codec = 0;
	}
}

while(! $channels)
{
	print "\nEnter the Output Media Channels [1-5] (e.g. '1', '2', etc.)\n> ";
	chomp($channels = <STDIN>);
	$channels =~ s/\D//g;
	if(($channels < 1) || ($channels > 5))
	{
		print "ERROR: This Output Media Channels entry appears to be invalid.\n";
		$channels = 0;
	}
}

while(! $bitrate)
{
	print "\nEnter the Output Media Bitrate [kbps] (e.g. '128kb', '320kb', '1411kb', etc.)\n> ";
	chomp($bitrate = <STDIN>);
	$bitrate =~ s/\D//g;
	if(($bitrate <= 0) || ($bitrate > 1411))
	{
		print "ERROR: This Output Media Bitrate appears to be invalid.\n";
		$bitrate = 0;
	}
	else
	{
		$bitrate .= 'kb';
	}
}

while(! $sample)
{
	print "\nEnter the Output Media Sampling Rate (e.g. '8000', '22050', '44100', etc.)\n> ";
	chomp($sample = <STDIN>);
	$sample =~ s/\D//g;
	if(($sample < 8000) || ($sample > 96000))
	{
		print "ERROR: This Output Media Sampling Rate appears to be invalid.\n";
		$sample = 0;
	}
}

while(! $overwrite)
{
	print "\nOverwrite files if they exist [be careful] (y/n)?\n> ";
	chomp($overyn = <STDIN>);
	if($overyn !~ m/^(y|n)/i)
	{
		$overwrite = 0;
	}
	else
	{
		if($overyn =~ m/^y/i)
		{
			$overyn = '-y';
		}
		else
		{
			$overyn = '';
		}
		$overwrite = 1;
	}
}
$overwrite = $overyn;

opendir(DIN, $indir);
my $dirroot = $indir;
my @diritr;
my @dirlist;
my @filelist;
push(@diritr, $dirroot);
while(@diritr)
{
    my $curdir = shift(@diritr);
    push(@dirlist, $curdir);
    opendir(DIN, $curdir);
    while(my $dirline = readdir(DIN))
    {
        if(($dirline !~ m/^\./) && (!-l ($curdir . '/' . $dirline)) && (-d ($curdir . '/' . $dirline)))
        {
            push(@diritr, ($curdir . '/' . $dirline));
        }
    }
    closedir(DIN);
}
@dirlist = sort {lc($a) cmp lc($b)} (@dirlist);
foreach(@dirlist)
{
    my $curdir = $_;
    opendir(DIN, $curdir);
    while(my $dirline = readdir(DIN))
    {
        if(($dirline !~ m/^\./) && (!-l ($curdir . '/' . $dirline)) && (!-d ($curdir . '/' . $dirline)) && ($dirline =~ m/\.$informat$/i))
        {
            push(@filelist, ($curdir . '/' . $dirline));
        }
    }
    closedir(DIN);
}
@filelist = sort {lc($a) cmp lc($b)} (@filelist);
for(my $index = 0; $index < scalar(@filelist); $index += 1)
{
    my $filein = $filelist[$index];
    if($filein =~ m/\.$informat/i)
    {
        $filein =~ m/\/([^\/]{1,})$/;
        my $fileout = $1;
        $fileout =~ s/$informat$/$outformat/i;
        system "ffmpeg $overwrite -er 4 -ec 1 -i \"$filein\" -vn -acodec $codec -ab $bitrate -ac $channels -ar $sample -map_meta_data \"$outdir/$fileout\":\"$filein\" \"$outdir/$fileout\"";
    }
}

exit;

```

Just paste that into a *.pl file, make it executable, and go! Now I'm sure some people who like to overanalyze code noticed the line:

```
for(my $index = 0; $index < scalar(@filelist); $index += 1)
```

and said, "Why not just use a "foreach"? The answer is that, in my own usage, I like to manipulate the array iteration a bit (to run two instances of the program on the same folder ... each iterator is offset from each other by one, each iterator increments by 2 ... doubling the conversion speed).

Anyway, hope that helps. =)

---

### Post by bobbiescap on 2010-05-08
Hey potman,

Sorry but I know nothing about programming and would like to know if your script would be suitable to perform batch video conversions also, as I have a lot of HDTV recordings that need to be converted to various formats so that I can share the files and it is painful doing them one by one.

Would it be possible to either modify the script to do this or to let me know what I should change to achieve it.

Kind regards

---

### Post by rpkopreski on 2010-06-29
hesapotman,

really great pearl-script thanks!  Now if I could just get it to work on a remote file over a secured network connection!

---

### Post by hesapotman on 2010-10-17
> **bobbiescap said:**
> Hey potman,

Sorry but I know nothing about programming and would like to know if your script would be suitable to perform batch video conversions also, as I have a lot of HDTV recordings that need to be converted to various formats so that I can share the files and it is painful doing them one by one.

Would it be possible to either modify the script to do this or to let me know what I should change to achieve it.

Kind regards

I don't use ffmpeg from the command line for video conversions ... too many confusing options that intimidate me. But I'm SURE that with some tweaking, a script like the one I shared could be used to batch convert video. You'll need to find an ffmpeg guru to help you with the many, many video options though.

---

### Post by hesapotman on 2010-11-17
> **rpkopreski said:**
> hesapotman,

really great pearl-script thanks!  Now if I could just get it to work on a remote file over a secured network connection!

Well, Perl does offer some wonderful modules like WWW::Mechanize, LWP, and Net::FTP for network communications and file exchange. But that script would be significantly more complex.

At least now you know 3 good modules to look into if you would like to take on the task yourself!

---

### Post by uaPtah on 2011-05-20
Simply install WinFF by using Syneptic package manager.
WinFF is a nice and easy GUI for ffmpeg.

---

### Post by shantiq on 2011-05-20
also command line easy to handle [here]("http://ubuntuforums.org/showthread.php?t=1609760")

---

### Post by fmoratti on 2011-06-05
> **hesapotman said:**
> Well ... I had some problems with that also. I tried "Sound Converter", and it was STILL "Adding Files" after 3 hours (because I have 10,000+ music files). Totally unacceptable. So my solution was to write a Perl script. It's not the best or prettiest code in the world, but it does the job and is extensible for various audio transcoding tasks.

```

#!/usr/bin/perl

my($indir, $outdir, $informat, $overyn,
   $outformat, $codec, $bitrate,
   $channels, $sample, $overwrite) =
  (0, 0, 0, 0, 0, 0, 0, 0, 0, 0);
  
my @lines = `/usr/bin/ffmpeg -formats e`;
system "clear";
shift(@lines);
my (@wrappers, @codecs, @dec_wraps, @enc_wraps, @dec_codecs, @enc_codecs);
while($lines[0] !~ m/^codecs:/i)
{
    push(@wrappers, shift(@lines));
}
pop(@wrappers);
shift(@lines);
while((length($lines[0])) > 5)
{
    push(@codecs, shift(@lines));
}
undef(@lines);
foreach my $wrapper (@wrappers)
{
    if($wrapper =~ m/^(.{4}).{1,}$/)
    {
        my $modes = $1;
        $wrapper =~ s/^.{4}//;
        $wrapper =~ m/^(\S{1,})\s/;
        my $details = $1;
        my @detail_arr = split(/,/, $details);
        foreach my $single (@detail_arr)
        {
            if($modes =~ m/^.D/i)
            {
                push(@dec_wraps, $single);
            }
            if($modes =~ m/^..E/i)
            {
                push(@enc_wraps, $single);
            }
        }
    }
}
foreach my $codx (@codecs)
{
    if($codx =~ m/^(.{8}).{1,}$/)
    {
        my $modes = $1;
        $codx =~ s/^.{8}//;
        $codx =~ m/^(\S{1,})\s/;
        my $details = $1;
        my @detail_arr = split(/,/, $details);
        foreach my $single (@detail_arr)
        {
            if($modes =~ m/^.D/i)
            {
                push(@dec_codecs, $single);
            }
            if($modes =~ m/^..E/i)
            {
                push(@enc_codecs, $single);
            }
        }
    }
}

while(! $indir)
{
    print "Enter Source Directory (e.g. '/home/user/music')\n> ";
    chomp($indir = <STDIN>);
    $indir =~ s/\\/\//g;
    $indir =~ s/\/{1,}$//;
    if((!-e $indir) || (!-r $indir))
    {
        print "\nERROR: The Source Directory does not exist or cannot be read.\n\n";
        $indir = 0;
    }
}

while(! $outdir)
{
    print "\nEnter Destination Directory (e.g. '/home/user/converted')\n> ";
    chomp($outdir = <STDIN>);
    $outdir =~ s/\\/\//g;
    $outdir =~ s/\/{1,}$//;
    if((!-e $outdir) || (!-w $outdir))
    {
        print "ERROR: The Destination Directory does not exist or is read-only.\n";
        $outdir = 0;
    }
}

while(! $informat)
{
    print "\nEnter the Input Media Wrapper (e.g. " . join(', ', @dec_wraps) . ")\n> ";
    chomp($informat = <STDIN>);
    $informat =~ s/\.//g;
    $informat = lc($informat);
    my $found = 0;
    foreach(@dec_wraps)
    {
        if($_ eq $informat)
        {
            $found = 1;
        }
    }
    if(! $found)
    {
        print "ERROR: Your 'ffmpeg' cannot process this Input Media Wrapper.\n";
        $informat = 0;
    }
}

while(! $outformat)
{
    print "\nEnter the Output Media Wrapper (e.g. " . join(', ', @enc_wraps) . ")\n> ";
    chomp($outformat = <STDIN>);
    $outformat =~ s/\.//g;
    $outformat = lc($outformat);
    my $found = 0;
    foreach(@enc_wraps)
    {
        if($_ eq $outformat)
        {
            $found = 1;
        }
    }
    if(! $found)
    {
        print "ERROR: Your 'ffmpeg' cannot process this Output Media Wrapper.\n";
        $outformat = 0;
    }
}

while(! $codec)
{
    print "\nEnter the Output Media Codec (e.g. " . join(', ', @enc_codecs) . ")\n> ";
    chomp($codec = <STDIN>);
    $codec = lc($codec);
    my $found = 0;
    foreach(@enc_codecs)
    {
        if($_ eq $codec)
        {
            $found = 1;
        }
    }
    if(! $found)
    {
        print "ERROR: Your 'ffmpeg' cannot process this Output Media Codec.\n";
        $codec = 0;
    }
}

while(! $channels)
{
    print "\nEnter the Output Media Channels [1-5] (e.g. '1', '2', etc.)\n> ";
    chomp($channels = <STDIN>);
    $channels =~ s/\D//g;
    if(($channels < 1) || ($channels > 5))
    {
        print "ERROR: This Output Media Channels entry appears to be invalid.\n";
        $channels = 0;
    }
}

while(! $bitrate)
{
    print "\nEnter the Output Media Bitrate [kbps] (e.g. '128kb', '320kb', '1411kb', etc.)\n> ";
    chomp($bitrate = <STDIN>);
    $bitrate =~ s/\D//g;
    if(($bitrate <= 0) || ($bitrate > 1411))
    {
        print "ERROR: This Output Media Bitrate appears to be invalid.\n";
        $bitrate = 0;
    }
    else
    {
        $bitrate .= 'kb';
    }
}

while(! $sample)
{
    print "\nEnter the Output Media Sampling Rate (e.g. '8000', '22050', '44100', etc.)\n> ";
    chomp($sample = <STDIN>);
    $sample =~ s/\D//g;
    if(($sample < 8000) || ($sample > 96000))
    {
        print "ERROR: This Output Media Sampling Rate appears to be invalid.\n";
        $sample = 0;
    }
}

while(! $overwrite)
{
    print "\nOverwrite files if they exist [be careful] (y/n)?\n> ";
    chomp($overyn = <STDIN>);
    if($overyn !~ m/^(y|n)/i)
    {
        $overwrite = 0;
    }
    else
    {
        if($overyn =~ m/^y/i)
        {
            $overyn = '-y';
        }
        else
        {
            $overyn = '';
        }
        $overwrite = 1;
    }
}
$overwrite = $overyn;

opendir(DIN, $indir);
my $dirroot = $indir;
my @diritr;
my @dirlist;
my @filelist;
push(@diritr, $dirroot);
while(@diritr)
{
    my $curdir = shift(@diritr);
    push(@dirlist, $curdir);
    opendir(DIN, $curdir);
    while(my $dirline = readdir(DIN))
    {
        if(($dirline !~ m/^\./) && (!-l ($curdir . '/' . $dirline)) && (-d ($curdir . '/' . $dirline)))
        {
            push(@diritr, ($curdir . '/' . $dirline));
        }
    }
    closedir(DIN);
}
@dirlist = sort {lc($a) cmp lc($b)} (@dirlist);
foreach(@dirlist)
{
    my $curdir = $_;
    opendir(DIN, $curdir);
    while(my $dirline = readdir(DIN))
    {
        if(($dirline !~ m/^\./) && (!-l ($curdir . '/' . $dirline)) && (!-d ($curdir . '/' . $dirline)) && ($dirline =~ m/\.$informat$/i))
        {
            push(@filelist, ($curdir . '/' . $dirline));
        }
    }
    closedir(DIN);
}
@filelist = sort {lc($a) cmp lc($b)} (@filelist);
for(my $index = 0; $index < scalar(@filelist); $index += 1)
{
    my $filein = $filelist[$index];
    if($filein =~ m/\.$informat/i)
    {
        $filein =~ m/\/([^\/]{1,})$/;
        my $fileout = $1;
        $fileout =~ s/$informat$/$outformat/i;
        system "ffmpeg $overwrite -er 4 -ec 1 -i \"$filein\" -vn -acodec $codec -ab $bitrate -ac $channels -ar $sample -map_meta_data \"$outdir/$fileout\":\"$filein\" \"$outdir/$fileout\"";
    }
}

exit;

```Just paste that into a *.pl file, make it executable, and go! Now I'm sure some people who like to overanalyze code noticed the line:

```
for(my $index = 0; $index < scalar(@filelist); $index += 1)
```and said, "Why not just use a "foreach"? The answer is that, in my own usage, I like to manipulate the array iteration a bit (to run two instances of the program on the same folder ... each iterator is offset from each other by one, each iterator increments by 2 ... doubling the conversion speed).

Anyway, hope that helps. =)

If anyone needs some extra feature of this useful script, i've added auto subfolder creation.

If you have music stored in /home/user/music/album_X  after the patch, music goes to /home/user/converted/album_X and so far.

I've done because original script put music without sub folders :-(

You can use attached script.


;)   >> IMPORTANT <<
Please, pay attention! I've used "$list[4]" because 4 is my folders deep  (/home/shark/Musica/My_Album), you have to adjust it accordly your folders deep!
:D

Anyway, thanks a lot!

Daniele

---

### Post by tonyzilla on 2011-07-18
perl one-liner to convert all the files in the current directory to mpg:

```
perl -e 'my @files=`ls`; foreach (@files){ print chomp($_); `ffmpeg -i "$_" "$_.mpg"`}'
```

---

