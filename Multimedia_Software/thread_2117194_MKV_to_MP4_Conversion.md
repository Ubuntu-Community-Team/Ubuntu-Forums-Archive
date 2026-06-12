---
title: "MKV to MP4 Conversion"
date: 2013-02-17
forum: Multimedia Software
---

### Post by gachnar on 2013-02-17
I'm working on converting some anime from MKV to MP4. I can get the videos converted, but I would like to keep the stylized subs as presented in the original video. I don't want to run it through handbrake as I would like to find a way to automate the whole process via scripting. Can anyone provide a way perhaps using FFMPEG to do this?

---

### Post by papibe on 2013-02-17
Hi gachnar.

Here are a few pointers to get you started:
[LIST]
[*]Main idea: do not convert. Most of the time you can get away by extracting the MKV tracks, and repackaging in a MP4 container.
[*]Install ffmpeg with the extra codecs as described [here]("https://help.ubuntu.com/community/FFmpeg").
[*]Install mkvtoolnix:
```
sudo apt-get-install mkvtoolnix
```
[*]Use mkvinfo to know the tracks numbers and type.
[*]Extracts the actual tracks using mkvextract.
[*]You can repack the tracks using ffmpeg itself, but I would recommend installing gpac:
```
sudo apt-get install gpac
```
and do the packing using MP4Box.
[/LIST]

Hope it helps. Let us know how it goes.
Regards.

---

