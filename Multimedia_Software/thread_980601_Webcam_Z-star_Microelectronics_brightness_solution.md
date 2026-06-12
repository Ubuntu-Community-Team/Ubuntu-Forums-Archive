---
title: "Webcam Z-star Microelectronics brightness solution"
date: 2008-11-13
forum: Multimedia Software
---

### Post by pmuzyk on 2008-11-13
Hi all,
Just to save a lot of grief with your webcam for people who have hardy or intrepid and are using either version of gspca(v1 or 2) and v4l(v1 or 2). When you have the webcam working and have Skype or any other vid application but the cam has its brightness way too high and you look like you're a white ghost, you can fix the brightness by simply installing 'xawtv'.

To get 'xawtv', just type in terminal 
> sudo apt-get install xawtv

Run xawtv by typing in terminal "xawtv" or clicking on the menu item from the gnome menu. Once it is open, right click on the video stream window once it shows up. 

A menu should popup. Look down until you see "Light frequency". It should be set to "NoFlicker" for outdoor capture (sunlight) or bright indoor lighting. 50Hz is good for low light indoor use. Once you set this option, you can close xawtv and then open Skype for example and your video stream should be full of contrast and captures everything perfectly.

I have been struggling with my webcam for a month. All I wanted to do is set the brightness or gamma or light frequency. Light frequency is what I was after to reduce the washed out video stream.

I hope this helps someone.

---

