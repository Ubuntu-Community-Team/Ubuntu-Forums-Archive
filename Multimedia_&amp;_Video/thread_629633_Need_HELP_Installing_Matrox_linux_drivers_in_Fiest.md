---
title: "Need HELP Installing Matrox linux drivers in Fiesty."
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by LegionOfAWWR on 2007-12-02
Hey all,

    So I have a Matrox Millennium G450 graphics card that I want to install in Fiesty. I have gone to matrox's website and I have downloaded the necessary linux drivers. Once I unzip the drivers I am left with 3 folders and an install.sh script file. Now this is where I have no clue on what to do. Am I supposed to run the install.sh file or am I supposed to run some other install code? Thanks for any help you can give.

Legion

---

### Post by clubsoda on 2007-12-06
Try the drivers from [http://matrox.tuxx-home.at](http://matrox.tuxx-home.at) instead.

---

### Post by LegionOfAWWR on 2007-12-06
Hey thank you so much. Question though. How do I tell which set to download? I have a choice of 4.4.1, 4.4.2, and 4.4.3. Thanks again!

Legion

P.S. Also which directory would I place the drivers in? I have read some other articles online concerning BSD, but none of Ubuntu. Thanks again!

---

### Post by clubsoda on 2007-12-06
Use the latest one, 4.4.3.  It's a while since I did this but I wouldn't even bother with the script if I had to do it again.  Just find the latest xserver directory in the package, probably 7.0.0, and manually copy the two files you need:-```
sudo cp -pi mga_drv.so mga_hal_drv.so /usr/lib/xorg/modules/drivers/
```
As long as your xorg.conf is using the mga driver that should at least get you started.  

Read some of the threads at that website I linked for the finer details on settings.  Make sure you have libgl1-mesa-dri and libgl1-mesa-glx packages installed too - that improves your framerate fivefold.  Check /var/log/Xorg.0.log to make sure your graphic memory is correctly recognised, DRI is getting enabled etc.

---

### Post by LegionOfAWWR on 2007-12-07
Hey clubsoda thanks for the help. I really appreciate it. I was looking everywhere for that damn drivers directory! lol. Could  you pm me the link because I don't see it in the thread. I'd appreciate it. Thanks again for all the help!

Legion

P.S. I am trying to set up my dual monitors similar to XP where I simply extend the main desktop to the next screen. Would I need to follow twinview or mergedFB? Thanks again!

---

### Post by LegionOfAWWR on 2007-12-07
P.P.S. I am a bit of a noob every now and then. What exactly are the two other packages and where would I find those? Thanks again, this REALLY helps :)

---

### Post by clubsoda on 2007-12-07
Hi LegionOfAWWR,[quote="LegionOfAWWR"]I was looking everywhere for that damn drivers directory! lol.[/quote]:) You don't have to remember them, just open a terminal and type ```
slocate mga_
```
[quote="LegionOfAWWR"]Could you pm me the link because I don't see it in the thread.
...
What exactly are the two other packages and where would I find those?[/quote]
Not sure if you're posting to this thread from an e-mail application(?)  If so, open this URL in a browser:-
[http://ubuntuforums.org/showthread.php?t=629633](http://ubuntuforums.org/showthread.php?t=629633)
Then, you should see the link I posted and the exact names of the other two packages in my earlier messages.

To check if those packages are already installed, find the **Synaptic Package Manager** in your menu and search for them from there.

Cheers

---

