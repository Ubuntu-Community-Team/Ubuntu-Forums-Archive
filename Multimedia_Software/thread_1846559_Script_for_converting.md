---
title: "Script for converting"
date: 2011-09-19
forum: Multimedia Software
---

### Post by asai on 2011-09-19
Hi

I'm trying to make a script for converting a swf file to avi.
The swf file is created from multible jpg files with this command: (also in script)
```
jpeg2swf *.jpg -o movie.swf
```

Then I use ffmpeg like this:
```
ffmpeg -i movie.swf movie.avi
```

But I get this error message:
```
picture size invalid (0x0)
```

Any suggestions to where I go wrong?

---

### Post by ofnuts on 2011-09-19
> **asai said:**
> Hi

I'm trying to make a script for converting a swf file to avi.
The swf file is created from multible jpg files with this command: (also in script)
```
jpeg2swf *.jpg -o movie.swf
```Then I use ffmpeg like this:
```
ffmpeg -i movie.swf movie.avi
```But I get this error message:
```
picture size invalid (0x0)
```Any suggestions to where I go wrong?
Just wondering why you don't convert directly from JPG to MPG? [http://electron.mit.edu/~gsteele/ffmpeg/](http://electron.mit.edu/~gsteele/ffmpeg/)

---

### Post by sisco311 on 2011-09-19
Not a programming question. Moved to **Multimedia & Video**.

---

### Post by asai on 2011-09-19
I tried this command:
```
ffmpeg -r 10 -b 1800 -i *.jpg test1800.mp4
```
But I get this error:
```
Unable for find a suitable output format for '0642jpgwebcam.jpg'

```
0642jpgwebcam.jpg is the first file.

---

### Post by ofnuts on 2011-09-19
> **asai said:**
> I tried this command:
```
ffmpeg -r 10 -b 1800 -i *.jpg test1800.mp4
```But I get this error:
```
Unable for find a suitable output format for '0642jpgwebcam.jpg'

```0642jpgwebcam.jpg is the first file.
Wrong syntax... with the synatx you use, "*.jpg" get expanded to all the present JPG files, while -i should be followed by one single token. See the syntax used in the referenced page.

---

### Post by .... on 2011-09-19
I don't think you can put swf in an avi because of the actionscript stuff. If you just want video, use flv.

---

### Post by asai on 2011-11-19
I'm still trying to make a output file from my webcam images.

Heres my command:
```
 ffmpeg -f image2 -i /home/eivind/img%.jpg > /home/eivind/allday.wmv
```
But it fails:
```
[image2 @ 0xb77ab110]Could not find codec parameters (Video: mjpeg)
/home/eivind/img%.jpg: could not find codec parameters
```
Any suggestions where I'm wrong?

---

### Post by FakeOutdoorsman on 2011-11-19
Are your images in sequential order? Give an example of one of the image file names: *img125.jpg* for example.

---

### Post by asai on 2011-11-20
Yes they are. img0701.jpeg, img0702.jpeg, img0703.jpeg and so on.
I tried to make a movie from the files in a windows program, and it worked perfectly. So, I am sure it is only a small error in my command line... :o

---

### Post by FakeOutdoorsman on 2011-11-20
I neglected to mention that they should also start with *1*, as in *img0001.jpeg*. If that's the case for you then you're good to go:
```
ffmpeg -i img%04d.jpeg -qscale 4 output.mp4
```
Adjust the *qscale* value to increase or decrease output quality. A lower value is higher quality and a higher output file size. Depending on your input source a good range is 3-5. Consider a value of 2 to be visually lossless (but not technically lossless).

---

### Post by asai on 2011-11-21
Oh... Now I understand the meaning of "%04d" :)

So it works, but two last questions:
How can i bulk rename the files to img0001.jpeg, img0002.jpeg and so on?
Can I increase the framerate?

Edit: I have tried this command:
```
num=0; for f in $(ls -t); do cp -p "$f" IMG_$(printf "%03d" $num).jpg; num=$((num+1));done
```
This renames the files, but wrong direction. (Newest 001 and so on).

---

### Post by FakeOutdoorsman on 2011-11-21
> **asai said:**
> Can I increase the framerate?
Yes. There are several ways to do this. This first method will simply drop or duplicate frames to achieve your desired frame rates. In this example, FFmpeg will read the inputs at 10 frames per second, and then make the output 30 frames per second. If you do not declare *-r*, then a default of 25 will be used for the input and also the output.
```
ffmpeg -r 10 -i img%04d.jpeg -qscale 4 -r 30 output.mp4
```
You can tell if it's duplicating or dropping frames with the console output. You will see something like: dup=237 drop=0.

Another option is the **setpts** filter: [examples](http://ubuntuforums.org/showpost.php?p=10946893&postcount=8). I'm not sure how it deals extra/missing frames. "ffmpeg" (actually libav masquerading as ffmpeg), from Oneiric has the filter. Older Ubuntu versions must [compile FFmpeg](http://ubuntuforums.org/showthread.php?t=786095) to gain access to this filter.

> **asai said:**
> Edit: I have tried this command:
```
num=0; for f in $(ls -t); do cp -p "$f" IMG_$(printf "%03d" $num).jpg; num=$((num+1));done
```
This renames the files, but wrong direction. (Newest 001 and so on).
Maybe this?
```
num=0; for f in $(ls -tr); do cp -p "$f" IMG_$(printf "%03d" $num).jpg; num=$((num+1));done
```

I added *-r* to the *ls* command to reverse the listed order, but I didn't try the script.

---

### Post by asai on 2011-11-22
> **FakeOutdoorsman said:**
> 
```
ffmpeg -r 10 -i img%04d.jpeg -qscale 4 -r 30 output.mp4
```.
I'll try a few different outputs, and see which I like best.

> **FakeOutdoorsman said:**
> 
Maybe this?
```
num=0; for f in $(ls -tr); do cp -p "$f" IMG_$(printf "%03d" $num).jpg; num=$((num+1));done
```

I added *-r* to the *ls* command to reverse the listed order, but I didn't try the script.
I think this might do the trick. I will test and post the result. Thanks for good advice so far. :D

---

### Post by sisco311 on 2011-11-23
> **asai said:**
> 
I think this might do the trick. I will test and post the result. 

It might, but not in all cases. Check out BashPitfalls #1, BashFAQ #003 (link in my signature) and [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

I'd try something like:
```


n=0
while IFS= read -r -d '' file
do
    echo cp -b -- "${file#* }" "IMG_$(printf '%03d' $n).jpg"
    ((n++))
done< <(find ./ -maxdepth 1 -type f -printf '%T@ %p\0' | sort -znr)

```

---

