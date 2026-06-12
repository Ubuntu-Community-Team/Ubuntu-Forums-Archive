---
title: "Cheese does not detect my webcam."
date: 2011-10-08
forum: Multimedia Software
---

### Post by asad.bukhari on 2011-10-08
I just installed cheese. I have a Samsung RV511 laptop. When I use Skype my webcam works fine. When I start cheese, there is nothing on the display, it is just a black screen. How do I go about fixing this? (I have Ubuntu 11.04)

---

### Post by asad.bukhari on 2011-10-08
I've been trouble shooting the issue myself. When I open up gstreamer-properties and test my default video input. 

The plugin: "Video for Linux 2 (v4l2)."
The device: "Default" or I can choose "WebCam SCB-0385N."

When I test the default input, I receive this error: "Video for LInux 2 (v4l2): Could not get buffers from device '/dev/video0.' 

I looked it up and this seems to be a bug: [https://bugzilla.gnome.org/show_bug.cgi?id=490034](https://bugzilla.gnome.org/show_bug.cgi?id=490034)
Although the article is quite old.

I think is causing the webcam to fail to run in Cheese. How do I fix this?

---

### Post by frenchn00b on 2011-10-08
> **asad.bukhari said:**
> I just installed cheese. I have a Samsung RV511 laptop. When I use Skype my webcam works fine. When I start cheese, there is nothing on the display, it is just a black screen. How do I go about fixing this? (I have Ubuntu 11.04)

You can use my Windows Manager (fvwm based / Themes)

It has a frontend for webcam control... 

win + shift + K : you get the multimedia menu
[http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans+%5BGold%5D?content=127893](http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans+%5BGold%5D?content=127893)

---

