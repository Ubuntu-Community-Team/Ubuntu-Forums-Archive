---
title: "Best programs for various multimedia?"
date: 2009-09-02
forum: Multimedia Software
---

### Post by loosie on 2009-09-02
Hi,

New to Ubuntu. I have been accustomed to using Serif Photo Plus & Photoshop in Windows. Ubuntu has Gimp Image Editor & Fspot Photo Manager. I'm wondering, are they similar type programs, or is there something better(well, more familiar for me:)) that you suggest?

Also I had a 'Fast Image Resizer' program & a 'movie saver' program and I could copy & save images from online in Windows. I'd like to know what I need to do these things? TIA

---

### Post by lovinglinux on 2009-09-03
> **loosie said:**
> Hi,

New to Ubuntu. I have been accustomed to using Serif Photo Plus & Photoshop in Windows. Ubuntu has Gimp Image Editor & Fspot Photo Manager. I'm wondering, are they similar type programs, or is there something better(well, more familiar for me:)) that you suggest?

Also I had a 'Fast Image Resizer' program & a 'movie saver' program and I could copy & save images from online in Windows. I'd like to know what I need to do these things? TIA

Fast Image Resizer: Phatch

Serif Photo Plus: digikam

'movie saver' - don't know what you mean by that, but I like Pitivi for editing, [Video Download Helper](https://addons.mozilla.org/en-US/firefox/addon/3006) extension for downloading

---

### Post by loosie on 2009-09-04
Thanks for that! I'll try the video download helper & see if that works for me. The 'Movie Saver' was a free program I discovered recently that you can save clips from Youtube or any other online source.

Can't save some pics, from Ebay & the likes, as I used to. Right clicking on the pic gives me the option 'save picture as' but it will only save it as html. I've been able to save some things but not others??

---

### Post by binbash on 2009-09-04
Phatch is a good software for resizing and other things. You can use a firefox extensions to download the videos or copy from your /tmp folder. You can convert them with handbrake, winff and so.

---

### Post by loosie on 2009-09-04
Thanks guys, just installed vid. download helper & going to search for Phatch & Serif now... Cheers!

---

### Post by lovinglinux on 2009-09-04
> **loosie said:**
> Thanks guys, just installed vid. download helper & going to search for Phatch & Serif now... Cheers!

[click here to install phatch](apt:phatch) [apt-get] 

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

### Post by loosie on 2009-09-04
Hi,

Pardon me being a dunce, but how do you install Phatch?? I've downloaded & extracted it to my desktop. Opened a terminal & typed sh phatch-0.1.6  as I've done for other progs, to no avail??

What is the 'patch' prog you've said to 'click here for', lovinglinux?

And I can't find 'digicam' as relates to a photo editing prog...

---

### Post by lovinglinux on 2009-09-04
> **loosie said:**
> Hi,

Pardon me being a dunce, but how do you install Phatch?? I've downloaded & extracted it to my desktop. Opened a terminal & typed sh phatch-0.1.6  as I've done for other progs, to no avail??

What is the 'patch' prog you've said to 'click here for', lovinglinux?

And I can't find 'digicam' as relates to a photo editing prog...

Sorry. It was a typo. fixed. Just click to install - [phatch](apt:phatch) and [digikam](apt:digikam)

---

### Post by loosie on 2009-09-04
Thanks mate! You're a star! Too easy!

---

### Post by loosie on 2009-09-07
All previous suggestions been very successful, thanks. But I've just thought of one more prog that I had on Windows.... A photo panorama program, which joins a selection of photos together to make a panorama. Any such beast in the Linux range??

---

### Post by lovinglinux on 2009-09-07
> **loosie said:**
> All previous suggestions been very successful, thanks. But I've just thought of one more prog that I had on Windows.... A photo panorama program, which joins a selection of photos together to make a panorama. Any such beast in the Linux range??

Go to Add/Remove Manager and search for panorama. You can also look for Linux alternatives at [http://linuxappfinder.com](http://linuxappfinder.com) if you can't find with the Add/Remove.

---

### Post by Bartender on 2009-09-07
I use hugin for panoramas.  There's a version in the repos.  
The repos are safe and relatively easy for new users, but newer versions of programs can often be found and installed once you figure out the extra steps.  I don't know if there is a newer version of hugin than the one in repos.
If you're not real familiar with Synaptic Package Manager, make sure to maximize the window when you open it.  If the window is not maximized, you won't see the real "Search" function, the one with the magnifying glass.  There's a "Quick search" box that comes up when Synaptic is downsized, but I don't know what the heck it does because it sure doesn't find what I'm asking for!  In the real "Search" window, type in 'hugin'.  Synaptic will also install enblend, enfuse, hugin-data, and hugin-tools.

Or, I'm pretty sure this command will do it:
```
sudo apt-get install hugin
```

hugin is a lot of fun.  Definitely want to google some hugin tutorials because there are several tools, such as "Optimizer" and "Stitcher", and it can be a little confusing.


Sometimes hugin can detect the focal length automagically from the file metadata, sometimes it can't.  If it can't it will ask you to type in a focal length.  If you don't know, guess, and if the results are horrible start over and guess again.

Also, hugin does not like complex file names.  I'm in the habit of copying the pictures to the desktop, then giving them very simple names.  "pic1.jpg" and "pic2.jpg" for instance, or something similar.  then start hugin and browse to the desktop.  If the file names are complex, hugin will throw an error about not being able to find control points.

Once you install hugin you will find it in Applications>Graphics

If you have two pictures up and you want to change from Stereographic to Fisheye or whatever (listed in lower left corner of the panorama preview), toggle to the new mode then click once right in the center of the crosshairs on top of the panorama to refresh.

---

### Post by loosie on 2009-09-07
Thanks very much, yet again guys!

---

### Post by HappyFeet on 2009-09-07
> **loosie said:**
> All previous suggestions been very successful, thanks. But I've just thought of one more prog that I had on Windows.... A photo panorama program, which joins a selection of photos together to make a panorama. Any such beast in the Linux range??

I believe fotoxx has that capability.

---

