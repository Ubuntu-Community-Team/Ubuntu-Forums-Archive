---
title: "Capture streaming video"
date: 2011-02-13
forum: Multimedia Software
---

### Post by coolclassic on 2011-02-13
Up untill this week I used to grab a streamed video from my root/tmp file. Video is nolonger streamed to this file. What has happened? and how can I grab streamed video?

---

### Post by Brain Fire on 2011-02-13
I was about to make the exact same thread! It seems like the change happened when I was in the middle of grabbing videos I was loading from YouTube. One minute they're showing up in the /tmp folder and literally the next, they no longer showed up there. It's the strangest thing!

---

### Post by coolclassic on 2011-02-14
):P hello there! Anyone able to answer the above problem?

---

### Post by ron999 on 2011-02-14
> **coolclassic said:**
> Up untill this week I used to grab a streamed video from my root/tmp file. Video is nolonger streamed to this file. What has happened? and how can I grab streamed video?
Flash plugin was upgraded to 10.2.
This method seems to work OK:- [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10454017&postcount=6]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10454017&postcount=6")

---

### Post by fmdex2011 on 2011-02-14
The location for flash files has changed

In Nautilus, click on View, then select Show Hidden Files,

then go to :

/home/yourlogin/.mozilla/firefox/xxxxxxxx.default/Cache

xxxxxxxx represents an 8 digit random string that your computer generates

Make sure you increase your cache size in Firefox to fit whatever you are watching, otherwise the file will vaporize after the download is complete. 

The default size is 50MB, I changed mine to 300MB to be safe. 

In Firefox click Edit, Preferences, Advanced, and the Network tab, use the Offline Storage spinner

Also, the files will stay in the Cache if you move to another web page, so make sure you have enough space

By the way, divx, xvid and avi files still go to /tmp/ 

Hope this helps     :)

---

### Post by Brain Fire on 2011-02-14
But why? Having them go into the /tmp folder was more convenient. While your video is loading, you keep surfing which makes the flash video in your cache hard to find. 

What is the purpose of this change?

---

### Post by dragon1111 on 2011-02-15
It doesnt go into the tmp folder anymore...The only other easy way out is to look for it in your Firefox cache as fmdex2011 rightly said

---

### Post by gcranston on 2011-02-18
> **ron999 said:**
> Flash plugin was upgraded to 10.2.
This method seems to work OK:- [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10454017&postcount=6]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=10454017&postcount=6")

This method worked perfectly for me. Reverted to 10.1.102.64 and can capture all my flash "movies" again.

Thanks.

---

### Post by chetancrasta on 2011-02-24
The method suggested by gcrantson works. Here is a more detailed description of the procedure:

To downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

### Post by Clancy_s on 2011-02-25
Thanks for the explanation - for the moment I'm going to leave the new flash; I've made a link to the cache directory for easy access.

If that doesn't work I may downgrade as described.

eta: the link to cache works fine, but if I put the vid on hold and let it download fully (planning on grabbing it to watch later off line) it disappears from the cache - reappears when I start the vid playing.  There was more than enough room for it, I like the load whilst on hold option so it's back to the old version for me.

---

