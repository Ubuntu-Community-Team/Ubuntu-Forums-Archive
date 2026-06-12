---
title: "Nuvexport shows ffmpeg as all disabled!"
date: 2009-12-02
forum: Mythbuntu
---

### Post by Seakip18 on 2009-12-02
Howdy all, 

Not sure if this is the right place to post, but I'm almost at wits end getting my .nuv files encoded to xvid. 

When I run nuvexport, I get all the options disabled, complaining about how I did not compile with the right options...```
Using ffmpeg for exporting.
What would you like to do?

  1. Export to XviD (disabled)
  2. Export to SVCD (disabled)
  3. Export to VCD (disabled)
  4. Export to DVCD (VCD with 48kHz audio for making DVDs) (disabled)
  5. Export to DVD (disabled)
  6. Export to DivX (disabled)
  7. Export to ASF (disabled)
  8. Export to MP3 (disabled)
  9. Export to PSP (disabled)
 10. Export to MP4 (iPod) (disabled)
 11. Export to .nuv and .sql

  q. Quit

Choose a function:  1

Your ffmpeg installation doesn't support encoding to xvid.
  (It must be compiled with the --enable-libxvid option)
Your ffmpeg installation doesn't support encoding to mp3 audio.
Press ENTER to continue.

```

However, my ffmpeg definitely has this compiled with that lib, as witnessed....

```
mediacenter@mediacenter:~$ ffmpeg
FFmpeg version SVN-r20610, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 25 2009 14:43:45 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad 
--enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb 
--enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 5. 0 / 50. 5. 0
  libavcodec    52.42. 0 / 52.42. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
At least one output file must be specified

```

Sorry if the solution appears to easily. 

I've also tried using mythnuv2mkv.sh, but I keep getting another error,  ERROR mencoder may not support libx264.so.

I figure that is a whole other problem, but maybe it'll help. 

Thanks in advance!

---

### Post by nickrout on 2009-12-02
> **Seakip18 said:**
> Howdy all, 

Not sure if this is the right place to post, but I'm almost at wits end getting my .nuv files encoded to xvid. 

When I run nuvexport, I get all the options disabled, complaining about how I did not compile with the right options...```
Using ffmpeg for exporting.
What would you like to do?

  1. Export to XviD (disabled)
  2. Export to SVCD (disabled)
  3. Export to VCD (disabled)
  4. Export to DVCD (VCD with 48kHz audio for making DVDs) (disabled)
  5. Export to DVD (disabled)
  6. Export to DivX (disabled)
  7. Export to ASF (disabled)
  8. Export to MP3 (disabled)
  9. Export to PSP (disabled)
 10. Export to MP4 (iPod) (disabled)
 11. Export to .nuv and .sql

  q. Quit

Choose a function:  1

Your ffmpeg installation doesn't support encoding to xvid.
  (It must be compiled with the --enable-libxvid option)
Your ffmpeg installation doesn't support encoding to mp3 audio.
Press ENTER to continue.

```

However, my ffmpeg definitely has this compiled with that lib, as witnessed....

```
mediacenter@mediacenter:~$ ffmpeg
FFmpeg version SVN-r20610, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Nov 25 2009 14:43:45 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad 
--enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb 
--enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 5. 0 / 50. 5. 0
  libavcodec    52.42. 0 / 52.42. 0
  libavformat   52.39. 2 / 52.39. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
At least one output file must be specified

```

Sorry if the solution appears to easily. 


work out what command nuvexport is running and then run it yourself on the commandline - see what output you get.

---

### Post by klc5555 on 2009-12-03
Your ffmpeg appears to be compiled correctly, but you may not have the libraries that the executable is calling for. For xvid, you might want to check whether the libxvidcore4 package is installed and available. Likewise with the libmp3lame0 package for mp3 audio.

---

### Post by Seakip18 on 2009-12-03
Thanks for your help so far! 

I've tried figuring out how nuvexport finds and determines how ffmpeg does not have these. I'm still in the process of tracking this down, as it is a bit obfuscated in the *.pm files. 

