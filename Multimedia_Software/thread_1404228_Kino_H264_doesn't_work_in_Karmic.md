---
title: "Kino H264 doesn't work in Karmic"
date: 2010-02-11
forum: Multimedia Software
---

### Post by charonred on 2010-02-11
I recently migrated my system to Karmic 9.10 from Hardy 8.04

Now that I want to convert some .avi videos to H.264 in Kino for upload, it doesn't work. In Hardy all was fine, I'd import the .avi files and export to h.264 mp4, then upload to youtube etc ... no problems. 

But with karmic; after I import the file into Kino, I then trim out the bits I don't want. Next I go to Export and select H.264 MP4 Single Pass (ffmpeg), then click the Export button; it 'locks the audio' and that's it - takes 5 seconds to 'finish' no matter how long the video clip is, and no mp4 file is generated or appears in the selected folder (same result with H.264 MP4 Dual Pass).

Any ideas on how to fix this?

---

### Post by FakeOutdoorsman on 2010-02-11
There are three issues here.

I opened Kino via the terminal and I got an error when I tried to export using the same setting as you:
```
ffmpeg: unrecognized option '-title'
```
So then I looked at the Kino preset file at:
```
/usr/share/kino/scripts/exports/ffmpeg_h264.sh
```
The FFmpeg commands in this script are ancient and won't work with FFmpeg in Karmic.  The old metadata options (-title, -comment, -author, -copyright) were replaced with *-metadata title="foo" -metadata comment="ham"*, etc.

Secondly, the script does not contain any of the libx264 presets that are now required to encode to H.264 with FFmpeg.

The third issue isn't Kino's fault.  FFmpeg in Karmic doesn't support AAC audio and I think that's what Kino would use to export using this setting.  It's a fairly easy fix.  See options A (I think option A may work, but I didn't test it) or C in:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg[/url]

You might be able to find a more up to date *ffmpeg_h264.sh*, or failing that I may eventually post an updated version.  Another option is to export to a DV file and then re-encode it with FFmpeg itself.  See the one-pass CRF FFmpeg usage example in:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

---

### Post by a2z on 2010-02-11
great fix! Thanks.
going after it right now.

a2z

FakeOutdoorsman, I believe blender 3D current package installs with ffmpeg. Would you happen to know how or if Ubuntu handles ffmpeg the same way?
Thanks

---

### Post by FakeOutdoorsman on 2010-02-11
> **a2z said:**
> great fix! Thanks.
going after it right now.

a2z

Just to let you know I probably obsessively updated my post with minute changes after/during your reply.

---

### Post by FakeOutdoorsman on 2010-02-11
> **a2z said:**
> FakeOutdoorsman, I believe blender 3D current package installs with ffmpeg. Would you happen to know how or if Ubuntu handles ffmpeg the same way?
Thanks

Are you asking if Option C would screw up Blender?  I doubt it.  In fact, it may be beneficial and may allow Blender to export to AAC audio as well.  I'm just guessing because I don't have any experience with Blender.  I don't know how Blender interfaces with FFmpeg.

---

### Post by a2z on 2010-02-11
> **FakeOutdoorsman said:**
> Are you asking if Option C would screw up Blender?  I doubt it.  In fact, it may be beneficial and may allow Blender to export to AAC audio as well.  I'm just guessing because I don't have any experience with Blender.  I don't know how Blender interfaces with FFmpeg.

I have been under the assumption ffmpeg was packaged with blender. I don't know for certain. 

If so, I wanted to know if Ubuntu ffmpeg pack would affect or override blenders...
No big deal right now. I'm not in need of anything super special right now. Perhaps in the near future though. 

Thanks for contributing. And once ironed out, I'd nominate this guide for a sticky since it's so beneficial to many. But lacking front exposure to those downloading/upgrading to karmic. 

a2z

---

### Post by charonred on 2010-02-11
hmm, dealing with the 3rd issue of ffmpeg; following the guide from above
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

I did both B & C, but that didn't change anything, Kino still won't export mp4.

