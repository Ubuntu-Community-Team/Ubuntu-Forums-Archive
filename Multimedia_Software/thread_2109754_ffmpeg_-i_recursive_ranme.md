---
title: "ffmpeg -i recursive ranme"
date: 2013-01-28
forum: Multimedia Software
---

### Post by sohlinux on 2013-01-28
Hello, 

How can I run ffmpeg -i recursively and write the output to the folder 

example : a folder has 10 sub folders

folder 1 has a video.mp4

folder 2 has a video.mp4

I need it to rename the folder and add the video info bitrate, size, duration

so the new folder will be called

folder 1 19700kbps 1920x1080 14 mins 9 seconds

I need to recurse all folders

thanks

---

### Post by evilsoup on 2013-01-28
I'd recommend using ffprobe if you're just getting information (it comes with ffmpeg). Well, actually I'd recommend using mediainfo, since I find that it's easier to regex.

This will get the resolution of a video:
```

ffprobe video.mp4 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p'

```'2>&1' makes ffprobe send stderr to stdout.

'/Video:/' tells sed to find a line containing 'Video:' (which is the line containing the video information, like resolution).

's/.* \([0-9]*x[0-9]*\).*/\1/p' tells sed to delete everything on the line except for the first match of the pattern '[0-9]*x[0-9]*'.

[Here]("http://www.grymoire.com/Unix/Sed.html") is a pretty comprehensive guide to sed.

Obviously you'll want to put the output of that into a variable.

```

resolution=$(ffprobe video.mp4 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p')

```

To get bit rate:
```

ffprobe video.mp4 2>&1 | sed -n '/bitrate:/s/.* \([0-9]*\) .*/\1kbps/p'

```File duration (note that this will output the time in the format hh:mm:ss):
```

ffprobe video.mp4 2>&1 | sed -n '/Duration:/s/.* \([0-9]*:[0-9]*:[0-9]*\)\..*/\1/p'

```For the actual renaming, you can simply use mv.

For recursive stuff, I would probably use find.
```

find . -maxdepth 1 -mindepth 1 -type d

```...will output all directories in the current directory. I would use it in combination with a while read loop, so your script will look something like:

```

find . -maxdepth 1 -mindepth 1 -type d | while read dir
do
    cd "$dir"
##  set variables containing your regexed ffprobe date
    cd ../
    mv "$dir" "$dir $bitrate $resolution $time"
done

```

---

### Post by sohlinux on 2013-01-29
> **evilsoup said:**
> I'd recommend using ffprobe if you're just getting information (it comes with ffmpeg). Well, actually I'd recommend using mediainfo, since I find that it's easier to regex.

This will get the resolution of a video:
```

ffprobe video.mp4 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p'

```'2>&1' makes ffprobe send stderr to stdout.

'/Video:/' tells sed to find a line containing 'Video:' (which is the line containing the video information, like resolution).

's/.* \([0-9]*x[0-9]*\).*/\1/p' tells sed to delete everything on the line except for the first match of the pattern '[0-9]*x[0-9]*'.

[Here]("http://www.grymoire.com/Unix/Sed.html") is a pretty comprehensive guide to sed.

Obviously you'll want to put the output of that into a variable.

```

resolution=$(ffprobe video.mp4 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p')

```

To get bit rate:
```

ffprobe video.mp4 2>&1 | sed -n '/bitrate:/s/.* \([0-9]*\) .*/\1kbps/p'

```File duration (note that this will output the time in the format hh:mm:ss):
```

ffprobe video.mp4 2>&1 | sed -n '/Duration:/s/.* \([0-9]*:[0-9]*:[0-9]*\)\..*/\1/p'

```For the actual renaming, you can simply use mv.

For recursive stuff, I would probably use find.
```

find . -maxdepth 1 -mindepth 1 -type d

```...will output all directories in the current directory. I would use it in combination with a while read loop, so your script will look something like:

```

find . -maxdepth 1 -mindepth 1 -type d | while read dir
do
    cd "$dir"
##  set variables containing your regexed ffprobe date
    cd ../
    mv "$dir" "$dir $bitrate $resolution $time"
done

```


thanks for the info, the following works ok with video size for example 720x576 but I needed to change the part where you wrote /video because in my case the name of the file is not video so I just removed that part

```
ffprobe *.avi 2>&1 | sed -n '/:/s/.* \([0-9]*x[0-9]*\).*/\1/p'

```

the following doesnt appear to do anything? I also removed /video
```
resolution=$(ffprobe *.avi 2>&1 | sed -n '/video:/s/.* \([0-9]*x[0-9]*\).*/\1/p')
```

