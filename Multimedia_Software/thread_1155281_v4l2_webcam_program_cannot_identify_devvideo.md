---
title: "v4l2 webcam program: cannot identify /dev/video"
date: 2009-05-10
forum: Multimedia Software
---

### Post by iochinome on 2009-05-10
hey guys, so i am trying to develop an application that uses webcameras (in jaunty), so i found this code here, which gives examples:

[http://v4l2spec.bytesex.org/spec/capture-example.html](http://v4l2spec.bytesex.org/spec/capture-example.html)

i compiled it on my computer (which has a built in webcam on top that i know works, tested it and it worked in luvcview) and then tried to run it. i get an error message that says:
Cannot identify '/dev/video': 2, No such file or directory

Cannot identify '/dev/video': 2, No such file or directory

i have located the part in the program where this comes from:

static void
open_device                     (void)
{
        struct stat st; 

        if (-1 == stat (dev_name, &st)) {    
/*dev_name is "/dev/video" btw, defined in main*/                         
                fprintf (stderr, "Cannot identify '%s': %d, %s\n",
                         dev_name, errno, strerror (errno));
                exit (EXIT_FAILURE);
        }

so what is going on here? i do not have a ton of experience with linux, if you cant tell. thanks, much appreciated!

---

