---
title: "aquaris m10 ubuntu edition"
date: 2016-03-25
forum: Mobile Technology Discussions (CLOSED)
---

### Post by bernard-godard on 2016-03-25
Aquaris M10 Ubuntu edition is going to be shipping very soon.
Unfortnately it is very difficult to get information about the software and hardware specs. Many articles have started appearing on the web but they are very superficial. The Canonical page  [http://www.ubuntu.com/tablet/devices](http://www.ubuntu.com/tablet/devices) is not better. I have many questions that are still unanswered after endless googling. Therefore I am hopping that knowledgeable people (maybe those using ubuntu touch on raspberry pi) lurking in the forums would kindly answer my questions:

- how does the native browser compare to Firefox/Chome? WebGL, HTML5 support? compatible with Firefox or Chrome extension such as noscript? 
- can the installed xmir run opengl apps? I need Cura ( [https://ultimaker.com/en/products/cura-software](https://ultimaker.com/en/products/cura-software) ), librecad, openscad, blender, stellarium and celestia. 
- anyone has experience with Cura on ARM linux to share?
- can the desktop mode be used without connecting any hardware  keyboard and mouse, but using an on screen keyboard and mouse?
- any good solutions for video-conferencing on ARM linux? apparently google hangouts is out, but maybe linphone might work.
- is there an equivalent of [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for Touch/arm? Or are the deb packages directly from Debian (if so what version?)
- does the hardware requires a modified kernel or can it run any modern linux distributions such as Arch ARM?

Thank you.

I am pissed off at Canonical for using Mir instead of Wayland and not supporting MER apps. This is painful for both users (less apps) and developers (more porting). Also I think that before selling such a product they should at least have made a native port of a video conferencing app such as linphone. But I need a tablet and there is not much other choice for a working Linux tablet except for Android (but this one is not a real Linux and not good as a Desktop).

---

### Post by grahammechanical on 2016-03-25
I was going to give some information but you could not resist adding that final comment and comments like that trigger an automatic response from me. You are not someone I want to have anything to do with.

---

### Post by bernard-godard on 2016-03-26
Dear Grahammechanical,

I am sorry that you feel that my comment is offensive. However I think it would have been dishonest for me not to add that comment. I have been using Linux almost exclusively for about 14 years 
and have seen the infancy of Ubuntu and a time where Canonical could really have made a larger difference in the Linux ecosystem. But Ubuntu owes a lot to upstream (Debian, Linux kernel and many other projects) and at times they have failed to work properly with upstream. Mir is one of those case. I think not working properly with upstream is very hurtful to the GNU/Linux ecosystem.
Now I am not saying it is always Canonical's fault: sometimes upstream is clearly wrong or doesn't want to work with you. But in the case of Mir I think Canonical made a big mistake. You may think otherwise and maybe you are right to think so, but as a potential customer for a Canonical product, I have to be sure that my complaints are heard. And I would repeat those complaints until either Canonical switches to Wayland or proves to me that Mir was a good choice (I have read a lot about Mir vs Wayland and I still cannot find any good reason for Mir except to get an hypothetical competitive/commercial advantage which in the end would hurt the ecosystem as a whole and thus also Ubuntu itself).
That said I like the Ubuntu distribution quite a lot and am using it nowadays on both my desktop and laptop.

Regards

---

### Post by warren3 on 2016-03-26
I have seen a video on You tube of the Aquaris M10 and it has Firefox in the apps section.

Is this false or real?  Will the M10 ship with Firefox as the browser?

---

### Post by bernard-godard on 2016-03-26
Warren3,

According to:
[http://www.omgubuntu.co.uk/2016/02/bq-aquaris-m10-ubuntu-tablet-announced-specs](http://www.omgubuntu.co.uk/2016/02/bq-aquaris-m10-ubuntu-tablet-announced-specs)
[http://www.omgubuntu.co.uk/2016/02/bq-m10-ubuntu-tablet-everything-you-need-to-know](http://www.omgubuntu.co.uk/2016/02/bq-m10-ubuntu-tablet-everything-you-need-to-know)

Firefox is pre-installed (so are Gimp, Libreoffice, XChat, Gedit) but this is a X11 app that runs in XMir (so called Desktop apps) and is not the default browser. It is also probably the same Firefox that you find in the desktop edition and is not optimised for tablet/touchscreen.

---

### Post by warren3 on 2016-03-26
Thanks.

I'm a bit disappointed in this really but not surprised.  I could not see Mozilla putting in the effort to design a FF edition for Ubuntu Touch considering the amount of market share.

Are you going to order one on Monday then Bernard?

---

### Post by bernard-godard on 2016-03-27
> **warren3 said:**
>  Are you going to order one on Monday then Bernard?

I have not decided yet.

On the plus side, I have just found out (thanks to this thread [http://ubuntuforums.org/showthread.php?t=2309165](http://ubuntuforums.org/showthread.php?t=2309165)) that there is another browser (Liri) available for Touch and based on the Chromium engine.

On the negative side, it seems that Ubuntu Touch is running on top of an Android kernel, likely using proprietary device drivers for Android ( [https://developer.ubuntu.com/en/start/ubuntu-for-devices/porting-new-device/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/porting-new-device/) ). This means it probably is not easy to install other Linux distributions on that device. 
However according to [https://wiki.ubuntu.com/Touch/FAQ#How_is_Ubuntu_Touch_connected_to_Android.3F](https://wiki.ubuntu.com/Touch/FAQ#How_is_Ubuntu_Touch_connected_to_Android.3F) newer versions of Ubuntu Touch runs Ubuntu as the underlying operating system and parts of Android are run in a LXC container. I would like to know which of the two architectures is used by the OS in BQ Aquaris.

Since in both case parts of Android is installed, it seems a pity if they don't support android apps. I wonder how difficult it is to install ART or Dalvik on top of Ubuntu Touch to run Android apps.

---

### Post by bernard-godard on 2016-03-28
In the end I pre-ordered the tablet. Will give feedback after I have tested it (first have to wait for delivery).

---

### Post by warren3 on 2016-03-28
I'm so tempted but I think I'll regret it.

---

### Post by handaxe on 2016-03-29
There is[ this initiative]("https://www.facebook.com/MJ-Technology-LLC-576568032444682/"), which if successful is a died-in-the-wool linux tablet, from the drivers up.  If successful is the big qualifier, as they are moving the fundraiser from FundRazr to IndieGoGo and it appears to be taking longer than they wrote it would. Good specs, attractive design.

---

### Post by Jon_Thomas on 2016-03-31
> **handaxe said:**
> There is[ this initiative]("https://www.facebook.com/MJ-Technology-LLC-576568032444682/"), which if successful is a died-in-the-wool linux tablet, from the drivers up.  If successful is the big qualifier, as they are moving the fundraiser from FundRazr to IndieGoGo and it appears to be taking longer than they wrote it would. Good specs, attractive design.

I have been following this tablet for the last 6-9 months on their FB page.  Their IndieGoGo campaign went live yesterday.  Check the videos out for yourself.

---

### Post by Jon_Thomas on 2016-03-31
> **bernard-godard said:**
> Warren3,

According to:
[http://www.omgubuntu.co.uk/2016/02/bq-aquaris-m10-ubuntu-tablet-announced-specs](http://www.omgubuntu.co.uk/2016/02/bq-aquaris-m10-ubuntu-tablet-announced-specs)
[http://www.omgubuntu.co.uk/2016/02/bq-m10-ubuntu-tablet-everything-you-need-to-know](http://www.omgubuntu.co.uk/2016/02/bq-m10-ubuntu-tablet-everything-you-need-to-know)

Firefox is pre-installed (so are Gimp, Libreoffice, XChat, Gedit) but this is a X11 app that runs in XMir (so called Desktop apps) and is not the default browser. It is also probably the same Firefox that you find in the desktop edition and is not optimised for tablet/touchscreen.

Am I understanding correctly then that XMir is a virtual environment then? 

 I have seen something like that on Android used by a developer to run the Gimp from within a virtual Lubuntu Linux desktop just for that app alone.  It was slow and a real pain to get data into and out of.

That would explain why I have seen some people question how to run x86 apps on Ubuntu Touch.  Not the most efficient use of resources.

---

### Post by bernard-godard on 2016-03-31
Jon,

XMir is not a virtual environment. It is an X server running on top of the Mir display server. This should have (almost) no impact on performance.

---

### Post by Jon_Thomas on 2016-03-31
> **bernard-godard said:**
> Jon,

XMir is not a virtual environment. It is an X server running on top of the Mir display server. This should have (almost) no impact in performance.

Ok, thanks for the clarification.

---

### Post by mmoutoux on 2016-05-07
Anyone interested in this product, please don't waste your money. The tablet itself is fine, if a bit underpowered. But, the OS is garbage as is the goofy interface. I've owned tablets since the earliest android ones and even version 1 was far better than the junk that is on the m10. As an example, the default browser doesn't support html5 so a lot of Web pages don't work properly. Firefox is installed but only works if you have a keyboard. Most of the other apps, if you can call them apps, are facades over a Web page. And finally, the soft keyboard, it was designed for European usage with a lot of characters only usable for romance languages. There are even vitally missing symbols for Linux such as the vertical bar. There doesn't seem to be any way of side loading software without unlocking the OS and voiding the warranty and disabling software updates. So, forget about using apt-get to install something else. Even if you could, you wouldn't be able to use the program because the soft keyboard only works with customized software. 

So, the bottom line is, don't waste your money like I did. I now have a $349 paperweight (oh,  with a cover and screen protector, I almost forgot). If anybody needs an expensive paperweight, I've got one you can have real cheap.

---

### Post by dtarrant on 2016-05-17
I disagree with a couple of points made by mmoutoux. My experience is that the browser does support html5 and the soft keyboard does provide a pipe key. I'm an optimist and although this product is certainly raw around the edges at the moment, I'm confident it's going to get a whole lot slicker.[SIZE=4][/SIZE]

---

### Post by eaz2 on 2016-07-05
I really wanted this tot succeed, hut i gave up, finally.
The m10 with Ubuntu is just not ready. No decent network support, browser limitations, all apps seem just prof of concept. Not write access etc on the drive for customisation. I must admit, the system is stable. 
Just not enough tot make me like the thing. So i flashed it tot Android and now I have a regular tablet. Ubuntu is on my laptop and desktop, nut not on the tablet..

---

### Post by Johan_Helsingius on 2016-07-06
> **eaz2 said:**
> So i flashed it tot Android and now I have a regular tablet.

Is there a supported (with security updates) android available for the M10?

---

### Post by eaz2 on 2016-07-06
There is very recent and decent android, supported by the supplier, this tablet is also supplied with android, so no problem:

I did not succeed to install it from windows, but from my xubuntu machine, it was a piece of cake:
download the android image
download the flash program

Make a couple of sudo's, and there it goes. Took about 1 hour in total (and some patience). You can always flash back to ubuntu, the image is available from the same site.

e.g:
[http://www.mibqyyo.com/en-articles/2015/09/16/ubuntu-android-installation-process-for-bq-aquaris-e4-5-and-e5/#/vanilla/discussion/embed/?vanilla_discussion_id=0](http://www.mibqyyo.com/en-articles/2015/09/16/ubuntu-android-installation-process-for-bq-aquaris-e4-5-and-e5/#/vanilla/discussion/embed/?vanilla_discussion_id=0)

---

### Post by Johan_Helsingius on 2016-07-07
Thanks! Worth looking into!

---

### Post by Johan_Helsingius on 2016-07-07
Hmm, I don't seem to be able to find the SP_Flash_Tool_exe_linux_v5.1424.00.zip file :(

---

### Post by eaz2 on 2016-07-07
[http://spflashtool.com](http://spflashtool.com))
[http://www.mibqyyo.com/en-download/](http://www.mibqyyo.com/en-download/)

---

### Post by Johan_Helsingius on 2016-07-08
> **eaz2 said:**
> [http://spflashtool.com](http://spflashtool.com)

Thanks!

---

### Post by Michael_Crees on 2016-08-08
This has been a useful thread, I have found that the M10 FHD makes a perfectly adequate Android tablet with none of the problems evident under Ubuntu Touch. So none of them are hardware problems.

---

### Post by Tao_Joannes on 2016-08-25
> **Michael_Crees said:**
> This has been a useful thread, I have found that the M10 FHD makes a perfectly adequate Android tablet with none of the problems evident under Ubuntu Touch. So none of them are hardware problems.

I flashed it to the Android rom about two weeks after I got it, use it constantly all day every day with no performance problems.

---

