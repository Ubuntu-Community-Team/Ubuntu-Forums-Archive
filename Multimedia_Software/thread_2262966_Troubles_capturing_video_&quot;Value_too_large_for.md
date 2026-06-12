---
title: "Troubles capturing video: &quot;Value too large for defined data type&quot;"
date: 2015-01-28
forum: Multimedia Software
---

### Post by faroutliving on 2015-01-28
At this point I'm just trying to find out what the actual problem is. I can't even ask a proper question since I don't know what is to blame for my troubles...

I'm trying to capture video from an HVR2250 (dual tuner) video card and convert to multiple quality streams in real time. Using azap and ffmpeg, I try and capture a stream using something like:

ffmpeg -i "/dev/dvb/adapter0/dvr0" -b:v 2400k "hi.m3u8" -b:v 1200k  "med.m3u8" -b:v 600k "low.m3u8" -vn "audio.m3u8"

but it fails with "/dev/dvb/adapter0/dvr0: Value too large for defined  data type"

However, if I copy the data using something like

cp /dev/dvb/adapter0/dvr0 data.ts

and then convert with

ffmpeg -i data.ts -b:v 2400k "hi.m3u8" -b:v 1200k "med.m3u8" -b:v 600k  "low.m3u8" -vn "audio.m3u8"

It runs faster than real time without error. (In fact, I can do this 5 times simultaneously and it still does it in better than real time)

If I run just

ffmpeg -i "/dev/dvb/adapter0/dvr0" -b:v 2400k "hi.m3u8"

It runs without problems as well.

Stranger still, if I try and pipe the data to ffmpeg like this:

cat "/dev/dvb/adapter0/dvr0" | ffmpeg -i - -b:v 2400k "hi.m3u8" -b:v 1200k "med.m3u8" -b:v 600k  "low.m3u8" -vn "audio.m3u8"

I get:

cat: /dev/dvb/adapter0/dvr0: Value too large for defined data type

So where is this error coming from? Any ideas on how to deal with it??

Thanks!
Deron

---

### Post by faroutliving on 2015-01-29
Am I posting in the wrong section, or ?? I'm really stumped on what to do at this point. Do I have too much info, or not enough, in my original post?

Thanks,
Deron

---

### Post by tom177 on 2015-04-19
Hi !!

