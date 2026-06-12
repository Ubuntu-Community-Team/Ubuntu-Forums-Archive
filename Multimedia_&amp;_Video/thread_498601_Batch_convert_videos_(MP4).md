---
title: "Batch convert videos (MP4)?"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by Mischief on 2007-07-11
Hi,

I'm looking for a way to convert videos to MP4-format for use with my PSP.
The application should be able to batch convert videos.

I downloaded PSPVC from [http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/)
At the page it states that:

> PSPVC is a FFMPEG front-end to convert video files for the PSP.
It allow you to _queue severals conversions_ with different parameters for each. 

I cannot figure out how to do it however. There's no such option in the application.
[IMG]http://pspvc.sourceforge.net/images/capture.png[/IMG]

Does anyone know an application that is capable of this? It would be too much work to convert them one by one.

Thanks!

//Mischief

---

### Post by netyire on 2007-07-15
Hello!

Heres a bash script to convert all the files in a folder of your choice to psp compatible files via mencoder. The script will place the converted files in a directory called "Converted" inside the folder you specify. The script is attached, just download it and place it the folder containing the folder with your files.

For example, if you have a folder named "video_clips" in your $HOME/Multimedia directory, place the script in the Multimedia directory, then open a terminal and type:

```

cd ~/Multimedia
chmod a+x 2psp.sh
./2psp.sh video_clips

```

Then just go to bed and leave it running while it works. It may take some time if you have alot of files. Do take note of the following though:

1. Make sure that the folder and the files inside do not have any spaces in their filenames, this will cause the script to fail.
2. Make sure you have mencoder installed, if not, type the following into your terminal:
```
sudo apt-get install mencoder
```
3. Take note of the firmware version on your psp, if it is above or at 2.0, the files may play just fine, if not, please update the firmware on your psp or download the 2nd script.

Enjoy Your Movies! Oh and feel free to open the script, you can change things like the video bitrate, audio bitrate and video framerate.

---

### Post by Mischief on 2007-07-30
Thanks buddy!

I'll try it out right away!

---

