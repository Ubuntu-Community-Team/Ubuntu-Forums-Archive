---
title: "MythExport does not work as now shipping..."
date: 2012-02-15
forum: Mythbuntu
---

### Post by RideMan on 2012-02-15
Uh-oh.  As it currently ships, "out of the box" so to speak, MythExport does not work.  I think I have figured out how to make it work, but I am not marking this [SOLVED] just yet because I still have questions about the presets, and I am hoping that there are people here who know a lot more than I do about ffmpeg and x264.  As "This doesn't freakin' work" is a pretty severe indictment of a shipping package, let me state for the record that I'm fairly certain that this is *probably* due to recent changes in ffmpeg and/or x264.  After all, I am sure this was tested before it got out!

WHAT I DID:
I activated MythExport from Mythbuntu Control Cent[er|re], and installed Medibuntu as instructed to get the new libaac support.  Then I set up MythExport using its web control...set its output directory to /var/lib/mythtv/videos, selected the high-resolution portable device preset, checked the box on a recording, and waited.

The conversion process took all of two minutes, and failed to create a file in the videos directory.  Something had to be wrong.  I know this is a fast machine, but it isn't THAT fast!

A look in /var/log/mythtv/mythexport.log revealed an error.  For the benefit of people searching for this thread, here is the error:

```
ERROR: No resulting file from ffmpeg, most likely your ffmpeg failed.  Enable debugging and test by hand. at line 453 in /usr/bin/mythexport-daemon
```

I did as it suggested.  One problem is that while debugging gives you a lot of data, the one thing that does not make it into the log is the actual ffmpeg command.  After some digging, I did find the input filename in the log, and I found the preset file I was working with.  By manually executing the ffmpeg commands I was able to get the file to encode.  As my first successful(?) encode is still in progress, I can't say for certain whether it is fixed.  But I can start the discussion.

The problem is in the preset files supplied.  They are located at:

/usr/share/mythexport/configs

The file that is getting my attention right now is:
PortableH264HighRes.pm

Here's the offending command "as shipped":

```
system("ffmpeg -i \'$self->{_inputFile}\' -y -pass 1 -an -vcodec libx264 -vpre slowfirstpass -vpre ipod640 -b 1500kb -bt 1000kb -threads 0 -s 800x480 -aspect 16:9 -f ipod \'$self->{_outputFile}$self->{_extension}\' && ffmpeg -i \'$self->{_inputFile}\' -y -pass 2 -vcodec libx264 -vpre hq -vpre ipod640 -b 1500kb -bt 1000kb -threads 0 -s 800x480 -acodec libfaac -ab 192k -ac 2 -aspect 16:9 -f ipod \'$self->{_outputFile}$self->{_extension}\'");

```

Yikes!  To make this easier to follow, I'm going to break this down by option and comment it "assembler style" to show what I did to make it work, because there were several things that generated errors in ffmpeg.

```
system("ffmpeg -i \'$self->{_inputFile}\'
               -y 
               -pass 1 
               -an 
               -vcodec libx264 
               -vpre slow           ; Changed from slowfirstpass
               -vpre ipod640 
               -b 1500k             ; Changed from 1500kb
               -bt 1000k            ; Changed from 1000kb
               -threads 0 
               -s 800x480
               -aspect 16:9 
               -f ipod 
               \'$self->{_outputFile}$self->{_extension}\' 
    && ffmpeg -i \'$self->{_inputFile}\' 
              -y 
              -pass 2 
              -vcodec libx264 
              -vpre medium          ; Changed from hq
              -vpre ipod640 
              -b 1500k              ; Changed from 1500kb
              -bt 1000k             ; Changed from 1000kb
              -threads 0 
              -s 800x480
              -acodec libfaac 
              -ab 192k 
              -ac 2 
              -aspect 16:9 
              -f ipod \'$self->{_outputFile}$self->{_extension}\'");

```

The one that I have seen plastered all over the Internet is that "kb" has to be changed to "k" because ffmpeg says so.  The other problem I had run into was that it threw an error on "-vpre slowfirstpass" saying that there was no preset file for that.  I changed that to "slow" and then changed "hq" to "medium" in the second pass for the same reason.

OUTSTANDING QUESTIONS:
Okay, so now I have settings for ffmpeg that seem to work...at least ffmpeg tries to do the conversion without throwing errors and giving up.  Sometime this evening I should actually be running automated conversions from MythExport, and I fully expect them to work.  But now I have other questions about these settings...

