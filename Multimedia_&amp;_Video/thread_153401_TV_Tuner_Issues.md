---
title: "TV Tuner Issues"
date: 2006-03-31
forum: Multimedia &amp; Video
---

### Post by CornMaster on 2006-03-31
Got a bunch. :)

Got an ATI TV Wonder VE...probably going on 5 years old now.
Runs well in tvtime (although a little laggy if I try to do other things like surf the web)

My goal was to install Mythtv so that I could record stuff.  I did get mytv installed and (mostly) working but here are my issues.

1) Sound.  Not a huge problem, but mythtv doesn't mute/unmute my line in when it turns on/off...so I have no sound unless I unmute manually.  Tvtime unmutes, but doesn't remute when closed.

2) Quality.  In Tvtime I had to finetune my channels to about +15 (same for xaw).  In windows using the ATI software it looks fine (but not as good as the finetuned image)....but in myth I cannot find the option...so the images are fuzzy and washed out.

3) Channels.  This happens in both tvtime and myth.  The channels are all off by 1.  So 44 (Space) needs to be entered as 45.  This natually messes up the guide info.

4) Complexity.  Anyone have a keymap for myth?  Like a nice visual one that I can print off or something.  I have no idea what all the buttons do...and I made a mess of it trying to find out. ;)

Anyway..that's all I can think of for now.  Anyone have any input on any of these issues?

Thanks

---

### Post by CornMaster on 2006-04-01
[QUOTE=CornMaster]
3) Channels.  This happens in both tvtime and myth.  The channels are all off by 1.  So 44 (Space) needs to be entered as 45.  This natually messes up the guide info.[/QUOTE]

I've sort of solved this by creating a perl script that will take the listings.xml file that tvtime uses, and add one to the channel numbers.  This corrects all the data for the on screen display.  But I'm still having an issue..any perl gurus here?

I'm guessing the problem is with the bolded parts.  A proper file is outputted, but when it detects the change in the xml file ("programme start") then nothing gets outputted.  So basically I'm left with all the proper channels, but no programs.  I'm sure it's where I'm trying to jump out of a loop, but I can't think of any other way to do it.  I basically just want to tack the rest of the file on to my modified stuff as is.  And it's a lot of file...like 7 MBish.

Anyone got some ideas?

PS If you can tell my why the very last part ALWAYS launches tvtime no matter what I type....I'll give you a virtual hug.

```

#!/usr/bin/perl

# This script adds one to all the chanels outputted by the XMLTV script
# Apr 1/06

$LISTINGS = "/home/thomas/testlistings.xml";
$OUTPUT = "/home/thomas/fixedlistings.xml";
$OUTBUFFER;
$NUM = 1;
$NEWSTRING;

print "This may take several minutes to process.\n";

open(LISTINGS) or die("Listings file not found.");
foreach $line (<LISTINGS>) {
	chomp($line); #remove the newline
	if ($line =~ m/(<display-name>)(\d\d?)(.+)/){ #this is one of the three lines we need. Actually
						#matches 4 lines, but no big deal.
		$NEWCHAN = $2 + 1; #adds 1 to the channel read in
		$NEWSTRING = "$1$NEWCHAN$3";
		$OUTBUFFER = "$OUTBUFFER$NEWSTRING\n";
	}
	else{
		if ($line =~ m/programme start/){
			**&FinishFile;**
		}
       	        $OUTBUFFER = "$OUTBUFFER$line\n";
	}
}

sub FinishFile{
[B]	foreach $line (<LISTINGS>) {
		$OUTBUFFER = "$OUTBUFFER$line\n";
	}[/B]
	open NEWLISTINGS, ">$OUTPUT";
        	print NEWLISTINGS $OUTBUFFER;
	close NEWLISTINGS;

	print "Finished!\n"; #Load tvtime now? [y/N]: ";
	close LISTINGS;
#	$a = <STDIN>;                   # Get input
#	chop $a;                        # Remove the newline at end
#	print $a;
#	if ($a = "y"){
#	        exec tvtime;
#       	exit();
#	}	
#	else{
#        	exit();
#	}
}


```

---

### Post by Omnios on 2006-04-01
Hi I have a ATI all in wonder pro tuner card and found the Zapping tv program fixed all my problems and it has a lot of tv encoding and set up stuff for channels with a slider fine toon which I did not have to use. Only downside is the channel thing is a bit complex but once you get it set up once its pretty good. I have TV time but found Zapping to work smoother with better picture quality.

---

### Post by Argon Sloth on 2006-04-10
Out of curiosity. Are you in Canada?

Autodetection fails to make the distinction between Canada-Cable and US-Cable on ATI cards. The symptoms of this sound very similar to the problems you label 2 and 3.

The solution is to add the following line

```

options bttv tuner=2
```

to /etc/modprobe.d/bttv

---

