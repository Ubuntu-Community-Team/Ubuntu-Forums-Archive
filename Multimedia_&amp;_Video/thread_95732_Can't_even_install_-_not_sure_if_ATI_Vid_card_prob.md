---
title: "Can't even install - not sure if ATI Vid card problem or something else"
date: 2005-11-27
forum: Multimedia &amp; Video
---

### Post by tuaz on 2005-11-27
I'm a total newbie to Linux.  I tried to install Kubuntu Breezy as a dual boot OS on my Windows PC, and I couldn't even get past/complete the installation process:  I press ENTER to start the boot process. After a long series of text scrolls past the screen, it goes blank, except for a little message on my LCD monitor telling me, "unable to display digital output" or something like that.  Everything hangs at that point.  The keyboard doesn't work so I have to switch off the machine.

I've gone thru all the Stickied threads and I'm guessing it's because I have a ATI Radeon X300 video card.  Certainly I can't believe it's because Kubuntu doesn't support DVI output on an LCD monitor.

However, in all the posts and threads I've looked at, it appears as if people were able to install their Ubuntu first, then because they had problems with their video output, they then removed the old ATI drivers, and obtained and reinstalled the new fglrx driver.  In my case, I can't even get past installation.

Would appreciate any help.  I'm really eager to learn more about Linux and I thought the mindset of the Ubuntu strain of Linux was particularly nice.  My aim is to slowly get less dependent on Windows (and Microsoft in general), and I have been following with great interest the news on what's been happening around the world regarding open-source software.

My set up is:

Dell Dimension 5150
CPU: Pentium 4, 3.20 GHz
RAM: 1 GB
Video Card: Radeon X300 SE 128MB HyperMemory
Dell LCD Monitor connected by DVI cable for digital output
Sound card: Creative Soundblaster Live!
2 SATA hard drives (intend to install Linux on 2nd drive)

POST-EDIT: Have just discovered that my Pentium 4 model 640 HT CPU _**MAY**_ be 64-bit, but I can't be sure.  I went to this link:

[http://www1.ap.dell.com/content/products/productdetails.aspx/dimen_5150_sg?c=sg&l=en&s=dhs&~tab=specstab#tabtop](http://www1.ap.dell.com/content/products/productdetails.aspx/dimen_5150_sg?c=sg&l=en&s=dhs&~tab=specstab#tabtop)

and clicked on "learn more", then "Details" in the pop-up window.  Under "64-bit enabled", it didn't state YES or NO, but "16K".  What in the world does that mean?  Do I install i386 or AMD64 versions of Kubuntu on my PC?




Thanks in advance,
tuaz

---

### Post by Iandefor on 2005-11-30
I'm not certain what that "16k" means, but I can tell you this: if it's an AMD64-based architecture (I doubt that this is the case with your system), not only will it run Ubuntu AMD64, it will also run Ubuntu i386, meaning that even if the processor is 64-bit, that isn't the problem.

---

### Post by nalmeth on 2005-12-01
although landefor says your 64-bit processor wouldn't make a difference, what have you got to lose but more time? Download the amd64 installer, just for the halibut! ;) 

never say never

---

### Post by Patsoe on 2005-12-01
or, you could opt for the shorter download first: 
[http://www.intel.com/support/processors/tools/piu/](http://www.intel.com/support/processors/tools/piu/)
this Intel tool, running from Windows or as bootable thing, will answer the question for you.

My advice: I'm running the 64bit flavour, and I've just been through the fun of doing all kinds of weird things (standing on my head included) to get 32-bit programs running. It was very instructive for me, but it takes some effort (see e.g. the '32-bit chroot' HOWTO...). 
If you do not need 64bit programs (mainly benefits scientific apps), having working flash-plugins for Firefox and being able to run Acroread and Wine easily (I got them running now, but not easily) may be good reasons to take the i386 flavour - especially since it is just as fast generally.

Videocard trouble: have you tried the boot option 'vga=771'? I had to do that too, because otherwise the installation would lock up, garbling the screen. It sets your card to a low res (compatibility) mode for the installation. So, at the 'boot:'-prompt you type: 'linux vga=771' then enter.

---

### Post by tuaz on 2005-12-01
Ya, I saw the vga=771 advice on another thread, and tried it.  Seemed to work.    I was allowed to install the whole thing, so I thought.  Until it said that it was time to reboot the whole system, and then something else happened.

On reboot, the "kubuntu" logo comes on the screen, text scrolls saying various modules are being loaded, but then, I'm asked to enter my user name and password in a text DOS-like screen.  I do that, but then I remain in this DOS-like environment.  

There's a flashing underscore cursor waiting for my commands.  I try to type in some rubbish commands like "run", "login", and it gives me a "bash [bla bla bla not a valid command, etc]" kind of message.  About the only things I am able to do from this command line is "exit" and "help" (which gives me a HELP screen which I do not understand).

That's where I am at the moment in the my attempt to install Kubuntu.  I can't get into the graphical environment and login screen of Kubuntu that I've seen on screenshots.  I'm really puzzled now.

---

### Post by eobanb on 2005-12-01
The Kubuntu logo you are seeing is just part of Breezy's graphical boot sequence.  It sounds like X failed to start, which means there's some problem with the video driver...which is kind of odd, really.  I would have a look at [this section on the Ubuntu FAQ]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver") on how to install the latest ATI driver, although instead of Synaptic you'll have to use apt, because Synaptic won't run without X.

To install the xorg-driver-fglrx package, type:

```
sudo apt-get install xorg-driver-fglrx
```

hit enter, and then you'll probably have to hit Y to confirm.

Since you've never used Linux before, this might be a good time to make sure you understand how package management works, too, so read[this section of the FAQ also]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-installing-applications").

Actually, just save yourself some trouble and read most/all of it.

--Eoban

---

