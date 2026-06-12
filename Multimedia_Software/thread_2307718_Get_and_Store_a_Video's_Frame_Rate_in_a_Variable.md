---
title: "Get and Store a Video's Frame Rate in a Variable"
date: 2015-12-27
forum: Multimedia Software
---

### Post by Elijah_Duffy on 2015-12-27
First off, I am not sure if this is in the right sub-forum, and if it isn't, sorry.

I am trying to create a bash script that will get, store, and output the frame rate of a video in a variable using FFMPEG. My purpose is to create a script that will do things such as change the frame rate of a video, convert the video format, etc...

From suggestions on other sites, I got the following:
```
ffmpeg -i ${input} 2>&1 | grep -o -P "(?<=fps ).*?(?=,)"
```
But that doesn't seem to work.

My full code is:
```
#! /bin/bash
#About this Program:
#fpsCheck outputs the frame rate and other information about a video in readable format.
#
#CREDIT:
#Source Code by: Elijah Duffy
#Contact: enduffy2014@outlook.com
#
#LICENSE
#YOU ARE FREE TO COPY AND USE THIS CODE FOR ANYTHING YOU WISH UNDER THE FOLLOWING CONDITIONS:
# 1. Include this LICENSE
# 2. Include the "CREDIT" section
# 3. Give specific credit to the original author (Elijah Duffy)

clear
#Debug Option
debug="$1"
  if [[ $debug == "--debug" ]]
    then dtf=true
    else dtf=false
  fi

  if [[ $dtf == true ]]
    then
      echo "Debug Mode Enabled"
      echo ""
    else
      echo "Debug Mode Disabled. To enable debug mode, include --debug when you run the script."
      echo ""
fi


#Enter input file full path
echo "NOTE: Please enter a real file path (not just a fake test)"
read -p "Please enter the full path to your input file (including the extension) : " input

ffmpeg -i ${input} 2>&1 | grep -o -P "(?<=fps ).*?(?=,)"


```

Thanks. Any help would be appreciated.

---

### Post by viewera on 2015-12-28
Try this
```
ffmpeg -i ${input} 2>&1 | sed -n "s/.*, \(.*\) fp.*/\1/p"
```

---

### Post by FakeOutdoorsman on 2015-12-28
From [FFmpeg Wiki: FFprobe Tips](https://trac.ffmpeg.org/wiki/FFprobeTips#FrameRate)
```
ffprobe -v error -select_streams v:0 -show_entries stream=avg_frame_rate -of default=noprint_wrappers=1:nokey=1 input.mp4
```

Example output:
```
24000/1001
```

[list]
[*]Using ffmpeg and parsing the output with awk, sed, grep, etc, can be fragile and often ends up incorrect depending on the input.
[*]Some inputs may contain several video streams. This example chooses the first one.
[*]Some streams may be variable frame rate.
[*]Use [shellcheck](http://www.shellcheck.net/) on your Bash script to check for errors, etc.
[/list]

---

