---
title: "A Bash ffmpeg progress indicator"
date: 2010-05-11
forum: Multimedia Software
---

### Post by prupert on 2010-05-11
For those that are interested, I have written a bash script for ffmpeg that allows you to monitor the progress, rather than have your CLI flooded with loads of garbage. 

I have written about it here:

[http://www.prupert.co.uk/2010/05/11/finally-a-bash-progress-indicator-for-ffmpeg-that-works/](http://www.prupert.co.uk/2010/05/11/finally-a-bash-progress-indicator-for-ffmpeg-that-works/)

Hope some people find it useful.

UPDATE:

The script now includes better error checking and an ETA in hours, minutes and seconds.

---

### Post by chiwi on 2010-05-12
i thought ffmpeg told you - among the 'garbage' - the progress.

Thanks for the script, i'll give it a try next time i use ffmpeg.

---

### Post by prupert on 2010-05-12
> **chiwi said:**
> i thought ffmpeg told you - among the 'garbage' - the progress.

Thanks for the script, i'll give it a try next time i use ffmpeg.

Well, it does it in a very roundabout way, printing what appears to be a new line every second or so with info about the current frame, FPS, time so far and bitrate. However, unless you log this all to a file, then open up the log and read through it all, it doesn't give you any easy to read indication about how far the conversion has progressed and how long there is to go.

My script simply does lots of crude bash workarounds to hide all this stuff away to simply show you just the following in the terminal:

```
/home/rupert/Downloads/Village of the Damned.mpg..mpg has 172447 frames, now converting
ffmpeg PID = 24868
ffmpeg: 43062 of 172447 frames, progress: 24% and ETA: 1h 42m 41s
```

With the last line updating every ten seconds to show you how long is left to go.

Which, if you ask me, is a lot more informative than:

```
frame=42992 fps= 21 q=29.0 size=  217692kB time=1717.72 bitrate=1038.2kbits/s dup=12 drop=0    
frame=43002 fps= 21 q=29.0 size=  217692kB time=1718.12 bitrate=1038.0kbits/s dup=12 drop=0    
frame=43018 fps= 21 q=29.0 size=  217756kB time=1718.76 bitrate=1037.9kbits/s dup=12 drop=0    
frame=43036 fps= 21 q=29.0 size=  217788kB time=1719.48 bitrate=1037.6kbits/s dup=12 drop=0    
frame=43050 fps= 21 q=29.0 size=  217820kB time=1720.04 bitrate=1037.4kbits/s dup=12 drop=0    
frame=43062 fps= 21 q=29.0 size=  217852kB time=1720.52 bitrate=1037.3kbits/s dup=12 drop=0    
frame=43078 fps= 21 q=29.0 size=  217884kB time=1721.16 bitrate=1037.0kbits/s dup=12 drop=0    
frame=43090 fps= 21 q=29.0 size=  217916kB time=1721.64 bitrate=1036.9kbits/s dup=12 drop=0    
frame=43106 fps= 21 q=29.0 size=  217948kB time=1722.28 bitrate=1036.7kbits/s dup=12 drop=0
    Last message repeated 2 times
[mpeg2video @ 0x8f7ebf0]ac-tex damaged at 15 0
[mpeg2video @ 0x8f7ebf0]concealing 90 DC, 90 AC, 90 MV errors    
frame=43122 fps= 21 q=29.0 size=  217981kB time=1722.92 bitrate=1036.4kbits/s dup=12 drop=0    
frame=43140 fps= 21 q=29.0 size=  218045kB time=1723.64 bitrate=1036.3kbits/s dup=12 drop=0    
frame=43155 fps= 21 q=29.0 size=  218077kB time=1724.24 bitrate=1036.1kbits/s dup=12 drop=0    
frame=43168 fps= 21 q=29.0 size=  218141kB time=1724.76 bitrate=1036.1kbits/s dup=12 drop=0    
frame=43182 fps= 21 q=29.0 size=  218205kB time=1725.32 bitrate=1036.1kbits/s dup=12 drop=0    
frame=43194 fps= 21 q=29.0 size=  218237kB time=1725.80 bitrate=1035.9kbits/s dup=12 drop=0    
frame=43207 fps= 21 q=29.0 size=  218269kB time=1726.32 bitrate=1035.8kbits/s dup=12 drop=0 
```

;)

---

### Post by chiwi on 2010-05-12
> **prupert said:**
> 


