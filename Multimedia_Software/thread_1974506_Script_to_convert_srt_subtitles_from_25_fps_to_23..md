---
title: "Script to convert srt subtitles from 25 fps to 23.976 fps"
date: 2012-05-06
forum: Multimedia Software
---

### Post by ki3456 on 2012-05-06
A typical srt subtitle looks like:

```
2129
01:26:57,688 --> 01:27:00,760
Well, you can guess
what happened next.

```The first line is the subtitle number
The next line has times when the subtitle display starts and when display stops
One or more lines follow with the text of the speech

PAL and NTSC subtitles have the same subtitle number and text  but the timing information
is normally different. This is because PAL video plays faster then NTSC - 25fps vs 23.978fps.
To use a NTSC subtitle for a PAL video the timings need to be reduced by about 4% (23.976/25)
To use a PAL subtitle for a NTSC video the timings need to be increased by about 4% (25/23.976)

This script calculates the new timings and outputs in srt format.
Awk was chosen because it is common and processes fields naturally.

1
Awk, by default, separates fields by spaces.
echo '00:00:12,479 --> 00:00:15,578' | awk '{ print $1 }'
00:00:12,479

2
Hours, minutes, seconds, milli-seconds must be split into separate fields. 
Use colon,space and comma as field delimiters.
echo '00:00:12,479 --> 00:00:15,578'  | awk '{ FS = "[ :,]" ; print $1 }'
00:00:12,479

3
That didn't work as input was processed before delimiters were set. 
Adding BEGIN will set delimiters before input is read
echo '00:00:12,479 --> 00:00:15,578'  | awk 'BEGIN { FS = "[ :,]"} { print $1 } { print $3 }'
00
12

4
To calculate the speedup times the time fields are all converted
to milliseconds, totalled then mulitplied by the speedup factor. 
The new time is then re-expressed as hours,minutes etc. 
Only do this if total time is greater than zero (/0)

5
The time fields now contain integers instead of strings so output must be formatted.
$1 needs to be displayed to two significant places followed by a colon and new line "\n"
echo '1' | awk '{$1=int($1)};{printf "%2.2d" "%s\n", $1, ":" }'
01:

6
$4 needs to be displayed to three significant places followed by " --> " and new line
echo '1 1 1 1' | awk '{$4=int($4)};{printf "%3.3d" "%s\n", $4, " --> " }'
001 --> 

7
Pass thru all lines that are not timing lines
echo 'Well, you can guess' | awk '{if ($0 !~ "-->") {print}}'
Well, you can guess

8
Script speedup.awk to change frame rate from 25fps to 23.976fps
```

#!/usr/bin/awk -f

# this script should convert a 25fps subtitle file to a 23.976fps file.
# to convert subtitle file from 23.976 to 25fps switch denominator and 
# numerator of speedup multiplier

BEGIN { FS = "[ :,]"; speedup=25/23.976 } 
{if ($0 !~ "-->") {print}
else
{ 
start_time_ms  = ($1*3600000 + $2*60000 + $3*1000 + $4) * speedup;
if (start_time_ms > 0) {
$1=int(start_time_ms/3600000); start_time_ms %= 3600000; 
$2=int(start_time_ms/60000);   start_time_ms %= 60000; 
$3=int(start_time_ms/1000);    start_time_ms %= 1000; 
$4 = int(start_time_ms);
} 
# $6 $7 $8 $9 are the hours minutes seconds and milliseconds of the finish time
finish_time_ms = ($6*3600000 + $7*60000 + $8*1000 + $9) * speedup;
if (finish_time_ms > 0) {
$6=int(finish_time_ms/3600000); finish_time_ms %= 3600000; 
$7=int(finish_time_ms/60000);   finish_time_ms %= 60000; 
$8=int(finish_time_ms/1000);    finish_time_ms %= 1000; 
$9=int(finish_time_ms); 
}
{printf "%2.2d" "%s" "%2.2d" "%s" "%2.2d" "%s" "%3.3d" "%s",$1,":",$2,":",$3,",",$4," --> "}
{printf "%2.2d" "%s" "%2.2d" "%s" "%2.2d" "%s" "%3.3d\n"   ,$6,":",$7,":",$8,",",$9}
}}


```

---

