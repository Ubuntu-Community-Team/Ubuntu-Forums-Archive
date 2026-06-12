---
title: "How to get 4od working in Ubuntu and Xubuntu"
date: 2013-12-14
forum: Multimedia Software
---

### Post by stevecook on 2013-12-14
Hello folks. As many of you will have discovered, 4oD doesn't work in Linux. I already found one solution for Ubuntu which involves installing Hal with the following command:

sudo apt-get install hal

However, I have just hopped over to Xubuntu 13 and found that hal will not install. The following is an alternative solution to get 4oD working in Xubuntu:

1) Install Play-On-Linux from the Software-Centre.

2) Install Firefox inside Play-On-Linux. When Play-On-Linux asks you if you want to install Flash-Player at the same time, accept the install. Firefox itself will ask if you want to run it during the install. Tell it no. In other words, don't try and run Firefox until Play-On-Linux has finished doing what it needs to do as well as the Firefox installation itself.

3) When completed, open up Firefox from inside Play-On-Linux

4) Navigate to the 4oD site and sign in, then play whatever media you want. It works just fine. It's as simple as that!

If you want it to be all nice and seamless inside your Xubuntu GUI, then make a desktop shortcut to the Play-On-linux version of Firefox. Then rename the desktop launcher to "4oD", launch it, navigate to the 40D site and save this as the homepage. Then, the next time you launch the Play-on-Linux/Firefox(40D)  launcher, it will go straight to 4oD.

Indeed, I see no reason why this method should not work for *any* kind of media that will ordinarily run in Firefox in MS Windows but wont run in Linux.

Hope the above helps.

Steve Cook

---

### Post by monkeybrain20122 on 2013-12-15
There is actually a hal ppa for 13.10 

[http://www.omgubuntu.co.uk/2013/10/fixing-amazon-prime-streaming-drm-protected-flash-13-10?utm_source=feedly](http://www.omgubuntu.co.uk/2013/10/fixing-amazon-prime-streaming-drm-protected-flash-13-10?utm_source=feedly)

otherwise pipelight allows you to install Windows (DRM enabled) flash on Linux browsers, you may need to use an agent switcher with it.

[http://fds-team.de/cms/pipelight-installation.html#section_4](http://fds-team.de/cms/pipelight-installation.html#section_4)

---

### Post by stevecook on 2013-12-15
That's brilliant thanks. I didn't know about that.

I have incldued a copy and paste of the relevant section of that for completeness here:

> **Download & Install HAL &#8211; The Easy Way**

 Ubuntu user *Michael Blennerhassett *maintains a PPA for Ubuntu 13.10 only that contains the required HAL package, along with a patch from (*the always awesome*) Arch Linux folks that [fixes several issues]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/1182801") that result from using the older HAL package in Saucy.
 To add the PPA open a new* Terminal* window and enter the following commands carefully:
 sudo add-apt-repository **ppa:mjblenner/ppa-hal** sudo apt-get update && sudo apt-get install hal And that&#8217;s it.
 Following installation, *Amazon Prime, Google Play Movies, 4OD, *and a number of other DRM-demanding Flash streaming sites should start to function again.
 Having installed from the PPA, we tested Amazon Prime in both Firefox  and Chromium using the version of Flash in the Ubuntu repos. We found  that Amazon Prime *didn&#8217;t* work with Chrome&#8217;s built-in version of &#8216;Pepper&#8217; Flash.



It may still be worth holding onto the Play-On_Linux method I outlined, though, as a backup option for other types of web-media that may also not want to play ball on Linux.

---