And, of course, running nuvexport with the -debug does not yield any information when using ffmpeg. 

I've double checked and the required libraries are indeed installed. 

I've run mythrename.pl and gotten more usable names, so I have no problems using ffmpeg  to convert them via commandline....I just need to know what commands to run! 

So if you've got ffmpeg and nuvexport, run: 
```
nuvexport -debug
```

try to convert something and lemme know what commands are being run. I'll tweak it from there

---

### Post by klc5555 on 2009-12-03
Sorry I don't have any more ideas with the main problem with ffmpeg, but until you're able to get the main problem solved, the workaround of running nuvexport with the --transcode or the --mencoder switch should also allow you to do your xvids while avoiding the ffmpeg issue. 

While slower, --transcode tends to give higher quality results with xvid at the same settings than the default with ffmpeg does.

---

### Post by Seakip18 on 2009-12-03
Nuvexport, being pretty behind, doesn't seem to play well with current versions of either mencoder or transcode. It is passing deprecated flags to both of them. This results in nuvexport failing, no matter what. 

I did take the commands it was passing, removed the deprecated flags and then executed a series of commands that seemed to work, but at an abysmal ~2.5fps. 

For those interested....here's the mythtranscode command
```
mythtranscode --showprogress -p 0 -c '2010' -s '2009-12-02T21:00:00' -f "/tmp/fifodir_31742/" -v most --honorcutlist

``` to setup the fifo. Bonus points if you can guess the show :D 

and for transcode

```
transcode --progress_meter 16 --import_asr 2 --export_asr 2 --export_fps 29.970,4 -Z 512x384 -k -i /tmp/fifodir_31742/vidout -p /tmp/fifodir_31742/audout -H 0 -x raw -g 480x480 -f 29.970,4 -n 0x1 -j 6,6,6,6 -J smartyuv  -y xvid -e 48000,16,2  -N 0x55 -b 128,0,2,0 -R 2,/tmp/xvid.31742.log -w 768  -o '/var/lib/mythtv/videos/TheShow.avi'
```

then for mencoder: 
```
mencoder -aspect 1.33333333333333 -noskip -idx /tmp/fifodir_31742/vidout -audiofile /tmp/fifodir_31742/audout   -demuxer 20 -audio-demuxer 20 -rawaudio rate=48000:channels=2 -demuxer 26 -rawvideo w=480:h=480:fps=29.970      -ovc xvid  -oac mp3lame -lameopts vbr=3:br=128 -xvidencopts fixed_quant=6 -o '/var/lib/mythtv/videos/TheShow.avi' -vf crop=468:468:6:6,lavcdeint,scale=512:384
```

I tried hacking ffmpeg to work using some commands other folks have used, but instead got could not write errors.

---

### Post by JBAlaska on 2009-12-03
American Idol?

---

### Post by Seakip18 on 2009-12-03
Not quite!

Looking at the output of nuvexport, it appears that it's not getting the right audio information before passing it along to mencoder or transcode(both have empty audio parts). 

That's why when I run nuvexport with either option, i get uninitialized variable errors. 


See the following error from transcode:
```
Now encoding:  The Show
Encode started:  Thu Dec  3 13:09:16 2009
First pass...
Use of uninitialized value in join or string at /usr/share/nuvexport/export/transcode.pm line 243, <STDIN> line 15.
Use of uninitialized value in join or string at /usr/share/nuvexport/export/transcode.pm line 243, <STDIN> line 15.
Use of uninitialized value in join or string at /usr/share/nuvexport/export/transcode.pm line 243, <STDIN> line 15.
Waiting for mythtranscode to set up the fifos.
Starting transcode.
processed:  0 of 55623 frames at 0 fps (~%, eta: unknown)
transcode finished.
processed:  0 of 55623 frames at 0 fps (~%, eta: unknown)

transcode died early.Please use the --debug option to figure out what went wrong.
http://www.mythtv.org/wiki/index.php/Nuvexport#Debug_Mode

```

