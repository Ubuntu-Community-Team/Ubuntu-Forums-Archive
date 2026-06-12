---
title: "Problem splitting a LONG mp3 in to parts with sox"
date: 2012-04-18
forum: Multimedia Software
---

### Post by Ferralll on 2012-04-18
So I have an audio book that I want to listen to on my Walkman. 

My problem is that it is in a single part.  27 hours long.  As a walkman can only fastforward at a rate of about 1 min per second, that is a real pain in the but if I loose my place in the middle of the book.  So I decided to split it up in to 1 hr segments. 

I did this with sox, I used the command
```
 sox file_in.mp3 file_out.mp3 trim START LENGTH
```

But I found that for any value of START and LENGTH that went beyond 13 hours in the MP3, it started over, or returned a truncated file.

Examples: 
```
 sox file_in.mp3 file_out.mp3 trim 46800 3600
```
This should start at hour 13 and end at hour 14.  Instead I get a 2 minute segment.  

If I do ```
 sox file_in.mp3 file_out.mp3 trim 46740 3600
```
Then I get a 3 minute segment, that ends at the same point of the first example.

If I do ```
sox DUNE_II.mp3 TEST.mp3 trim 54000 120
```
It should start at hour 15, and be 2 min long.  I get a 2 minute segment (as expected) but it begins at time 1:23:29 for some reason.  


I can not figure out why it will not go beyond that length, and why it is not working.  Any thoughts? Or some alternitive to break up the file?


I am running ubuntu 10.04.

---

### Post by shantiq on 2012-04-19
of course and i think you have seen my thread too   the problem is that SoX re-encodes and takes forever


[**there is**]("http://ubuntuforums.org/showpost.php?p=11853909&postcount=6") **a much easier route** with mp3splt   [pointed out to me by Temujin]    and it is extremely fast since it does not re-encode [unlike SoX] but simply cuts

Took me 10 seconds to split a six-hour file into six equal parts and it makes sure about corrections too



```
mp3splt -f -t 60.0 -a -d split inputfile.mp3

```

---

### Post by flurospar on 2012-04-19
Or use ffmpeg:

Install:
```

sudo apt-get install ffmpeg

```Do the splitting:
```

ffmpeg -ss 00:00:00.000 -t 3600 -acodec copy -i audiobook.mp3 split.book.1.mp3

```

Repeat till the whole thing is split, increasing the [hh]:[mm]:[ss].[millisecond] by one hour each time.

---

### Post by Ferralll on 2012-04-19
I just used mp3splt,
and it seems to work perfectly. And it is very fast! Took only a minute, where sox took about 3 hours.  Thanks for the heads up.

The only thing that I did not like was the output format that was default. So I used the command 
```
 mp3splt -f -t 60.0 -a -o @toutput_name-@N -d split  input_file.mp3 
```

So instead of getting file names of : input_file_00m_00s__60m_00s.mp3

I get : output_name-01.mp3

(option -o @t[file name]@N; where  @t uses [file name] as the initial tag, and adds on @N which increments the file names)

I have not tried ffmpeg, but for that I would have to write up a simple batch command to do lots of files.  (for 27 hours, it is to much of a pain in the butt to do it manually 27 times)

---

