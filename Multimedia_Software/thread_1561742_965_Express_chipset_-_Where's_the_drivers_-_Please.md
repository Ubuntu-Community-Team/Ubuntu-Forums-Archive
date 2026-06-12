---
title: "965 Express chipset - Where's the drivers? - Please help! &gt;_X"
date: 2010-08-26
forum: Multimedia Software
---

### Post by xjesse on 2010-08-26
Hi, from what I've read I know that Ubuntu should provide me with the best drivers available for my vga. My main problem is Runescape. I'm sure you've heard of it? I play daily and on Ubuntu I'm only able to get the run down cheesey graphics of the game; NOT the high detail. On the same machine while running Windows I'm able to install the Intel driver for my vga and out comes the high detail graphics. Now, where is this driver for Ubuntu?

System specs:
Dell Latitude D530 
Ubuntu 10.04 x86


Like I said, PLEASE someone must know something. I've been struggling with this problem for a while now. 

The command lspci | grep vga returns nothing in a terminal. 
What should I do?

Thanks.

---

### Post by tommcd on 2010-08-26
> **xjesse said:**
> 
System specs:
Dell Latitude D530 
Ubuntu 10.04 x86
According to this page:
[http://reviews.cnet.com/laptops/dell-latitude-d530-laptop/1707-3121_7-32757813.html](http://reviews.cnet.com/laptops/dell-latitude-d530-laptop/1707-3121_7-32757813.html)
Your laptop uses intel x3100 graphics. This should work ok as far as I know. Is Runescape the only thing you have problems with?
> **xjesse said:**
> 
The command lspci | grep vga returns nothing in a terminal. 
What should I do?

Run lspci like this:
```
lspci | grep -i vga
```
It should show your graphics card then.

---

### Post by xjesse on 2010-08-26
Thanks for your interest in my problem. :)

I've attached a screen shot to give you an idea of what I'm seeing. I'm stuck on safe mode graphics only and my terminal reads:

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller 

as my video card. 

Also yes, Runescape is the only game I actually play at the moment. So I haven't tried or had any other problems with any other games while running Ubuntu.

So I'm guessing the driver isn't the issue here. What is it that I'm missing?

Edit: I forgot the screen shot, ha. 

Also, I have compiz installed and running. I've uninstalled and it made no difference to the graphics in Runescape. Blah. 

Any more suggestions or ideas? .... Please? :|

---

### Post by xjesse on 2010-08-26
I'm giving up on trying to upload the screen shot. So here. ><

[IMG]http://i33.tinypic.com/et8pdd.png[/IMG]

---

### Post by Yellow Pasque on 2010-08-26
The intel linux driver is just slower than the intel windows driver..

---

### Post by xjesse on 2010-08-26
> **Temüjin said:**
> The intel linux driver is just slower than the intel windows driver..

So there's nothing I can really do then except maybe wait for an updated driver? If even...

---

### Post by xjesse on 2010-08-27
Update:

I happened to stumble upon this little guide:
[http://www.gamedev.net/community/forums/topic.asp?topic_id=575297](http://www.gamedev.net/community/forums/topic.asp?topic_id=575297)

and decided to try it out thinking maybe I was missing an OpenGL package or something. 

Nothing improved with Runescape but when I select OpenGL instead of Safe Mode, I now just get a blank grey screen instead. So something must have changed with OpenGL, right? Obviously not the better though.

I beginning to give up after hours of looking around the forums and such. If you've played Runescape, you know it's difference between Safe Mode and High Detail. It's HUGE.

Thanks.

---

### Post by xjesse on 2010-08-27
I hate to keep bumping this thread but I wanted to update you guys again. I've installed the update packages for Maverick (10.10) and look at my screen shot I've attached. Runescape is in **High Detail!!** Obviously it's still extremely buggy but it's one step closer in the right direction. It was using the OpenGL setting in Runescape. Before I wasn't even able to choose OpenGL. 

Can't wait till October. :D

What do you guys think??

---

### Post by Yellow Pasque on 2010-08-27
I think you should try xorg-edgers PPA on your Lucid install.

---

### Post by xjesse on 2010-08-27
> **Temüjin said:**
> I think you should try xorg-edgers PPA on your Lucid install.

What package then would I be installing after adding it?
This may come as a dumb question.

---

### Post by tommcd on 2010-08-27
> **xjesse said:**
>  I've installed the update packages for Maverick (10.10) and look at my screen shot I've attached. Runescape is in **High Detail!!** 
What packages from 10.10 did you install? And how did you install them?

---

### Post by xjesse on 2010-08-27
> **tommcd said:**
> What packages from 10.10 did you install? And how did you install them?

I simply just upgraded my distro via update-manager and let it install all the necessary packages. I'm now back on 10.04. I was a bit more curious about the ppa you mentioned. After adding the source, what package should I be looking for?



Thanks.

Edit: Sorry, it wasn't you that mentioned the ppa. Ha.

---

### Post by xjesse on 2010-09-05
bump. I'm still having this issue. I'm running 10.04 32 and only able to run Runescape with safe mode still.

Suggestions PLEASE!

---