1) RESOLUTION
In what world is 800 x 480 a 16:9 resolution?  It seems to me that a more obvious choice for resolution would be 853x480, which would be just about right for an interlaced SD source.  Or, now that we're in a largely HD world, how about 960x540, which in addition to being (a) exactly half of 1920 x 1080 and (b) still smaller than my 1024 x 768 iPad, would by its very nature deinterlace a 1920x1080 source so that it would then scale cleanly to any resolution.  Is there a reason that these non-square resolutions (800x480) were chosen?  Is this a macroblock issue?  In that case why not 864x480? Oh, dear, how do we preserve macroblock size and resize interlaced video in an appropriate way?  976x544?

2) x264 PRESETS
I changed the presets from the apparently non-existent "slowfirstpass" to "slow" and from "hq" to "medium".  Are those the best substitute choices?

3) 2-PASS ENCODING
Is 2-pass encoding really the best option?  I'm looking at some of the information on Handbrake, which also uses ffmpeg and x264, which notes that because of "recent" (2010) improvements in x264, it's practical to use constant quality encoding, and still apply the equipment limitations.  

Any comments on tweaks that anyone has tried?  Once I get this working, I am thinking about writing my own preset based on the Handbrake presets just to see how that compares to this...

--Dave Althoff, Jr.

---

### Post by nickrout on 2012-02-15
> **RideMan said:**
> Uh-oh.  As it currently ships, "out of the box" so to speak, MythExport does not work. 

OUTSTANDING QUESTIONS:
Okay, so now I have settings for ffmpeg that seem to work...at least ffmpeg tries to do the conversion without throwing errors and giving up.  Sometime this evening I should actually be running automated conversions from MythExport, and I fully expect them to work.  But now I have other questions about these settings...

1) RESOLUTION
In what world is 800 x 480 a 16:9 resolution?  It seems to me that a more obvious choice for resolution would be 853x480, which would be just about right for an interlaced SD source.  Or, now that we're in a largely HD world, how about 960x540, which in addition to being (a) exactly half of 1920 x 1080 and (b) still smaller than my 1024 x 768 iPad, would by its very nature deinterlace a 1920x1080 source so that it would then scale cleanly to any resolution.  Is there a reason that these non-square resolutions (800x480) were chosen?  Is this a macroblock issue?  In that case why not 864x480? Oh, dear, how do we preserve macroblock size and resize interlaced video in an appropriate way?  976x544?

I believe 800x480 is the screen size of many devices, and is not far off 16:9 - remembering that most encoding software wants dimensions that are a multiple of 8 or 16.
> 
2) x264 PRESETS
I changed the presets from the apparently non-existent "slowfirstpass" to "slow" and from "hq" to "medium".  Are those the best substitute choices?
 dunno but the whole thing is clearly a result of ffmpeg randomly changing the names of their presets etc (same as the k/kb thing)> 
3) 2-PASS ENCODING
Is 2-pass encoding really the best option?  I'm looking at some of the information on Handbrake, which also uses ffmpeg and x264, which notes that because of "recent" (2010) improvements in x264, it's practical to use constant quality encoding, and still apply the equipment limitations.  I believe that would be correct> 

Any comments on tweaks that anyone has tried?  Once I get this working, I am thinking about writing my own preset based on the Handbrake presets just to see how that compares to this...

--Dave Althoff, Jr.No further comments but thanks for tracking all this down. Well  done.

Exactly what versions of ffmpeg are you using?

---

### Post by RideMan on 2012-02-15
Versions of ffmpeg and x264:  Don't know for certain; I'll check when I get home. But this is a new system,  so it's presumably the most current stable/release versions of ffmpeg, x264 and Medibuntu, as suggested by the system update mechanism.

As for this all being about seemingly random changes in ffmpeg...yeah, that's why I wanted to be careful not to indict the MythExport developer[s]. 

My second pass on my test video was running when I left for work this morning; I'll post an update once I know how it all went.

--Dave Althoff, Jr.

---

### Post by RideMan on 2012-02-22
Here's an update...

I now have a new export configuration that uses the X264 constant quality settings.  With just a little bit of tweaking, I am now getting exports of 1 hour HD tv shows that are 230-250 Mbytes.  By comparison, the original files are around 6Gb/hour, and the files generated by the "high res H264 export" as described and repaired earlier in this thread were around 700 Mb/hour.