I ended up 'Undoing Changes Made By This Guide' both B & C; and then removed Kino and restarted the PC.

I then by followed C only for adding Medibuntu restricted and libavcodec-extra-52; and finally reinstalled Kino, and rebooted.

But selecting h.264 still doesn't export a mp4 file; the only difference is instead of this > click the Export button; it 'locks the audio' and that's it - takes 5 seconds to 'finish' no matter how long the video clip is, and no mp4 file is generated or appears in the selected folder (same result with H.264 MP4 Dual Pass). it now takes 16 seconds to finish, but still no mp4 file.

So, how do I fix the first 2 issues with Kino?

.

---

### Post by FakeOutdoorsman on 2010-02-11
> **charonred said:**
> hmm, dealing with the 3rd issue of ffmpeg; following the guide from above
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

I did both B & C, but that didn't change anything, Kino still won't export mp4.

I ended up 'Undoing Changes Made By This Guide' both B & C; and then removed Kino and restarted the PC.

I then by followed C only for adding Medibuntu restricted and libavcodec-extra-52; and finally reinstalled Kino, and rebooted.

But selecting h.264 still doesn't export a mp4 file; the only difference is instead of this  it now takes 16 seconds to finish, but still no mp4 file.

So, how do I fix the first 2 issues with Kino?

.

You have to fix the first two issues (wrong metadata options, and lack of libx264 presets usage) before Kino will export to H.264 video.  You could look for an up to date *ffmpeg_h264.sh* file (surely someone already did this?), or I can perhaps work on one over the weekend.

---

### Post by basujansb0110 on 2010-02-11
Great fix   !!!!!!!!!

I just have decided to go after it.

But I do not know whatever you happen to know how or if Ubuntu handles ffmpeg the same way....................

Thanks a lot ..

---

### Post by charonred on 2010-02-11
I still can't get it to work; I've been here '/usr/share/kino/scripts/exports/ffmpeg_h264_dual.sh' & 'ffmpeg_h264.sh' reading/editing scripts via gedit (as sudo) made changes from $x264 to $libx264 - made no difference, so changed them back again - I'm just rough hacking cause I really don't know much about Linux scripts etc.

I also visited kinodv.org and found that the most current build 'kino-1.3.4.tar.gz' is available for download (so I did), but have forgotten how to install those sort of packages.

The site only list packages from Dapper up to Jaunty, but nothing for Karmic, so not sure if this latest one would even work.

.

---

### Post by charonred on 2010-02-12
bump

---

### Post by FakeOutdoorsman on 2010-02-13
I re-wrote the *ffmpeg_h264.sh* script to work with FFmpeg from Karmic, but I'll have to test it tomorrow because this machine doesn't have Kino.  Might save you the trouble of compiling Kino if the new script works.

---

### Post by charonred on 2010-02-13
would be joy if that fixes it ... many thanks in advance

---

### Post by FakeOutdoorsman on 2010-02-13
Here's the revised script:
```
sudo cp /usr/share/kino/scripts/exports/ffmpeg_h264.sh{,.original}
sudo mv ffmpeg_h264.sh /usr/share/kino/scripts/exports/
sudo chmod 755 /usr/share/kino/scripts/exports/ffmpeg_h264.sh
```

Kino may use a *.kino* directory in your home directory, and placing the script in there would be a less messy way of doing this, but I didn't look into that.

