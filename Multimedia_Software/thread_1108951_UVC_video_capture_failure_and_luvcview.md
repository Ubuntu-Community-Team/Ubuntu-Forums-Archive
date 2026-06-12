---
title: "UVC video capture failure and luvcview"
date: 2009-03-28
forum: Multimedia Software
---

### Post by HABalloonGirl on 2009-03-28
Hi,

I have a logitech quickcam pro for notebooks and I'm having trouble recording a video with v4l2 and the uvc driver.  I've modified the luvcview program and made a custom one since I don't want a screen, buttons, etc and a few other things.  I can take and save a picture succesfully.  However, when I go to grab a video, I have failures in my ioctl functions.  For example, the first one that fails is:

memset(&videoIn->fmt, 0, sizeof(struct v4l2_format));
videoIn->fmt.type = V4L2_BUF_TYPE_VIDEO_CAPTURE;
videoIn->fmt.fmt.pix.width = videoIn->width;
videoIn->fmt.fmt.pix.height = videoIn->height;
videoIn->fmt.fmt.pix.pixelformat = videoIn->formatIn;
videoIn->fmt.fmt.pix.field = V4L2_FIELD_ANY;

ret = ioctl(videoIn->fd, VIDIOC_S_FMT, &videoIn->fmt);
cout << "ret FORMAT_SET is:" << ret << endl;
if (ret < 0) 
{
	cout<< "Error in formatting request\n";
	return -1;
} 

ret returns as -1 and I get a formatting error. Other ioctl functions fail similarly.  The only ioctl that returns without errors is:

ret = ioctl(videoIn->fd, VIDIOC_QUERYCAP, &videoIn->cap);

My camera is opening correctly (returns a value of 5) and a .avi file is opened.

Later, I get an error saying
Unable to stop capture: 16.
but I think that's an unrelated problem right?

If I take the ioctl functions out entirely, I save a video that is only a single still frame.

Does anyone know anything about luvcview or what the problem might be?
Thanks.

Connie

---