Which, if you ask me, is a lot more informative than:

```
frame=42992 fps= 21 q=29.0 size=  217692kB time=1717.72 bitrate=1038.2kbits/s dup=12 drop=0    
frame=43002 fps= 21 q=29.0 size=  217692kB time=1718.12 bitrate=1038.0kbits/s dup=12 drop=0    
frame=43018 fps= 21 q=29.0 size=  217756kB time=1718.76 bitrate=1037.9kbits/s dup=12 drop=0    
frame=43036 fps= 21 q=29.0 size=  217788kB time=1719.48 bitrate=1037.6kbits/s dup=12 drop=0    
frame=43050 fps= 21 q=29.0 size=  217820kB time=1720.04 bitrate=1037.4kbits/s dup=12 drop=0    
frame=43062 fps= 21 q=29.0 size=  217852kB time=1720.52 bitrate=1037.3kbits/s dup=12 drop=0    
frame=43078 fps= 21 q=29.0 size=  217884kB time=1721.16 bitrate=1037.0kbits/s dup=12 drop=0    
frame=43090 fps= 21 q=29.0 size=  217916kB time=1721.64 bitrate=1036.9kbits/s dup=12 drop=0    
frame=43106 fps= 21 q=29.0 size=  217948kB time=1722.28 bitrate=1036.7kbits/s dup=12 drop=0
    Last message repeated 2 times
[mpeg2video @ 0x8f7ebf0]ac-tex damaged at 15 0
[mpeg2video @ 0x8f7ebf0]concealing 90 DC, 90 AC, 90 MV errors    
frame=43122 fps= 21 q=29.0 size=  217981kB time=1722.92 bitrate=1036.4kbits/s dup=12 drop=0    
frame=43140 fps= 21 q=29.0 size=  218045kB time=1723.64 bitrate=1036.3kbits/s dup=12 drop=0    
frame=43155 fps= 21 q=29.0 size=  218077kB time=1724.24 bitrate=1036.1kbits/s dup=12 drop=0    
frame=43168 fps= 21 q=29.0 size=  218141kB time=1724.76 bitrate=1036.1kbits/s dup=12 drop=0    
frame=43182 fps= 21 q=29.0 size=  218205kB time=1725.32 bitrate=1036.1kbits/s dup=12 drop=0    
frame=43194 fps= 21 q=29.0 size=  218237kB time=1725.80 bitrate=1035.9kbits/s dup=12 drop=0    
frame=43207 fps= 21 q=29.0 size=  218269kB time=1726.32 bitrate=1035.8kbits/s dup=12 drop=0 
```


That's why you can't see the Matrix... ;)

---

### Post by prupert on 2010-05-12
> **chiwi said:**
> That's why you can't see the Matrix... ;)

LOL, I haven't laughed so much to a forum post for a long time!

Well, maybe I can see the matrix, I just don't like it being all in green ;)

---

### Post by paramvir on 2010-09-10
Hi prupert 

How are things - ok here is something that might interest you :D

Had already worked out how to show information for mencoder some years back so was now using ffmpeg for libx264 encoding and saw ur post as well. Have used awk aggressively as you will see below in the code and have done away with the need for - among other things 'bc' for floating point stuff and also a simpler direct approach for file information.

this routine is for getting the total frames in a video:

```


ffframes ()
{
	# same as what you had
	ff_length1=( $(ffmpeg -i "$movie" 2>&1 | sed -n "s/.* Duration: \([^,]*\), start: .*/\1/p") )
	# here straight awk output of total length
	ff_length=( $(echo "$ff_length1" | awk -F':'  '{ print $1*3600 + $2*60 + $3 }'));
		
	ff_fps=( $(ffmpeg -i "$movie" 2>&1 | sed -n "s/.*, \(.*\) tbr.*/\1/p") )
	# here we have total number of frames
	total_frames=( $(echo $ff_length $ff_fps | awk '{ printf( "%3.0f\n" ,($1*$2)) } '));
	
	echo total-frames $total_frames 
}


```


Now the video encoding output 

