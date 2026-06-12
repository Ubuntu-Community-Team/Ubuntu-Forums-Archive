---
title: "Twitch streaming howto (ffmpeg, linux, how-to)"
date: 2014-06-21
forum: Multimedia Software
---

### Post by gargl on 2014-06-21
Hey there,

after having a lot(!) of issues to get my stream working properly, I finally did it.
Because I've received a lot of help from the web and earlier also a lot of
help from this forum I though to put up my solution here as well to mb also help
others.

If you use google you will find a ton of scripts and helps but none of them
solved my issue with continuous frame drops. So in this small tutorial I will try
to highlight those aspects which I think might be important to focus on
in order to be able to stream your screen (or parts of it) from your local
computer to a streaming platform like twitch/justin/azubu.

In order to try out the script immediately I put down two versions. The first
on can easily be copied and pasted to test on the fly (you only have to insert
your streaming key and the adress of your streaming server).

The second one is identical, except that I haven't replaced the variables from
my script with values. In order to keep it simple, I'll try to explain some aspects.
Please be aware that the script is neither perfect nor that I do understand
all aspects of it. It is more a result of a "work in progress" that I wanted to share
so that other people could mb benefit from it.

My upload bandwidth: ~1100kbit/s

Each 'k' also means (afaik)  kbit/s.

First, (copy and try) version:
```

	ffmpeg \
	-f x11grab -s 640x480 -framerate 25 -i :0.0 \
	-f alsa -ac 2 -i pulse \
	-vcodec libx264 -framerate 25 -rtbufsize 2500k -s 640x480 -preset veryfast -pix_fmt yuv420p -crf 26 -force_key_frames 'expr:gte(t,n_forced*2)' -minrate 850k -maxrate 850k -b:v 900k -bufsize 280k \
	-acodec libmp3lame -rtbufsize 2500k -ab 96k -ar 44100 \
	-f flv - |\
		ffmpeg -f flv -i - -c copy -f flv "rtmp://SERVER_ADRESS.twitch.tv/app/STREAM_KEY"

```


Second (elongated) version:
```

SERVER="streaming_server"
#Resolutions
INRES="640x480" # input resolution
OUTRES="640x480" # Output resolution 
FPS="25" #Define your input frames per second.

QUAL="veryfast" # one of the many FFMPEG preset 
# If you have low bandwidth, put the qual preset on 'fast' (upload bandwidth)
# If you have medium bandwitch put it on normal to medium
See: https://trac.ffmpeg.org/wiki/Encode/H.264

# Streamkey (you might want to put your streaming key in a file...)
STREAM_KEY=$(cat .file_name)

	ffmpeg -benchmark -report \
	-f x11grab -s $INRES -framerate "$FPS" -i :0.0 \
	-f alsa -ac 2 -i pulse \
	-vcodec libx264 -framerate "$FPS" -rtbufsize 2500k -s $OUTRES -preset $QUAL -pix_fmt yuv420p -crf 26 -force_key_frames 'expr:gte(t,n_forced*2)' -minrate 850k -maxrate 850k -b:v 900k -bufsize 280k \
	-acodec libmp3lame -rtbufsize 2500k -ab 96k -ar 44100 \
	-f flv - |\
		ffmpeg -f flv -i - -c copy -f flv "rtmp://$SERVER.twitch.tv/app/$STREAM_KEY"

```


**Explanation**
> -report
The  '-report' flag lets ffmpeg create a log file 'program-YYYYMMDD-HHMMSS.log' in
the directory the ffmpeg command is executed. I found this kinda helpful for analyzing
although I didn't understand all the content of the created file. '-report' can be removed
without a problem.

> -rtbufsize
-rtbufsize -> To be honest, I do not have a clue if it affects the overall result at all.
I've added it but it might be that it can be removed as well.