the following works fine with bit rate
```
ffprobe *.avi 2>&1 | sed -n '/bitrate:/s/.* \([0-9]*\) .*/\1kbps/p'

```

the following works fine with duration
```
ffprobe *.avi 2>&1 | sed -n '/Duration:/s/.* \([0-9]*:[0-9]*:[0-9]*\)\..*/\1/p'
```

at this point I am stuck,
[/home_videos2007]# /scripts/1-ffprobe.sh
./0390-26
./0380-16
./0389-16
./0379-20
./0381-19
/scripts/1-ffprobe.sh: line 41: cd: ./0390-26: No such file or directory
mv: cannot stat `./0390-26': No such file or directory


```
find . -maxdepth 1 -mindepth 1 -type d
find . -maxdepth 1 -mindepth 1 -type d | while read dir
do
    cd "$dir"
##  set variables containing your regexed ffprobe date
    cd ../
    mv "$dir" "$dir $bitrate $resolution $time"
done
```

thanks

---

### Post by evilsoup on 2013-01-29
> 
thanks for the info, the following works ok with video size for example  720x576 but I needed to change the part where you wrote /video because  in my case the name of the file is not video so I just removed that part
'/Video:/' (capital V is important) looks for a line containing the string 'Video:' - it's like using 'grep "Video:"' and feeding that to sed. FFprobe always identifies the video stream in a video with a line a bit like:

```

    Stream #0:0(und): Video: h264 (Constrained Baseline) (avc1 / 0x31637661), yuv420p, 320x180 [SAR 1:1 DAR 16:9], 694 kb/s, 24 fps, 24 tbr, 12288 tbn, 48 tbc

```The line contains 'Video:' no matter what the actual filename is, since it signifies that the line is describing a video stream.

Furthermore, using '/:/' will tell sed to use every line containing a colon - and with ffprobe's output, that's most of the lines. Which can give you problems if you're trying to put it into a variable (it won't in this particular case, but in general you should get into the habit of being as specific as possible for the problem at hand).

> 
```

[/home_videos2007]# /scripts/1-ffprobe.sh
...
/scripts/1-ffprobe.sh: line 41: cd: ./0390-26: No such file or directory
mv: cannot stat `./0390-26': No such file or directory

```I *think* the problem is that you are trying to run the script from within the directory '/scripts', and so the script is trying to cd into '/scripts/0390-26' - which obviously doesn't exist.

I would just put the script in a directory described in my $PATH (~/bin is the standard one for user scripts).

Alternatively, you can
```

##  Replace:
find . -maxdepth 1 -mindepth 1 -type d
## with
find . -maxdepth 1 -mindepth 1 -type d -exec readlink -f {} \;

```

This will make find output the absolute /path/to/each/directory.

Also, can you paste up the script as you have it written so far?

---

### Post by sohlinux on 2013-01-29
> **evilsoup said:**
> '/Video:/' (capital V is important) looks for a line containing the string 'Video:' - it's like using 'grep "Video:"' and feeding that to sed. FFprobe always identifies the video stream in a video with a line a bit like:

```

    Stream #0:0(und): Video: h264 (Constrained Baseline) (avc1 / 0x31637661), yuv420p, 320x180 [SAR 1:1 DAR 16:9], 694 kb/s, 24 fps, 24 tbr, 12288 tbn, 48 tbc

```The line contains 'Video:' no matter what the actual filename is, since it signifies that the line is describing a video stream.

Furthermore, using '/:/' will tell sed to use every line containing a colon - and with ffprobe's output, that's most of the lines. Which can give you problems if you're trying to put it into a variable (it won't in this particular case, but in general you should get into the habit of being as specific as possible for the problem at hand).

I *think* the problem is that you are trying to run the script from within the directory '/scripts', and so the script is trying to cd into '/scripts/0390-26' - which obviously doesn't exist.

I would just put the script in a directory described in my $PATH (~/bin is the standard one for user scripts).

Alternatively, you can
```

##  Replace:
find . -maxdepth 1 -mindepth 1 -type d
## with
find . -maxdepth 1 -mindepth 1 -type d -exec readlink -f {} \;

```

This will make find output the absolute /path/to/each/directory.

Also, can you paste up the script as you have it written so far?

I moved the scrip to bin and ran sh 1-ffprobe.sh  

