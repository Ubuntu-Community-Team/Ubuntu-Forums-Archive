---
title: "Microsoft XBOX Live Vision extremely inconsistent in 12.04"
date: 2013-08-19
forum: Multimedia Software
---

### Post by bcschmerker on 2013-08-19
I am currently testing the Microsoft® XBOX® Live&#8482; Vision&#8482; USB camera (ID: 045e:0294) on the Hot Rod gPC&#8482; and finding that [s]most of my[/s] *certain* Video4LinUX&#8482; applications return the following error code 90+ per cent of the time: 
```
Could not connect to video device (/dev/video0)
Please check connection.
```
According to [Ideas On Board](http://www.ideasonboard.org/uvc/), certain Microsoft® LifeCam® webcams have a known issue, which potentially also applies to the XBOX® Live&#8482; Vision&#8482;:
[quote=http://www.ideasonboard.org/uvc/]Despite being able to work with lower USB bandwidths, this device always requests the maximum possible bandwidth, even for the MJPEG format. Using one of those cameras in conjunction with another USB device (including the camera internal microphone) will likely fail. You can tell the uvcvideo driver to estimate the required bandwidth instead of trusting the camera by setting the FIX_BANDWIDTH quirk. This will only affect uncompressed formats, and even there there's no guarantee of success. See [the FAQ](http://www.ideasonboard.org/uvc/faq/#faq7) for more information.[/quote]
This gives me reason to suspect that the adherence of the XBOX® Live&#8482; Vision&#8482; to the UVC Video specification is only partial; the actual make and model CCD for this camera is not published.  What is necessary to fix the inconsistency described herein?

**Update:**  Some V4L programs can process the XBOX® Live&#8482; Vision&#8482; more readily than others.  GNOME® Cheese&#8482; (freshly-installed 19 August 2013) had little trouble accessing this camera, unlike Camorama&#8482;; and the Video4LinUX&#8482; Control Panel can access all functions except Auto-Exposure.

---

