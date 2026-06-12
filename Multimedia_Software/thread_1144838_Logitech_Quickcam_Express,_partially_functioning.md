---
title: "Logitech Quickcam Express, partially functioning"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Saibot Sivad on 2009-05-01
Alright, I have just spent about six hours trolling the vast internets, following leads, etc., so I figured it was probably time to ask for help:

I have a Logitech Quickcam USB webcam, I plug it in to my laptop, running Intrepid (8.10). I have problems:

Installed and ran Cheese. Pictures show up in the finest detail, very clear and colors are perfect.

Installed aMSN (for webcam chatting, I hope...). It runs fine, but when I go to set up the webcam it says "Choose your device" and the only one available is "v4l2: Camera" but it shows up as black space. No good.

I run Ekiga Softphone. Wait a minute. Just a minute ago it was showing green screen, now it shows fine. WTH? Well, continuing...

Now I install Camorama, and it starts to an error "Unable to capture image" and the camera view is scrambled black and pink (nothing very interesting, I think?)

Now I continue to VLC and go to "Capture device", but no camera is auto listed (most other forums said it should automatically be there), so I type in "/dev/video0" which I found from "ls /dev/vid*" from another forum. When I hit "Play" VLC just goes to the player bar, but no video on the screen.

I know from lsusb and dmesg that the device is found correctly, and I would assume that it is functioning mostly correctly, since it works in Cheese, but why won't it work in aMSN, Camorama, and VLC?

Sorry if somebody came up with a conclusive fix, but after six hours of searching, I ended up going in circles on forums and not finding a solution.

Thanks in advance.

---

### Post by robbi60 on 2009-05-01
I also have a logitech quickcam E3500 and kubuntu 9.04.

It works fine with skype and (not very well) with xawtv.

At the beginning it worked really very fine with cheese out of the box  for to say, one hour, but suddenly it started to crash when opening, leaving  the message: 
cheese: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

It doesn't work with camorama (could not connect to video device /dev/video0)
or VLC. I didn't try aMSN. 

Can somebody help me for cheese? Many thanks. r

---

### Post by Saibot Sivad on 2009-05-02
Hey robbi60, does yours still work with Skype? Do you mean that, after an hour of playing with Cheese it stops working on Cheese? That doesn't sound like any of the problems I saw while forum searching...

Anybody have any thoughts on this? I bought this camera specifically because it was said to work "Out of the box" with Linux, but now maybe various upgrades have broken it again?

---

### Post by Saibot Sivad on 2009-05-02
Okay, I was fishing around in VLC and I went to "Capture Device", typed in "/dev/video0" for the "Video device name", then I clicked on "Show more options" which gives you the full command that it passes to VLC. So I copied that line, went to a terminal, and typed in:
```
vlc `v4l2:// :v4l2-dev=/dev/video0 :v4l2-adev= :v4l2-standard=0`
```

Now, when I press return, the very first thing it says (on the terminal) is this:
```
bash: v4l2://: No such file or directory
```

VLC still starts, and it does just what it did if I were to start it from within it's GUI, i.e., nothing.

I don't know what this means...

---

### Post by robbi60 on 2009-05-02
I have kubuntu 9.04 on an amilo Pro  fujitsu siemens and my logitec quickcam E3500 works very well and out of the box with skype and xawtv. It works also with vlc and camorama and sometimes (I don't know why...) with cheese but I need to give the command
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

I see also it using gstreamer-properties test. 
You have to check that v4l video4linux is installed (it's a default anyway, but please check it). That's allo. Best. r

---

### Post by Saibot Sivad on 2009-05-03
I went to the command line and typed in "cheese export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" and it popped up saying I had no camera plugged in. That's when I realized I left it at home, doh! I am out of town, but I will fiddle with it more on Monday, thanks for the suggestion.

---

### Post by robbi60 on 2009-05-03
I was not clear. 
You have to type the command in a terminal and then to try camorama or VLC (for cheese it is just random...). But first try skype, you have to choose the USB device in the video preferences and then to test. r

---

### Post by Saibot Sivad on 2009-05-04
Alright, I got home and tried it out. Here are the results, which are good!

I didn't think of trying what you said until you said it, but now it makes sense. So I typed this in on the terminal:
```
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
```
I don't know what exactly that is doing, but then when I started Camorama it didn't go to the error it had previously. Camorama started fine, but the picture box showed some crazy lines. I wasn't sure what it was, but when I waved my hand in front of the camera the lines changed, so I was getting something anyway.

Then, I looked in the preferences of Camorama to see what I could see, and when I changed the "View" option to "Large" the image showed up! Hooray! It's a bit darker than I would have guessed, and the controls don't do anything, but it works!

So now Camorama works, let's check out VLC... Trying "Capture Media" using "Video for Linux 2" and "/dev/video2" it still captures nothing. On a whim, thinking about Camorama not displaying correctly, I remembered in Cheese that it had shown me the display size, checking it again yielded 352x288. Going back to VLC, I put in those options, thinking it could be the issue: Now it pops up an error saying "v4l2://" cannot be found. Trying "Video for Linux" yields no results, but no video either...

Checking aMSN yields no change from before: Black screen.

Is there any way I can check that my install of v4l2 is correctly configured apart from other programs like Camorama/Cheese/VLC? To double check, I did the following earlier with no changes:
```
sudo aptitude purge v4l2
sudo aptitude install v4l2
```

VLC seems to think v4l2 is not accessible or something, any thoughts?

---

### Post by robbi60 on 2009-05-05
Have you tried 
/dev/video0 ?
This is actually the default option...
Best. r

---

### Post by Saibot Sivad on 2009-05-06
Sorry, that was a mistype on my part: I used /dev/video0

I originally used "ls /dev/vid*" to find out which one it was.

I think this is turning into another of those dreaded unanswered threads, another of the hundred that I found when I was trying to figure this out... :(

Thanks for your help so far robbi60, I just can't seem to make any progress on the issue. I may have more time this weekend to mess around with it, but for now I am going to call it a dead end.

---