Any news about this probelm ?
I have exactly the same :-(

Thomas

---

### Post by steeldriver on 2015-04-19
This seems to be a low-level error from coreutils:

[http://www.gnu.org/software/coreutils/faq/coreutils-faq.html#Value-too-large-for-defined-data-type](http://www.gnu.org/software/coreutils/faq/coreutils-faq.html#Value-too-large-for-defined-data-type)

Perhaps the version of ffmpeg that you are using was compiled without large file support?

---

### Post by faroutliving on 2015-04-19
Hi Thomas,

Before today, no one has even acknowledged my posts here and on the ffmpeg user list. (No, I'm not whining, I realize this is a very unusual problem.)

Sadly, I'm still troubled by this problem and currently only capture a single video stream.

Hello Steeldriver,

Thanks for the tip. I don't ever recall seeing an option to compile without/with large file support. I process files often that are >> 4gb, but that doesn't mean too much. I just did a cp from /dev/dvb/adapter0/dvr0 and it is accumulating data at about 97MB per minute. It would take a good while to exceed a (signed) 32bit number at that rate. It only takes approximately 15 seconds for that error to come up and ffmpeg to quit.

Thanks for even looking!

Deron

---

### Post by mc4man on 2015-04-19
What does this report (if anything

cat /dev/dvb/adapter0/dvr0 > file.ts

If you get the value error then maybe look at - 
[http://panteltje.com/panteltje/dvd/](http://panteltje.com/panteltje/dvd/) in the Attention section.

---

### Post by faroutliving on 2015-04-20
Hello mc4man,

cat appears to work as well as cp, gleefully filling my hard drive with mpegts data. Thanks, maybe something will inspire a solution (or at least identify the source of the problem).


Playing around with this again, I'm pretty sure this is in ffmpeg and not in some system. I changed from

ffmpeg -i /dev/dvb/adapter0/dvr0 ...

to

ffmpeg -i movie=/dev/dvb/adapter0/dvr0:f=mpegts:s=dv+da[out0+subcc][out1] ...

(which is the sequence I am using now to pull out the closed captioning as well) and the error I get is:

movie=/dev/dvb/adapter6/dvr0:f=mpegts:s=dv+da[out0+subcc][out1]: Value too large for defined data type

I would have expected that a system call would be complaining about a system device/file, not an internal ffmpeg source descriptor. So unless there is an ffmpeg guru lurking, I'm going to start by grepping the ffmpeg source and repost on the ffmpeg mailing list. Normally ffmpeg errors are preceded by which part of ffmpeg is generating the error. Not so in this case. That plus the similarity to the coreutils error led me to believe it was something other than ffmpeg.

Thanks for all the help past, present and future! Any other ideas are always welcome!

Deron

---

### Post by faroutliving on 2015-04-20
No, the error is not in ffmpeg. It appears to be the error returned from a POSIX call that ffmpeg fluffs out. Still looking but loosing hope...

Deron

---

### Post by mc4man on 2015-04-20
No clue (& no means at all  to try hardware wise, ect.
Though i'd probably try the suggestion to modify dmxdev.h & recompile the kernel module, ect.
(- changing the highlighted line in screen to  - 
#define DVR_BUFFER_SIZE (100*188*1024)

---

### Post by faroutliving on 2015-04-21
Thanks, I think I will give it a try. Since ffmpeg can process the data from a file faster than real time, it just seems like it should be able to process it from the device. What do I know...

Deron

---

### Post by tom177 on 2015-04-21
Hi Deron,

which kind of hardware do you use ?
Im running it on ARMV7 (odroid-c3). I also tried to change the dmxdev.h buffer size but without success :-(

Do you have avconv installed ? It seems that avconv can handle the input stream a bit better.
Could you please try to pass the mpegts stream via avconv to ffmpeg ?

Should be working as follow:

avconv -i /dev/dvb/adapter0/dvr0 -c:v copy -c:a copy -c:s copy -map 0 -f mpegts - | ffmpeg -i pipe:0 ..................................................

And another question I have:
You wrote that you can capture one strem: "[COLOR=#000000]I'm still troubled by this problem and currently only capture a single video stream.[/COLOR]"
Is this running without probmes ? I also try to capture one stream but this will terminate after some seconds.

Can you send me the commands you are using to do this ?
How do you switch on a channel, by szap ?


Regards, Thomas

---

### Post by faroutliving on 2015-04-23
> **mc4man said:**
> No clue (& no means at all  to try hardware wise, ect.
Though i'd probably try the suggestion to modify dmxdev.h & recompile the kernel module, ect.
(- changing the highlighted line in screen to  - 
#define DVR_BUFFER_SIZE (100*188*1024)

Problem solved! This did resolve it. I presume this is the dvb device that azap is writing to, and that the buffer just doesn't get drained fast enough on startup.

Shame this is not configurable via some simple method.

Thanks for everyone's help!

Deron

---

### Post by faroutliving on 2015-04-23
> **tom177 said:**
> which kind of hardware do you use ?

This is running on an Intel s2600coe dual proc motherboard with 64gb ram and two of the fastest Xeon procs Intel sells.


> **tom177 said:**
> Do you have avconv installed ? It seems that avconv can handle the input stream a bit better. Could you please try to pass the mpegts stream via avconv to ffmpeg ?

That might have worked, never got to test it. However, I'm trying to keep this as low resource usage as possible.


> **tom177 said:**
> And another question I have:
You wrote that you can capture one stream: "[COLOR=#000000]I'm still troubled by this problem and currently only capture a single video stream.[/COLOR]"
Is this running without probmes ? I also try to capture one stream but this will terminate after some seconds.

Yes, I can actually capture 6 channels at a time (I have 3 dual tuner cards in the machine) and it will stay up and running for days. I should have been more clear in that I could only encode one video stream per incoming channel at a time when reading from the dvb device.



> **tom177 said:**
>  Can you send me the commands you are using to do this ?

With your system, I don't know if this will help you any. Here is the single video stream command I use that worked without the kernel module change. It also outputs audio only HLS stream, HLS webvtt subtitles, and images.

ffmpeg -loglevel 30 -f lavfi -i "movie=/dev/dvb/adapter0/dvr0:f=mpegts:s=dv+da[out0+subcc][out1]" -force_key_frames expr:gte\(t,n_forced*2\) -c:v libx264 -vf scale=1280:720 -s 1280x720 -aspect 1280:720 -pix_fmt yuv420p -r 59.94 -preset veryfast -b:v 1200k -c:a libfaac -ar 48000 -ac 2 -af volume=volume=11dB -flags:a -global_header -f hls -hls_time 2 -hls_allow_cache 0 -hls_list_size 10 -hls_wrap 20000 -hls_flags delete_segments -hls_segment_filename "/var/www/html/stream/wflx/v.mid.%d.ts" -y "/var/www/html/stream/wflx/v.mid.m3u8" -sn -vn -c:a libfaac -ar 32000 -ac 1 -af volume=volume=11dB -flags:a -global_header -f hls -hls_time 2 -hls_allow_cache 0 -hls_list_size 10 -hls_wrap 20000 -hls_flags delete_segments -hls_segment_filename "/var/www/html/stream/wflx/a.low.%d.ts" -y "/var/www/html/stream/wflx/a.low.m3u8" -vf scale=426:240 -s 426x240 -aspect 426:240 -f image2 -vf fps=1 -strftime 1 -y "/var/www/html/stream/wflx/t.%Y-%m-%d_%H:%M:%S.jpg" >> /var/www/html/stream/log_wflx 2>&1

Some of this is unnecessary, since I've been trying different things, and includes output of HLS compatible closed captioning. For that to work, you need to apply a yet unapproved patch to ffmpeg that was posted a few weeks ago.

> **tom177 said:**
> How do you switch on a channel, by szap ?

Regards, Thomas

Close. azap.

Deron

---

