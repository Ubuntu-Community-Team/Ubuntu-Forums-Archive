---
title: "v4l2 framegrabber: logitech orbit af does not support pan/tilt controls?"
date: 2009-05-14
forum: Multimedia Software
---

### Post by iochinome on 2009-05-14
hey guys, so i am writing a v4l2 framegrabber application at the moment that requires that i utilize the pan/tilt functions of my logitech orbit af. (which is built for that, mind you.)
here is a function  to do one control:
```

static void
try_control (void) {
	memset (&queryctrl, 0, sizeof (queryctrl));
	queryctrl.id = V4L2_CID_PAN_ABSOLUTE;

	if (-1 == ioctl (fd, VIDIOC_QUERYCTRL, &queryctrl)) {
	        if (errno != EINVAL) {                            /*when its not einval, that means VIDIOC_QUERYCTRL screwed up somehow*/
	                perror ("VIDIOC_QUERYCTRL");
	                exit (EXIT_FAILURE);
	        } 
		else {
	                printf ("V4L2_CID_PAN_ABSOLUTE is not supported\n"); /*when it is einval, the brightness just isnt supported.*/
	        }
	} 
	else if (queryctrl.flags & V4L2_CTRL_FLAG_DISABLED) {              
	        printf ("V4L2_CID_PAN_ABSOLUTE is not supported\n");
	} 
	else {                                                           /*when all is according to plan, sets up control for it.*/
	        memset (&control, 0, sizeof (control));
	        control.id = V4L2_CID_PAN_ABSOLUTE;
	        control.value = queryctrl.default_value;
	
	        if (-1 == ioctl (fd, VIDIOC_S_CTRL, &control)) {
	                perror ("VIDIOC_S_CTRL");
	                exit (EXIT_FAILURE);
	        }
	}
	
	
}	

```	

but the thing is, it returns with "V4L2_CID_PAN_ABSOLUTE is not supported." i cannot get at it with V4L2_QUERYCTRL either. why not? it should totally support these controls, seeing as how it is a pan/tilt camera and all. (the Exposure, Auto and Exposure, Absolute do show up, by the way, which are also part of the camera control class.)

thanks for any help in advance, much appreciated!
-j

btw here is a link to a helpful site for any v4l2 developers:
  [http://v4l2spec.bytesex.org/spec-single/v4l2.html#CONTROL](http://v4l2spec.bytesex.org/spec-single/v4l2.html#CONTROL)

---

### Post by bterwijn on 2009-06-04
I followed these instructions and now have the Orbit AF moving. 

[http://forums.quickcamteam.net/printthread.php?tid=141](http://forums.quickcamteam.net/printthread.php?tid=141)

However the movements are not correct yet, as when panning it also tilts, or it pans in the wrong direction. Probably because of the mix up in control ID's as described in the link. I still have to look into that.

regards,
Bas Terwijn

---

