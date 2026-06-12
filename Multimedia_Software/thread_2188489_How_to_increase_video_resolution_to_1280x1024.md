---
title: "How to increase video resolution to 1280x1024"
date: 2013-11-17
forum: Multimedia Software
---

### Post by Stan_Meissner on 2013-11-17
I recently experienced a computer crash and was offered a free Dell Optiplex 760.  After swapping out drives and adding memory I installed Ubuntu Studio seeing as I did not have an OS.  After messing around with it for a month I've pretty much got things sorted out exept for a few nagging issues.  I use my computer for photo editing and typically edit and post hundreds of photos to my website each week (gotomn.com/gotomn-photo-gallery.htm).  

One of the nagging issues I've been struggling with is increasing my screen resolution to 1280x1024.  This is what I'm seeing in terminal for the onboard video so correct me if I'm wrong but it appears that it should handle 1280x1024.  The problem is that I'm still in the process of learing how to work in terminal so I'm struggling trying to get this resolved.  

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

At first I thought that perhaps the onboard video was not capable of a higher resolution than 1024x768 so a friend gave me a Radeon HD 3450 video card which is made specifically for the Optiplex 760.  I was able to successfully install the card but got an "out of range" error.  I tried dozens of conflicting and confusing directions posted online for both issues so far with no success.  I got frustrated after messing around with the video card so I pulled it out for the time being and am using onboard video at 1024x768. 

My monitor is a 17" Norwood Micro VGA that handled 1280x1024 fine with the old PC that bit the dust so I know that the monitor is capable of that resolution.  Help!!! The simple task of upping monitor resolution for the onboard video or putting in an OEM video card made for a computer that is certified to work with Ubuntu shouldn't have to be an ordeal.

My first preference would be to reinstall the video card and get rid of the "out of range" error.  Second choice would be to up the resolution of the onboard video to 1280x1024.

I'm a rookie with 30 years of computer experience if that makes any sense.  ;)

---

### Post by Stan_Meissner on 2013-11-17
I stumbled across a fix that worked and was able to run at 1280x1024 but the resolution reverts back to 1024x768 on reboot.  I guess there's a way to make it work after reboot but I tried following along using something called gedit but I must not have done it correctly.  This was accomplished using the onboard video so I probably won't install the card as I'm happy with the higher res.  Now my only challenge is to figure out how to get it to work after reboot so I don't have to redo the fix every time.

---

### Post by Stan_Meissner on 2013-11-17
I figured out how to get Ubuntu to retain the monitor settings after reboot so I have marked this thread as resolved.

---

### Post by mörgæs on 2013-11-17
Good, please post the solution for others to benefit from.

---

### Post by Adler on 2013-11-17
Hi All,

I tweak my H-P Spectre Ultrabook to no end! Recently, I have been  playing with screen reolution, or better put, trying to change it.

I have  been Googling for days, and have just run across this posting. I should mention that I am using a varient of  UBUNTU 12.04 LTS (Backbox Linux), with the XFCE DM. 

If I run "xrandr" I get: 
[B]
adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ [/B]


I see that I should be able to take my screen resolution to my desired 1920x1080 level (I think). 

When I use cvt, with my desired, screen resolution I do generate a modeline:

[B]adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
adler@adler-HP-Spectre-XT-Ultrabook-PC:~$[/B]

I have tried numerous xrandr terminal commands, looked through my  xorg.conf file, but see nothing where I can change my screen from the  stated resolutions. Nor, can I find where my presently available choices  live.

My graphics card is:

[B]adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
adler@adler-HP-Spectre-XT-Ultrabook-PC:~$ xrandr
[/B]

Any help would be appreciated, and I'll be watching this thread!

---

### Post by Adler on 2013-11-18
Stan_Meissner,

Can you get back to us with how you acheived success? Thanks in advance!

der Adler

---

### Post by Stan_Meissner on 2013-11-18
I used the suggestions found in this link and changed the values to match my system.  Also after figuring out how to do this I followed the link at the bottom of the page so that it would retain the settings on reboot.  I'm a 62 year old "rookie" so I'm considering myself lucky to have worked out my monitor and scanner problems with a minimum of help.  If I can do this anybody can.  ;)

[http://askubuntu.com/questions/138408/how-to-add-display-resolution-fo-an-lcd-in-ubuntu-12-04-xrandr-problem](http://askubuntu.com/questions/138408/how-to-add-display-resolution-fo-an-lcd-in-ubuntu-12-04-xrandr-problem)

---

