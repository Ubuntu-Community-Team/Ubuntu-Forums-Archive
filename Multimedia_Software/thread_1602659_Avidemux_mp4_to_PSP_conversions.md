---
title: "Avidemux mp4 to PSP conversions"
date: 2010-10-21
forum: Multimedia Software
---

### Post by migs73 on 2010-10-21
Anybody know how to do this??

I never had any problems with Karmic (just used to set the auto PSP setting) , but every attempt I make now seems to end in Unsupported data in my PSP.
I have made the changes to the XML doc mentioned here;
[http://ubuntuforums.org/showthread.php?t=1573354](http://ubuntuforums.org/showthread.php?t=1573354)

I have restricted extras, medibuntu and the libavcodec package.

I am using Avidemux version 2.5.3 from the repos.

HELP??:confused:

---

### Post by 12apennachi on 2010-10-21
I had the same exact problem a few days ago. I tried everything on every forum but couldn't get it to work. I eventually just gave up and found it easiest to use psp video 9 on windows. I was told it would run on wine but I never tried.

---

### Post by migs73 on 2010-10-21
> **12apennachi said:**
> I had the same exact problem a few days ago. I tried everything on every forum but couldn't get it to work. I eventually just gave up and found it easiest to use psp video 9 on windows. I was told it would run on wine but I never tried.
Encoding video on my single core low powered laptop takes long enough without adding wine (or a VM, I have vista on VM) into the mix.
Never mind it may be my final option, although annoying as the mp4 I am trying to convert is in .mov (quicktime) format, so is already mp4/aac, just needs tweaking for the PSP I think.

:(

---

### Post by migs73 on 2010-10-25
Bump.

I also tried just converting the file into mp4-AVC and AAC (faac), my PSP recognised the file, but could not play it. I assume this was due to the screen resolution being too high.
Why have a PSP auto button that doesn't auto select everything right :confused:

EDIT; just tried to alter the screen resolution, but it is already 480x272???????

Is there any other app out there that can do this for Linux?

---

### Post by migs73 on 2010-10-25
Just found Arista Transcoder in the USC. Giving it a go now, will let you know how it turns out.

---

### Post by migs73 on 2010-10-25
Same sort of result :(

Corrupted data if I give it a .mp4 extension, remove it and I get unsupported file format :(

Must be problem in the libraries for Maverick?

EDIT now trying Transmageddon.

---

### Post by migs73 on 2010-10-25
Well tried that. Only has an auto setting so used that (for PSP).
Took a while to encode, encoded it at a resolution of 320x182 (not great). Copied to PSP , 
file not reported as corrupted :) 
file not reported as being of wrong file type :) 
Pressed play......'This video cannot be played' :(
I never had a problem in karmic (using avidemux) never actually tried any in Lucid.

Anybody got any other ideas??? PLEASE!!!!

---

### Post by bluekarasu on 2010-10-25
Avidemux never was very stable nor produce perfectly "standard" files.
Perhaps you'll get more luck with Handbrake.
You can try an ipod profile, and maybe you'll find a psp profile in the hadrake website : [http://handbrake.fr/](http://handbrake.fr/)

---

### Post by JohnAStebbins on 2010-10-25
> **bluekarasu said:**
> Avidemux never was very stable nor produce perfectly "standard" files.
Perhaps you'll get more luck with Handbrake.
You can try an ipod profile, and maybe you'll find a psp profile in the hadrake website : [http://handbrake.fr/](http://handbrake.fr/)
If you decide to give HandBrake a try, here's a PSP preset you can import.
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<array>
    <dict>
        <key>AudioList</key>
        <array>
            <dict>
                <key>AudioBitrate</key>
                <string>128</string>
                <key>AudioEncoder</key>
                <string>AAC (faac)</string>
                <key>AudioEncoderActual</key>
                <string>faac</string>
                <key>AudioMixdown</key>
                <string>Dolby Pro Logic II</string>
                <key>AudioSamplerate</key>
                <string>Same as source</string>
                <key>AudioTrack</key>
                <integer>1</integer>
                <key>AudioTrackDRCSlider</key>
                <real>0</real>
                <key>AudioTrackDescription</key>
                <string>English (AC3) (5.1 ch)</string>
            </dict>
        </array>
        <key>ChapterMarkers</key>
        <true />
        <key>Default</key>
        <false />
        <key>FileFormat</key>
        <string>MP4 file</string>
        <key>Folder</key>
        <false />
        <key>Mp4HttpOptimize</key>
        <false />
        <key>Mp4LargeFile</key>
        <false />
        <key>Mp4iPodCompatible</key>
        <false />
        <key>PictureAutoCrop</key>
        <true />
        <key>PictureBottomCrop</key>
        <integer>58</integer>
        <key>PictureDeblock</key>
        <integer>4</integer>
        <key>PictureDecomb</key>
        <integer>0</integer>
        <key>PictureDecombCustom</key>
        <string></string>
        <key>PictureDecombDeinterlace</key>
        <true />
        <key>PictureDeinterlace</key>
        <integer>0</integer>
        <key>PictureDeinterlaceCustom</key>
        <string></string>
        <key>PictureDenoise</key>
        <integer>0</integer>
        <key>PictureDenoiseCustom</key>
        <string></string>
        <key>PictureDetelecine</key>
        <integer>0</integer>
        <key>PictureDetelecineCustom</key>
        <string></string>
        <key>PictureHeight</key>
        <integer>272</integer>
        <key>PictureKeepRatio</key>
        <true />
        <key>PictureLeftCrop</key>
        <integer>2</integer>
        <key>PictureLooseCrop</key>
        <false />
        <key>PictureModulus</key>
        <string>16</string>
        <key>PicturePAR</key>
        <string>0</string>
        <key>PicturePARHeight</key>
        <integer>1</integer>
        <key>PicturePARWidth</key>
        <integer>1</integer>
        <key>PictureRightCrop</key>
        <integer>2</integer>
        <key>PictureTopCrop</key>
        <integer>58</integer>
        <key>PictureWidth</key>
        <integer>480</integer>
        <key>PresetBuildNumber</key>
        <integer>2010062701</integer>
        <key>PresetDescription</key>
        <string>HandBrake&apos;s settings for all iPhones and iPod Touches going back to the original iPhone 2G.</string>
        <key>PresetName</key>
        <string>PSP</string>
        <key>SubtitleList</key>
        <array>
        </array>
        <key>Type</key>
        <integer>1</integer>
        <key>UsesPictureFilters</key>
        <integer>1</integer>
        <key>UsesPictureSettings</key>
        <integer>1</integer>
        <key>VideoAvgBitrate</key>
        <integer>960</integer>
        <key>VideoEncoder</key>
        <string>H.264 (x264)</string>
        <key>VideoFramerate</key>
        <string>Same as source</string>
        <key>VideoFrameratePFR</key>
        <false />
        <key>VideoGrayScale</key>
        <false />
        <key>VideoQualitySlider</key>
        <real>25</real>
        <key>VideoQualityType</key>
        <integer>2</integer>
        <key>VideoTargetSize</key>
        <integer>700</integer>
        <key>VideoTurboTwoPass</key>
        <false />
        <key>VideoTwoPass</key>
        <false />
        <key>anamorphic</key>
        <true />
        <key>par_height</key>
        <integer>0</integer>
        <key>par_width</key>
        <integer>0</integer>
        <key>x264Option</key>
        <string>cabac=0:ref=2:bframes=0:8x8dct=0:vbv-maxrate=2000:vbv-bufsize=2000</string>
    </dict>
</array>
</plist>

```

---

### Post by migs73 on 2010-10-26
Thanks Guys, I'll give that a try.

I don't understand how I never had any problems wit Avidemux in Karmic, but now all the transcoders I could find in the repo have similar problems. I assume they all use shared libraries and/or ffmpeg, so was beggining to think it was problems there.

I'll let you know how I get on.

---

### Post by migs73 on 2010-10-27
> **JohnAStebbins said:**
> If you decide to give HandBrake a try, here's a PSP preset you can import.
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<array>
    <dict>
        <key>AudioList</key>
        <array>
            <dict>
                <key>AudioBitrate</key>
                <string>128</string>
                <key>AudioEncoder</key>
                <string>AAC (faac)</string>
                <key>AudioEncoderActual</key>
                <string>faac</string>
                <key>AudioMixdown</key>
                <string>Dolby Pro Logic II</string>
                <key>AudioSamplerate</key>
                <string>Same as source</string>
                <key>AudioTrack</key>
                <integer>1</integer>
                <key>AudioTrackDRCSlider</key>
                <real>0</real>
                <key>AudioTrackDescription</key>
                <string>English (AC3) (5.1 ch)</string>
            </dict>
        </array>
        <key>ChapterMarkers</key>
        <true />
        <key>Default</key>
        <false />
        <key>FileFormat</key>
        <string>MP4 file</string>
        <key>Folder</key>
        <false />
        <key>Mp4HttpOptimize</key>
        <false />
        <key>Mp4LargeFile</key>
        <false />
        <key>Mp4iPodCompatible</key>
        <false />
        <key>PictureAutoCrop</key>
        <true />
        <key>PictureBottomCrop</key>
        <integer>58</integer>
        <key>PictureDeblock</key>
        <integer>4</integer>
        <key>PictureDecomb</key>
        <integer>0</integer>
        <key>PictureDecombCustom</key>
        <string></string>
        <key>PictureDecombDeinterlace</key>
        <true />
        <key>PictureDeinterlace</key>
        <integer>0</integer>
        <key>PictureDeinterlaceCustom</key>
        <string></string>
        <key>PictureDenoise</key>
        <integer>0</integer>
        <key>PictureDenoiseCustom</key>
        <string></string>
        <key>PictureDetelecine</key>
        <integer>0</integer>
        <key>PictureDetelecineCustom</key>
        <string></string>
        <key>PictureHeight</key>
        <integer>272</integer>
        <key>PictureKeepRatio</key>
        <true />
        <key>PictureLeftCrop</key>
        <integer>2</integer>
        <key>PictureLooseCrop</key>
        <false />
        <key>PictureModulus</key>
        <string>16</string>
        <key>PicturePAR</key>
        <string>0</string>
        <key>PicturePARHeight</key>
        <integer>1</integer>
        <key>PicturePARWidth</key>
        <integer>1</integer>
        <key>PictureRightCrop</key>
        <integer>2</integer>
        <key>PictureTopCrop</key>
        <integer>58</integer>
        <key>PictureWidth</key>
        <integer>480</integer>
        <key>PresetBuildNumber</key>
        <integer>2010062701</integer>
        <key>PresetDescription</key>
        <string>HandBrake&apos;s settings for all iPhones and iPod Touches going back to the original iPhone 2G.</string>
        <key>PresetName</key>
        <string>PSP</string>
        <key>SubtitleList</key>
        <array>
        </array>
        <key>Type</key>
        <integer>1</integer>
        <key>UsesPictureFilters</key>
        <integer>1</integer>
        <key>UsesPictureSettings</key>
        <integer>1</integer>
        <key>VideoAvgBitrate</key>
        <integer>960</integer>
        <key>VideoEncoder</key>
        <string>H.264 (x264)</string>
        <key>VideoFramerate</key>
        <string>Same as source</string>
        <key>VideoFrameratePFR</key>
        <false />
        <key>VideoGrayScale</key>
        <false />
        <key>VideoQualitySlider</key>
        <real>25</real>
        <key>VideoQualityType</key>
        <integer>2</integer>
        <key>VideoTargetSize</key>
        <integer>700</integer>
        <key>VideoTurboTwoPass</key>
        <false />
        <key>VideoTwoPass</key>
        <false />
        <key>anamorphic</key>
        <true />
        <key>par_height</key>
        <integer>0</integer>
        <key>par_width</key>
        <integer>0</integer>
        <key>x264Option</key>
        <string>cabac=0:ref=2:bframes=0:8x8dct=0:vbv-maxrate=2000:vbv-bufsize=2000</string>
    </dict>
</array>
</plist>

```

:(:(:(

Still getting corrupted data. Thanks for the import John, I take it the apple stuff at the top is because it is a modified ipod preset.

I must be doing something wrong if this works for others. I did notice that once the enconding was completed the file extension was given as m4v. Is this a problem?? Wikipedia tells me m4v is an itunes file extension that is nearly identical to mp4.:confused:

BTW removed the file extension altogether and PSP sees no file, add an mp4 file extension and I get corrupted data.

EDIT above I changed the file extension of the file extension on the PSP, I tried changing the file extension on ht ePC then loaded onto PSP, now it reports unsupported data! If I do a side by side comparison of the properties of working files, I cannot see much difference to what I have.

---

### Post by JohnAStebbins on 2010-10-27
> **migs73 said:**
> :(:(:(

Still getting corrupted data. Thanks for the import John, I take it the apple stuff at the top is because it is a modified ipod preset.

The apple stuff at the very top is just stuff required by apple's plist xml format which handbrake uses for saving presets.  However, you are correct in that the preset was created by starting with the iPod preset and making the necessary modifications.
> 
I must be doing something wrong if this works for others. I did notice that once the enconding was completed the file extension was given as m4v. Is this a problem?? Wikipedia tells me m4v is an itunes file extension that is nearly identical to mp4.:confused:

They aren't 'nearly' identical.  They are **completely** identical.  The extension is changed because QuickTime is braindead and requires any mp4 stream that has ac3 audio, subtitles, or chapter markers to have the m4v extension. Else it won't recognize it.  That PSP preset has chapter markers enabled, so you get the m4v extension.  Disable chapter markers, save the preset, scan a new source, and you should get mp4 extension.
> 
BTW removed the file extension altogether and PSP sees no file, add an mp4 file extension and I get corrupted data.

EDIT above I changed the file extension of the file extension on the PSP, I tried changing the file extension on ht ePC then loaded onto PSP, now it reports unsupported data! If I do a side by side comparison of the properties of working files, I cannot see much difference to what I have.

I'm sorry this didn't help you.  But I know this preset has worked for others.  I don't have a PSP myself, but I created this preset for a coworker that uses it all the time.

Oh, hey, something just occurred to me.  The most recent HandBrake nightlies have a change that could be causing a problem with that old PSP preset.  Try setting weightp to off in the h264 settings.  Or just import this updated preset where I've disabled chapters and weightp.
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<array>
	<dict>
		<key>AudioList</key>
		<array>
			<dict>
				<key>AudioBitrate</key>
				<string>128</string>
				<key>AudioEncoder</key>
				<string>AAC (faac)</string>
				<key>AudioEncoderActual</key>
				<string>faac</string>
				<key>AudioMixdown</key>
				<string>Dolby Pro Logic II</string>
				<key>AudioSamplerate</key>
				<string>Same as source</string>
				<key>AudioTrack</key>
				<integer>1</integer>
				<key>AudioTrackDRCSlider</key>
				<real>0</real>
				<key>AudioTrackDescription</key>
				<string>English (AC3) (5.1 ch)</string>
			</dict>
		</array>
		<key>ChapterMarkers</key>
		<false />
		<key>Default</key>
		<false />
		<key>FileFormat</key>
		<string>MP4 file</string>
		<key>Folder</key>
		<false />
		<key>Mp4HttpOptimize</key>
		<false />
		<key>Mp4LargeFile</key>
		<false />
		<key>Mp4iPodCompatible</key>
		<false />
		<key>PictureAutoCrop</key>
		<true />
		<key>PictureBottomCrop</key>
		<integer>0</integer>
		<key>PictureDeblock</key>
		<integer>4</integer>
		<key>PictureDecomb</key>
		<integer>0</integer>
		<key>PictureDecombCustom</key>
		<string></string>
		<key>PictureDecombDeinterlace</key>
		<true />
		<key>PictureDeinterlace</key>
		<integer>0</integer>
		<key>PictureDeinterlaceCustom</key>
		<string></string>
		<key>PictureDenoise</key>
		<integer>0</integer>
		<key>PictureDenoiseCustom</key>
		<string></string>
		<key>PictureDetelecine</key>
		<integer>0</integer>
		<key>PictureDetelecineCustom</key>
		<string></string>
		<key>PictureHeight</key>
		<integer>272</integer>
		<key>PictureKeepRatio</key>
		<true />
		<key>PictureLeftCrop</key>
		<integer>0</integer>
		<key>PictureLooseCrop</key>
		<false />
		<key>PictureModulus</key>
		<string>16</string>
		<key>PicturePAR</key>
		<string>0</string>
		<key>PicturePARHeight</key>
		<integer>1</integer>
		<key>PicturePARWidth</key>
		<integer>1</integer>
		<key>PictureRightCrop</key>
		<integer>0</integer>
		<key>PictureTopCrop</key>
		<integer>0</integer>
		<key>PictureWidth</key>
		<integer>480</integer>
		<key>PresetBuildNumber</key>
		<integer>2010102601</integer>
		<key>PresetDescription</key>
		<string>PSP compatible settings</string>
		<key>PresetName</key>
		<string>PSP</string>
		<key>SubtitleList</key>
		<array>
		</array>
		<key>Type</key>
		<integer>1</integer>
		<key>UsesPictureFilters</key>
		<integer>1</integer>
		<key>UsesPictureSettings</key>
		<integer>1</integer>
		<key>VideoAvgBitrate</key>
		<integer>960</integer>
		<key>VideoEncoder</key>
		<string>H.264 (x264)</string>
		<key>VideoFramerate</key>
		<string>Same as source</string>
		<key>VideoFrameratePFR</key>
		<false />
		<key>VideoGrayScale</key>
		<false />
		<key>VideoQualitySlider</key>
		<real>25</real>
		<key>VideoQualityType</key>
		<integer>2</integer>
		<key>VideoTargetSize</key>
		<integer>700</integer>
		<key>VideoTurboTwoPass</key>
		<false />
		<key>VideoTwoPass</key>
		<false />
		<key>anamorphic</key>
		<true />
		<key>par_height</key>
		<integer>0</integer>
		<key>par_width</key>
		<integer>0</integer>
		<key>x264Option</key>
		<string>cabac=0:ref=2:bframes=0:8x8dct=0:vbv-maxrate=2000:vbv-bufsize=2000:weightp=0</string>
	</dict>
</array>
</plist>

```

---

### Post by migs73 on 2010-10-27
Thanks again John, I'm giving it a go now. I'll let you know if it worked in about 20mins. BTW it still insists on the file extension being m4v. Not that it matters.
Also thanks for the PPA and good work you're doing on the Nightly's.

---

### Post by migs73 on 2010-10-27
Same results I am afraid. Does me changing the file name from *.m4v to *.mp4 actually make any difference? 
The file extension is set in handbrake and won't let me change it.
I might give up on this and (through gritted teeth) try via windows.

Thanks for all your help

Mike

---

### Post by JohnAStebbins on 2010-10-27
> **migs73 said:**
> Same results I am afraid. Does me changing the file name from *.m4v to *.mp4 actually make any difference? 
The file extension is set in handbrake and won't let me change it.
I might give up on this and (through gritted teeth) try via windows.

Thanks for all your help

Mike
If it is still using the m4v extension after updating the preset, then there is some disconnect somewhere.  Because that preset does not result in an m4v extension here.  The next step would be for you to post an activity log so I can see exactly what the encode is doing.  All activity logs are saved in ~/.config/ghb/EncodeLogs directory.

---

### Post by migs73 on 2010-10-28
Thanks again John

Please find attached the logs as requested. The earlier time stamped one is from the first attempt, the second was after the change to the preset list.

Many Thanks

Mike

---

### Post by JohnAStebbins on 2010-10-28
> **migs73 said:**
> Thanks again John

Please find attached the logs as requested. The earlier time stamped one is from the first attempt, the second was after the change to the preset list.

Many Thanks

Mike
I don't understand why it is defaulting to m4v extension, but that won't cause problems if you are renaming to mp4.  Aside from that, everything looks good.  Can you tell me what firmware revision you are running in your PSP?  I'll see if I can get a few minutes of my friends time to retest this preset for me with his PSP.

---

### Post by migs73 on 2010-10-29
Thanks for all the trouble you're going to.

My PSP firmware is 3.80.

I'll give it another try and see if I can find a file I have converted in the past and try that, just in case there is something in the source files.

---

### Post by migs73 on 2010-10-29
Tried converting a file that already plays on the PSP. Changed the extension to .mp4 (was .m4v again) and downloaded to PSP but with the same result...Unsupported data.
Attached is the video/audio properties for each file. Left is original.
Main change is the codec (changed to H.264) but I have other files that have this codec that work on the PSP too.

---

### Post by JohnAStebbins on 2010-10-29
> **migs73 said:**
> Tried converting a file that already plays on the PSP. Changed the extension to .mp4 (was .m4v again) and downloaded to PSP but with the same result...Unsupported data.
Attached is the video/audio properties for each file. Left is original.
Main change is the codec (changed to H.264) but I have other files that have this codec that work on the PSP too.

I had my friend retest that preset with the latest handbrake and it works fine for him.  He says he is using firmware version 5.5.  Maybe a firmware upgrade would solve the problem.  Also, whenever he copies the file to his PSP, he changes the extension ***to*** m4v.  I don't know if that is required, but that's what he does.

Edit: Another thing you could try if you don't want to play with firmware.  Change the video codec on the video tab to MPEG-4 (ffmpeg).  That will match the codec being used in the file you said already works on your PSP in your last post.  Don't forget to increase the quality slider.  mpeg-4 quality is a different scale.  A value of 3 or 4 should be good.

---

### Post by migs73 on 2010-10-30
Thanks again,

I'll try leaving the file extension at m4v, if not I'll go for mpeg as you suggest. I can't upgrade my firmware as it is well.......I think you might know why!!!  ;)

---

### Post by JohnAStebbins on 2010-10-31
> **migs73 said:**
> Thanks again,

I'll try leaving the file extension at m4v, if not I'll go for mpeg as you suggest. I can't upgrade my firmware as it is well.......I think you might know why!!!  ;)

My friend is using some patchset to overcome the firmware upgrade issue.
[http://psphacks.me/tag/prometheus/](http://psphacks.me/tag/prometheus/)

---

### Post by Chronon on 2010-10-31
I looked through this topic and didn't see WinFF mentioned.  I used to use it to transcode stuff for iPod and it should have presets for PSP too.  WinFF is just a front-end or ffmpeg.

---

### Post by SadaraX on 2010-11-14
Hmm, I'm sorry to hear of all your various troubles. Allow to offer my humble solution here. I've been using it for several months to watch various bits of video on my PSP. I don't know what firmware version I have though, so this might not work for you.....

I have been using FFMPEG to transcode video to work on my PSP by running it on command line. This is basically a template version of the command I use (where $video_file and $bitrate are replaced with actual values):

```
ffmpeg -i "$video_file" -acodec libfaac -ab 128k -ar 48000 -s 360x272 -vcodec libx264 -b "$bitrate" -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me_method umh -subq 6 -trellis 1 -refs 2 -bf 1 -coder 1 -me_range 16 -g 300 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -maxrate 4M -bufsize 4M -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 21 -threads 0 "$video_file.mp4"
```

I do not know how comfortable you feel with scripting, but I actually wrote a small perl script to handle automatically processing an entire directory for me.

```

#!/usr/bin/perl -w

use warnings;
use strict;

opendir (DIR_VAR_NAME, ".");
my @files = readdir(DIR_VAR_NAME);

foreach my $f (@files)
{
  if( "$f" !~ /.pl$/ )
  {
    my $bitrate = "640kb";
    use File::Spec;
    File::Spec->rel2abs( $f );
    print("ffmpeg -i \"$f\" -acodec libfaac -ab 128k -ar 48000 -s 360x272 -vcodec libx264 -b \"$bitrate\" -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me_method umh -subq 6 -trellis 1 -refs 2 -bf 1 -coder 1 -me_range 16 -g 300 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -maxrate 4M -bufsize 4M -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 21 -threads 0 \"$f.mp4\"\n\n");
    system("ffmpeg -i \"$f\" -acodec libfaac -ab 128k -ar 48000 -s 360x272 -vcodec libx264 -b \"$bitrate\" -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me_method umh -subq 6 -trellis 1 -refs 2 -bf 1 -coder 1 -me_range 16 -g 300 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -maxrate 4M -bufsize 4M -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 21 -threads 0 \"$f.mp4\"");
  }
}
closedir(DIR_VAR_NAME);

```

To use the script, in an empty directory/folder, put ONLY the videos you want to convert to PSP format (MP4) into it. Put the downloaded perl script into there. From a commandline in that directory, run the script. It will try to convert every file that isn't an *.pl file.

If you want bigger or smaller MP4 files, just change the number for the $bitrate variable. I've tried as small as 450kb with decent results but I haven't really bothered with anything larger than 640kb.

I don't remember what folder you have to put the videos into on your PSP though. I can't remember offhand.

---

### Post by beccatoria on 2010-12-07
If anyone is still having difficulty, I find this tutorial still works:  
 
[http://blog.yogarine.com/2007/12/converting-video-for-psp-on-linux.html](http://blog.yogarine.com/2007/12/converting-video-for-psp-on-linux.html)
 
I have a slightly newer version of avidemux, I think, which means that some of the options are a little different, but by following it as closely as I can, I get videos that work on my PSP.  
 
One important thing I will note - the writer of the tutorial suggests saving this rendering profile as a project to prevent having to re-enter the settings every time.  However, I do not find this works as for some reason not all of the settings save correctly.  
 
Further, after converting one video file, when I open another video - even though Avidemux appears to keep all identical settings, the second video I convert will again show up on my PSP as unreadable.  I have absolutely no idea why this is as it seems to make no sense, but it's very consistently the case.  
 
So every time I want to convert a video, I open a new instance of Avidemux and manually enter the settings described in the above tutorial.  It's a pain and time consuming, but it does seem to work.

---

