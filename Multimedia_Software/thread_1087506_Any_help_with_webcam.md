---
title: "Any help with webcam"
date: 2009-03-05
forum: Multimedia Software
---

### Post by covertops808 on 2009-03-05
When I try to run skype or cheese, the webcam isn't functioning. Well in skype, when I go to test the camera in the settings, all I see is a white box with a grey rectangle. When I run cheese through a terminal, the program starts, but than a second after the camera light comes on, the program just closes. I get the following output:

The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 61 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Running Intrepid AMD64. 

It's very weird because both programs worked previously. I have no idea which upgrades took place that could have affected this.

---

### Post by krlhc8 on 2009-03-05
To get my webcam working for skype, I open it up in a terminal with the following command: 

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

For the settings, audio outputs are set to pulse, and the input is set to USBDevice...plughw...

You should see the video working when you do 'test video' in the video options.

Hope this worked for you.

---