And it's companion error for mencoder:
```
Now encoding:  The Show
Encode started:  Thu Dec  3 13:11:41 2009
Use of uninitialized value in concatenation (.) or string at /usr/share/nuvexport/export/mencoder.pm line 104, <STDIN> line 16.
Use of uninitialized value in concatenation (.) or string at /usr/share/nuvexport/export/mencoder.pm line 104, <STDIN> line 16.
Waiting for mythtranscode to set up the fifos.
Starting mencoder.
processed:  0 of 107717 frames (0.00%), 0 fps
mencoder finished.
processed:  0 of 107717 frames (0.00%), 0 fps

mencoder died early.Please use the --debug option to figure out what went wrong.
http://www.mythtv.org/wiki/index.php/Nuvexport#Debug_Mode


Cleaning up temp files.
Cleaning up child processes.

```

The common issue? At both of the lines in the code is where the script passes the audio information(channels, sample rate, etc.)

For Transcode this is ```
243               $transcode .= " -i /tmp/fifodir_$$/vidout -p /tmp/fifodir_$$/audout"
    244                          .' -H 0 -x raw'
    245                          .' -g '.join('x', $episode->{'finfo'}{'width'}, $episode->{'finfo'}{'height'})
    246                          .' -f '.$episode->{'finfo'}{'fps'}.','
    247                          . (($episode->{'finfo'}{'fps'} =~ /^2(?:5|4\.9)/) ? 3 : 4)
    248                          .' -n 0x1'
    249                          .' -e '.join(',', $episode->{'finfo'}{'audio_sample_rate'}, $episode->{'finfo'}{'aud        io_bits_per_sample'}, $episode->{'finfo'}{'audio_channels'}
```


For mencoder, this is
```
104 $mencoder .= " -noskip -idx /tmp/fifodir_$$/vidout -audiofile /tmp/fifodir_$$/audout  "
    105                          .' -demuxer 20 -audio-demuxer 20 -rawaudio'
    106                          .' rate='.$episode->{'finfo'}{'audio_sample_rate'}.':channels='.$episode->{'finfo'}{        'audio_channels'}
    107                          .' -demuxer 26 -rawvideo'
    108                          .' w='.$episode->{'finfo'}{'width'}.':h='.$episode->{'finfo'}{'height'}
    109                          .':fps='.$episode->{'finfo'}{'fps'}
    110                          ;

```

---

### Post by FakeOutdoorsman on 2009-12-03
Nuvexport may be looking for the shared libraries for FFmpeg, so you may have to recompile FFmpeg with the additional option, *--enable-shared*.  After you install FFmpeg, update the links to your shared libraries with:
```
sudo ldconfig
```

Also, if you're on a 64-bit system, and install x264 as well, you will probably need to recompile that with *--enable-shared* as well.

I'm not sure if this will even work though.  Nuvexport might be looking for a specific version of FFmpeg's library files, and/or Nuvexport may not "see" them in /usr/local/.  Just a guess.

An alternative step would be to uninstall your compiled FFmpeg and use the one from the repository and then enable the restricted encoders:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Seakip18 on 2009-12-03
Hmmph....

I did recompile ffmpeg with --enable-shared and ran sudo ldconfig. 

Nuvexport still reports it as disabled. Older versions of ffmpeg will work as I discovered, but the nuvexport still hits the same problem: It cannot process the audio information. 

Nuvexport's last update was back in April, so I'm going to assume it's not up to date with mythtv .22. 

Looks like I'll need some sort of custom .nuv to .avi conversion script to pull this off.

---

### Post by blackoper on 2009-12-03
mythnuv2mkv seems to be what works for everyone that was having problems with the nuvexport script/conversion

