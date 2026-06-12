---
title: "How to set Skype webcam INPUT size ?"
date: 2008-10-06
forum: Multimedia Software
---

### Post by statikeffeck on 2008-10-06
I have been trying to get my webcam to work with skype. I think I know what is causing the problem, I just don't know how to fix it.
**I have a Philips Toucam XS and it only works if the application with which you are viewing it is set to resolution of 352 x 288 .**

In other words, running this command works fine:
mplayer tv:// -tv driver=v4l:width=352:height=288:device=/dev/video1

but if I do something like 
mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video1
I will only get garbage.

With simple apps like "Cheese" there is no way to set the width and height (that I know of). As a result, a black screen shows up instead. **And with Skype I also get just a black screen**. I'm sure it has something to do with setting the video size properly. 
Anyone know what I'm talking about? I really appreciate any hints or directions for this.

Thanks

other specs: Running Ubuntu Hardy Heron 8.04 with Nvidia 9800 GT (Nvidia.com drivers).
Using the ov51x-jpeg driver grabbed from EasyCam for the webcam.

---

### Post by Mr. Francis J. Ball Esq. on 2008-10-16
I Fitted a Trust WB-1400T Webcam!
 :p It Plugged & Played, with SKYPE from the box :p  

I Changed my screen res, so my 1280x1024 external panel showed full screen and the LAPTOP screen "was the partial window ( ... x 900 )

  SKYPE video went BLACK SCREEN ...
  £ on <Shift> 3  became a Blue 3  ...
  :confused:(Ha Ha secure password?  Try loging on!) :confused:

Fixed £ with  "" xmodmap -e 'keycode 12 = 3 sterling'  ""
  as Start-up rule!  

Installed Cheese & camorama ! !

camorama gives video  ...

cheese = BLACK SCREEN
SKYPE = BLACK SCREEN

---

### Post by Mr. Francis J. Ball Esq. on 2008-10-16
Just checked & noticed ... View is camera view not
BLACK SCREEN when I look at the Laptop rather than the added panel.

must be res. problem ... But I would like a fix!

Thanks to all!

---

### Post by no2498 on 2009-09-05
in cheese
click edit
preferences
set it to 352x288

---

### Post by Jose Catre-Vandis on 2009-09-05
> **statikeffeck said:**
> I have been trying to get my webcam to work with skype. I think I know what is causing the problem, I just don't know how to fix it.
**I have a Philips Toucam XS and it only works if the application with which you are viewing it is set to resolution of 352 x 288 .**

In other words, running this command works fine:
mplayer tv:// -tv driver=v4l:width=352:height=288:device=/dev/video1

but if I do something like 
mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video1
I will only get garbage.

With simple apps like "Cheese" there is no way to set the width and height (that I know of). As a result, a black screen shows up instead. **And with Skype I also get just a black screen**. I'm sure it has something to do with setting the video size properly. 
Anyone know what I'm talking about? I really appreciate any hints or directions for this.

Thanks

other specs: Running Ubuntu Hardy Heron 8.04 with Nvidia 9800 GT (Nvidia.com drivers).
Using the ov51x-jpeg driver grabbed from EasyCam for the webcam.

For Skype, (first close Skype) have a look at:
```
nano ~/.Skype/skype-username/config.xml
```
Back up the file first before you edit it

Scroll through the file to look at the Video section.
If you don't have a Video section you will need to include it, at the end of the file add:
```
<Video>
</Video>
```

If you have a video section try adding something like this:
```
<Video>
<CaptureHeight>480</CaptureHeight>
<CaptureWidth>640</CaptureWidth>
<RecvPolicy>callpolicy</RecvPolicy>
</Video> 
```
Edit the height and width settings as required


Hope this helps

---

