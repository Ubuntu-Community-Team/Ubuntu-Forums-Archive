---
title: "batch conversion using ffmpeg"
date: 2017-01-28
forum: Multimedia Software
---

### Post by jerome1232 on 2017-01-28
I have an entire folder of files that I want to convert using ffmpeg, I'm unsure of how to go about it.

I want to grab "filename which has spaces.m4v" feed it to an ffmpeg command and spit it out as "filename which has spaces - h265.mkv"

Can I do this with find and -exec?

---

### Post by Keith_Helms on 2017-01-28
There was a similar question not long ago and you could modify the script that we put together for that person.

```
#!/bin/bash

inputdir="***path to folder you want to convert***"
outputdir="***path to folder to write output files to***"
while IFS= read -r -d $'\0' file ; do
  video=`basename "$file"`
  videonotype=${video:0:${#video}-4}
  outputfile="${outputdir}/${videonotype}-h265.mkv"
  # check if output file already exists
  if [ ! -e "$outputfile" ]
  then
    ffmpeg -i "$file" ***options-to-create-output-file*** "$outputfile" < /dev/null
  fi
done < <(find "$inputdir" -name "*.m4v" -print0)
```

Change the portions in italics to the correct values, save the code in a file in your ~/bin directory (create it and log out and back in if ~/bin does not exist), mark it as executable with "chmod +x scriptname" and then you should be able to run it.

---

### Post by jerome1232 on 2017-01-28
Do you have a link to the original thread? I'm a little confused about the "videonotype" line and what it is doing.

I assume if I wanted to find all files I can modify that last line to find -type f? I have to run this with my pwd at the folder I'd like to convert?

my modified version:

```
#/bin/bash

inputdir="/home/jeremy/mkemkvrips"
outputdir="/home/jeremy/Videos"
while IFS= read -r -d $'\0' file; do
        video=`basename "$file"`
        videonotype=${video:0:${#video}-4}
        outputfile="${outputdir}/${videonotype}-h265.mkv"
        # check that output file exists
        if [ ! -e "$outputfile" ]
                then ffmpeg -i "$file" -c:v nvenc_hevc -profile:v main -pixel_format yuv444p -preset slow "$outputfile" < /dev/null
        fi
done < <( find "$inputdir" -type f -print0)

```

---

### Post by lisati on 2017-01-29
*Thread moved to **Multimedia Software**.*

---

### Post by Keith_Helms on 2017-01-29
The original thread was
[https://ubuntuforums.org/showthread.php?t=2331392](https://ubuntuforums.org/showthread.php?t=2331392)

The videonotype line is stripping off the m4a suffix so that a new filename can be created with the same name, but with a -h265.mkv suffix instead.

Using type -f would indeed find all files under whatever input directory you specified.  If there are any non m4a files, if would pull those in and the ffmpeg command might not work for that file.

The example code I gave is basically good for a single input directory containing m4a files.   If you want to be able to run it against any directory you could modify it to accept the input directory as a parameter.  Add the following after the #!/bin/bash line
```

if [ $# -ne 1 ]; then
    echo ""
    echo "USAGE: scriptname input-directory"
    exit
fi

```
And make the following change
```

inputdir="$1"

```
If you just want it to run against whatever directory you are currently in, you could make the following change instead
```

inputdir=`pwd`

```

Unless you use the "current directory" variation, you don't have to run the script within the target directory.  There's no reason you need to supply a password either.  Neither the directories nor the ffmpeg command require root access.

---

### Post by jerome1232 on 2017-01-29
Thanks!

---

### Post by jerome1232 on 2017-07-12
I wanted to leave this here for anyone stumbling on this thread. I recently decided to rip more dvd's and convert them, I had since lost this script and returned here to find it. As it was running I noticed that my video card in psensor showed at only around 50% usage. A little googling revealed that it can handle two jobs at once.

Running two encodes manually at the same time confirmed my card jumped to high 90%'s while running two jobs. So I set about finding a way to make the script run two jobs. I found this GNU tool called parallel.

[https://www.gnu.org/software/parallel/](https://www.gnu.org/software/parallel/)


Because I'm running this on a directory I know only has videos I want to convert, I don't have to anything fancy, just toss find at ffmpeg and let parallel do it's thing. Pretty awesome. It's really slamming through! I had to limit parallel to 2 jobs at once, ffmpeg throws an error about not being able to find a card since my card can only accept two encode jobs at once if a 3rd job is attempted. This one liner replaces that previous while loop for me.
```
time find -type f | parallel -j 2 --no-notice ffmpeg -i {/} -c:v nvenc_hevc -profile:v main -pixel_format yuv444p -preset slow test/{/}
```

---

