---
title: "Urgent FFMPEG help needed! Please"
date: 2009-03-20
forum: Multimedia Software
---

### Post by ajclarkson on 2009-03-20
Hi Guys,

Working against the clock here so all suggestions are much appreciated thanks.

A brief summary of the problem. 

I want to take my laptop to a party tonight to make a timelapse of it using the webcam. I have managed to automate the capture and get a series of images. I did this by using Cheese and automating button clicks. (Messy I know but it gets the best quality from my webcam) 

My problem is that Cheese outputs the files with names such as:

```
2009-03-19-195721.jpg
```

Which is a timestamp. This is all well and good as it ensures that all images are uniquely named, but I cannot work out how to get FFMPEG to stich them back together. I know that the command:

```
ffmpeg -f image2 -i %d.jpg video.mpg
```

Will work for a sequence of images named 1, 2, 3 etc but I cannot seem to figure out the pattern for the timestamp.

If you can help please do as I need to work this out in the next 6 hours or less!

Thanks in advance again

Adam

---

### Post by jbrevik on 2009-03-20
The last 6 digits are probably in the HHMMSS format.

So as an example, 195733 would be 19:57:33

---

### Post by ajclarkson on 2009-03-20
Hi,

Yeah I guessed it would be, but it is the pattern to insert after the -i option of FFMPEG which I am struggling with. Any ideas?

Thanks for the reply

---

### Post by jbrevik on 2009-03-20
> **ajclarkson said:**
> Hi,

Yeah I guessed it would be, but it is the pattern to insert after the -i option of FFMPEG which I am struggling with. Any ideas?

Thanks for the reply

I would assume just put in each file name in order like,

```
ffmpeg -f image2 -i 1st_file.jpg 2nd.file.jpg 3rd_file.jpg output.mpg
```

---

### Post by ajclarkson on 2009-03-20
Hi,

Yeah but I have potentially 40,000 images here, if they were all named 

1.jpg, 2.jpg, 3.jpg ... 40000.jpg

then the pattern for "-i" would be %d.jpg (this would retreive all in the folder) so what I need is a pattern which will pull out the ones named with the timestamp.

I hope that is a bit clearer? 

Alternatively if anyone knows how to change the output naming for Cheese this would also work as I could probably set it to 1.jpg etc but I have not yet found a way

---

### Post by jbrevik on 2009-03-20
In this case, I might recommend using something like kino to do this. You are dealing with a large amount of files and it might take a little scripting to extract the contents of the directory and copy and paste them into the command.

```
sudo apt-get install kino
```

Hope this helps:)

---

### Post by ajclarkson on 2009-03-21
Hi,

Didn't have chance to reply before the party last night so here is my solution:

I didn't install kino as I didnt want to bloat my EEE, running openbox to keep everything lightweight, so I did a little more research into other options.

I ended up using mencoder to do this as you can specify *.jpg as the input files and also set the framerate.

Thanks for all the help though, just included this to help other future users with this problem

Adam

---

