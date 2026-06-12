---
title: "framegrabber, then manipulation of frames"
date: 2009-04-20
forum: Multimedia Software
---

### Post by iochinome on 2009-04-20
hello all,

so i want to be able to manipulate the frames that i get from my webcam on ubuntu linux using c/c++/python, and something tells me this is the place to come. what i would love to have happen is to make a modified version of some already established framegrabber application, which delivers the frames as data structures (or the pixels of the frames as data structures or both) which my own self-generated code would manipulate. (make blue, lower resolution, etc) truth is, i know relatively little about the libwebcam library and the code seems pretty complicated, and i am not incredibly interested in that aspect of the project. any suggestions on which way to go? thanks for any suggestions.

---

### Post by tidris on 2009-04-21
This will be useful:
[http://www.linuxtv.org/downloads/video4linux/API/V4L2_API/spec-single/v4l2.html](http://www.linuxtv.org/downloads/video4linux/API/V4L2_API/spec-single/v4l2.html)

For a relatively simple program that uses the V4L2 API check luvcview.

For a higher level API check gstreamer.

---

### Post by iochinome on 2009-05-03
hmm... okay, I can definitely work with the v4l2 API. so i compiled the example program that it gives, here:

[http://v4l2spec.bytesex.org/spec/capture-example.html](http://v4l2spec.bytesex.org/spec/capture-example.html)

and tried to run it on a laptop running ubuntu with a built in webcam at the top. it failed, gave me this error message in terminal:

Cannot identify '/dev/video' : 2, no such file or directory

and i traced it to these lines of code:
```
tatic void
open_device                     (void)
{
        struct stat st; 

        if (-1 == stat (dev_name, &st)) {                             /*get the status on dev_name (which is /dev/video btw, defined in main)*/
                fprintf (stderr, "Cannot identify '%s': %d, %s\n",
                         dev_name, errno, strerror (errno));
                exit (EXIT_FAILURE);
        }
```

the function open_device() continues to perform other tests on this file. is there a reason that it cannot open this file? it occured to me that they continually refer to the 'driver' in the tutorials/api explanations, and that i never had any contact with a driver, just assumed it was pre-loaded. is there a specific driver i should download (for an hp pavilion entertainment version) that would make this file miraculously appear? 

on a side note, what exactly do the %s and %d stand for, in the code? i tried google searching it, but that doesnt work: google does not do all punctuation.

thanks for any help! much appreciated!

---

### Post by iochinome on 2009-05-09
nobody knows? there is just no /dev/video0 file...?

---

