---
title: "Android Tethering for my HTC Droid Incredible (like PDANet)"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by ionFreeman on 2010-05-01
Hi!

I just got my Incredible running, and wanted to tether my laptop to it. Is there anything like PDANet that runs in Ubuntu?

Ion

---

### Post by agenthex on 2010-05-04
I did a bit of research, as I expected to inherit my brother's Motorola Droid.  There is a package called android-wifi-tether that will only work on a root-ed Droid.  I do not think this will work on the Incredible, since I see no information on how to root it.

Perhaps soon enough they will have root access to the Incredible and you can use this hack.

---

### Post by vacaloca on 2010-05-06
Hey guys, just posted this on androidforums, but it sprung up into a debate. :p

[http://androidforums.com/tips-tricks-incredible/74400-howto-tether-natively.html#post691147](http://androidforums.com/tips-tricks-incredible/74400-howto-tether-natively.html#post691147)

Follow the guide [here]("http://ubuntuforums.org/showthread.php?t=343989") to set it up on the Ubuntu side. I remember I set up an older Motorola feature phone by following step 2 of that guide using usbserial driver.

Cheers!

Edit: This should work for the HTC Droid Eris as well.
Unfortunately, I don't believe the Motorola Droid has a native USB modem, so the only choice for Ubuntu/Linux might be PDANet over bluetooth without rooting.

---

### Post by c_wilson on 2010-05-20
Since this is high in the search results for "linux tethering on Droid Incredible" i thought i'd share some love.

Using this guide for the original droid:

[http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html]("http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html")

all i had to do was change the device ID and it worked flawlessly. 

Under step 4 where you're creating a new udev rule, we have to use a device id of "0bb4" for the incredible. i.e:

replace ATTRS{idVendor}=="22b8" with ATTRS{idVendor}=="0bb4"

If you want to use the script from that link instead of the step-by-step, you'll have to go into the .py file and change the {idVendor} line like above - I just followed his step-by-step and was up and running in 5 minutes. 

Now *that* is some hot linux on linux action.

---

### Post by growlf on 2010-05-31
Definitely - the [http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html](http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html) is the way to go.  I am on mine now through this.  All ports work, and it flys!  In comparing the connectivity speeds with my MiFi - it is winning fairly consistently, I think that this is due to the better built-in antenna in the phone.

Shannon VanWagner - you got my vote!  I'd like to see a version in the Launchpad PPA repos soon!  Any chances of this?  I offer my assistance if you want it.

---

### Post by UUB86 on 2010-06-04
The python script given at the above link worked with xubuntu 10.04 on an htc incredible.  Using it now to post this.

---

### Post by linuxpoet on 2010-06-24
FYI, I had to install ia32-libs to get it to work as I run 64bit Ubuntu

---

### Post by MoebusNet on 2010-07-10
+1

Shannon's script worked perfectly for me the first time; after enduring a 1 month wait for my HTC Incredible, it tethers perfectly with my Dell Latitude D800 running Ubuntu 8.04. I'm using this setup to post this comment now.

Shannon rocks!
:guitar:

---

### Post by HDave on 2010-07-27
I've tethered 2 other verizon wireless cell phones with ubuntu in the past and the network manager's mobile broadband capability always "just worked" -- why doesn't it with the htc incredible and has anyone here filed a bug in launchpad?

---

### Post by NongA_TongE on 2010-07-29
+1
Shannon's Script worked perfectly, with no additional configuration necessary for my Droid Eris!
Posting with it now!
\\:D/

---

### Post by Tim_Crandall on 2010-09-10
Hey everyone. I'm new to the Android Incredible and fairly new to Ubuntu as well. I'm trying really hard to understand how to get proxoid or azilink to work with my android, but I think that I need someone to really dumb it down for me, because the step by step instructions I've been reading through on all of these links are not working for me. I'm sure I have sometime wrong that is simple. 

I'm currently operating the newest version of Ubuntu, and I have the latest software on my android. My computer is old. IBM Thinkpad, T40. If any of you are willing to take the time to step me though this, I would really appreciate it. Thanks everyone!

tim

---

### Post by TurtleJuice on 2010-09-22
I'm having the same problem. I'm using 10.04 along with my incredible and after downloading the files I extract them and paste in the first step for tar which I'm guessing sets that file as the Target but it says the file doesn't exist in the terminal though.its.on there.  Any  help appreciated.

---

### Post by linwiz on 2010-11-17
an easier way is discussed here: [http://ubuntuforums.org/showthread.php?t=1530546](http://ubuntuforums.org/showthread.php?t=1530546)

---

