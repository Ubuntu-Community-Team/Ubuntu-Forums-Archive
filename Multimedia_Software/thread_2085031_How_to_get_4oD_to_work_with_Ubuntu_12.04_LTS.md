---
title: "How to get 4oD to work with Ubuntu 12.04 LTS"
date: 2012-11-17
forum: Multimedia Software
---

### Post by stevecook on 2012-11-17
Hello there,  Steve Cook calling.

I have Ubuntu 12.04 LTS 32 bit installed with a gnome classic interface. 

Whenever I have logged onto the 4oD website and tried to play their videos, the video just gets stuck in a loading pattern and never actually plays. After searching round for solutions for about a month I found the following solution. I have no idea how it works. But, all the 4oD videos play now so I thought I would share the information:

Firstly, make sure you have got the latest version of flash installed. You can do this from the Ubuntu Software Centre located in your main menu. Type "flash" in the search box and then follow the installation instructions. Chances are, of course, you may well have the latest version installed and so you either don't need to do the above or the software centre will tell you you already have the latest version installed.

Assuming the latest version of flash is installed:

Copy and paste the following command into a terminal window (you need to press CTRL/SHIFT/V in the terminal window to do this).

** sudo apt-get install hal**

Then press ENTER

Follow any installation instructions in the terminal window (there may not be any)

That's it.

If you now go to the 4oD website and try to play a video, it works!

Or, at least, it does for me.

---

### Post by ciphoenix on 2012-11-17
thanks, it works

---

### Post by coldraven on 2012-11-17
From here:
[https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy)

"Hal is in the process of being deprecated, since it has become a large monolithic unmaintainable mess, and also duplicates a lot of functionality which are nowadays provided by udev and the kernel itself. Please see [David Zeuthen's]("http://lists.freedesktop.org/archives/hal/2008-May/011560.html") and [Kay Siever's]("http://lists.freedesktop.org/archives/devkit-devel/2009-April/000140.html") summaries of plans."

So what is hal? I too was wondering why 4OD would not play in Kubuntu 12.04

Edit: I have looked at the Wikipedia page for hal. I still don't understand, does 4OD use a special version of flash or is this javascript related?
I usually just avoid sites that want me to install Silverlight or some other plug-in, their loss.

---

