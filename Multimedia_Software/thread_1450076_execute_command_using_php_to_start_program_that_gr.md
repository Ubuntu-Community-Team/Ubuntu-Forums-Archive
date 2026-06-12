---
title: "execute command using php to start program that grabs screen from webcam"
date: 2010-04-08
forum: Multimedia Software
---

### Post by stiankarlsen on 2010-04-08
I'm trying to setup a webcam surveillance system. Zoneminder didn't work for me regardless of how I tried configuring it, so I gave up and have now settled on a more primitive solution.

I've currently got 6 cams and looping streamer (webcam screen grabber) I can grab a picture from each camera with about a 1 second interval. The previous picture is overwritten and using javascript to reload the image continuously in a browser I get the desired "movie" effect I'm after.

The problem however is that as soon as I start using streamer on more than two cameras at once I run into this little snag:

> libv4l2: error turning on stream: No space left on device
ioctl: VIDIOC_STREAMON(int=1): No space left on device


I've been searching around and it seems I need to increase my shared memory. I've done that (tried many different values and "solutions") but the problem remains the same.

Therefore I am left with this idea:

My setup is as follows.

1.php (refreshes updated grab from camera 1 every second in the browser)
2.php (refreshes updated grab from camera 2 every second in the browser)
3.php (refreshes updated grab from camera 3 every second in the browser)
etc
etc.

Is it possible to use something like php exec to execute the command that starts 'streamer' that grabs the image from the specific webcam (/dev/video1 for 1.php and so forth) when 1.php is opened in the browser.

Is this even possible, or am I just dreaming?

PS, I realize this might be terribly unsecure and whatnot (or is it?) but at this point I don't really care.

Thanks so much for you input! 

later.

---

### Post by tgalati4 on 2010-04-08
There's no reason that you can't use php to execute those scripts.  Not the best for performance because the zend engine has to interpret the script each time it's run, so it might use up some serious CPU.

apt-cache search webcam

There are lots of webcam utilities.  Have you looked at motion?

What was the killer issue with zoneminder?

---

### Post by stiankarlsen on 2010-04-08
Thanks for the quick reply.

So how exactly do I have php execute at bash script? I can make it do a simple 'ls' etc, but I'm assuming the reason anything more "advanced" won't work is because of a permissions problem.

I'm really new at this stuff, so bear with me. Thanks.

---

