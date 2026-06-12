---
title: "Encoding HiRes video to Nokia 5800 XpressMusic"
date: 2009-08-16
forum: Multimedia Software
---

### Post by LaLLi on 2009-08-16
After trying literaly dozens of ways to encode video to my 5800 I became frustrated. Some of them worked and produced a decent video but with a low resolution of 320*240. Nokia 5800 has a screen resolution of 640*360 and I wasn't going to accept that my videos were sub-par and streched on the device.

So I found a free Windows program that works well in wine, is easy to use and has a decent performance, *Free Zune Video Encoder*.

Wine is needed to run this program. **[B]*sudo apt-get install wine***[/B] should do the trick.

1. Download the program. For example [here]("http://www.softpedia.com/get/Multimedia/Video/Encoders-Converter-DIVX-Related/Free-Zune-Video-Converter.shtml"). I used version 1.1.

2. Extract the zip file to a new folder. The program doesn't need to be installed. I created a folder to my home directory.

3. Run the prgram by double clicking ZuneConverter.exe.

4. Drag-n-Drop the files you want to convert.

5. Select the next options.
Output Format: MP4 (MPEG4/AAC)
Video bitrate: 600
Video FPS: 25
Resolution: 640 x 350 EGA

6. Click **CONVERT**.

Hope it works for you too.

---

### Post by sn0m on 2010-01-13
I do not know whether people still look this thread up but the following did it for me:

ffmpeg -i "input.avi" -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 "output.mp4"

---

### Post by 0xdeadcode on 2010-01-24
```
#!/bin/bash

echo enter source file folder, relative to Desktop
read FOLDER
echo enter name of source video file
read VIDFILE
echo extra ffmpeg parameters:
read PARAMS
VIDFILE2="$VIDFILE 5800.mp4"
echo "" > "/home/user/Desktop/$VIDFILE2"
chmod 0777 "/home/user/Desktop/$VIDFILE2"
ffmpeg -i "/home/user/Desktop/$FOLDER/$VIDFILE" -f mp4 -vcodec libxvid -acodec libfaac $PARAMS "/home/user/Desktop/$VIDFILE2"
echo DONE!
read DUMMY
```

here is a little script i wrote for myself. just copy 'n paste the code in a file named for example convert.sh, open a command line, execute chmod 0755 path/to/convert.sh, and then ./convert.sh. the vid keeps it's original size and will play in good quality on the phone.

hth

---

### Post by Ekeluo on 2010-08-15
> **LaLLi said:**
> After trying literaly dozens of ways to encode video to my 5800 I became frustrated. Some of them worked and produced a decent video but with a low resolution of 320*240. Nokia 5800 has a screen resolution of 640*360 and I wasn't going to accept that my videos were sub-par and streched on the device.

So I found a free Windows program that works well in wine, is easy to use and has a decent performance, *Free Zune Video Encoder*.

Wine is needed to run this program. **[B]*sudo apt-get install wine***[/B] should do the trick.

1. Download the program. For example [here]("http://www.softpedia.com/get/Multimedia/Video/Encoders-Converter-DIVX-Related/Free-Zune-Video-Converter.shtml"). I used version 1.1.

2. Extract the zip file to a new folder. The program doesn't need to be installed. I created a folder to my home directory.

3. Run the prgram by double clicking ZuneConverter.exe.

4. Drag-n-Drop the files you want to convert.

5. Select the next options.
Output Format: MP4 (MPEG4/AAC)
Video bitrate: 600
Video FPS: 25
Resolution: 640 x 350 EGA

6. Click **CONVERT**.

Hope it works for you too.

Thanks for this, have been looking for a reliable converter for videos for my newly purchased 5800. Trying it now.

---

