---
title: "Auto Convert Videos"
date: 2010-07-24
forum: Multimedia Software
---

### Post by Kurzweil on 2010-07-24
Okay, here is what I have and am looking to do.

I've got an old box running Ubuntu server headless and I'm setting it up as a media server. Basically what I would like is a way to convert videos that get downloaded to it into a format my PS3 and iPhone can read automatically which I think would be mp4. 

I'm been scouring the forums and it looks like I'll need to use an ffmpeg and crontab combo but I'm having a hard time putting it all together.

Ideally, the script would need to check though folders to find video files that aren't mp4 and convert them. 

Thank you for any help.

---

### Post by FakeOutdoorsman on 2010-07-25
I'm no bashologist, but here's simple script:
```
#!/bin/sh

# stop script upon error
set -e

# encode all files in ~/incoming to iPod compatible videos
echo "Encoding videos."
find ~/incoming -type f -exec basename '{}' \; | xargs -i ffmpeg -i ~incoming/'{}' -vcodec libx264 -vpre slow -vpre ipod640 -acodec libfaac -aq 100 -ac 2 -vf scale=640:-1 -threads 0 -map_meta_data 0:0 -y ~/ipod/'{}'.mp4

# move encoded videos from ~/incoming to ~/converted
mv ~/incoming/* ~/converted

echo "Job is done."

exit
```

You can dump this into a file named *vidvert.sh* or whatever and then give it the proper permissions with:
```
chmod +x vidvert.sh
```
Combine this script with crontab: [How-to for crontab](http://ubuntuforums.org/showthread.php?t=102626). What the script does is encode all files in the *incoming* directory (in my home directory in my example). The encoded videos go in *~/ipod*, and then the original videos are moved to the *~/converted* directory. I don't own an iPod or a PS3, so I did not test this on those devices, although I'm confident that it will work on iPod.

Unfortunately the encoded videos will still have the old extension in the file name, such as *monkeys-have-hands-for-feet.avi.mp4*.  The **basename** part of the code intended to deal with that but I didn't figure it out.

You may need a recent FFmpeg for the command to work: specifically **-vf scale=640:-1** which will resize the video properly for iPod. Good thing compiling FFmpeg is easy on Ubuntu:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

