---
title: "What is the best pratice for encoding video for google"
date: 2008-02-05
forum: Multimedia Production
---

### Post by sefs on 2008-02-05
Some gave me a DVD with video on it.

I am supposed to 

1)  Get it off the DVD

2) Encode it in a format acceptable by google/youtube

3) Upload it ( I have this part covered lol)


But for 1) and 2)

Can someone give me some steps?

Thanks.

---

### Post by lakersforce on 2008-02-05
If you have the connection, I would just recommend to upload the *.VOB files from your DVD. That way you retain the best possible quality. If you need to encode you should take a look at mencoder.

That's all there is too it. Unless ofcourse your DVD is CSS encoded. Then it is an e n t i r e l y different story, not to mention illegal!

---

### Post by sefs on 2008-02-14
VOB file is too large, thats why i want to make it smaller.  I'm having no luck with Acidrip.  when i click the button to start it completes immediately without doing anything.

---

### Post by santaslittlehelper on 2008-02-14
Hi

I would give avidemux a shot. 
Depending on your specs it might be favorable to upgrade or install 2.4.0
[http://www.getdeb.net/search.php?keywords=avidemux](http://www.getdeb.net/search.php?keywords=avidemux)

Try to dump the DVD to your harddrive, this should work (As long as there's no copy protection).
dd if=/dev/dvd of=DVD.iso bs=2048

Then open the iso with avidemux and have a look at your options.
One way could be to encode with x264, AAC to mp4 and change the resolution to 320x240 under video filters.
I can get a DVD down to about ~240 MB, you can use avidemux to split the file in to small pieces as well if needed.

---

### Post by sefs on 2008-02-15
2.4 installed and options selected such as sizing ect...but then shen i go file save it saves as the same size.  Is there a way to actually start the compression?

---

### Post by santaslittlehelper on 2008-02-15
You are doing "Save > Save Video" right?

I should probably have suggested this to begin with but there's so many options, try to use "Singel Pass - Quality Quantizer (Average)" under "Video > configure > bitrate". 
Same if you get any sound issues, then have a look "Audio > configure".
As long as the iso is good you should be alright. 

If you got any trouble with your iso you can look here - [http://townx.org/blog/elliot/doing-all-sorts-burning-ripping-and-encoding-video-and-dvds](http://townx.org/blog/elliot/doing-all-sorts-burning-ripping-and-encoding-video-and-dvds)
But I don't usually use it for ripping just as I figured yours was kinda home made from the sound of it. Other then that there's applications like devede and k9copy but I can't tell you much about either.

---

### Post by sefs on 2008-02-15
Ok thanks for the advice, will try this when i reach home.

---