> -preset
-preset
(See: [https://trac.ffmpeg.org/wiki/Encode/H.264](https://trac.ffmpeg.org/wiki/Encode/H.264))

> -crf
-crf 26
Using '-crf' [...]allows the encoder to attempt to achieve a certain output quality for the whole file[...]'.
So '-crf' is a **QUALITY** setting, telling ffmpeg to keep the same QUALITY all over the whole file/stream.
If I understood it correctly this does mean that ffmpeg VARIES the bitrate in order to achive the same quality.
However, for most streaming services it is importat to have a constant bitrate, therefore the tradeoff between
quality and constant bitrate will be addressed later.
(Further details on 'crf': [https://trac.ffmpeg.org/wiki/Encode/H.264](https://trac.ffmpeg.org/wiki/Encode/H.264))

> -force_key_frames
-force_key_frames 'expr:gte(t,n_forced*2)'
In order to get an 'excellent' stream quality, when streaming to twitch,
you have to have 'key_frames' every 2 seconds.

Using '-force_key_frames' should be similar to:
'-g $FPSx2 -keyint_min $FPS'.
Where '-g' relates to the '[...]Keyframe interval, also known as GOP length.[...]'
and '-keyint_min' is 'Minimum GOP length, the minimum distance between I-frames.'
However, when I used these two options the keyframes have been _around_ 2seconds
but almost never have been exactly 2 seconds, which lead to an 'acceptable'
rating instead of an 'excellent' from twitch (and I wanted to have an excellent).
Although '-force_key_frames' doesn't solve this problem, sometimes I got the
impression it works better, but, tbh, I think you can go with either option
setting. (For further information on '-g' and '-keyint_min' see: [https://sites.google.com/site/linuxencoding/x264-ffmpeg-mapping](https://sites.google.com/site/linuxencoding/x264-ffmpeg-mapping)).

If I remember correctly I've read anywhere that '-g' and 'keyint_min' is an option
which ffmpeg "tries" to follow but doesn't it strictly. Instead '-force_key_frames'
worked for me, forcing ffmpeg to strictly follow the keyframe interval and gave me
(at least in this regard) an 'excellent' rating from twitch.tv. Test and use the
arguments you like and which works best for you.



**Important**
> -b:v 900k -bufsize 280k(!!!)
Let's come to the real gems:
'-b:v 900k -bufsize 280k'
I had (for a couple of weeks) problems figuring out why I had constant
frame drops so that my stream wasn't watchable after 10-15minutes.

Lets start with the most important (two) arguments in order to not have
frame drops (at least for my problem) and still a constant bitrate.
'-b:v'  or (-vb which is the same) and '-bufsize'.
Both belong together and it is very important to understand their
meaning!

As I am lazy I copy some of the excellent written explanation
from one of the sources below:
**Bufsize** '...tells the encoder how often to calculate the average bit rate and
check to see if it conforms to the average bit rate specified on the command
line (-b:v 64k). If we don't specify the -bufsize option, ffmpeg will still calculate
and correct the average bit rate produced, but more lazy, at some intervals
which can be significantly longer than we would want. This would cause the current
bit rate to frequently jump a lot over and below the specified average bit rate and
would cause an unsteady output bit rate.'.

So, first define a bitrate which should be oriented at the upload speed which
is available (e.g. 900kbit/s having a 1100kbit/s upload speed).
Secondly we need to define a bufsize. How do we get the size of 'bufsize'
and what does it mean?

The value of bufsize tells ffmpeg how often/frequent it checks for the output bitrate.
Further, for a small '-buffsize' value '...ffmpeg will more frequently check for the
output bit rate and constrain it to the specified average bit rate from the command line.
Specifying too small -bufsize would cause ffmpeg to degrade the output image quality,
because it would have to (frequently) conform to the limitations and would not have
enough of a free space to use some optimizations (for example, optimizations based
on the frame repetitions and similar), because the buffer would not contain enough frames
for the optimizations to be effective.'.

However if you make the bufsize (in relation to '-b:v') too large you end up with
frame drops (at least I did).

[B]This means, you have to play around with the bitrate and the bufsize, to find
suitable values for your specific setup.[/B] I havn't had these values in my script
before and had massive framedrops for weeks! So, this was the solution for me!
Maybe this helps others as well!

For further details on '-maxrate' 'minrate' '-b:v' 'vb' and/or 'bufsize' I highly
recommend to read this:
[http://trac.ffmpeg.org/wiki/Limiting%20the%20output%20bitrate](http://trac.ffmpeg.org/wiki/Limiting%20the%20output%20bitrate)
and this:
[http://superuser.com/questions/536001/variable-bit-rates-with-vb-and-minrate-maxrate-settings-in-ffmpeg](http://superuser.com/questions/536001/variable-bit-rates-with-vb-and-minrate-maxrate-settings-in-ffmpeg)

But you can also go with my explanation if you think it is sufficient.


> -minrate 850k -maxrate 850k
Lets come to the final options: '-minrate 850k -maxrate 850k'.
To be honest I do not know if it makes sense in the way that I use these
two.
Minrate sets the '...minimum bitrate tolerance [...] useful in setting up a CBR encode.'
and '-maxrate'  sets the '...maximum bitrate tolerance [...]' which requires '...bufsize to be set.'.

I've set them because it works and I know that this is not a good answer,
but at least it does it for me. I would also recommend to create a script for
each resolution setup as I assume that the values for each setup might differ.

For further details on '-maxrate' 'minrate' '-b:v' 'vb' and/or 'bufsize' I highly
recommend to read this:
[http://trac.ffmpeg.org/wiki/Limiting%20the%20output%20bitrate](http://trac.ffmpeg.org/wiki/Limiting%20the%20output%20bitrate)
and this:
[http://superuser.com/questions/536001/variable-bit-rates-with-vb-and-minrate-maxrate-settings-in-ffmpeg](http://superuser.com/questions/536001/variable-bit-rates-with-vb-and-minrate-maxrate-settings-in-ffmpeg)


Finally we are at the end and I would like to thank all people who have helped
me with their own tutorials, posts, youtubevideo-howtos on how to create
a ffmpeg streaming environment on linux and also those sources I've listed
here explicitly.

Maybe my version might also help some people who have the problem of frame
dropping with their streaming scripts I had before. Hope so! Also you can see
that you can easily create your own script, optimizing what I have copied
here as I think there is plenty of potential to improve it.

Best,
Marc!

Addition: If you want to test this setup or play around but you do not have
an account at a streamingservice, you can easily replace the last line
from:
```

		ffmpeg -f flv -i - -c copy -f flv "rtmp://$SERVER.twitch.tv/app/$STREAM_KEY"

```
with
```

		ffmpeg -f flv -i - -c copy -f flv filename.flv

```
directing the output into a local '.flv' file.

---