```


ffvideo ()
{
	ffframes

	ffmpeg -i "$fftfile1" $ffmakespecs "$fftfile" 2>&1 | \
		awk -vRS="\r" '$1 ~ /frame/ {gsub(/frame=/," ");gsub(/fps=/," ");gsub(/kB/," ");gsub(/time=/," ");gsub(/ \(/," ");print "\n#Converting video : '"$fftfile"'.\\n\\nCurrent Frame :\\t\t"$1"\\t\t\tFrame rate (s) :\\t\t\t"$2"\\nFile size (mb) :\\t\t"int($5/1024)"."int((($5/1024)-(int($5/1024)))*10)"\\nDuration of video :\\t'$ff_length1'\\tTime elapsed in video :\\t"int($6/3600)":"int((($6/3600)-(int($6/3600)))*60)":"int((($6/60)-(int($6/60)))*60)"\\nTime Remaining :\\t"int((('$total_frames'-$1)/$2)/3600)":"int((((('$total_frames'-$1)/$2)/3600)-(int((('$total_frames'-$1)/$2)/3600)))*60)":"int((((('$total_frames'-$1)/$2)/60)-(int((('$total_frames'-$1)/$2)/60)))*60)"\\t\tPercent complete :\\t\t"int(($6/'$ff_length')*100) "%"; \
		fflush();}' | \
		zenity --progress \
			--auto-kill \
			--auto-close \
			--title="$title" \
			--width=500

}



```

For use in Mencoder encoding :
```


/usr/bin/mencoder "$vid_in" "$vid_pass0" "$logo_in" "$tfile" 2>&1 | awk -vRS="\r" '$1 ~ /Pos/ {gsub(/Pos:/," ");gsub(/%\)/," ");gsub(/ \(/," ");print $3"\n#Position :\\t"$1"\\nFrame :\\t"$2"\\nPercentage :\\t"$3"%\\nFrame Rate :\\t"$4"\\nTime Remaining :\\t"$6; fflush();}' | zenity --progress --auto-kill --auto-close --title='${mpg_file_1}' --width=500


```


Only issue with FFMPEG - so far - is I am unable to get the sliding progress indicator working in the zenity progress dialog.

Hope it helps - let me know what you think of it 

cheers

Param

ps.. oh and chiwi that was really funnny ha ha ha

---

### Post by prupert on 2010-09-14
This is great, I shall investigate your suggestions with interest and see how it all works.

Thanks for taking the time to post this.

---

### Post by paramvir on 2010-10-19
Now things look much better - been busy but magic still happens :guitar:

I am now on KDE 4.5.2 on Arch and it is just fantabulous...

and my scripts wouldn't work - so I was back diving into them and after some head banging etc - have a solution to the progress bar for ffmpeg output::

For ffmpeg the change is the "print" statement b4 fflush!

```

ffvideo ()
{
    ffmpeg -i "$1" $2 "$3" 2>&1 | \
        awk -vRS="\r" '$1 ~ /frame/ {gsub(/frame=/," ");gsub(/fps=/," ");gsub(/kB/," ");gsub(/time=/," ");gsub(/ \(/," ");print "\n#Converting video : '"$4 : $1"'.\\n\\nTotal Frames : \\t\t'$total_frames'\\t\tCurrent Frame :\\t"$1"\\nFrame rate (s) :\\t"$2"\\nTarget File size  :\\t"int(($5/($1/'$total_frames'))/1024)"."int(((($5/($1/'$total_frames'))/1024)-int(($5/($1/'$total_frames'))/1024))*10)" \\nDuration of video :\\t'$ff_length1'\\tTime Remaining :\\t"int((('$total_frames'-$1)/$2)/3600)":"int((((('$total_frames'-$1)/$2)/3600)-(int((('$total_frames'-$1)/$2)/3600)))*60)":"int((((('$total_frames'-$1)/$2)/60)-(int((('$total_frames'-$1)/$2)/60)))*60)"\\nPercent complete :\\t"int(($1/'$total_frames')*100) " %";print int(($1/'$total_frames')*100);fflush();}' | \
        zenity --progress \
            --auto-kill \
            --auto-close \
            --title="$3" \
            --width=500 \
            --percentage=0
}


```have a blast 

cheers :-\"

---

### Post by paul kinell on 2010-11-07
Hi, another take on the idea using ffmpeg's --vstats switch and Zenity,
prupert you might recognize some of your code ideas here. :)

