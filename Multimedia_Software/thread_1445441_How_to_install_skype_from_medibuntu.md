---
title: "How to install skype from medibuntu"
date: 2010-04-02
forum: Multimedia Software
---

### Post by fishtoprecords on 2010-04-02
I had my Logitech Webcam/mic working perfectly, in 8.10, but when I upgraded to 9.10, the video stopped working. The camera works in lots of other software, Cheese to luvcview to testing with  gstreamer-properties

But Skype's video crashes when I try to use the video camera. Usually a segmentation fault.

Lots of other threads here suggest that using the version of skpye packages in medibuntu is the solution. So I added medibuntu to my /etc/apt/sources.list, reloaded to get the latest directories.

I don't see any "skype" to install, either in Synaptics or in the shell with apt-get

Output from apt-cache search is

# apt-cache search skype
skytools - Database management tools from Skype to PostgreSQL
python-skype - Skype API wrapper for Python
skysentials - extra functionalities for Linux Skype client
skype-mid - Skype for MIDs


What do I load to get skype itself?

thanks
pat

p.s. any one have clues as to why this broke going from 9.04 to 9.10?

---

### Post by NightwishFan on 2010-04-02
I do not see skype in medibuntu, however here is a help document on skype.
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by kgarbutt on 2010-04-02
Hey Fish,

Here is how to install Skype.

First: open terminal and type: sudo gedit /etc/apt/sources.list

Second: add this to the end of your sources.list file:

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

Third: Save & close gedit, and close the terminal (important to close terminal).

Fourth: Open terminal again & type: sudo apt-get update

Five: from same terminal type this: sudo aptitude install skype

Fifth: Edit out sources.list again like this (if you want to):

# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

Six: close terminal & open Skype (Applications/Internet)

Seven: Enjoy.

---

### Post by fishtoprecords on 2010-04-02
Why is closing the terminal/shell important? I've never seen that before.

I used apt-get rather than aptitude, and while it installs fine, and audio works, video still causes skype to crash

---

### Post by kgarbutt on 2010-04-02
Hey Fish,

Does your video work in cheese? Do you have cheese installed. It may mean you need to have cheese installed. If you don't have cheese -- do this to get it:

sudo apt-get update
sudo apt-get install cheese

perhaps a restart (not sure here), then try Skype's video again.

Good luck man. Ken

---

### Post by fishtoprecords on 2010-04-02
Yes, it works perfectly in Cheese and luvcview and gstreamer-properties But it fails in Skype.

Before I bought my QuickCam® Pro for Notebooks, I had a Logitech QuickCam Chat, which worked perfectly but had poor video quality, which was not a surprise, since it was really cheap.

As part of debugging this today, I tried the cheap QuickCam Chat, and it works perfectly.

Most strange. The Pro used to work, but no longer does.

---

### Post by kgarbutt on 2010-04-03
Hey Fish, Glad you got a solution. Good talking with you. Ken

---

### Post by Island_Jon on 2010-04-10
I found the Skype for **Linux Beta v2.1.0.81** direct from Skype's web site to be the successful route.

First failed attempt was by enabling Medibuntu and using Synaptic to install: skype-mid, libqt4-svg.  
However once I started the application and registered an account (successfully) I could not login to the newly created account.  I therefore used Synaptic to uninstall both skype-mid, libqt4-sv and just downloaded the Skype for Linux Beta v2.1.0.81 package from the Skype website as described in [http://ubuntu-tutorials.com/2010/01/21/install-skype-for-linux-beta-v2-1-0-81-on-ubuntu-9-10/]("http://ubuntu-tutorials.com/2010/01/21/install-skype-for-linux-beta-v2-1-0-81-on-ubuntu-9-10/")

And as described in this above link, everything installed properly. I was not able to test the web cam since I do not have one, but voice did work.
------------
This PC is an old Dell Inspiron 8600 Pentium M running Intrepid v. 8.10.

---

### Post by libssd on 2010-05-19
**Environment**: 
Acer AA1 D150 netbook, running Ubuntu 9.04 (with all current updates).
Skype-Mid installed using Synaptic. From the package description: 

> This version of Skype is intended for use on Linux-based MIDs.

Canonical provides critical updates for skype-mid until October 2011.

After extensive experimentation, I finally got both the Acer and Skype talking to each other. Based on the test call, everything is working perfectly. 

One problem remains: There is no way to quit Skype after it has started. While Skype is running, the machine cannot be shut down. I have a work-around to this, using force-quit, but that is a brute force approach.

I have tried installing skype-ubuntu-intrepid_2.1.0.81-1_i386.deb, but was unable to get it to recognize the built-in microphone. Uninstalled Skype 2.1.0.81-1, and re-installed Skype-mid. The problem described above existed after a clean install of Ubuntu 9.04, and before installing Skype 2.1.0.81-1, so there is no possible interaction. 

**BUT**... Skype won't quit, and the machine can't be shut down while Skype is running. I can force Skype-mid to quit, and then shutdown normally, but there ought to be a better way. Suggestions?

---

### Post by cybrsaylr on 2010-05-19
I just installed Skype on 10.04 by simply downloading it off the Skype website.

---

### Post by libssd on 2010-05-19
Doh! :redface: After spending 24 hours trying to get Skype working...

In the leftside Skype-mid panel, click on More. 
Three options are presented: **History**, **Sign Out**, and **Quit**.

:biggrin:

---

