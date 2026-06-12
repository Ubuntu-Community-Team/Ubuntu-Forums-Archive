---
title: "FFMPEG - Renaming MULTIPLE files using metadata tags"
date: 2019-02-15
forum: Multimedia Software
---

### Post by Alan5127 on 2019-02-15
Hi All,

I asked a previous question a few days ago, about how to rename mkv files, using ffmpeg, by pulling the 'Title' metadata tag from the file using ffmpeg.

That question was answered by Holger_Gehrke here:

[https://ubuntuforums.org/showthread.php?t=2412446](https://ubuntuforums.org/showthread.php?t=2412446)

The solution provided was:

```
ffmpeg -i InputFile.mkv -vcodec copy -acodec mp3 "$(ffmpeg -hide_banner -loglevel quiet -i InputFile.mkv -f ffmetadata -|awk -F'=' -- '/^title/ {print $2}' -)".mkv
```

That works perfectly (thanks again Holger!).


Now, if possible, I'd like to apply that to multiple files in a single directory.

I know I can create a bash script that will do this, but I was trying to do it on a single line ;)


So, I started from this, which does something similar to what I want, albeit the purpose of this command is to take each mkv, and convert the audio stream to MP3 so it will play on a given device (that only likes MP3):

```
mkdir NEW; find . -iname "*.mkv" -print0 | xargs -0 -i -n1 ffmpeg -i {} -vcodec copy -acodec mp3 -scodec copy "NEW/{}"
```

As you can probably tell, it takes each file in the directory, converts the audio to MP3, and writes the new file to the NEW\ sub-directory.


So, I figured I could repurpose that, and substitute Holger_Gehrke's line, into the multiple-file command above, and got this:

```
mkdir NEW; find . -iname "*.mkv" -print0 | xargs -0 -i -n1 ffmpeg -i {} -vcodec copy -acodec "NEW/$(ffmpeg -hide_banner -loglevel quiet -i {} -f ffmetadata -|awk -F'=' -- '/^title/ {print $2}' -)".mkv"
```

However, this fails, and I am guessing (but not certain by any means) that it might be due to the output filename failing to 'construct' between the double quotes and the use of the variables.


Can anyone suggest a way to do this on one line?

Thanks,

Alan.

---

### Post by Holger_Gehrke on 2019-02-16
The problem is that the command substitution (the commands inside $(... ) ) is executed before xargs, so {} can't be used in there. Unless you actually need the 'find' / 'xargs' combination because the input files are spread over several sub-directories of '.' , I'd use a loop instead:
```

for i in in *.mkv ; do echo ffmpeg -i "$i" -vcodec copy -acodec mp3 "NEW/$(ffmpeg -hide_banner -loglevel quiet -i "$i" -f ffmetadata -|awk -F'=' -- '/^title/ {print $2}' - )".mkv ; done

```
This has (at least) one problem (if there's an mkv-file without a title-tag in the batch, it will be named '.mkv'; if there's two or more of them, ffmpeg will stall and ask whether you want to overwrite that file), but should work.

Holger

---

### Post by Alan5127 on 2019-02-16
Hi Holger,

> **Holger_Gehrke said:**
> The problem is that the command substitution (the commands inside $(... ) ) is executed before xargs, so {} can't be used in there. Unless you actually need the 'find' / 'xargs' combination because the input files are spread over several sub-directories of '.' , I'd use a loop instead:
```

for i in in *.mkv ; do echo ffmpeg -i "$i" -vcodec copy -acodec mp3 "NEW/$(ffmpeg -hide_banner -loglevel quiet -i "$i" -f ffmetadata -|awk -F'=' -- '/^title/ {print $2}' - )".mkv ; done

```
This has (at least) one problem (if there's an mkv-file without a title-tag in the batch, it will be named '.mkv'; if there's two or more of them, ffmpeg will stall and ask whether you want to overwrite that file), but should work.

Holger


This looks very close, but it doesn't seem to actually do anything.  I first figured I needed to create the subfolder, so I tried this:

```

mkdir NEW; for i in in *.mkv ; do echo ffmpeg -i "$i" -vcodec copy -acodec mp3  "NEW/$(ffmpeg -hide_banner -loglevel quiet -i "$i" -f ffmetadata -|awk  -F'=' -- '/^title/ {print $2}' - )".mkv ; done

```

This does seem to be required (I did not mention that the subfolder does not pre-exist - my bad), however, that still fails, and I am wondering if it is due to spaces in the input and output filenames, causing it to fail.

One individual line of the loop evaluates like this:

```
ffmpeg -i 20190131 1600.mkv -vcodec copy -acodec mp3 NEW/Report 20190131 North.mkv
```


If I run that line standalone, it does not work, whereas if I put each of the input and output filenames in double quotes like this, it works:

```
ffmpeg -i "20190131 1600.mkv" -vcodec copy -acodec mp3 "NEW/Report 20190131 North.mkv"
```


Is there any way to get around that?

Thanks,

Alan.

---

### Post by Holger_Gehrke on 2019-02-17
Sorry, I forgot to take out the 'echo" command I used to test this. I tried it in a directory with some videos and didn't want to wait for  it to complete converting all those videos, so I made it output the  commands it would execute instead of actually doing it ...
 So it should be :
```

mkdir NEW; for i in in *.mkv ; do ffmpeg -i "$i" -vcodec copy -acodec mp3 "NEW/$(ffmpeg -hide_banner -loglevel quiet -i "$i" -f ffmetadata -|awk -F'=' -- '/^title/ {print $2}' - )".mkv ; done

```
If you look closely, you'll see that there already are double quotes surrounding $i and the command substitution used to generate the output file name in the command; they don't get printed but they do their job - making the shell see a string containing spaces as one token. You might want to put an 'echo $i;' after the 'do ' so you can see what it's currently working on, because the options '--hide_banner' and '--loglevel quit' should stop ffmpeg from printing out the usual report.

Holger

---

### Post by Alan5127 on 2019-02-18
Hi Holger,

> **Holger_Gehrke said:**
> Sorry, I forgot to take out the 'echo" command I used to test this. I tried it in a directory with some videos and didn't want to wait for  it to complete converting all those videos, so I made it output the  commands it would execute instead of actually doing it ...
 So it should be :
```

mkdir NEW; for i in in *.mkv ; do ffmpeg -i "$i" -vcodec copy -acodec mp3 "NEW/$(ffmpeg -hide_banner -loglevel quiet -i "$i" -f ffmetadata -|awk -F'=' -- '/^title/ {print $2}' - )".mkv ; done

```
If you look closely, you'll see that there already are double quotes surrounding $i and the command substitution used to generate the output file name in the command; they don't get printed but they do their job - making the shell see a string containing spaces as one token. You might want to put an 'echo $i;' after the 'do ' so you can see what it's currently working on, because the options '--hide_banner' and '--loglevel quit' should stop ffmpeg from printing out the usual report.

Holger


Ha - Can't believe I didn't notice the 'echo' in there.

{Alan hangs his head in shame}

Just  to note that there is also a repeat 'in' (for i in in *.mkv), which I did notice  originally, and forgot to mention above.  This is the final version that  works for me:

```

mkdir NEW; for i in *.mkv ; do ffmpeg -i "$i" -vcodec copy -acodec  mp3 "NEW/$(ffmpeg -hide_banner -loglevel quiet -i "$i" -f ffmetadata  -|awk -F'=' -- '/^title/ {print $2}' - )".mkv ; done

```


Brilliant - You're a star!

I definitely learned a few things over the last week :-)

Thanks,

Alan.

---

### Post by trebelnik-stefina on 2020-01-07
Can this be done with **mkvmerge/mkvinfo/mkvextract/mkvpropedit** without reencoding video files?

I have after checking disk running during PC boot found folder with about 100 file000000A1.chk ... files,
chk extension I was able to change, but now I searching a way to somehow change filename of mkv's, read from tag **Title** and then change **filename**

---

### Post by trebelnik-stefina on 2020-01-07
I found this solution:
```
for f in *.mkv;do mv -- "$f" "$(mkvinfo "$f"  | grep "Title:" | awk -F":" '{print $2$3$4}').mkv";done
```
This is renaming files without copying them.

---