[http://handybashscripts.blogspot.com/2010/10/ffmpeg-with-progress-bar.html](http://handybashscripts.blogspot.com/2010/10/ffmpeg-with-progress-bar.html)

Not much in the way of error checking but it works ok fer me.

Cheers,
paul kinell aka robz

---

### Post by prupert on 2010-11-08
Always good to see improvements to the FFmpeg progres indicator. I still find it so hit and miss.

---

### Post by paramvir on 2010-11-08
> **prupert said:**
> Always good to see improvements to the FFmpeg progres indicator. I still find it so hit and miss.

Hi Prupert

In my cases I find the code very spot on - perhaps if you could send me the cases where you are having an issue while using the code I presented - I could help...

Mencoder and FFMPEG code will work with any type of media file and give you the right stats - but if you are finding errors - I would like to know where :-)

Cheers

Param

---

### Post by bashologist on 2010-12-19
Here's another way...

```
input=test.mpg
export duration=$(ffprobe "$input" 2>&1 | perl -n -e 'print $1 * 3600 + $2 * 60 + $3, "\n" and exit if /Duration: (\d+):(\d+):(\d+)/')

ffmpeg -i "$input" options... < /dev/null 2>&1 | \
perl -e '$/ = "\r"; $| = 1; /time=(\d+)/ and print 100 / ($ENV{"duration"} / $1), "\n" while readline' | \
zenity --progress --auto-close --auto-kill --title converting...

```

Now I gotta just figure out how to get 2 pass encoding to show the first half of the progress then for the second pass get it to show the next half of the progress....

edit...

example 2 pass encoding...
```
input=input.mp4
output=output.mp4

unset WINDOWID
export duration=$(ffprobe "$input" 2>&1 | perl -n -e 'print $1 * 3600 + $2 * 60 + $3, "\n" and exit if /Duration: (\d+):(\d+):(\d+)/')
{
	ffmpeg -i "$input" \
		-an \
		-vcodec mpeg4 -s 320x180 -b 400k -r 15 \
		-f mp4 -y -pass 1 /dev/null < /dev/null 2>&1 | \
	perl -e '$/ = "\r"; $| = 1; /time=(\d+)/ and print 50 / ($ENV{"duration"} / $1), "\n" while readline'
	ffmpeg -i "$input" \
		-acodec libfaac -ab 128k -ac 2 \
		-vcodec mpeg4 -s 320x180 -b 400k -r 15 \
		-f mp4 -pass 2 -y "$output" < /dev/null 2>&1 | \
	perl -e '$/ = "\r"; $| = 1; /time=(\d+)/ and print 50 + 50 / ($ENV{"duration"} / $1), "\n" while readline'
} | zenity --progress --width 600 --auto-close --auto-kill --title Converting...
```

---

### Post by prupert on 2010-12-20
Great to see people still trying to tackle this. I am not surprised you couldn't work out how I was using AWK to get the progress - it was totally hacky and I can't remember either now!

I'll check out your code when I get a mo.

---

### Post by bashologist on 2010-12-21
Just for fun...

One pass with error handling and using a script.

```
#!/usr/bin/env bash

while read parameter; do
	case "$parameter" in
		-i) read input;;
		-pass) read pass;;
	esac
done < <(for input in "$@"; do
	echo "$input"
done)

export duration=$(ffprobe "$input" 2>&1 | perl -n -e 'print $1 * 3600 + $2 * 60 + $3, "\n" and exit if /duration:\s+(\d+):(\d+):(\d+)/i')
unset WINDOWID

ffmpeg "$@" < /dev/null 2>&1 | \
perl -015 -e '$| = 1; /time=(\d+)/ and print 100 / ($ENV{"duration"} / $1), "\n" or print STDERR while readline' | \
zenity --progress --width 600 --auto-close --auto-kill --title Converting...
```

Put that in a script and call it like you would call ffmpeg.
```
bash scriptname -i input.flv -pass 1 test.mp4
```
You could name it something like pffmpeg for progress ffmpeg.
You could print out a progress bar to stderr while printing to stdout for zenity.
You could add options to disalbe or show progress bars in gui or terminal.
You could have zenity popup an error box if there's an error.
You could write some custom gtk gui in perl.

Writing that script only takes up 549 bytes.

---

### Post by prupert on 2011-04-07
Thanks for everyone's input, in particular handybashscripts's I have updated my own script:

[http://www.prupert.co.uk/2011/04/07/a-better-ffmpeg-progress-script/](http://www.prupert.co.uk/2011/04/07/a-better-ffmpeg-progress-script/)

It seems much more robust. I did try other people's suggestions, but couldn't get them to run as well.

Enjoy.

---