### Post by evilsoup on 2013-02-18
Subtitle support in MP4 is limited, you either have to use bitmap-based VOBSUB (not really an option here), or 3gpp times text (supported in ffmpeg as -c:s mov_text). For soft subtitles, you would have to use (assuming the video is h.264 & the audio is AAC, which most MKVs are; if the video or audio isn't compatible with MP4, ffmpeg will throw out an error & stop):

```

ffmpeg -i input.mkv -c copy -c:s mov_text output.mp4

```

...however, that will not preserve any fancy formatting. If you want that in an MP4, I think you'll have to hardcode the subtitles iwth the 'subtitles' video filter, and before that you'll have to extract the subtitles into a separate file. Note that I haven't actually tested if this preserves any fancy text, I've only used it with plain SRT subtitles:

```

ffmpeg -i input.mkv -map 0:s:0 subtitle.ass
ffmpeg -i input.mkv -filter:v 'subtitles=subtitle.ass' \
-c:v libx264 -preset veryfast -crf 22 -c:a copy -sn output.mkv

```

The version of ffmpeg in the repositories doesn't have access to the subtitles filter, you can see options for getting an up-to-date version from [here](http://ffmpeg.org/download.html). 

See also: [x264](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) and [AAC](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide) encoding guides.

---

### Post by FakeOutdoorsman on 2013-02-18
> **papibe said:**
> 
[*]Install ffmpeg with the extra codecs as described [here]("http://ubuntuforums.org/showthread.php?t=1117283").

I asked for that thread to be deleted, but instead it was moved to The Jail and it appears that it is still visible to some users. It is unmaintained due to the neutering of the Tutorials & Tips section, and it was designed for FFmpeg, not libav which is what Ubuntu unfortunately switched to. Therefore, it should not be used. I don't know who has permission to view it (just the forum staff and me?), but I would have preferred it to have been actually deleted.

---

### Post by gachnar on 2013-02-20
I was able to get things working in a slightly different way, but I am having an issue when trying to do the actual conversion as I keep getting errors with the fonts not being there... Now they (The fonts from the source file) are added to the initial MKV as attachments, but do not actually work when I extract and move to my system font location and then restart the encoding process. Ideas?

---

### Post by papibe on 2013-02-20
What is the original subtitles format?

It would be possible that using 'Gnome Subtitles' (GUI tool) may help you to convert the subtitles to a mp4 compatible format.

Just a thought.
Regards.

---

### Post by gachnar on 2013-02-21
All of the files have subs in the A-S-S format. It seems like I read that some people have had luck converting to the "TTXT" format, but I'm not sure about it. I want to keep all the fancy formatting if possible.

---

### Post by papibe on 2013-02-21
Install 'Gnome Subtitles'. Open the .ass file with it, and save the file to SubRip (.srt).

Then on the terminal:
```
MP4Box -ttxt subtitles.srt 
```
That should get you a .ttxt file compatible with mp4.

Let us know how it goes.
Regards.

---

### Post by Wolfpup on 2013-02-21
I have been working on a project like this for a while and even have a nearly completed script for doing the encoding.

here is the link to my forum post -> [http://ubuntuforums.org/showthread.php?t=2113242](http://ubuntuforums.org/showthread.php?t=2113242)

I still need to polish the script as it has issues with filenames that have special charecters and spaces in them.

The script dose hard subbing btw so that all the nice work the sub groups do is persevered even on hardware decoders that would normally ruin the subs.

---

### Post by gachnar on 2013-02-21
I've got a script very similar to yours wolf... I will paste it below... I managed to get around all the fancy commandline-fu with a extremely simple, yet in my opinion elegant solution in regards to escaping all the special characters.

granted, it's a MAJOR workaround, but it works quite well.

```

#!/bin/bash

for TEST in *.mkv
do
    
    mv "$TEST" "TEMP.mkv"
    subno=`mkvmerge -i "TEMP.mkv" | grep subtitles | awk -F " " '{print $3}' | sed 's/://g'`
    mkvextract tracks "TEMP.mkv" "$subno":"TEMP.ass"
    ffmpeg -i "TEMP.mkv" -c:v libx264 -crf 22 -preset veryfast -c:a copy -vf "ass=TEMP.ass" "`basename "$TEST" .mkv`.mp4"
    mv "TEMP.mkv" "$TEST"
    rm "TEMP.ass"

done

exit 0


```

sorry... I had to edit out the comments on the script

---

### Post by Wolfpup on 2013-02-26
Here is my script after making some changes to use some of what you have in your script although there is still one minor issue that i need to figure out how to over come as far as file names are concerned.
```

#!/bin/bash
echo "Time Encode Batch Start: "$(date +%m%d%Y%I%M%S%p)
shopt -s nullglob
for f in *.mkv
do
  cp "$f" "TEMP.mkv"
  echo "Trying file $f"
  info=$(mkvmerge --identify "TEMP.mkv")
  echo "mkvmerge --identify: $info"
  fonts=$( echo "$info" | sed -n 's/^[^0-9]*\([0-9]*\): type .application\/x-truetype-font.*$/\1/p')
  for font in $fonts
  do
    echo 'Extract attachment $font from $f'
    mkvextract attachments TEMP.mkv $font
  done
  rm "TEMP.mkv"
  mkdir -p $HOME/.fonts/
  shopt -s nullglob
  mv -f *.?t? $HOME/.fonts
  mv -f *.?T? $HOME/.fonts
done
sudo fc-cache -fv
shopt -s nullglob
for f in *.mkv
do
  cp "$f" "TEMP.mkv"
  #newName=$( echo "$f" | sed "s/^\[[^]]*\][_ ]\([^[]*\)[ _].*$/\1/")
  echo "Going to encode $f into $f.mp4"
  mkvextract chapters -s TEMP.mkv > TEMP.txt
  ffmpeg -i TEMP.mkv -map 0:s:0 TEMP.ass
  echo "Time Encode Start: "$(date +%m%d%Y%I%M%S%p)
  ffmpeg -i TEMP.mkv -vf "ass=TEMP.ass" -c:v libx264 -profile:v high -level 4.1 -crf 18 -preset veryslow -tune animation -deblock -1:-1 -x264opts qpmin=10:qpmax=28:aq-mode=2:no-mbtree:threads=auto:ref=8 -c:a copy TEMP.mp4
  echo "Time Encode Done : "$(date +%m%d%Y%I%M%S%p)
  MP4Box -add TEMP.mp4#video -add TEMP.mp4#audio -chap TEMP.txt TEMP-chaps.mp4
  mv "TEMP-chaps.mp4" "$f.mp4"
  rm "TEMP.mkv"
  rm "TEMP.mp4"
  rm "TEMP.ass"
  rm "TEMP.txt"
done
echo "Time Encode Batch Done: "$(date +%m%d%Y%I%M%S%p)

```

I still have to modify the final mp4's name to the formatting I want since it uses the full original filename including .mkv for the mp4 file name.

---

### Post by mirko-cm-klemm on 2013-11-02
With ffmpeg, you can do almost everything you want to convert just about anything to MP4 playable in, let's say, iTunes and IOS.
The only thing that was quite tricky was the conversion of bitmap-based "HDMV_PGS" subtitles to the "mov_text" subtitles required by MP4.
Burning in the subtitles was not an option for me because I still wanted to be able to select different languages or turn them off during playback.
My solution to this was as follows, and worked quite well now on many BD movies.
[LIST]
[*]In addition to ffmpeg, you need the following tools:
[LIST]
[*]mkvextract (part of the "mkvtoolnix" package")
[*]tesseract (ubuntu package "tesseract-ocr"), a very accurate free OCR system
[*]xsltproc (package "xsltproc") XSLT processor
[*]BDSup2Sub (available from [https://github.com/mjuhasz/BDSup2Sub/wiki](https://github.com/mjuhasz/BDSup2Sub/wiki)). Java runtime 1.6 or later is needed for this to work.
[/LIST]

[*]What you basically do is:
[LIST]
[*]extract the subtitles to a separate SUP file with mkvextract (In theory, ffmpeg should also be able to do this, but I did't get it to work yet):
```
mkvextract tracks inputfile.mkv 3:subtitle3.sup 4:subtitle4.sup
``` ...
[*]use BDSup2Sub to convert the SUP to individual PNG images with a descriptive XML file (make a temp directory first, this will produce lots of files):
```
java -jar BDSup2Sub.jar -o subtitle.xml subtitle3.sup
```
[*]let "tesseract" loop over the files and do an OCR on them, producing a text file for each of the PNG files. tesseract's options should include the correct subtitle language, e.g. "-l eng" and a hint to parse the whole image as a single block of text "-psm 6":
```
for pngfile in subtitle_????.png; do tesseract $pngfile ${pngfile%.png} -l eng -psm 6; done
```
[*]wrap all the resulting text files in a <subtext> xml tag in order to make it parseable by xsltproc:
```
for txtfile in subtitle_????.txt; do echo "<subtext>" >${txtfile%.txt}.xml; cat $txtfile >>${txtfile%.txt}.xml; echo "</subtext>" >>${txtfile%.txt}.xml; done
```
[*]run an XSLT transformation on the XML files to convert to a SRT file, which can be fed into ffmpeg during multiplexing:
```
xsltproc -o subtitle.srt bds2srt.xsl subtitle.xml
```
Note: the "subtitle.xml" file must be in the same direcory as the "subtitle_????.xml" files. The stylesheet will pull them in. Because this forum doesn't allow XSL attachments, just contact me if you wish to have it.
[*]Review the SRT file in a text editor for OCR errors. However, I found tesseract very accurate and OCR garbage very rare. There may be issues with text in italics or text blocks in different languages, though.
[*]specify the resulting SRT file as an additional input file to ffmpeg during MKV->MP4 transcoding (note the UTF-8 character encoding hint) Example:
```
ffmpeg -i video.mkv -sub_charenc="utf-8" -i subtitle.srt -codec:s mov_text -codec:v x264 -codec:a libfdk_aac outvideo.m4v
```
[/LIST]
[/LIST]
I was surprised how accurate tesseract OCR was out of the box without much additional intervention. Of course, I wrapped all of the above into a perl script, but this is still too specialized on my personal environment to simply publish it here. If you are still interested, just send me a PM.

EDIT:
Since I couldn'T attach the scripts, I'll post them here. 
The first script extracts the selected subtitles (edit "@selected_subtitles" in the script) and creates an SRT file from them, the second one transforms BD video to iOS and iTunes-ready MP4 after your reviewed the SRT file for OCR errors. You should make sure that you run the latest version of ffmpeg. This script also tries to extract attached cover artwork and add it to the MP4 so iTunes et al will show a useful icon for the movie. You need the package "mp4v2", however, for this to work.
The third one is the XSL stylesheet mentioned above.

```

#!/usr/bin/perl
use v5.14;
use strict;
use File::Basename;


my @selected_subtitles = (3,4);


my $scriptdir = dirname(__FILE__);


my $simulate=0;
if($ARGV[0] eq "-s") {
	shift;
	$simulate=1;
}




my $infilename = shift;
my ($basename,$dirname,$source_suffix) = fileparse($infilename, (".mkv"));
my $subdir=$dirname.$basename."_sub";
mkdir $subdir if(!$simulate);




my @probeout = `ffprobe "$infilename" 2>&1`;
my %subtitlemap = map {/^\s+Stream\s\#0\:(\d+)\((\w{3})\)\:\sSubtitle.*$/} @probeout;


my @mkvextract = (
	"mkvextract", "tracks",
	$infilename);
	
my @subnames;


foreach my $subtitle (@selected_subtitles) {
	my $lang = $subtitlemap{$subtitle};
	my $subname=$subtitle."_".$lang;
	push @subnames, $subname;
	push @mkvextract, $subtitle.":".$subdir."/".$subname.".sup";
}


printcmd(@mkvextract);


system @mkvextract if !$simulate;


foreach my $subname (@subnames) {
	mkdir $subdir."/".$subname if(!$simulate);
	
	my @bdsup2sub = (
		"java", "-jar", $scriptdir."/BDSup2Sub.jar",
		"-o", $subdir."/".$subname."/subtitles.xml",
		$subdir."/".$subname.".sup"
	);
	
	printcmd(@bdsup2sub);
	
	system @bdsup2sub if(!$simulate);
	
	my $escaped_subdir = ($subdir."/".$subname);
	$escaped_subdir =~ s/ /\\ /g;
	
	print "\"".$escaped_subdir."\"" if ($simulate);
	
	my @pngs = glob $escaped_subdir."/subtitles_????.png";


	printcmd(@pngs) if($simulate);
	
	foreach my $png (@pngs) {
		my ($txt) = $png =~ /(.*)\.png$/;
		my @tesseract = (
			"tesseract", $png, $txt,
			"-l", ($subname =~ /^\d+_(.*)$/)[0],
			"-psm", "6"
		);
		
		printcmd(@tesseract);
		
		system @tesseract if(!$simulate);
		
		open(TXT, "<$txt.txt");
		open(XML, ">$txt.xml");
		
		print XML "<subtext>\n";
		while(<TXT>) {
			print XML $_;
		}
		print XML "</subtext>";
		close XML;
		close TXT;
		unlink $txt.".txt";
	}
	
	my @xsltproc = (
		"xsltproc", 
		"-o", $subdir."/".$subname."/subtitles.srt",
		$scriptdir."/bds2srt.xsl",
		$subdir."/".$subname."/subtitles.xml"
	);
	
	printcmd(@xsltproc);


	system @xsltproc if(!$simulate);
}




sub printcmd {
	foreach my $line (@_) {
		print "\"".$line."\" ";
	};
	print "\n";
}

```

transcode BD movie:
```

#!/usr/bin/perl
use v5.14;
use strict;
use File::Basename;
use File::Path 'rmtree';


my $media_type = 9;
my $hd_video = 1;
my $title = "mymovie";
my $suffix = ".m4v";
my @selected_audio_tracks = (1,2);
my @selected_subtitles = (3);


my $scriptdir = dirname(__FILE__);


my $simulate=0;
my $addcover=0;
my $clean=0;
if($ARGV[0] eq "-s") {
	shift;
	$simulate=1;
} elsif($ARGV[0] eq "-a") {
	shift;
	$addcover=1;
} elsif($ARGV[0] eq "-c") {
	shift;
	$clean = 1;
}


my $infilename = shift;
my ($basename,$dirname,$source_suffix) = fileparse($infilename, (".mkv"));


my %metadata = (
	"media_type" => $media_type,
	"hd_video" => $hd_video	,
	"title" => $title,
	"synopsis" => "long description of movie, don't know character limit",
	"description" => "short decription (max 255 chrs)"
);


my @ffmpeg_options;




if(! (exists $metadata{'description'})) {
	$metadata{'description'} = substr $metadata{'synopsis'}, 0, 254;
}


my @probeout = `ffprobe "$infilename" 2>&1`;
my %audiomap = map {/^\s+Stream\s\#0\:(\d+)\((\w{3})\)\:\sAudio.*$/} @probeout;
my %subtitlemap = map {/^\s+Stream\s\#0\:(\d+)\((\w{3})\)\:\sSubtitle.*$/} @probeout;
my %thumbnails =  map {/^\s+Stream\s\#0\:(\d+)\:\sAttachment\:\s(\S+)\s*$/} @probeout;


my $out_file_name = exists $metadata{title} ? $metadata{title}.$suffix : $basename.$suffix;


my $attachment_index = 1;
foreach my $thumbnail (keys %thumbnails) {
	my $thumbnail_file=$dirname.$basename."_".$thumbnail.".".$thumbnails{$thumbnail};
	if(!$clean) {
		my @mkvextract = (
			"mkvextract","attachments",
			$infilename,
			$attachment_index.":".$thumbnail_file
		);
	
		system @mkvextract;
	} else {
		unlink $thumbnail_file;
	}
	$attachment_index++;
}




my @transcode_command = (
	"ffmpeg",
	"-v", "verbose",
	"-i", $infilename,
);


my @mappings = (
	"-map", "0:0"
);		




my @meta_args;
foreach my $atom_key (keys %metadata) {
	push @meta_args, ("-metadata", $atom_key."=".$metadata{$atom_key});
}


foreach my $audiotrack (@selected_audio_tracks) {
	push @mappings, ("-map","0:".$audiotrack );
}


my $subtitledir = $dirname.$basename."_sub/";
my $subtitleindex = 0;


if($clean) {
	rmtree([$subtitledir]);
}


my $subtitleindex = 0;
foreach my $subtitle (@selected_subtitles) {
	my $lang = $subtitlemap{$subtitle};
	push @transcode_command, (
		"-sub_charenc","utf-8",
		"-i", $subtitledir.$subtitle."_".$isolang."/subtitles.srt"
	);
	push @mappings, ("-map", ($subtitleindex +1).":0");
	push @meta_args, ("-metadata:s:s:".$subtitleindex, "language=".$lang );
	$subtitleindex++;
}




push @transcode_command, @mappings;
push @transcode_command, @meta_args;
push @transcode_command, @ffmpeg_options;
push @transcode_command, (
	"-c:a", "libfdk_aac",
	"-vbr","3",
	"-cutoff","18000",
	"-ac","2",
	"-ab","160k",
	"-c:s", "mov_text",
	"-c:v", "libx264",
	"-strict", "experimental",
	"-preset", "slow",
	"-crf","22",
	"-threads","0",
	"-level","30",
	"-maxrate", "6000000",
	"-bufsize", "6000000",
	"-movflags", "faststart",
	"-f","mp4",
	$out_file_name);




foreach(@transcode_command) {
	print "\"$_\", ";
}
print "\n";


system @transcode_command if(!$simulate && !$addcover && !$clean);


foreach my $thumbnail (keys %thumbnails) {
	my @mp4art = (
		"mp4art", "--optimize", "--overwrite",
		"--add", $dirname.$basename."_".$thumbnail.".".$thumbnails{$thumbnail},
		$out_file_name
	);
	printcmd(@mp4art);
	system @mp4art if(!$simulate && !$clean);
}


	




sub printcmd {
	foreach my $line (@_) {
		print "\"".$line."\" ";
	};
	print "\n";
}

```

bds2srt.xsl:
```

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
	<xsl:param name="framerate" select="number(23.98)"/>
	<xsl:output method="text" encoding="utf-8"/>
	
	<xsl:template match="/">
		<xsl:apply-templates select="BDN/Events/Event"></xsl:apply-templates>
	</xsl:template>
	
	<xsl:template match="Event">
		<xsl:value-of select="position()"/>
<xsl:text xml:space="preserve">
</xsl:text>
		<xsl:apply-templates select="@InTC" mode="tc"/> --> <xsl:apply-templates select="@OutTC" mode="tc"/>
<xsl:text xml:space="preserve">
</xsl:text>
	<xsl:value-of select="normalize-space(document(concat(substring-before(Graphic,'.png'),'.xml'), .))"/>
<xsl:text xml:space="preserve">


</xsl:text>
</xsl:template>
	
	<xsl:template match="@*" mode="tc">
		<xsl:variable name="tc" select="substring(., 1, 8)"/>
		<xsl:variable name="ms" select="substring(.,10,2) * 1000.0 div $framerate"/>		
		<xsl:value-of select="$tc"/>,<xsl:value-of select="format-number($ms, '000')"/>		
	</xsl:template>
</xsl:stylesheet>

```

---