### Post by emptythevoid on 2011-03-01
This won't work in all cases, but you could try ClipGrab or DownloadHelper
[http://clipgrab.de/en](http://clipgrab.de/en)
[https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/)

I know with Youtube, you can copy and paste in a URL of the Youtube video and ClipGrab will start downloading the file independent of your web browser, so you don't have to worry about your cached video vanishing if you've left it on hold.  However, I have noticed ClibGrab has a hard time downloading Youtube vids that have an age restriction warning on them.

---

### Post by chetancrasta on 2011-04-10
Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/2011...ash-files.html](http://davesource.com/Solutions/2011...ash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

---

### Post by Mariane on 2011-09-21
I cannot make this work. My cache seems to contain still images, html code, gzipped C code (of all things), and advertisement videos. But the videos I wanted to watch are either not there or they are somehow hidden... 

What should I do, please? 

Mariane

---

### Post by chetancrasta on 2011-09-21
> **Mariane said:**
> I cannot make this work. My cache seems to contain still images, html code, gzipped C code (of all things), and advertisement videos. But the videos I wanted to watch are either not there or they are somehow hidden... 

What should I do, please? 

Mariane

Read the previous post...

---

### Post by josephmills on 2011-09-21
Hi there dont know if this will help but here you go. 
take this script and copy it 
```

#!/usr/bin/perl
# Description:	Copy flash files in your browsers cache
# Dependencies:	Unix command 'lsof'
use strict;

##################################################
# Setup the variables
##################################################
my $PROGNAME = $0; $PROGNAME =~ s|.*/||;

my $LSOF = 'lsof';

my $FIND = 'flash';	# Find flash files
my $POST = 'flv';	# Postfix to save to

# Where we save files
#   %f is $FIND
#   %d is the next available number
#   %p is .$POST
my $DEST = "found%f.%d%p";

##################################################
# Usage
##################################################
sub fatal {
	foreach my $msg (@_) { print STDERR "[$PROGNAME] ERROR:  $msg\n"; }
	exit(-1);
}

sub usage {
	foreach my $msg (@_) { print STDERR "ERROR:  $msg\n"; }
	print STDERR <<USAGE;

Usage:\t$PROGNAME [-d]
  Copies deleted flash files currently open in your browser's cache
  -d             Set debug mode
  -find <str>    What to search for  [default $FIND]
  -post <str>    Postfix for saving files [default $POST]
  -dest <str>    Or just specify full destination [default $DEST]
                 (see the script for meanings of %f, %d, %p)

USAGE
	exit -1;
}

sub parseArgs {
	usage("You need to be on a system that uses /proc") unless -d '/proc';

	my $opt = {
		find => $FIND,
		post => $POST,
		dest => $DEST,
	};
	while (my $arg=shift(@ARGV)) {
		if ($arg =~ /^-h$/) { usage(); }
		if ($arg =~ /^-d$/) { $MAIN::DEBUG=1; next; }
		if ($arg =~ /^-find$/) { $opt->{find} = shift(@ARGV); next; }
		if ($arg =~ /^-post$/) { $opt->{post} = shift(@ARGV); next; }
		if ($arg =~ /^-dest$/) { $opt->{dest} = shift(@ARGV); next; }
		if ($arg =~ /^-/) { usage("Unknown option: $arg"); }
		usage("Too many files specified [$arg and $opt->{file}]") if $opt->{file};
	}

	usage("You need to specify a destination with -dest")
		unless $opt->{dest};
	
	usage("You need to specify something to search for with -find")
		unless $opt->{find};
	
	$opt;
}

sub debug {
	return unless $MAIN::DEBUG;
	foreach my $msg (@_) { print STDERR "[$PROGNAME] $msg\n"; }
}

##################################################
# Main code
##################################################
sub findFiles {
	my ($opt) = @_;
	my @found;
	# 'lsof /'  (The '/' just does files, no sockets, and is faster)
	open(LSOF,"$LSOF /|") || usage("Can't run [$LSOF]");
	while (<LSOF>) {
		next unless /delete/i;
		next unless /\Q$opt->{find}\E/i;
		next if /\.adobe/; 	# Ignore adobe 'flash' db files
		chomp;
		# procname  pid  user   fd
		usage("Found it, can't parse it [$_]")
			unless /^\S+\s+(\d+)\s+\S+\s+(\d+)/;
		push(@found, [$1,$2]);
	}
	usage("Couldn't find any deleted cached $opt->{find} files")
		unless @found;
	@found;
}

sub procPath {
	my ($pid,$fd) = @_;
	my $path = "/proc/$pid";
	usage("Couldn't find $path") unless -d $path;
	$path .= '/fd';
	usage("Couldn't find $path") unless -d $path;
	$path .= "/$fd";
	usage("Couldn't read $path") unless -e $path;
	$path;
}

sub destPath {
	my ($opt) = @_;
	my $p = $opt->{dest};
	$p =~ s/%f/\Q$opt->{find}\E/g;
	$p =~ s/%p/.\Q$opt->{post}\E/g;
	my $num = 0;
	my $path;
	do {
		$path = $p;  $num++;
		$path =~ s/%d/$num/g;
	} until ! -f $path;
	$path;
}

sub main {
	my $opt = parseArgs();
	
	my @found = findFiles($opt);
	foreach my $found ( @found ) {
		my $src = procPath(@$found);
		my $dest = destPath($opt);
		print "$src -> $dest\n";
		system("/bin/cp",$src,$dest);
	}
}
main();


```


Next open gedit and paste it there . then save as [COLOR="Red"]flash.sh[/COLOR]   in your [COLOR="Red"]/home/Videos[/COLOR]  dir 


now open your terminal and type in 
```
cd ~/Videos
```
then 
```
sudo chmod +x flash.sh 
```

then open up a browser and go to youtube. open a video and let it load. after it has loaded. 

open terminal again and 
```
cd ~/Videos 
```
then 
```
./flash.sh 
```
then open up your file manager and go to your Videos folder it the video in there ?

---

