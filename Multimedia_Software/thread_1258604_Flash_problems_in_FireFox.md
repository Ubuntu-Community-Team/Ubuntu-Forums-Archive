---
title: "Flash problems in FireFox"
date: 2009-09-05
forum: Multimedia Software
---

### Post by Struki on 2009-09-05
I'm a first time linux user, and by now I prity much got the hang of it all, and I generally like it better then windows.
Till now I managed around most of my bigger problems except 1. All of my flash videos in FF are running or should I say not running as they should. Meaning they are all kind of laggy, breaking frame by frame instead of normal stream. Sites like DailyMotion.com, Tube8, youtube, and not to mention that full screen viewing is out of thepicture. I've tried gecko, totem, mplayer, adobe flash for linux, resticted extras and so on, without any results.
The thing I hate the most is that situation when you hear "man just use windows", that one really gets me cause I'm really fed up with that Ms sh*** nevertheless the advantages.
'm really starting to like ubuntu and I'm using win less and less, but as I sad there are still some issues.

So can any of you advise on how to solve my problem?
tech specs are in my sig...
and if you need any other details for youto help me just ask...

---

### Post by Moop on 2009-09-05
In Synaptic do a search for gnash and swfdec. If they are installed you should un-install them. Then install the flashplugin-nonfree (if it's not already installed) restart firefox and test your flash.

---

### Post by lovinglinux on 2009-09-05
Check the Flash Optimization section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Rainbowsix on 2009-09-05
If you are using 64-bit, you need a different plugin.
With 64-bit, follow the instructions here:
[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

---

### Post by lzboy4jake on 2009-09-05
I have tried every possible online solution to actually getting flash 64bit and nothing works.  I do all the steps and the terminal will say it's installed but when I go to about:plugins there are no plugins listed.  Need serious help or I'm giving up hope on ubuntu.

---

### Post by RedRat on 2009-09-05
OK you say that you have tried various players in your original post. What exactly do you mean by that? Do you mean that you have downloaded the flash file, say from YouTube and it does not play in  a program like VLC? Or are you just having problems within Firefox? Do all videos give you this problem, e.g., .avi, Divix, mpg, and mov files? 

If you are having problems with various type multimedia files, then you have a codec related problem and not a Firefox problem per se. Furthermore, are running a 32bit or 64bit system, you were not clear about that. Try to give as much information about your situation as possible so that others here might help.

---

### Post by Barijazz on 2009-09-05
I ran into the same issue after installing swfdec.  It turned out I also had adobeflash_plugin installed (at least I think that was the name of the package).  The problem seemed corrected after completely removing both using Synaptic and installing the adobeflash_plugin package afresh.  I'd check the actual package name but I don't have my Ubuntu rig with me.

---

### Post by Struki on 2009-09-06
Ok so here goes:
I dont have gnash or swfdec installed...

I think I'm using 32bit but I'm not sure, how can I check?

I'll check [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567"), post changes if any.

My video players like vlc are working fine, the problem is within firefox, and its with all video files I came across. Also the problems is when I try full screen like on youtube, it's unwatchable.

And wow! As I look around on the forum this flash thing is a realy big issue in jaunty, I was starting to think it was something about my laptop

---

### Post by xieqiao on 2009-09-06
You have installed the 64-bit flashplayer correctly.  The problem seems to be Firefox 3.5.2, which does not support 64-bit Ubuntu 9.0.4.

---

### Post by Struki on 2009-09-06
> **xieqiao said:**
> You have installed the 64-bit flashplayer correctly.

I did? huh? How do you know that?

On the other news...
I tried some of the things written here:[**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567")

To be more specific what did is:

[I]sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree[/I]

Then I did this:

[I]sudo mkdir /etc/adobe
[/I]*echo "*[I]OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/[/I]
  
and in the end edited the xorg file:

     Code:
    * gksudo gedit /etc/X11/xorg.con*f 
 
adding the following lines:

     Code:

    [I]Section "DRI"
   Mode 0666
   EndSection
   Section "Extensions"
   Option "Composite" "Enable"
   EndSection [/I] 

So I think I got some improvments, but the whole thing still doesn't look like it's running like it should.

---

### Post by Struki on 2009-09-08
I've read all over the forums, this is a HUGE problem for ubuntu, and there are solutions, but I'm still not getting flash to work right, are there any other members that got something similar to me, or if any1 got any other ideas.

I'm pritty much used to ubuntu and I like the way whole thing is working, but lets face it todays sites are very much flash based, and i can't use the net without it working right, is there any notion on fixing this in the future by some officila ubuntu errr pepole?

---

### Post by lovinglinux on 2009-09-08
> **Struki said:**
> I've read all over the forums, this is a HUGE problem for ubuntu, and there are solutions, but I'm still not getting flash to work right, are there any other members that got something similar to me, or if any1 got any other ideas.

I'm pritty much used to ubuntu and I like the way whole thing is working, but lets face it todays sites are very much flash based, and i can't use the net without it working right, is there any notion on fixing this in the future by some officila ubuntu errr pepole?

It's not Ubuntu fault, but Adobe's fault.

---

### Post by Struki on 2009-09-08
But isn't there some open-source-third-party-something way to fix this??? I mean I'm freaking out here man!!

And all those windows guys go : nah nah nah thats why you use windows, cause u can make everything work there, and u can crack it, and bla bla bla.

sick of it man...

---

### Post by Rainbowsix on 2009-09-08
Try another web browser to see if it works in that one. It works in Opera perfectly.

---

### Post by lovinglinux on 2009-09-08
> **Struki said:**
> But isn't there some open-source-third-party-something way to fix this??? I mean I'm freaking out here man!!

And all those windows guys go : nah nah nah thats why you use windows, cause u can make everything work there, and u can crack it, and bla bla bla.

sick of it man...

There are open source alternatives, like gnash and swfdec, but they are not compatible with all sites.

At least there is light at the end of the tunnel for flash video, since Firefox 3.5 already supports html5 video, which is capable of playing videos without any plug-ins. If this will be widely adopted is to be seen, but there are already some important sites like YouTube and Dailymotion making experiments with it.

> **Rainbowsix said:**
> Try another web browser to see if it works in that one. It works in Opera perfectly.

Works the same on Opera here. Besides, I don't like the idea of giving up on my beloved Firefox :)

---

### Post by Rainbowsix on 2009-09-08
> **lovinglinux said:**
> Works the same on Opera here. Besides, I don't like the idea of giving up on my beloved Firefox :)

I've only opened Firefox once since installing Ubuntu, and that was to download Opera.

Anyway back on topic: if all else fails, you could try forcing the 32-bit version via ndiswrapper

---

### Post by RedRat on 2009-09-08
> **lovinglinux said:**
> It's not Ubuntu fault, but Adobe's fault.
I find this kind of glib response a bit patronizing and also not good for Ubuntu's future. If indeed it is Adobe's fault, why does it work for some but not others? If it was all Adobe's fault, then it should just plain fail on all Ubuntu installations. Yet it does not. Works fine for me and for many others. 

Whether we like it or not, flash websites are now out there and that is the way the web is being driven. Perhaps this is a ploy by MS to try to do in Linux, I don't know. But if Ubuntu and Firefox are to have a happy marriage, then someone, someplace is going to have work out these problems.

---

### Post by dynamics on 2009-09-08
Let me tell you frankly... Use new version of Opera (10.00 beta 3). Its just fantastic for any video playing. I use both Firefox and Opera (Firefox for search, mail etc and opera for all video streaming)

---

### Post by RedRat on 2009-09-08
> **dynamics said:**
> Let me tell you frankly... Use new version of Opera (10.00 beta 3). Its just fantastic for any video playing. I use both Firefox and Opera (Firefox for search, mail etc and opera for all video streaming)

Thanks! I am now trying Opera and I do agree it seems to work very well with Flash. At least I have tried YouTube and it works quite well. Seems a bit speedier than FireFox, but I am running the older FireFox 3.0 and not the most recent version. I will try Opera out.
Thanks again for recommending it.

---

### Post by RJARRRPCGP on 2009-09-09
Try this, seems to have fixed it:

[http://launchpadlibrarian.net/26188260/fixmtrr.sh](http://launchpadlibrarian.net/26188260/fixmtrr.sh)


-> Looks like it's **not** Adobe's fault.

-> Looks like it's **not** Mozilla's fault.

---

### Post by lovinglinux on 2009-09-09
> **RJARRRPCGP said:**
> Try this, seems to have fixed it:

[http://launchpadlibrarian.net/26188260/fixmtrr.sh](http://launchpadlibrarian.net/26188260/fixmtrr.sh)


-> Looks like it's **not** Adobe's fault.

-> Looks like it's **not** Mozilla's fault.

Would you mind providing the original discussion where you get that, so I can refer to it on my Firefox optimization tutorial?

I doesn't solve the problem, but it seems to help a little bit.

---

### Post by michael37 on 2009-09-13
> **lovinglinux said:**
> Would you mind providing the original discussion where you get that, so I can refer to it on my Firefox optimization tutorial?

I doesn't solve the problem, but it seems to help a little bit.

Affects only users who have Intel video card and are running Jaunty or Karmic.

[About the bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928") and [thread=1130582]where solution is described, see part A point 2[/thread].

---

### Post by lovinglinux on 2009-09-13
> **michael37 said:**
> Affects only users who have Intel video card and are running Jaunty or Karmic.

[About the bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928") and [thread=1130582]where solution is described, see part A point 2[/thread].

Thanks. That tutorial is already linked from mine.

---