**ffmpeg_h264.sh**
```
#!/bin/sh
# A Kino export script that outputs to H.264 MP4 using ffmpeg with x264

usage()
{
	# Title
	echo "Title: H.264 MP4 Single Pass (FFMPEG)"

	# Usable?
	aac=`ffmpeg -formats 2> /dev/null | egrep "(Encoders:)|(.*EA.*aac)" | grep aac | wc -l`
	h264=`ffmpeg -formats 2> /dev/null | egrep "(Encoders:)|(.*EV.*264)" | grep 264 | wc -l`
	[ "$aac" -gt 0 ] && [ "$h264" -gt 0 ] && echo Status: Active || echo Status: Inactive

	# Type
	echo Flags: single-pass file-producer

	# Profiles
	echo "Profile: High Quality (same size as input)"
	echo "Profile: High Quality (640x480)"
}

execute()
{
	# Arguments
	normalisation="$1"
	length="$2"
	profile="$3"
	file="$4"
	project="$5"
	pass="$6"
	aspect="$7"

	. "`dirname $0`/ffmpeg_utils.sh"
	ffmpeg_generate_hq
	test_lf=`echo $ffmpeg_help | grep '\-lf' | wc -l`
	[ "$test_lf" -gt 0 ] && hq="$hq -lf"
	test_flags=`echo $ffmpeg_help | grep '\-flags' | wc -l`
	[ "$test_flags" -gt 0 ] && hq="$hq -flags +loop"

	# generate filename if missing
	[ "x$file" = "x" ] && file="kino_export_"`date +%Y-%m-%d_%H.%M.%S`
	
	# Create metadata options
	title=`awk '/title="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /title=/) z = y + 1; print x[z]; exit}' "$project"`
	author=`awk '/author="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /author=/) z = y + 1; print x[z]; exit}' "$project"`
	comment=`awk '/abstract="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /abstract=/) z = y + 1; print x[z]; exit}' "$project"`
	copyright=`awk '/copyright="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /copyright=/) z = y + 1; print x[z]; exit}' "$project"`
	
	# Run the command
	case "$profile" in 
		"0" ) 	ffmpeg -threads $threads -f dv -i pipe: \
			-vcodec libx264 -vpre hq -crf 20 -aspect $aspect -ab 192k \
			-metadata title="$title" -metadata author="$author" -metadata comment="$comment" -metadata copyright="$copyright" \
			-y "$file".mp4 ;;
		"1" ) 	ffmpeg -threads $threads -f dv -i pipe: \
			-vcodec libx264 -vpre hq -crf 20 -aspect $aspect -ab 192k -s 640x480 \
			-metadata title="$title" -metadata author="$author" -metadata comment="$comment" -metadata copyright="$copyright" \
			-y "$file".mp4 ;;
	esac
}

[ "$1" = "--usage" ] || [ -z "$1" ] && usage "$@" || execute "$@"
```

---

### Post by FakeOutdoorsman on 2010-02-13
[s]Nevermind.  It doesn't work.  I didn't actually watch the output due to an issue with my virtual machine and assumed it worked but it looks bad (using FFmpeg from the Ubuntu repository and *libavcodec-extra-52* from Medibuntu).  I'll try a few more test runs and actually watch the output this time.[/s]

Update: I had a third preset that included the *-deinterlace* option.  The first two presets did not contain this and did work, so I simply removed that preset.  Everything should work now.

---

### Post by charonred on 2010-02-14
thanks fakeoutdoorsman;

the first script looks like something I run in Terminal  ... correct ?

but what do I do with the second long script ?

---

### Post by FakeOutdoorsman on 2010-02-14
The second, long script is ffmpeg_h264.sh.  Copy it and save it as ffmpeg_h264.sh and then run the first set of commands.

---

### Post by charonred on 2010-02-14
1st command seemed to do whatever it was supposed to do; hit enter and back to the prompt.

2nd  command got - mv: cannot stat `ffmpeg_h264.sh': No such file or directory

3rd was - Operation not permitted

anyhow running kino; when importing an .avi Kino gets to '265' onthe progress bar and then freezes; but if you cancel out, then the file has been imported ?

Good news is that single pass h264 is exporting mp4 files.

---

### Post by FakeOutdoorsman on 2010-02-14
> **charonred said:**
> 1st command seemed to do whatever it was supposed to do; hit enter and back to the prompt.

2nd  command got - mv: cannot stat `ffmpeg_h264.sh': No such file or directory
This means that you did not have ffmpeg_h264.sh in your home directory.  I should have mentioned this.  Let's start over.