see this page for setup: [http://ubuntuforums.org/showthread.php?t=1341863]("http://ubuntuforums.org/showthread.php?t=1341863")

---

### Post by Seakip18 on 2009-12-03
> **blackoper said:**
> mythnuv2mkv seems to be what works for everyone that was having problems with the nuvexport script/conversion

see this page for setup: [http://ubuntuforums.org/showthread.php?t=1341863]("http://ubuntuforums.org/showthread.php?t=1341863")


Which I initially thougt to use next....and hit yet another error. 

In my first post, it gave me an error:

```
ERROR mencoder may not support libx264.so.
```

There's nothing out there dealing with this error that I've seen and I've compiled the latest mplayer....so....yep.

---

### Post by nickrout on 2009-12-03
> **Seakip18 said:**
> Which I initially thougt to use next....and hit yet another error. 

In my first post, it gave me an error:

```
ERROR mencoder may not support libx264.so.
```

There's nothing out there dealing with this error that I've seen and I've compiled the latest mplayer....so....yep.

re ffmpeg, are you using the ubuntu version or the one from medibuntu repos? IIRC I fixed some problems with mytharchive by using the medibuntu variety.

---

### Post by Seakip18 on 2009-12-03
> **nickrout said:**
> re ffmpeg, are you using the ubuntu version or the one from medibuntu repos? IIRC I fixed some problems with mytharchive by using the medibuntu variety.

It's being compiled from the latest source via FakeOutdoorsman's guide.

---

### Post by FakeOutdoorsman on 2009-12-03
> **nickrout said:**
> re ffmpeg, are you using the ubuntu version or the one from medibuntu repos? IIRC I fixed some problems with mytharchive by using the medibuntu variety.

Medibuntu only offers a FFmpeg for Ubuntu Hardy 8.04.  Users of more recent Ubuntu versions can simply [enable the restricted encoders](http://ubuntuforums.org/showthread.php?t=1117283) using packages from the official Ubuntu repository.

---

### Post by Seakip18 on 2009-12-10
I ended up using my own script to do a two pass mencoder on them + mythrename.pl. I stripped the .nuv off the files to start as well. 

After 3 days of converting 198 episodes, the results are good enough, given the existing quality of the recordings. 

If anyone cares, this was the script:
```
#!/bin/sh

width=$1
height=$2
bitrate=$3

for f in `dir`
do
nice -n 18 mencoder $f -ni -vf scale=${width}:${height} -ofps 6000/1001 -of avi -oac mp3lame -o ../converted/$f.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=${bitrate}:vhq:vpass=1
nice -n 18 mencoder $f -ni -vf scale=${width}:${height} -ofps 6000/1001 -of avi -oac mp3lame -o ../converted/$f.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=${bitrate}:vhq:vpass=2
echo $f>>filesdone.txt
done

```
Suggestions/improvments are of course invited, but I'm sure there are much better ways of doing this Q&D convert. 

It'll try to also convert any files that aren't what we care about, but it'll of course fail to do so.

---

### Post by CoolDreamZ on 2009-12-12
I have been looking at this problem for a few hours now (including building ffmpeg from scratch!). I can confitm that even though ffmpeg is installed ok and correctly transcodes .mpg to .mp3 files **nuvexport** is showing the MP3 option as "disabled".

I have looked at the perl source code for nuvexport and */usr/local/share/nuvexport/export/ffpmeg.pm* seems to be incorrectly parsing the ffmpeg version and available formats.

Unfortunately I don't speak very good perl otherwise I would have a go at fixing it!

---

### Post by meresda on 2010-02-03
> **CoolDreamZ said:**
> I have been looking at this problem for a few hours now (including building ffmpeg from scratch!). I can confitm that even though ffmpeg is installed ok and correctly transcodes .mpg to .mp3 files **nuvexport** is showing the MP3 option as "disabled".

I have looked at the perl source code for nuvexport and */usr/local/share/nuvexport/export/ffpmeg.pm* seems to be incorrectly parsing the ffmpeg version and available formats.

Unfortunately I don't speak very good perl otherwise I would have a go at fixing it!
It seems that ffmpeg changed how they display information. To correct this, I did this in */usr/local/share/nuvexport/export/ffmpeg.pm*;

```
    # Gather the supported codecs
        $data         = `$ffmpeg -formats 2>&1`;
        my ($formats) = $data =~ /(?:^|\n\s*)File\sformats:\s*\n(.+?\n)\s*\n/s;
        if ($formats) {
            while ($formats =~ /^\s(..)\s(\S+)\b/mg) {
                $self->{'formats'}{$2} = $1;
            }
        }
# change to gather codecs
        $data2       = `$ffmpeg -codecs 2>&1`;
        my ($codecs)  = $data2 =~ /(?:^|\n\s*)Codecs:\s*\n(.+?\n)\s*\n/s;
        if ($codecs) {
            while ($codecs =~ /^\s(.{6})\s(\S+)\b/mg) {
                $self->{'codecs'}{$2} = $1;
            }
        }
    }

```
Older versions of ffmpeg seem to give formats and codecs from the ffmpeg -formats command. I added ffmpeg -codecs to specifically pull out the codecs.

---

### Post by Seakip18 on 2010-02-03
> **meresda said:**
> It seems that ffmpeg changed how they display information. To correct this, I did this in */usr/local/share/nuvexport/export/ffmpeg.pm*;

```
    # Gather the supported codecs
        $data         = `$ffmpeg -formats 2>&1`;
        my ($formats) = $data =~ /(?:^|\n\s*)File\sformats:\s*\n(.+?\n)\s*\n/s;
        if ($formats) {
            while ($formats =~ /^\s(..)\s(\S+)\b/mg) {
                $self->{'formats'}{$2} = $1;
            }
        }
# change to gather codecs
        $data2       = `$ffmpeg -codecs 2>&1`;
        my ($codecs)  = $data2 =~ /(?:^|\n\s*)Codecs:\s*\n(.+?\n)\s*\n/s;
        if ($codecs) {
            while ($codecs =~ /^\s(.{6})\s(\S+)\b/mg) {
                $self->{'codecs'}{$2} = $1;
            }
        }
    }

```
Older versions of ffmpeg seem to give formats and codecs from the ffmpeg -formats command. I added ffmpeg -codecs to specifically pull out the codecs.

Scratch that!

Turns out I had two nuvexport files. 

Doing this in the RIGHT ffmpeg.pm removed the error...though it caused an error:
```
Encode started:  Wed Feb  3 21:51:28 2010
First pass...
Waiting for mythtranscode to set up the fifos.
Starting ffmpeg.
Use of uninitialized value in numeric gt (>) at /usr/share/nuvexport/export/ffmpeg.pm line 386, <STDIN> line 15.
processed:  0 of 0 frames at 0 fps (~%, eta: unknown)

ffmpeg had critical errors:

pipe:: Error while opening file
```

Thanks so far... I think I'll look into it and see whats going on with the piping.

---

### Post by meresda on 2010-02-04
I forgot to mention that my "fix' was for FFmpeg version SVN-r21633.

---

### Post by GuiGuy on 2010-02-14
> **blackoper said:**
> mythnuv2mkv seems to be what works for everyone that was having problems with the nuvexport script/conversion

see this page for setup: [http://ubuntuforums.org/showthread.php?t=1341863]("http://ubuntuforums.org/showthread.php?t=1341863")

Yea, but is is so ssssllllooooowwwww.........

---

### Post by eldragon on 2010-02-22
i editied the ffmpeg.pm file, and hardcoded it to always return 1 with the 'can_encode' subroutine.

this is around line 130.

```

#        return ($self->{'codecs'}{$codec} && $self->{'codecs'}{$codec} =~ /    ^.E/
#               || $self->{'formats'}{$codec} && $self->{'formats'}{$codec}     =~ /^.E/) ? 1 : 0;
   return 1 #hardcoded. make sure you can actually encode

```

---

### Post by dsauxier on 2010-07-31
Switching to mythnuv2kv.sh : [http://web.aanet.com.au/~auric/?q=node/6](http://web.aanet.com.au/~auric/?q=node/6)
Had to install mencoder faac vorbis-tools mkvtoolnix

---