me@box [/data/videos7]# sh 1-ffprobe.sh                  
/data/videos7/0390-26                                         
/data/videos7/0380-16                                         
/data/videos7/0389-16                                         
/data/videos7/0379-20                                         
/data/videos7/0381-19                                         
1-ffprobe.sh: line 15: cd: ./0390-26: No such file or directory
mv: cannot stat `./0390-26': No such file or directory         
1-ffprobe.sh: line 15: cd: ./0380-16: No such file or directory
mv: cannot stat `./0380-16': No such file or directory         
1-ffprobe.sh: line 15: cd: ./0389-16: No such file or directory
mv: cannot stat `./0389-16': No such file or directory
1-ffprobe.sh: line 15: cd: ./0379-20: No such file or directory
mv: cannot stat `./0379-20': No such file or directory
1-ffprobe.sh: line 15: cd: ./0381-19: No such file or directory
mv: cannot stat `./0381-19': No such file or directory
me@box [/data/videos7]#


here is the script, I changed video.mp4 for *.avi because this folder are all avi files

```
#!/bin/bash

ffprobe *.avi 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p'

resolution=$(ffprobe *.avi 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p')

ffprobe *.avi 2>&1 | sed -n '/bitrate:/s/.* \([0-9]*\) .*/\1kbps/p'

ffprobe *.avi 2>&1 | sed -n '/Duration:/s/.* \([0-9]*:[0-9]*:[0-9]*\)\..*/\1/p'

find . -maxdepth 1 -mindepth 1 -type d -exec readlink -f {} \;

find . -maxdepth 1 -mindepth 1 -type d | while read dir
do
    cd "$dir"
##  set variables containing your regexed ffprobe date
    cd ../
    mv "$dir" "$dir $bitrate $resolution $time"
done
```

---

### Post by evilsoup on 2013-01-29
OK try this:

```

#!/bin/bash

find . -maxdepth 1 -mindepth 1 -type d -exec readlink -f '{}' \; | while read dir
do
vid=$(find "$dir" -type f -name "*.avi" | head -n 1)

    bitrate=$(ffprobe "$vid" 2>&1 | sed -n '/bitrate:/s/.* \([0-9]*\) .*/\1kbps/p')
    resolution=$(ffprobe "$vid" 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p')
    duration=$(ffprobe "$vid" 2>&1 | sed -n '/Duration:/s/.* \([0-9]*:[0-9]*:[0-9]*\)\..*/\1kbps/p')

    mv "$dir" "$dir $bitrate $resolution $duration"
done

exit 0

```

---

### Post by sohlinux on 2013-01-29
> **evilsoup said:**
> OK try this:

```

#!/bin/bash

find . -maxdepth 1 -mindepth 1 -type d -exec readlink -f '{}' \; | while read dir
do
vid=$(find "$dir" -type f -name "*.avi" | head -n 1)

    bitrate=$(ffprobe "$vid" 2>&1 | sed -n '/bitrate:/s/.* \([0-9]*\) .*/\1kbps/p')
    resolution=$(ffprobe "$vid" 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p')
    duration=$(ffprobe "$vid" 2>&1 | sed -n '/Duration:/s/.* \([0-9]*:[0-9]*:[0-9]*\)\..*/\1kbps/p')

    mv "$dir" "$dir $bitrate $resolution $duration"
done

exit 0

```

thanks but I must be missing something very basic here

I placed the script in /bin/1-ffprobe.sh  

I ran the command from the directory which has all the videos in sub directories

while inside /data/videos/ directory I typed sh 1-ffprobe.sh  

but still getting mv: cannot stat `./0381-19': No such file or directory

---

### Post by evilsoup on 2013-01-29
I just tested it, and it worked fine on a few test directories on my machine.

Since 1-ffprobe.sh is in your $PATH (and you've presumably marked it as executable), ditch the sh - I suspect that what is happening is that you have the broken version of the script you quoted upthread within your working directory (sh doesn't read your $PATH, it needs a /path/to/script). Just type
```

1-ffprobe.sh

```...and it should work.

---

### Post by sohlinux on 2013-01-29
> **evilsoup said:**
> I just tested it, and it worked fine on a few test directories on my machine.

Since 1-ffprobe.sh is in your $PATH (and you've presumably marked it as executable), ditch the sh - I suspect that what is happening is that you have the broken version of the script you quoted upthread within your working directory (sh doesn't read your $PATH, it needs a /path/to/script). Just type
```

1-ffprobe.sh

```...and it should work.


Its working fine now, thanks for all your help

a couple more things, what do I need to change in the script so it renames the files not the directories?

also if some directories have mp4 or wmv how do I add those so I dont need to keep changing the script to *.mp4 or *.wmv

---