Here's my constant-quality export config file--

/usr/share/mythexport/configs/H264CQiPad.pm:

```

#!/usr/bin/perl 

package H264CQiPad;

use ExportBase;

our @ISA = qw(ExportBase);

my $description = "Constant Quality (960x540) H264 Settings.";
my $devices = "High Resolution devices - uses H.264 High Profile (iPhone 4, iPad)";
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
     
       system("ffmpeg -i \'$self->{_inputFile}\' -y -vcodec libx264 -vpre medium -crf 28 -threads 0 -s 960x540 -acodec libfaac -ab 96k -ac 2 -aspect 16:9 -f ipod \'$self->{_outputFile}$self->{_extension}\'"); 

}

1;


```

Notice in there that I am using a quality setting of 28.  One of the things I discovered is that, counterintuitively, *higher* numbers yield apparently a lower quality setting, resulting in a smaller file.  A -crf 10 yielded a 4 Gb file!  -crf 30 gave me an even smaller file, but on the iPad I started to see compression artifacts, and the file wasn't *that much* smaller.

I honestly don't know what I am doing with ffmpeg settings.  These settings are working for me, and I am open to suggestions for improvements!

--Dave Althoff, Jr.

---

### Post by markcerv on 2012-03-23
Dave,

Thank you for your quality follow-up.  I was able to successfully do an export out to iTunes!

Mark

---

### Post by SpaceBas on 2012-04-22
> **RideMan said:**
> Here's an update...


I honestly don't know what I am doing with ffmpeg settings.  These settings are working for me, and I am open to suggestions for improvements!

--Dave Althoff, Jr.

Dave, for starters, THANK YOU!
This post led me to the solution I've been after for a year!

I'm no FFMPEG expert, but I always find when posts like these get me close to a solution, I'm inspired to learn enough to be dangerous :) 

I used your iPad.pm code as a starting point but was still hitting errors with the presets not being found. That led me to delve into ffmpeg and spend some time in #ffmpeg on freenode where some folks where nice enough to hold my hand through some testing. 

For starters, with 0.10.x builds of ffmpeg, I compiled from source today, -vpre is no longer a valid flag. The correct flag is -preset. Further, most of the preset files have gone away, since they are baked into the latest x264 (which I also compiled from source). So, for those looking in their filesystem for the libx264-medium.ffpreset file, it's no longer there... although there are still presets for libx265 (eg:[http://pastebin.com/XXz34k3k](http://pastebin.com/XXz34k3k) ) Regardless, you don't need the files BUT **you must replace -vpre with -preset**
 
The IRC gurus also suggested, for quality, setting the -crf to 25 or less. I'm experimenting with that now. They also suggested removing -f ipod if you don't need support for old video ipods... and I don't. 

So, my file differs from yours only in the nuances of the arguments in this line: 

   ```
    system("ffmpeg -i \'$self->{_inputFile}\' -y -vcodec libx264 -preset medium  -crf 25 -threads 0 -s 960x540 -acodec libfaac -ab 96k -ac 2 -aspect 16:9  \'$self->{_outputFile}$self->{_extension}\'");
```

And with those changes, mythexport is actually working :D !

I'll keep tinkering with quality settings, but I'm thrilled to have a solution here and it's all thinks to Dave's great post. Again, thank you!!!

Now, all this makes me wonder, is the MythExport package maintainer up to speed and is it being maintained? Like I said, I had this problem for a year, so it's not just something that happened with the latest ffmpeg release... and the crux of it was the -vpre when it should be -preset. I'm guessing anyone on a current release of ubuntu is facing the same issue, so how does the package even get in the repo? I'm not calling anyone out, just curious how the process works and if we can contribute these fixes somehow?

---

### Post by rhpot1991 on 2012-04-24
I'll admit I got bit with the presets on this one.  The whole reason for moving to the presets was to avoid changing the ffmpeg arguments every release.  Then the presets that I used were dropped.

There are updated configs here which should fix all your issues: [http://www.baablogic.net/mythexport/](http://www.baablogic.net/mythexport/)
There a link to this in the web interface as well.

Since no one has bothered to open a bug on this, I assumed that everyone was finding their way to the updated configs.

---

