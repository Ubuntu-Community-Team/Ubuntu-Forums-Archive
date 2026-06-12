---
title: "solution for saving .flv files with 11.10 and firefox?"
date: 2012-02-29
forum: Multimedia Software
---

### Post by ijason on 2012-02-29
greetings.

i am continuing to struggle with finding a solution to saving the .FLV videos from a movie site. i am working up hill on two fronts - my computer is slow enough that trying to watch movie-length videos from the web browser doesn't really work, and my internet connection is slow enough that i really can't stream them to begin with! let's assume that neither of these sad conditions can be immediately corrected. :c

things are further complicated by the site's security denying any plug-in downloaders that would normally be the first solution. they only want to stream their content DIRECTLY through a browser. copying the path to the .FLV video and plugging that into any of several "flash download" plug-ins for firefox has resulted in "hacking attempt logged" pop-up notices and no videos.

i've seen several threads on here, but none very recently updated, so i thought i would start a new one.

so far i have followed several threads on my mission...

i've tried finding the "deleted" cache file in system memory, as suggested in the following two threads. but there are NO files tagged "(deleted)". i have tried this with downgraded flash version 9.x and 10.x. i should note that 9.x DID reveal unlinked files using this method and after viewing You-Tube video content, but that 9.x is apparently too old to pass security mustard for my particular site. 
[COLOR="Navy"]([http://liori.jogger.pl/2010/11/08/getting-flash-videos-from-almost-deleted-files/]("http://liori.jogger.pl/2010/11/08/getting-flash-videos-from-almost-deleted-files/"))
([http://superuser.com/questions/235535/in-google-chrome-on-linux-where-is-the-flv-if-not-in-tmp]("http://superuser.com/questions/235535/in-google-chrome-on-linux-where-is-the-flv-if-not-in-tmp"))[/COLOR]

speaking of downgrading flash, i have tried this as well. following the suggestion in this thread 
[COLOR="Navy"]([http://ubuntuforums.org/showthread.php?t=1690673]("http://ubuntuforums.org/showthread.php?t=1690673"))[/COLOR]

i have followed a few other threads, among them 
[COLOR="Navy"]([http://ubuntuforums.org/showthread.php?t=1688948]("http://ubuntuforums.org/showthread.php?t=1688948"))
([http://ubuntuforums.org/showthread.php?t=1714940&highlight=firefox+save+.flv]("http://ubuntuforums.org/showthread.php?t=1714940&highlight=firefox+save+.flv"))[/COLOR]

sadly, the FlashVideoReplacer does not work for this particular site.
[COLOR="Navy"]([http://ubuntuforums.org/showthread.php?t=1487327&highlight=save+.flv&page=23]("http://ubuntuforums.org/showthread.php?t=1487327&highlight=save+.flv&page=23"))[/COLOR]

SO THEN...

has there been any recent developement in saving .FLV videos through firefox? i am happy to download chrome or any other browser that will fix my problem. all of the threads i have seen are a few months old... and i don't know whether a universal solution was discovered, or whether the community has just given up.

i FEEL like the solution will lay in tracing the process used by flash to put the video on the screen, and then to somehow save the cache that is being used. but that's just a feeling, i really don't know.

lastly, i have just tried and had no success with the screen capture route, as the cpu load bogs my machine down enough to render the video choppy and useless.

thank for reading!

---

### Post by ajgreeny on 2012-02-29
Downloading from you-tube is against their terms and conditions so I will say nothing about that, but flash from some other web-sites can sometimes be downloaded as .flv files using the FF add-on **download-helper.**  I have not tried any other add-ons to do this so can not comment further.
If that add-on is one you've already tried without success, it is probably because the site you are trying to download from does not allow it to be done in any way at all.

---

### Post by ijason on 2012-02-29
thank you for your reply, ajgreeny :)

as i stated in my post, i have tried several different "flash downloader" helper type add-ons for firefox. all to no evail as they apparently run afoul of the site's efforts to prevent multiple windows being opened, or bots from downloading the entire site if an account gets compromised. i am only able to view content through a normal web browser... as far as i can tell. 

as for the UAP or T&C for You-tube, i suppose i appreciate any efforts to help keep people informed about the world around them. i specifically said that i was trying to save videos from a different site and only mentioned You-tube in reference to experiments i have done to try and find my solution. 

your concern over the legality of saving my purchased content is certainly commendable in these troubling times, i think your suggestion of simply catagorising as illegal anything which can't be accomplished thru a simple plug-in may be the most prodent advice. however, i have specific subscription rights to the content i'm trying to save for my own personal viewing, so i must struggle on. unfortunately i am hamstrung by a derlict computer and mediocre internet speed :<

i am looking forward to more technical suggestions from this great forum.

again, thank you for your input :)

---

### Post by Mad Tux on 2012-02-29
Fully downloaded flash files in firefox are saved @ /tmp. I dunno if that's also true for Ubuntu as I only watch Youtube on Opensuse 11.1 and recently swiched to Ubuntu cause KDE 4 still sucks. (I could as well use Win7 if I wanted a bloated GUI)

---

### Post by ron999 on 2012-02-29
Hi
There's information at stream-recorder.com...
but if you ask generic questions about
"saving the .FLV videos from a movie site"
and
"save videos from a different site"
nobody there will help you.:p

---

### Post by winh8r on 2012-02-29
Apologies in advance if this has not worked for you but I would recommend using the following combination:

do this first:
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss")

then these:

[https://addons.mozilla.org/en-US/firefox/addon/flashgot/]("https://addons.mozilla.org/en-US/firefox/addon/flashgot/")

[https://addons.mozilla.org/en-US/firefox/addon/ghostery/?src=ss]("https://addons.mozilla.org/en-US/firefox/addon/ghostery/?src=ss")

[https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/?src=ss]("https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/?src=ss")

I had a similar problem when I wanted to save an educational video made by a colleague but was prevented by the server he used to host it on.

This little combination worked a treat, just make sure you read the documentation for flashgot carefully.

---

### Post by lovinglinux on 2012-02-29
Most likely the server is using rtmp, so you wont be able to find any temporary file and download extensions won't be able to download it.

You could try RTMPDump

---

### Post by ijason on 2012-02-29
> **lovinglinux said:**
> Most likely the server is using rtmp, so you wont be able to find any temporary file and download extensions won't be able to download it.

You could try RTMPDump

thank you for joining this thread... i had all appendages crossed that your replacement plugin would be the solution! good work all the same :) i have seen some discussion of RTMPDump, but when i followed up a walkthru of it's use, it appeared to be a command line tool that would start a unique "session" to try and request the .flv file from the server - which means it would get denied like all the other firefox add-ons.

if i am incorrect and it performs differently, then i will happily try and use it. all they can do is ask me (again) for my credentials to be sure i'm not trying to hack them.

---

### Post by ijason on 2012-02-29
> **Mad Tux said:**
> Fully downloaded flash files in firefox are saved @ /tmp. I dunno if that's also true for Ubuntu as I only watch Youtube on Opensuse 11.1 and recently swiched to Ubuntu cause KDE 4 still sucks. (I could as well use Win7 if I wanted a bloated GUI)

unfortunately, flash >10.2 no longer saves files of any kind into a temp folder. at best, it is apparently saved and them immediately deleted, although occasionally recoverable. 

thank you for your contribution :)

---

### Post by josephmills on 2012-02-29
Not sure if this will help or not 
[img]https://encrypted-tbn1.google.com/images?q=tbn:ANd9GcSvRVS6OVdIqK1JF8mTH8hkkqGw7MRWzhSL-afwL4nsXXQ9dD9E6w[/img]
```


#copy flash from browser 
#!/usr/bin/env perl
# Description:    Copy flash files in your browsers cache
# Dependencies:    Unix command 'lsof'
use strict;

##################################################
# Setup the variables
##################################################
my $PROGNAME = $0; $PROGNAME =~ s|.*/||;

my $LSOF = 'lsof';

my $FIND = 'flash';    # Find flash files
my $POST = 'flv';    # Postfix to save to

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
       usage("Too many files specified [$arg and $opt->{file}]") if
$opt->{file};
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
       next if /\.adobe/;     # Ignore adobe 'flash' db files
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

how to use 

[http://www.youtube.com/watch?v=9zFOAibVHiU](http://www.youtube.com/watch?v=9zFOAibVHiU)

---

### Post by ijason on 2012-02-29
> **winh8r said:**
> Apologies in advance if this has not worked for you but I would recommend using the following combination:

do this first:
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss")

then these:

[https://addons.mozilla.org/en-US/firefox/addon/flashgot/]("https://addons.mozilla.org/en-US/firefox/addon/flashgot/")

[https://addons.mozilla.org/en-US/firefox/addon/ghostery/?src=ss]("https://addons.mozilla.org/en-US/firefox/addon/ghostery/?src=ss")

[https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/?src=ss]("https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/?src=ss")

I had a similar problem when I wanted to save an educational video made by a colleague but was prevented by the server he used to host it on.

This little combination worked a treat, just make sure you read the documentation for flashgot carefully.

i already have two of your suggested add-ons! i added Flash-Aid while following a thread which suggested it could be used to downgrade flash to older versions... and have been unable to find that function for it. however, it does look like it will be a brilliant tool to keep my flash up-to-date. 

ABP is a staple of any firefox install for me, but i am unsure of how the flash manager and ABP or Ghostery will combine to help me save the videos? if they work in combination to somehow let me save the videos i am willing to try them, but on first glance they seem to work to aid my privacy and reduce tracking cookies etc. laudable goals certainly, but not specifically what i am currently looking for. 

have you had success using flashgot? i tried the windows version briefly, and it was more of an external download manager than anything particularly helpful for me. for saving standard videos i use DownloadHelper and have been satisfied... however this particular site denies all add-on requests to save files  :<

thank you for your help.

---

### Post by ijason on 2012-02-29
> **ron999 said:**
> Hi
There's information at stream-recorder.com...
but if you ask generic questions about
"saving the .FLV videos from a movie site"
and
"save videos from a different site"
nobody there will help you.:p

great! i will begin scouring their forums for help as well. thank you for your suggestion

---

### Post by lovinglinux on 2012-02-29
> **ijason said:**
> thank you for joining this thread... i had all appendages crossed that your replacement plugin would be the solution! good work all the same :) i have seen some discussion of RTMPDump, but when i followed up a walkthru of it's use, it appeared to be a command line tool that would start a unique "session" to try and request the .flv file from the server - which means it would get denied like all the other firefox add-ons.

if i am incorrect and it performs differently, then i will happily try and use it. all they can do is ask me (again) for my credentials to be sure i'm not trying to hack them.

If rtmpdump access is denied, then I don't know what else you can do.

---

### Post by ijason on 2012-02-29
> **josephmills said:**
> Not sure if this will help or not 
[img]https://encrypted-tbn1.google.com/images?q=tbn:ANd9GcSvRVS6OVdIqK1JF8mTH8hkkqGw7MRWzhSL-afwL4nsXXQ9dD9E6w[/img]
```


#copy flash from browser 
#!/usr/bin/env perl

code

}
main();

```

how to use 

[http://www.youtube.com/watch?v=9zFOAibVHiU](http://www.youtube.com/watch?v=9zFOAibVHiU)

thank you for replying. 

watching the video, it appears that you save this code as a text, and then enable the text to run? and that you start the script BEFORE opening your browser... then watch your video... and the script will dump the cached file for you after you let the video buffer?

forgive my ignorance, but that's how it seemed to work. if so, i think that may be exactly what i was looking for!

---

### Post by ijason on 2012-02-29
> **lovinglinux said:**
> If rtmpdump access is denied, then I don't know what else you can do.

am i correct that the usage of RTMPdump is to open a terminal and enter the address to the .FLV video using RTMPdump command line tool to save the video? if RTMPdump somehow goes through an open instance of firefox it might work, but if it opens a command line request (such as apt-get or wget) i don't think it will work :<

---

### Post by josephmills on 2012-02-29
> **ijason said:**
> thank you for replying. 

watching the video, it appears that you save this code as a text, and then enable the text to run? and that you start the script BEFORE opening your browser... then watch your video... and the script will dump the cached file for you after you let the video buffer?

forgive my ignorance, but that's how it seemed to work. if so, i think that may be exactly what i was looking for!

take the script save it in your ~/Videos folder as ripper 
open terminal 
```
cd ~/Videos/
```
then 
```
sudo chmod +x ripper
```
then 
open a browser and find a flash video. press play let load all the way then. 
in terminal 
```
cd ~/Videos
```
then run the script after loaded DO NOT CLOSE browser WINDOW
```
./ripper
```

lOok in video folder ...



The script user the unix command lsof or list open files. then it finds them and saves you can also just run ```
./ripper --help
```
there are a couple of other options put in there also :?

Now if quickly([http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/)) / Glade would work like this still [http://www.youtube.com/watch?v=3JuvSobjMi4](http://www.youtube.com/watch?v=3JuvSobjMi4) I would make into gui. But I cannot figure it out. :?

---

### Post by ijason on 2012-02-29
@josephmills

script breaks on line 5. Command not found, which then causes it to break in a few other places.  

"use strict;"

is that supposed to be on the same line as the # comment about lsof? or do i need to 'apt-get install strict'?

thank you for your continued help, i'm looking forward to this being my fix!

---

### Post by josephmills on 2012-02-29
> **ijason said:**
> @josephmills

script breaks on line 5. Command not found, which then causes it to break in a few other places.  

"use strict;"

is that supposed to be on the same line as the # comment about lsof? or do i need to 'apt-get install strict'?

thank you for your continued help, i'm looking forward to this being my fix!

No that is not it it was me typo sorry  Here is the correct code 
```
#!/usr/bin/env perl
# Description:    Copy flash files in your browsers cache
# Dependencies:    Unix command 'lsof'
use strict;

##################################################
# Setup the variables
##################################################
my $PROGNAME = $0; $PROGNAME =~ s|.*/||;

my $LSOF = 'lsof';

my $FIND = 'flash';    # Find flash files
my $POST = 'flv';    # Postfix to save to

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
       usage("Too many files specified [$arg and $opt->{file}]") if
$opt->{file};
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
       next if /\.adobe/;     # Ignore adobe 'flash' db files
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

---

### Post by ijason on 2012-02-29
@josephmills

tragically 

> jason@jason:~/Videos$ sudo chmod +x ripper
jason@jason:~/Videos$ ./ripper
ERROR: Couldn't find any deleted cached flash files

and this is with the firefox window still sitting there with the end of the video i just watched. the most annoying part is that the bar for the video is entirely grey, i KNOW the whole thing is saved in cache somewhere. and i KNOW it writes to the drive, because my hard disk flashes as the video loads up :<

---

### Post by ijason on 2012-02-29
i saw a brilliant suggestion in one thread, that was a script somebody had put together that would use rSync to constantly dump the newest file in the temp directory that was over x megabytes in size, and would keep backing it up and overwriting the saved copy as long as the file in the temp folder was larger than the saved copy. you would lose the last quarter second of the clip when flash deleted it after playing... but you got everything you needed.

unfortunately, with flash +10 there is apparently no temp file to copy, it buffers it up into ram (which is half the reason my computer can't play long videos), but all my attempts to fetch it out of the ram failed to locate it :/

---

### Post by josephmills on 2012-02-29
try it again ? dont know never really had that trouble maybe close firfox and open again and let load. try on other sites too just to see


EDIT 
what is video's site ?

---

### Post by ijason on 2012-02-29
> **josephmills said:**
> try it again ? dont know never really had that trouble maybe close firfox and open again and let load. try on other sites too just to see


EDIT 
what is video's site ?

still no luck. and that's after closing firefox completely, and then restarting it to go directly to the site. let the video buffer up completely (15 minutes) and then let it play all the way through (jaggedly, took 20 minutes). then ran your script from a terminal without closing the firefox window.

same results, unfortunately :<

the video's site is a rediculously overpriced retraining company that's somehow so secret all of the tech's sign paperwork to not give out the address... although, apparently their concern is undeeded as half the subscribers can't even view the stuff, let alone save it to try and view without the internet being part of the problem.

i appreciate your continued interest. i will be checking this thread tomorrow :)

---

### Post by lovinglinux on 2012-03-01
> **ijason said:**
> unfortunately, with flash +10 there is apparently no temp file to copy, it buffers it up into ram (which is half the reason my computer can't play long videos), but all my attempts to fetch it out of the ram failed to locate it :/

That's because  it is using rtmp as mentioned before. Sites that use regular flash streaming generate a temp file and can be downloaded using Video Download Helper. Those that use rtmp don't generate a temp file and can't be downloaded using Video Download Helper. That's why I suggested rtmpDump.

---

### Post by ijason on 2012-03-13
greetings! my appologies for a week long pause in the progress of this thread. i have been unable to work on this project for this time, but i can finally pursue it again. 

thanks to **LovingLinux** for your continued support. however, i have yet to have successful results from using RTMPdump (or RTMPsrv). i have followed - as best i could - these tutorials :
([http://stream-recorder.com/forum/use-rtmpdump-rtmp-dump-tutorials-t8911.html?]("http://stream-recorder.com/forum/use-rtmpdump-rtmp-dump-tutorials-t8911.html?"))
([http://constcuriosity.blogspot.com/2010/01/revisiting-rtmpdump.html]("http://constcuriosity.blogspot.com/2010/01/revisiting-rtmpdump.html"))
([http://www.youtube.com/watch?v=c1PtnSGNPlg]("http://www.youtube.com/watch?v=c1PtnSGNPlg"))

i noticed that after using iptables to redirect the RTMP port, the videos on a test website (comedy central's southpark studios) would fail to display on my browser. and that the RTMPsrv command would successfully output a long command line to use RTMPdump to save the stream. after restoring iptables the video content would again display on the browser (although the actual download through RTMPdump didn't work...)

when i followed the same process with my tutorial website i observed that the flash video CONTINUED TO PLAY, even with iptables set to redirect RTMP content. can i conclude that the content i am having trouble with is NOT being delivered through RTMP? running RTMPsrv yielded no output :c

while trying to follow the Stream-Recorder.com walkthrough i failed to see similar content on my website as one of the authors did on their guide. here is the container code for one of the videos i need to save :

> <object id="f4Player" width="720" height="400" type="application/x-shockwave-flash" data="loader.swf?v1.3"> 
  <param name="movie" value="loader.swf?v1.3" /> 
  <param name="quality" value="high" /> 
  <param name="menu" value="false" /> 
  <param name="scale" value="noscale" /> 
  <param name="allowfullscreen" value="true"> 
  <param name="allowscriptaccess" value="always"> 
  <param name="swlivevonnect" value="true" /> 
  <param name="cachebusting" value="false"> 
  <param name="flashvars"   value="skin=streamer.swf&file=0025/low/0001"/> 
  <a href="http://www.adobe.com/go/getflash"> 
    <img src="http://www.adobe.com/images/shared/download_buttons/get_flash_player.gif" alt="Get Adobe Flash player"/> 
  </a> 
</object>

does this offer any information useful for saving this content?

thank you for your continued help!

---

### Post by ridgeland on 2012-06-03
I found this looking for a solution for saving firefox video.  I still have Ubuntu 9.04 with Firefox 3.0.19 on a partition on my hard drive.  I can boot there for easy downloads of videos.
I just checked again. Firefox stores the video in /tmp/.  So the youtube I just watched was stored as /tmp/FlashllvkDZ
Just copy the file to a safe place before rebooting erases it.  Also Firefox often erases it when you go to the next video.
That doesn't meet your constraint of using 11.10 but if you really want that video try installing an older version on a spare partition.
I just checked the ftp sites and Ubuntu only has 8.04, 10.04 etc now.  humm....

---

