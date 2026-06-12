---
title: "What can I use to replace GoPro Studio?"
date: 2018-09-03
forum: Multimedia Software
---

### Post by Lonnie_S on 2018-09-03
Hi, What I need is to take my GoPro photos to create a time lapse. I know there has to be a way to do it. But so far all I find is slideshows. I am using Ubuntu Studio 18.3 and  GoPro3 Black. Ok What I found is this [https://ubuntuforums.org/showthread.php?t=2022316](https://ubuntuforums.org/showthread.php?t=2022316) . I am not a command line user.                                                                                                                                                                                                                                                                        [COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
mkdir source_folder_of_pictures
cp /media/cf/* source_folder_of_pictures/
cd source_folder_of_pictures
mkdir renamed
counter=1
ls -1tr *.jpg | while read filename; do cp $filename renamed/$(printf %05d $counter)_$filename; ((counter++)); done
cd renamed

---

### Post by Frogs Hair on 2018-09-03
Hello and Welcome 

I found the following [project ]("https://github.com/konradit/gopro-linux")which would require manual installation. I have not installed or used this software.

---

### Post by Lonnie_S on 2018-09-04
Thanks for the help. I installed the mplayer and ffmpeg . then ran this command .

sudo curl [https://raw.githubusercontent.com/KonradIT/gopro-linux/master/gopro](https://raw.githubusercontent.com/KonradIT/gopro-linux/master/gopro) -o /usr/local/bin/gopro[sudo] password for lonnie: 
sudo: curl: command not found
This didn't work for me, but I did find a Youtube video on how to use Kdenlive to do what I want. I will post that link here if that's ok. [https://www.youtube.com/watch?v=_6KKf2ccKiw](https://www.youtube.com/watch?v=_6KKf2ccKiw) 
Maybe it will help someone else who is trying to do this. Kdenlive is already part of Ubuntu Studio I just didn't know how to use it.

---

### Post by monkeybrain20122 on 2018-09-05
> **Lonnie_S said:**
> Thanks for the help. I installed the mplayer and ffmpeg . then ran this command .

sudo curl [https://raw.githubusercontent.com/KonradIT/gopro-linux/master/gopro](https://raw.githubusercontent.com/KonradIT/gopro-linux/master/gopro) -o /usr/local/bin/gopro[sudo] password for lonnie: 
sudo: curl: command not found
This didn't work for me, but I did find a Youtube video on how to use Kdenlive to do what I want. I will post that link here if that's ok. [https://www.youtube.com/watch?v=_6KKf2ccKiw](https://www.youtube.com/watch?v=_6KKf2ccKiw) 
Maybe it will help someone else who is trying to do this. Kdenlive is already part of Ubuntu Studio I just didn't know how to use it.


curl is not installed by default, so you need to install it. But that command is just for downloading the zip file so instead of runnig the curl command in the terminal all you have to do is to go to the github webpage and download the zip file from your browser.

---

