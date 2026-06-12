---
title: "ffmpeg converting to H.264"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by Slace on 2006-11-14
I'm trying to set up my kubuntu edgy install to convert video's to H.264 using ffmpeg and the x264 library.

I've got everything installed (ffmpeg and x264 from the latest CSV's) but I'm not really sure what I need to use as my command line switches I need though.

The reason I'm doing it is so I can put the video's on my iPod.

This is the command I'm using:
```
ffmpeg -i "${input_file}" -acodec aac -ab 96 -maxrate 1000 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -vcodec h264 -b 256000 -mbd 2 -coder 1 -cmp 2 -subcmp 2 -s 320x240 -aspect 4:3 -title "${output_file_name}" "${output_dir}/${output_file_name}.mp4"
```

When running that I get this:
```
[h264 @ 0x84ddcd8]VBV underflow (-217168 bits)
backstep:187, lastbuf:92
invalid new backstep 83
backstep:190, lastbuf:92
invalid new backstep 83
```

And it just fills up my screen, but the video keeps on encoding, and can be played once finished, but it just bothers me that I get a but load of messages while trying to encode...

Anyone know what I should use as my switches?

---

### Post by encho on 2006-12-02
I have to bump this. Does your video, when encoded this way, play on your iPod? Is it 5th gen iPod?

---

### Post by jdong on 2006-12-22
> **encho said:**
> I have to bump this. Does your video, when encoded this way, play on your iPod? Is it 5th gen iPod?

See [https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding) I just recently added how to do 5.5gen (firmware 1.2+) H.264 encodes for the iPod.

---

### Post by Mau on 2006-12-22
[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding) -- the above link had a semi-colon added in to lead to a 404.  :)

---

### Post by jdong on 2006-12-22
Fixed, and thanks for pointing that out! (nope, after all this time I still haven't learned what characters hotlink and what don't!)

---