1. Copy the big hunk of text labeled **ffmpeg_h264.sh** from [post #14](http://ubuntuforums.org/showpost.php?p=8822137&postcount=14).

2. Open gedit or any other text editor and paste the text you just copied into this text editor.

3. Save this file as *ffmpeg_h264.sh* into your home directory.

4. Open a terminal.

5. Make sure you are in your home directory with:
```
cd
```

6. Now give the new script the same permissions as all the other Kino scripts:
```
chmod 755 ffmpeg_h264.sh
```

7. Now move ffmpeg_h264.sh from your home directory to where the other Kino scripts are located:
```
sudo mv ffmpeg_h264.sh /usr/share/kino/scripts/exports/
```

Now Kino should use the new script for H.264 single pass.  You will know if it is using the new script when you get the following choices:
```
High Quality (same size as input)
High Quality (640x480)
```

If this is still too confusing, you could venture over to the *#ubuntu-beginners* IRC room and they could help you in real-time and would probably do a better job at explaining these steps.

---

### Post by charonred on 2010-02-14
thanks, I follow that.

So in /usr/share/kino/scripts/exports the ffmpeg_h264.sh original is the file that I copied, pasted and saved that script into yesterday; and the ffmpeg_h264.sh is the file I just created and moved to same folder.

Now in Kino I have 
H.264 MP4 dual Pass (FFMPEG)
H.264 MP4 single Pass (FFMPEG)
H.264 MP4 single Pass (FFMPEG)

the dual pass fails the same as before, but both the single pass work fine (many, many thanks for that; I'm happy with single pass that works).

But, should I reinstall Kino via Synaptic, so that the original single pass will actually contain the original script rather than the script I copied/pasted into it before following amended instructions; and then I run these gedit scripts again to get Kino working again as now, or will it be ok to leave as is ?

---

### Post by FakeOutdoorsman on 2010-02-15
If the single pass is working now then there is no reason to re-install.  The script I revised is only for single-pass.  You don't need to use dual-pass unless you absolutely require a certain output file size for your encoded movie.  Personally, I never use two-pass anymore.

---

### Post by charonred on 2010-02-15
cool, I'll leave as is then; and again many thanks for writing the script - I'm sure it'll be used by many others having the same Kino/Karmic problems.

---

### Post by dannyboy79 on 2010-06-18
> **FakeOutdoorsman said:**
> [s]Nevermind.  It doesn't work.  I didn't actually watch the output due to an issue with my virtual machine and assumed it worked but it looks bad (using FFmpeg from the Ubuntu repository and *libavcodec-extra-52* from Medibuntu).  I'll try a few more test runs and actually watch the output this time.[/s]

Update: I had a third preset that included the *-deinterlace* option.  The first two presets did not contain this and did work, so I simply removed that preset.  Everything should work now.
since the dv avi type 2 files in kino are interlaced don't you get better quality on a computer screen if you deinterlace? i noticed that using the deinterlace option got rid of crazy horizontal lines i had on final output when using ffmpeg libx264 on the command line as I wasn't sure how to incorporate my ffmpeg command into kino but now due to you i think i'll give it a try. I have been just trying the Profile: High Quality (full size, progressive, 2240 kb/s) which I believe is a MP4 dual pass which is actually pretty decent but want to improve it a little so i can read the text better. My purpose is to upload captured and edited xbox 360 game play specifically COD-MW2 which is a very fast moving game which is why i thought i had to deinterlace it.

---

### Post by Glinx on 2010-07-29
Thanks to FakeOutdoorsman for his fix. I came across this h264 issue a day or two ago. Has anyone found a deinterlaced h264 script yet - or can FakeOutdoorsman possibly be persuaded to try and fix this?
Many thanks again for your time with the first fix.

Ahh! A bit of copy and paste did the trick;

Just add  "$progressive"  to FakeOutdoorsmans resulting /usr/share/kino/scripts/exports/ffmpeg_h264.sh  file. Either as root after his instructions, or make the changes before his instructions (i.e. add it to the block of text in post 14 and proceed).

Ive added it as an extra option; High Quality (same as input) Progressive.
Here is my Kino H264 script with the additional bits highlighted in bold;



#!/bin/sh
# A Kino export script that outputs to H.264 MP4 using ffmpeg with x264

usage()
{
    # Title
    echo "Title: H.264 MP4 Single Pass (FFMPEG)"

    # Usable?
    aac=`ffmpeg -formats 2> /dev/null | egrep "(Encoders:)|(.*EA.*aac)" | grep aac | wc -l`
    h264=`ffmpeg -formats 2> /dev/null | egrep "(Encoders:)|(.*EV.*264)" | grep 264 | wc -l`
    [ "$aac" -gt 0 ] && [ "$h264" -gt 0 ] && echo Status: Active || echo Status: Inactive

    # Type
    echo Flags: single-pass file-producer

    # Profiles
    echo "Profile: High Quality (same size as input)"
    **echo "Profile: High Quality (same size as input) Progressive"**
    echo "Profile: High Quality (640x480)"
}

execute()
{
    # Arguments
    normalisation="$1"
    length="$2"
    profile="$3"
    file="$4"
    project="$5"
    pass="$6"
    aspect="$7"

    . "`dirname $0`/ffmpeg_utils.sh"
    ffmpeg_generate_hq
    test_lf=`echo $ffmpeg_help | grep '\-lf' | wc -l`
    [ "$test_lf" -gt 0 ] && hq="$hq -lf"
    test_flags=`echo $ffmpeg_help | grep '\-flags' | wc -l`
    [ "$test_flags" -gt 0 ] && hq="$hq -flags +loop"

    # generate filename if missing
    [ "x$file" = "x" ] && file="kino_export_"`date +%Y-%m-%d_%H.%M.%S`
    
    # Create metadata options
    title=`awk '/title="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /title=/) z = y + 1; print x[z]; exit}' "$project"`
    author=`awk '/author="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /author=/) z = y + 1; print x[z]; exit}' "$project"`
    comment=`awk '/abstract="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /abstract=/) z = y + 1; print x[z]; exit}' "$project"`
    copyright=`awk '/copyright="/ {split($0, x, "\""); z = 0; for (y in x) if (x[y] ~ /copyright=/) z = y + 1; print x[z]; exit}' "$project"`
    
    # Run the command
    case "$profile" in 
        "0" )     ffmpeg -threads $threads -f dv -i pipe: \
            -vcodec libx264 -vpre hq -crf 20 -aspect $aspect -ab 192k \
            -metadata title="$title" -metadata author="$author" -metadata comment="$comment" -metadata copyright="$copyright" \
            -y "$file".mp4 ;;
        [B]"1" )    ffmpeg -threads $threads -f dv -i pipe: \
            -vcodec libx264 -vpre hq $progressive -crf 20 -aspect $aspect -ab 192k \
            -metadata title="$title" -metadata author="$author" -metadata comment="$comment" -metadata copyright="$copyright" \[/B]
            -y "$file".mp4 ;;
        "2" )     ffmpeg -threads $threads -f dv -i pipe: \
            -vcodec libx264 -vpre hq -crf 20 -aspect $aspect -ab 192k -s 640x480 \
            -metadata title="$title" -metadata author="$author" -metadata comment="$comment" -metadata copyright="$copyright" \
            -y "$file".mp4 ;;
    esac
}

[ "$1" = "--usage" ] || [ -z "$1" ] && usage "$@" || execute "$@"




This for me results in very good quality interlaced or de-interlaced video clips.
Thanks to FakeOutdoorsman and the great Kino!

Sorry about the smiley faces and incorrect spacing - I dont know how to get rid of them!

---

### Post by dannyboy79 on 2010-07-29
so I ended up giving up on Kino for editing, I still use it to capture but I now use kdenlive to edit, add transitions and audio etc and then export to x264 and aac. I believe I can capture straight away in kdenlive but haven't fiddled with it yet. so i just cap with kino, and import the avi file in kdenlive. videos are turning out well IMO.

[http://www.youtube.com/watch?v=FFBgT7invGE]("http://www.youtube.com/watch?v=FFBgT7invGE")

---

