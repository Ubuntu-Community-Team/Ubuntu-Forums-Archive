---
title: "DVD ripper"
date: 2011-03-25
forum: Multimedia Software
---

### Post by Jagoly on 2011-03-25
I'm sure it's probably already been answered, but I can't find it in the searches. Whats a good DVD ripper for Linux?

I AM NOT A PIRATE. I WANT TO RIP DVD'S TO PUT THEM ON MY IPOD.

Something supporting copy protected, very high quality, archive style ripping, to then be converted with other programs for specific purposes. Does such free software exist? Thanks for any info.

---

### Post by rgb1701 on 2011-03-25
Your real choices are MakeMKV (Linux) or DVDFab (under Wine)

[http://www.makemkv.com/](http://www.makemkv.com/)

[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

[http://www.dvdfab.com/download.htm](http://www.dvdfab.com/download.htm)

The best DVD ripper is DVDfab. Just download the .exe and double click to install just like on Windows, after you install Wine first-

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

There are several FOSS DVD rippers like K9copy and others, but they are not updated often enough to handle the latest disc releases.

---

### Post by Ghost_Mazal on 2011-04-24
This is a real problem for me as well. I just can't find any tool for Ubuntu that actually works. All I want is to rip the DVD to HDD in Folder structure form without any encoding. But nothing works.

K9 just keeps crashing , DVD::Rip wants to do encoding and Handbrake as well is for encoding.

Is there anything in Ubuntu that can rip the video DVD structure to HDD that actually works ?

---

### Post by kelvin spratt on 2011-04-24
dvdcopy, dvd95, these will rip to hardrive

---

### Post by vdubguy on 2011-04-24
I use handBrake. Works on every dvd i have ever wanted to backup. Will also rip to iPod format.

[http://handbrake.fr/](http://handbrake.fr/)

Try this.

```
sudo add-apt-repository ppa:stebbins/handbrake-releases

sudo apt-get update
```Then hit the package manager for the install.

Make sure you get both from the package manager

Handbrake-cli
Handbrake-glk

---

### Post by Jagoly on 2011-04-24
I have handbrake. I've used it for two years for converting stuff to iPod format, even back in the dark ages when I used Windows. Handbrake never works for any of my copy-protected DVD's. It either will read the DVD for ever, or output a useless jumble. Also k9copy does the same thing.

---

### Post by Ghost_Mazal on 2011-04-25
I already said that Handbrake is not an option because it encodes to another format

---

### Post by Jagoly on 2011-04-25
> **Ghost_Mazal said:**
> I already said that Handbrake is not an option because it encodes to another format

If you just want the folder structure on the hdd, why not use brasero? By the way, I am the OP and handbrake can rip to as high a quality as you like. If it could rip copy protected DVD's, it would be perfect.

---

### Post by Ghost_Mazal on 2011-04-25
How can Brasero rip the folder structure ? You mean make an .iso image ? That won't work for me , my convertion scripts needs the VOB files

---

### Post by Ghost_Mazal on 2011-04-25
> **zonezo786 said:**
> CXB DVD Ripper is excellent DVD ripping software which helps you convert  DVD to various video and audio formats like DVD to MKV, MP4, AVI, DivX,  XviD, WMV, VCD, WMA, and MP3 with amazing sound and image quality.

Can it rip without encoding ?

---

### Post by Elfy on 2011-04-25
> **Ghost_Mazal said:**
> Can it rip without encoding ?

They'll not answer - they were spamming.

---

### Post by handy on 2011-04-25
I've used DVDShrink via Wine for over 5 years on Linux. It does a great job of ripping DVD's, & it is so simple to use.

Occasionally a DVD couldn't be ripped with DVDShrink, so I would use SmartRipper, via Wine. It is slightly more complicated to use, & has some other options that DVDShrink does not.

Then there were the rarely complicated copy protected DVD's that I had to use DVD Fab Decryptor on.

Over the last year I have been using HandBrakeCLI. It has never let me down. I choose to make .mp4 files, it will also make .mkv .

Here are the currently available options, you will see that it deals with iPod's too:

> handy ~  $  hbhelp
Syntax: HandBrakeCLI [options] -i <device> -o <file>

### General Handbrake Options------------------------------------------------

    -h, --help              Print help
    -u, --update            Check for updates and exit
    -v, --verbose <#>       Be verbose (optional argument: logging level)
    -C, --cpu               Set CPU count (default: autodetected)
    -Z. --preset <string>   Use a built-in preset. Capitalization matters, and
                            if the preset name has spaces, surround it with
                            double quotation marks
    -z, --preset-list       See a list of available built-in presets
        --no-dvdnav         Do not use dvdnav for reading DVDs
                            (experimental, enabled by default for testing)

### Source Options-----------------------------------------------------------

    -i, --input <string>    Set input device
    -t, --title <number>    Select a title to encode (0 to scan all titles only,
                            default: 1)
        --scan              Scan selected title only.
        --main-feature      Detect and select the main feature title.
    -c, --chapters <string> Select chapters (e.g. "1-3" for chapters
                            1 to 3, or "3" for chapter 3 only,
                            default: all chapters)
        --angle <number>    Select the DVD angle
        --previews <#:B>    Select how many preview images are generated (max 30),
                            and whether or not they're stored to disk (0 or 1).
                            (default: 10:0)
    --start-at-preview <#>  Start encoding at a given preview.
    --start-at    <unit:#>  Start encoding at a given frame, duration (in seconds),
                            or pts (on a 90kHz clock)
    --stop-at     <unit:#>  Stop encoding at a given frame, duration (in seconds),
                            or pts (on a 90kHz clock)
### Destination Options------------------------------------------------------

    -o, --output <string>   Set output file name
    -f, --format <string>   Set output format (mp4/mkv, default:
                            autodetected from file name)
    -m, --markers           Add chapter markers (mp4 and mkv output formats only)
    -4, --large-file        Use 64-bit mp4 files that can hold more than
                            4 GB. Note: Breaks iPod, PS3 compatibility.
    -O, --optimize          Optimize mp4 files for HTTP streaming
    -I, --ipod-atom         Mark mp4 files so 5.5G iPods will accept them

### Video Options------------------------------------------------------------

    -e, --encoder <string>  Set video library encoder (ffmpeg,x264,theora)
                            (default: ffmpeg)
    -x, --x264opts <string> Specify advanced x264 options in the
                            same style as mencoder:
                            option1=value1:option2=value2
    -q, --quality <number>  Set video quality
    -S, --size <MB>         Set target size
    -b, --vb <kb/s>         Set video bitrate (default: 1000)
    -2, --two-pass          Use two-pass mode
    -T, --turbo             When using 2-pass use the turbo options
                            on the first pass to improve speed
                            (only works with x264, affects PSNR by about 0.05dB,
                            and increases first pass speed two to four times)
    -r, --rate              Set video framerate (5/10/12/15/23.976/24/25/29.97)
                            Be aware that not specifying a framerate lets
                            HandBrake preserve a source's time stamps,
                            potentially creating variable framerate video
    --vfr, --cfr, --pfr     Select variable, constant or peak-limited
                            frame rate control. VFR preserves the source
                            timing. CFR makes the output constant rate at
                            the rate given by the -r flag (or the source's
                            average rate if no -r is given). PFR doesn't
                            allow the rate to go over the rate specified
                            with the -r flag but won't change the source
                            timing if it's below that rate.
                            If none of these flags are given, the default
                            is --cfr when -r is given and --vfr otherwise

### Audio Options-----------------------------------------------------------

    -a, --audio <string>    Select audio track(s), separated by commas
                            More than one output track can be used for one
                            input.
                            ("none" for no audio, "1,2,3" for multiple
                             tracks, default: first one)
    -E, --aencoder <string> Audio encoder(s):
                                (faac/lame/vorbis/ac3/copy/copy:ac3/copy:dts)
                            copy, copy:ac3 and copy:dts meaning passthrough.
                            copy will passthrough either ac3 or dts.
                            Separated by commas for more than one audio track.
                            (default: faac for mp4, lame for mkv)
    -B, --ab <kb/s>         Set audio bitrate(s) (default: depends on the
                            selected codec, mixdown and samplerate)
                            Separated by commas for more than one audio track.
    -6, --mixdown <string>  Format(s) for surround sound downmixing
                            Separated by commas for more than one audio track.
                            (mono/stereo/dpl1/dpl2/6ch, default: up to 6ch for ac3,
                            up to dpl2 for other encoders)
    -R, --arate             Set audio samplerate(s) (22.05/24/32/44.1/48 kHz)
                            Separated by commas for more than one audio track.
    -D, --drc <float>       Apply extra dynamic range compression to the audio,
                            making soft sounds louder. Range is 1.0 to 4.0
                            (too loud), with 1.5 - 2.5 being a useful range.
                            Separated by commas for more than one audio track.
    -A, --aname <string>    Audio track name(s),
                            Separated by commas for more than one audio track.

### Picture Settings---------------------------------------------------------

    -w, --width <number>    Set picture width
    -l, --height <number>   Set picture height
        --crop <T:B:L:R>    Set cropping values (default: autocrop)
    -Y, --maxHeight <#>     Set maximum height
    -X, --maxWidth <#>      Set maximum width
    --strict-anamorphic     Store pixel aspect ratio in video stream
    --loose-anamorphic      Store pixel aspect ratio with specified width
    --custom-anamorphic     Store pixel aspect ratio in video stream and
                            directly control all parameters.
    --display-width         Set the width to scale the actual pixels to
      <number>              at playback, for custom anamorphic.
    --keep-display-aspect   Preserve the source's display aspect ratio
                            when using custom anamorphic
    --pixel-aspect          Set a custom pixel aspect for custom anamorphic
      <PARX:PARY>
                            (--display-width and --pixel-aspect are mutually
                             exclusive and the former will override the latter)
    --itu-par               Use wider, ITU pixel aspect values for loose and
                            custom anamorphic, useful with underscanned sources
    --modulus               Set the number you want the scaled pixel dimensions
      <number>              to divide cleanly by. Does not affect strict
                            anamorphic mode, which is always mod 2 (default: 16)
    -M  --color-matrix      Set the color space signaled by the output
          <601 or 709>      (Bt.601 is mostly for SD content, Bt.709 for HD,
                             default: set by resolution)

### Filters---------------------------------------------------------

    -d, --deinterlace       Deinterlace video with yadif/mcdeint filter
          <YM:FD:MM:QP>     (default 0:-1:-1:1)
           or
          <fast/slow/slower>
    -5, --decomb            Selectively deinterlaces when it detects combing
          <MO:ME:MT:ST:BT:BX:BY:MG:VA:LA:DI:ER:NO:MD:PP:FD>
          (default: 7:2:6:9:80:16:16:10:20:20:4:2:50:24:1:-1)
    -9, --detelecine        Detelecine (ivtc) video with pullup filter
                            Note: this filter drops duplicate frames to
                            restore the pre-telecine framerate, unless you
                            specify a constant framerate (--rate 29.97)
          <L:R:T:B:SB:MP:FD>   (default 1:1:4:4:0:0:-1)
    -8, --denoise           Denoise video with hqdn3d filter
          <SL:SC:TL:TC>     (default 4:3:6:4.5)
           or
          <weak/medium/strong>
    -7, --deblock           Deblock video with pp7 filter
          <QP:M>            (default 5:2)
        --rotate            Flips images axes
          <M>               (default 3)
    -g, --grayscale         Grayscale encoding

### Subtitle Options------------------------------------------------------------

    -s, --subtitle <string> Select subtitle track(s), separated by commas
                            More than one output track can be used for one
                            input.
                            Example: "1,2,3" for multiple tracks.
                            A special track name "scan" adds an extra 1st pass.
                            This extra pass scans subtitles matching the
                            language of the first audio or the language 
                            selected by --native-language.
                            The one that's only used 10 percent of the time
                            or less is selected. This should locate subtitles
                            for short foreign language segments. Best used in
                            conjunction with --subtitle-forced.
    -F, --subtitle-forced   Only display subtitles from the selected stream if
          <string>          the subtitle has the forced flag set. The values in
                            "string" are indexes into the subtitle list
                            specified with '--subtitle'.
                            Separated by commas for more than one audio track.
                            Example: "1,2,3" for multiple tracks.
                            If "string" is omitted, the first track is forced.
        --subtitle-burn     "Burn" the selected subtitle into the video track
          <number>          If "number" is omitted, the first track is burned.
                            "number" is an index into the subtitle list
                            specified with '--subtitle'.
        --subtitle-default  Flag the selected subtitle as the default subtitle
          <number>          to be displayed upon playback.  Setting no default
                            means no subtitle will be automatically displayed
                            If "number" is omitted, the first track is default.
                            "number" is an index into the subtitle list
                            specified with '--subtitle'.
    -N, --native-language   Specifiy the your language preference. When the first
          <string>          audio track does not match your native language then
                            select the first subtitle that does. When used in
                            conjunction with --native-dub the audio track is
                            changed in preference to subtitles. Provide the
                            language's iso639-2 code (fre, eng, spa, dut, et cetera)
        --native-dub        Used in conjunction with --native-language
                            requests that if no audio tracks are selected the
                            default selected audio track will be the first one
                            that matches the --native-language. If there are no
                            matching audio tracks then the first matching
                            subtitle track is used instead.
        --srt-file <string> SubRip SRT filename(s), separated by commas.
        --srt-codeset       Character codeset(s) that the SRT file(s) are
          <string>          encoded in, separted by commas.
                            Use 'iconv -l' for a list of valid
                            codesets. If not specified latin1 is assumed
        --srt-offset        Offset in milli-seconds to apply to the SRT file(s)
          <string>          separted by commas. If not specified zero is assumed.
                            Offsets may be negative.
        --srt-lang <string> Language as an iso639-2 code fra, eng, spa et cetera)
                            for the SRT file(s) separated by commas. If not specified
                            then 'und' is used.
        --srt-default       Flag the selected srt as the default subtitle
          <number>          to be displayed upon playback.  Setting no default
                            means no subtitle will be automatically displayed
                            If "number" is omitted, the first srt is default.
                            "number" is an 1 based index into the srt-file list

handy ~  $  

---

### Post by vdubguy on 2011-04-25
> **Jagoly said:**
> I have handbrake. I've used it for two years for converting stuff to iPod format, even back in the dark ages when I used Windows. Handbrake never works for any of my copy-protected DVD's. It either will read the DVD for ever, or output a useless jumble. Also k9copy does the same thing.

Thats weird,it works for EVERYTHING for me. Even the newest copy-protected DVD's. I can not speak for k9copy I have never used it.

---

### Post by Ghost_Mazal on 2011-04-25
How do you actually install DVDshrink with wine ? I have downloaded it , marked it executable and choose "Open with wine".

It says "opening" for a while and closes without anything happening ?

---

### Post by Jagoly on 2011-04-25
OMG I just remembered that I have Blundows 7 in a VirtualBox :redface:

---

### Post by handy on 2011-04-25
> **Ghost_Mazal said:**
> How do you actually install DVDshrink with wine ? I have downloaded it , marked it executable and choose "Open with wine".

It says "opening" for a while and closes without anything happening ?

I used the Terminal, "cd" into the directory holding dvdshrink32setup.exe then type the following at the bash prompt (without the quotes):

**$  "wine dvdshrink32setup.exe"**

I don't do anything with permissions to the installation file or the installed DVDShrink.exe file, which is installed in my /home/handy/.wine/ <blah, blah> directory ready for me to use.

---

### Post by VanillaMozilla on 2011-04-26
Just open the disk and copy the files.  It really is as simple as that (usually).  No ripping program needed.

---

### Post by handy on 2011-04-26
> **VanillaMozilla said:**
> Just open the disk and copy the files.  It really is as simple as that (usually).  No ripping program needed.

Not where I live it isn't. Very few DVD's don't at least use the Content Scrambling System (CSS).

Apart from doing away with that, DVDShrink, amongst the many others, removes the region code (if you tell it to) & shrinks 8GB dual layer DVD movies down to 4.3GB single layer DVD size which saves people money on media if they want to be able to watch the DVD in a standard player.

If you are archiving movies onto a HDD, then personally, I've found nothing more effective than HandBrakeCLI. Which allows you to set the level of compression; if you want subtitles or not, & if need be, which titles you want off, of the DVD. You can also easily add subtitles found on the web into the same directory as the .mp4 or .mkv file & use them.

---

### Post by Jagoly on 2011-04-27
Will HBcli work if HBgui doesn't? I thought that they were the same thing, bar the interface.

---

### Post by thinmintaddict on 2011-04-27
Maybe I'm missing something, but if you just need the vob files in proper folder structure, why not just use vobcopy from the command line?

---

### Post by Ghost_Mazal on 2011-04-27
> **thinmintaddict said:**
> Maybe I'm missing something, but if you just need the vob files in proper folder structure, why not just use vobcopy from the command line?

I tried vobcopy , but it's DREADFULLY slow. Takes hours just to rip 1 dvd

---

### Post by handy on 2011-04-27
> **Jagoly said:**
> Will HBcli work if HBgui doesn't? I thought that they were the same thing, bar the interface.

I've never used HBgui. I expect that it is possible that there is more control available via the CLI, but I'm only guessing.

I've had HBcli work when the others fail. So all in all I'm pretty impressed with it.

Here is a link to a how-to thread I started. It is a little messy but you'll get the idea that it really isn't so hard to use the non-gui version of HandBrake:

[http://spiralinear.org/forum/viewtopic.php?f=17&t=21](http://spiralinear.org/forum/viewtopic.php?f=17&t=21)

---

### Post by inobe on 2011-04-27
> **Ghost_Mazal said:**
> I tried vobcopy , but it's DREADFULLY slow. Takes hours just to rip 1 dvd

are you trying it on a netbook, or that beast of yours with the e6850?

come on man, hours?

---

### Post by Ghost_Mazal on 2011-04-27
> **inobe said:**
> are you trying it on a netbook, or that beast of yours with the e6850?

come on man, hours?

Nope it was on my laptop.

I'm serious man , it was like 1mb per minute stuff.
It baffled me completely.

---

### Post by inobe on 2011-04-27
not sure if it's what you want, arista should be in software manager, set dewice to dvd player and preset to ntsc dvd.

or you can just choose ipod device.

i really don't know, also your beast system would be best, i have the same chip, it rips in minutes.

---

### Post by Ghost_Mazal on 2011-04-27
> **inobe said:**
> not sure if it's what you want, arista should be in software manager, set dewice to dvd player and preset to ntsc dvd.

or you can just choose ipod device.

i really don't know, also your beast system would be best, i have the same chip, it rips in minutes.

Arista doesn't work either. I add the job to the que and then nothing happens further. It just sits there. No start or go buttons or anything.

---

### Post by inobe on 2011-04-27
i think you are missing some restricted dependencies, these apps are nothing without certain libs "libraries" these apps are just front ends.

read here [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/) to get an idea what you need.


you may want to read this [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Ghost_Mazal on 2011-04-27
> **inobe said:**
> i think you are missing some restricted dependencies, these apps are nothing without certain libs "libraries" these apps are just front ends.

read here [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/) to get an idea what you need.


you may want to read this [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Nope that's not it. Restricted extras is one of the first things I always install.

---

### Post by inobe on 2011-04-27
> **Ghost_Mazal said:**
> Nope that's not it. Restricted extras is one of the first things I always install.

ubuntu-restricted-extras ?

---

### Post by inobe on 2011-04-27
lets play show and tell, except the other way around, you tell and i'll show :P

what restricted extras have you installed, tell me all the things you installed to get this working besides ripping apps, and i will tell you what you are missing :)

i don't mean to be selfish, but everything is working peachy here.

---

### Post by JohnAStebbins on 2011-04-27
```

sudo apt-get install libdvdread4
sudo apt-get install libdvdnav4
sudo /usr/share/doc/libdvdread4/install-css.sh

```

---

### Post by inobe on 2011-04-27
> **JohnAStebbins said:**
> ```

sudo apt-get install libdvdread4
sudo apt-get install libdvdnav4
sudo /usr/share/doc/libdvdread4/install-css.sh

```

that'll work great for playing a dvd, but i don't see anywhere in the thread stating someone wants to play a dvd, in fact the topic title is an example :)

---

### Post by JohnAStebbins on 2011-04-27
> **inobe said:**
> that'll work great for playing a dvd, but i don't see anywhere in the thread stating someone wants to play a dvd, in fact the topic title is an example :)

If you want to rip dvd's you have to "play" them.  HandBrake will not be able to transcode a dvd without libdvdcss.

---

### Post by Ghost_Mazal on 2011-04-28
> **inobe said:**
> lets play show and tell, except the other way around, you tell and i'll show :P

what restricted extras have you installed, tell me all the things you installed to get this working besides ripping apps, and i will tell you what you are missing :)

i don't mean to be selfish, but everything is working peachy here.

Restrcited extras , libdvdcss2 , libdvdread , libdvdnav

I also added other encoding things like ffmpeg , faac , x264 , mencoder. (Although none of these is needed for ripping a dvd structure. That top 4 is all that should be needed)

These are the things I always install first on my fresh installs.

---

### Post by Seattleite on 2011-04-28
Hey everyone, I hope it's okay to post here, as this is my first go. It's relevant to the topic, but more of a question, than anything I can contribute...

I used to have a setup with Ubuntu 10.10 and had Handbrake installed, and working like a dream ripping all my DVDs to 1024MB each (I've got a few hundred DVDs, and I wanted to have good quality rips). I have since lost that installation (moved to SSD for my desktop) and with it, I seem to have lost the ability to adjust the desired file size in Handbrake.

I'm using Ubuntu Tweak to add the required repositories, and packages, just as I did before, but when I go to rip the DVD, I can't for the life of me adjust the desired file size no matter what I try. Did they change it in an update? Am I missing a checkbox somewhere (not the one right next to 'file size' in the GUI, I got that one)? If anyone could please help, I would greatly appreciate it, I still have a couple hundred DVDs left to go, and Ubuntu made it so easy to do with Handbrake.

Thanks ahead of time for any help, and if this is posted in the wrong place, please don't flame, just tell me where I should go to get the help I need.

Take care!

---

### Post by Ghost_Mazal on 2011-04-28
> **inobe said:**
> not sure if it's what you want, arista should be in software manager, set dewice to dvd player and preset to ntsc dvd.

or you can just choose ipod device.

i really don't know, also your beast system would be best, i have the same chip, it rips in minutes.

Inobe , here something interesting. I saw the setting "Playstation 3" in Arista and tried it out. That works perfectly. Rips and encodes to a single mp4 files. And ok speed as well. Took about 48min on a 105min dvd which is normal about. Not what I need , but that works. When I put Arista on "dvdplayer" then it freezes again and does nothing. strange.

But for people who do want encoding with your ripping , check out this Arista. The easiest 3 click encoding I saw yet. Even easier than Handbrake.

Now if I can just get a ripper to rip dvd structure.

---

### Post by mc4man on 2011-04-28
> **Ghost_Mazal said:**
> I tried vobcopy , but it's DREADFULLY slow. Takes hours just to rip 1 dvd
If your title has structure protection that inc. unreadable sectors then vobcopy can take a long time depending on the number of those sectors, so in those cases not usually a suitable method 
(typically from a couple of hundred to several thousand, the default for vobcopy is 9 re-tries per so the time can add up, plus many drives will slow down after repeated read errors to a min 'rip' speed

---

### Post by JohnAStebbins on 2011-04-28
> **Seattleite said:**
> Hey everyone, I hope it's okay to post here, as this is my first go. It's relevant to the topic, but more of a question, than anything I can contribute...

I used to have a setup with Ubuntu 10.10 and had Handbrake installed, and working like a dream ripping all my DVDs to 1024MB each (I've got a few hundred DVDs, and I wanted to have good quality rips). I have since lost that installation (moved to SSD for my desktop) and with it, I seem to have lost the ability to adjust the desired file size in Handbrake.

I'm using Ubuntu Tweak to add the required repositories, and packages, just as I did before, but when I go to rip the DVD, I can't for the life of me adjust the desired file size no matter what I try. Did they change it in an update? Am I missing a checkbox somewhere (not the one right next to 'file size' in the GUI, I got that one)? If anyone could please help, I would greatly appreciate it, I still have a couple hundred DVDs left to go, and Ubuntu made it so easy to do with Handbrake.

Thanks ahead of time for any help, and if this is posted in the wrong place, please don't flame, just tell me where I should go to get the help I need.

Take care!

If you lost the target file size option, then you must be using the snapshot builds rather than the 0.9.5 release build.  Yes, target file size was removed from current code.  It often didn't work right, and new features that we would like to add would have made it even more unreliable (e.g. variable bitrate audio).  If you really need target file size (99.9% of people who think they do are mistaken) the general formula is:

total bitrate = target size / movie duration

Then you divvy up that total bitrate between your audio and video tracks.

---

### Post by handy on 2011-04-28
I use HandBrakeCLI. Once you have your settings (the hardest part of the whole thing, you save them in ~/.bashrc so that you can call them up by using a simple alias.

This is what I use in my .bashrc:

```
alias .tmp="cd /mnt/store/pkg/vid/.tmp"

alias hb="echo HandBrakeCLI -t --main-feature -i /media/dvd -o NAME.HERE.mp4 -e x264 -b 1000 -B 192 -s 1 --subtitle-burn"

alias hbt="echo HandBrakeCLI -t <title number here> -i /media/dvd -o NAME-HERE.mp4 -e x264 -b 1000 -B 192 -s 1 --subtitle-burn"

alias hbhelp="HandBrakeCLI --help"
```

When I use the alias "hb" to call its associated command line, it fails, allowing me to then copy the failed command to the prompt & use it (with or without modification).

This method saves me, with my weak memory having to reinvent the wheel every time I want to use HandBrakeCLI. 

You would have noticed that the first alias, ".tmp" changes directory to where I want the output from HandBrakeCLI initially stored.

I have backed up hundreds of DVD's using this method & the above settings, which give me .mp4 files approx' 1GB in size, with English subtitles if they exist on the disk. 

HB-CLI has never given me a bad video file & will work (as I noticed the other day) when DVDShrink won't. So all in all I'm thoroughly impressed with its quality. As an additional bonus it loves multi-core CPU's & uses all of the cores very intelligently.

---

### Post by Jagoly on 2011-10-15
Spam in a can!!!

---

