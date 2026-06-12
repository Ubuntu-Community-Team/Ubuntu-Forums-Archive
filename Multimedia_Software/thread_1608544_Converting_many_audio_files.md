---
title: "Converting many audio files"
date: 2010-10-29
forum: Multimedia Software
---

### Post by rmcellig on 2010-10-29
I have over 35,000 .m4a files I need to convert to MP3 format. When I use Sound converter I get errors similar to the attached file. Is Sound converter the right tool for me to use or is there a better way for me to convert all of these files?

When I am on the Mac side of my partition on my iMac, I use Max. It's an audio conversion application. I never have any of the problems I am having with Sound Recorder. I would like to stay in my Ubuntu environment instead of using my Mac because I am getting to know Ubuntu. Thanks!!

---

### Post by tripmix on 2010-10-29
I would do something like this:  ```
#!/bin/bash
criteria=.m4a
re_match=m4a
replace=mp3
for i in $( ls *$criteria );
do
        src=$i
        tgt=$(echo $i | sed -e "s/$re_match/$replace/")
        lame $src $tgt
        #mencoder -i $src -oac mp3lame -lameopts cbr:br=128 -of rawaudio -o $tgt
done
```  if you are unfamiliar with bash scrips all you have to do is put that in a text file and save it in the folder your m4a files are. Now run "chmod +x what-you-named-the-scipt" then ./what-you-named-the-scipt it should continue until all your m4a files are mp3. You can modify this line "for i in $( ls *$criteria );" like this "for i in $( ls */*$criteria );" or "for i in $( ls */*/*$criteria );" to get it to move into folders, basically one */ for each folder level.

EDIT: Also it looks like your app fails because you don't have write permission on your usb (or the app doesn't), notice how it fail while creating a folder.

---

### Post by rmcellig on 2010-10-29
I have write access on the USB drive. Can I use the application Configure Scheduled Tasks instead of running chmod from the command line? I was hoping that I could use a GUI solution and avoid having to deal with scripts. I really struggle when it comes to using code and the command line.

Thanks!!

---

