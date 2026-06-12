---
title: "Download and merge multiple mp4 files on the fly"
date: 2021-01-10
forum: Multimedia Software
---

### Post by dome78 on 2021-01-10
Hi,
I need to download and merge multiple mp4 files on the fly. These are many 1 megabyte mp4 files. I created a script (I'm not an expert in this) to download them individually, but then manually merging them with avidemux fills all the ram of the PC.  The script looks like this:  

for i in $ (seq 1000000);    
do 
wget https://address.com/file$i.mp4
done

Is there a way to download and merge all these files on the fly?
Thanks

---

### Post by TheFu on 2021-01-10
I'm sure there is, but I'd pull the files down 1 at a time and use mkvmerge myself. I have a script that will merge file-001.mkv .... file-999.mkv into a single file.mkv.   From the mkvmerge manpage:

```
SYNOPSIS
       mkvmerge [global options] {-o out} [options1] {file1}
                [[options2] {file2}] [@optionsfile]
```

$ more ~/bin/mkv-merge.sh 
```
#!/bin/bash

if [ "X$1" = "X" ] ; then
  echo "Usage: $0 file-001.mkv"
  exit 1;
fi

ROOT=`echo $1 | sed -e 's/-001.mkv//g'` 
CNT=1

OUT="mkvmerge -o \"$ROOT.mkv\" \"$ROOT-00$CNT.mkv\" "

for CNT in {002..999} ; do
  if [ -f "$ROOT-$CNT.mkv" ] ; then
    OUT="$OUT + \"$ROOT-$CNT.mkv\""
  fi
done
echo $OUT | sh -

```

It is for mkv files, but tweaking it to support .mp4 input files wouldn't be hard.  Leading zeros can be moved in the for-loop line.  Just change the 002 --> 2.

Hope this gives you some ideas.  Oh - and no spaces (or other odd characters) are allowed in the filenames. Some might work. Who knows?

Update: this tool will also validate that the input files all match on important muxing parameters.  It doesn't transcode anything, so it is as fast as a file copy and because most of the files will likely be in the OS-managed buffers, performance will be about the same as a file copy.

---

### Post by vanadium on 2021-01-10
In principle, ffmpeg can take input from an URL, but I am not sure whether you could concatenate this way. I would rather work with a script that 1) downloads the file and 2) concatenates that to the video file that contains the already downloaded parts. See [here]("https://trac.ffmpeg.org/wiki/Concatenate") on how that works. It boils down to creating a text file listing files you want to concatenate ("mylist.txt"), after which you concatenate the files with
```
ffmpeg -f concat -safe 0 -i mylist.txt -c copy output.mp4
```

Actually, to concatenate only a few files, following also works:
```
ffmpeg -i concat:"input1.mp4|input2.mp4" output.mp4
```

You could have your script 1) download a new file 2) add it to the concatenated file of the previous downloads to a new concatenated file 3) move the new file out or delete it 4) delete the contaminated file of the previous downloads and give its name to the new concatenated file to append in the next loop.

This command transmuxes, i.e., it does not recode and should not need excessive memory. For this to work, the files you download should be exactly the same format (codecs, resolution).

On a more advanced level, true on the fly concatenation may be possible with a [named pipe]("https://www.networkworld.com/article/3251853/why-use-named-pipes-on-linux.html"). You would download to the pipe, and on the other end ffmpeg would read from the pipe. I have no experience whatsoever if and how this would work with ffmpeg.

---

### Post by dome78 on 2021-01-10
Thanks, i will try

---

