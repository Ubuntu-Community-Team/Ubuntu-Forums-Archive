---
title: "converting various video type files in to one type and resolution"
date: 2012-07-25
forum: Multimedia Software
---

### Post by pacman401 on 2012-07-25
I am looking for a solution to convert many(~50GB) video files of various types placed in subdirectories in to same subdirectories but one video type and one resolution

any one know that application could do that automatically or app+bash script (I just don't won't to covert every single video file one by one)

---

### Post by lukeiamyourfather on 2012-07-25
Why would you want to do that? Transcoding lossy video to another lossy codec results in lost quality (hence lossy). HandBrake has batch processing and is fairly user friendly. Or the command line FFmpeg and a bash script could do it too. If this is just a one time thing I'd use HandBrake, if this is a recurring thing I'd write a script for it. Here's a bash example of a for loop going through a directory if you decide to go that route.

```

i=1
cd ~
for item in *
do
 echo "Item $((i++)) : $item"
done

```

```

$ ./for5.sh
Item 1 : positional-parameters.sh
Item 2 : backup.sh
Item 3 : emp-report.awk
Item 4 : item-list.sed
Item 5 : employee.db
Item 8 : storage
Item 9 : downloads
```

[http://www.thegeekstuff.com/2011/07/bash-for-loop-examples/](http://www.thegeekstuff.com/2011/07/bash-for-loop-examples/)

---

### Post by Kreaninw on 2012-07-25
I think you need **FF-Multi-Converter**. Go easy on GUI tool, my friend. :D
```
sudo add-apt-repository ppa:ffmulticonverter/stable
sudo apt-get update
sudo apt-get install ffmulticonverter
```

---

### Post by pacman401 on 2012-07-30
FF-Multi-Converter could be very good for me but ptyhon takes all of one core(don't know why) and of curse ffmpeg takes the second core 

solved by using winff only one core is taken by ffmpeg

---

### Post by Dawnbandit on 2012-07-31
You could try WinFF
You can get it from Synaptic.

---

