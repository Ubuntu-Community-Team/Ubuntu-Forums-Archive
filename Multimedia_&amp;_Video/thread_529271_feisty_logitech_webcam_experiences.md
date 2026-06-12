---
title: "feisty logitech webcam experiences"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by gatman3 on 2007-08-19
I just wanted to share my recent experiences with selecting webcams to use with Feisty, since I could only find sketchy information on up-to-date Feisty webcam support when I searched on my own.  It appears from my searches that Edgy had some serious problems with webcams, and that Feisty works better, but there still isn't much up-to-date information (that I could find, anyway) on Feisty support for specific webcams.  Hopefully this will be helpful to others who may be trying to get webcams going (this info would have saved me a lot of time had it been available).

Note that this is purely based on trial-and-error experience, and is limited to the specific Logitech webcams that I experimented with; I am not an expert in the drivers associated with the various webcams, and mostly tried to get something to just work "out-of-the-box".  I'm also not sure that my machines are representative of "typical", whatever that might be.

The first webcam I purchased was a "Logitech QuickCam or Notebooks Deluxe" not to be confused with the "Logitech QuickCam Deluxe for Notebooks" which appears to be a different and perhaps older product (a sarcastic thank-you to Logitech, although not unlike most computer peripheral vendors, for using confusing marketing names and little or no real technical info about the differentiation of their products). The QuickCam for Notebooks Deluxe advertised 640x480 resolution with 1.3 megapixel stills.   In any case, I plugged this webcam into my MSI 1013 notebook (yes, it's an unusual but oddly sexy little diy notebook) running Ubuntu Feisty, fired up Camorama, and found that it "just worked"... although, the colors were messed up in Camorama (I think the blues and yellow or greens were swapped, so my blue shirt looked yellow, and my skin looked blue).  In Kopete, it worked perfectly and with correct colors, and the picture quality was quite good in my opinion.  After searching for more info on the web, it appears that others have experienced this blue/yellow swap in Camorama, and can be fixed by adding a "color adjustment" effect in Camorama.  Picture quality with Kopete is good enough to even use to share whiteboard drawings with remote coworkers.

Emboldened by my first easy success, I decided to try to trade up to the "Logitech QuickCam for Notebooks Pro" which advertises higher resolution (a "True 1.3 Megapixel Sensor") and was only $20 more.  So, I took advantage of the no questions asked return policy where I bought my first camera and traded up.  This turned out to be a big mistake.  This camera did not work at all out-of-the-box and, in fact, I never got it working at all in any capacity.  After researching on the web, I learned that there -may- be some support for this camera... or perhaps older versions of it... using Video4Linux2, and I compiled and installed the latest linux-uvc driver which was my only hope to get it to work.  Nothing.  I also tried the, apparently now abandoned, PWC (Philips WebCam) driver which was also hinted at as a possibility, but nothing.  Even if I could have gotten it to work, I don't think that Kopete supports Video4Linux2 (I could be wrong about this) and it looked like I may have had to switch to Ekiga.

So... I returned that one and went back to the first QuickCam for Notebooks Deluxe.

Now on to my home desktop, which is an older Athlon XP 2600 also running Feisty.  After reading some favorable testimonials about the Logitech QuickCam Chat (half the price of the QuickCam for Notebooks Deluxe) I took the plunge.  This one worked out-of-the-box with Kopete, sort of.  Two problems: (1) image quality is significantly inferior to the QuickCam for Notebooks Deluxe, which advertises "RightLight" technology, and (2) the image would always start in Kopete in a very washed out state, but after pulling up the "Settings->Configure->Devices" menu it would correct itself.  I decided I could probably live with the lesser image quality, but I figured my wife wasn't going to be real happy using it if I told her that she had to jump through this goofy configuration hoop every time I asked her to bring up the webcam (we use Yahoo IM with Kopete, which works GREAT, by the way).  So I returned it and traded up to a "Logitech QuickCam Communicate STX".

My rationale with choosing the QuickCam Communicate STX was that, like the QuickCam for Notebooks Deluxe, it advertised the exact same resolution and the exact same "RightLight Technology" and "RightSound Technology", so I guessed (hoped) that it used the same chip as the one that I previously had such good success with.  Sure enough, I got it home, plugged it in and it "just worked", and looked and behaved identically to the excellent QuickCam for Notebooks Deluxe that I use on my laptop.  Plus, it mounts much better to my flat panel monitor than the QuickCam Chat, and it has a shutter to cover the lense which, although technically unnecessary, was something that I figured would raise my wife's comfort level with having a camera sitting on top of the home computer monitor pointed at her whenever she was using it.

I wish that Logitech would publish better technical specs, perhaps even list the specific chips used in their products.  Why do these computer peripheral vendors treat the whole world like a bunch of idiots that can't understand anything more than phrases like "RightLight technology" or arbitrary descriptions like "sharper video even in dim lighting".  Sharper than what?  Which other inferior product of yours is it sharper than, do tell?!  I had to deduce that the QC for Notebooks Deluxe and the QC Communicate STX use the same chip - and therefore have the same level of compatibility - because of certain shared marketing terms such as "RightLight" and "RightSound".  You wouldn't guess from the names that they share much in common.

To summarize (hopefully this will save others the hassles that I went through):

1. Logitech QuickCam Chat
Price = $
Worked out of the box, but had relatively poor image quality (compared with options #2 and #3 below) and required manually hitting the Kopete configuration every time it was initialized.  Also did not mount very well on my flat panel monitor, kept slipping off.

2. Logitech QuickCam Communicate STX
Price = $$
Worked out of the box very well, good image quality (for a webcam).  Worked perfectly with Kopete.  Works with Camorama, but need the "color correction" effect.  Mounted very well on my flat panel monitor (Samsung 931B).  Nice black color and black cord, blends well on my black monitor and in my dimly lit home office.

3. Logitech QuickCam for Notebooks Deluxe
Price = $$
Identical to #2 Logitech QuickCam Communicate STX (must use the same chip, just constructed for mounting on a notebook instead of on a desktop monitor).

4. Logitech QuickCam for Notebooks Pro
Price = $$$
Could not get it to work at all.  Yes I did try the uvc and the pwc drivers.  No joy.  Maybe some Linux guru could get it to work, but not me.  My guess is that it has a newer chip (it is supposedly a true 1.3 megapixel CCD, compared with the 0.3 megapixel CCDs in the options #2 and #3 above that worked well for me) and the Linux drivers probably haven't caught up to it yet (aside from the fact that uvc seems to have very limited application support, and pwc development seems to have been abandoned).

Both Logitech webcams that I settled on (QC for Laptops Deluxe and QC Communicate STX) appear to use the gspca driver, which was loaded automatically for me by my vanilla Feisty i386 installation (my gratitude to the fabulous Ubuntu developers).

I'm also not sure if this means that all Logitech webcams with true 1.3 megapixel CCDs (QuickCam Fusion, QuickCam Orbit, etc.) will not work well with Feisty (web searching suggested that there may be some success with other drivers like the linux_uvc driver... but not for me), but based on my experiences I'd be wary.  If I had to guess (and I can make at least an educated guess, since I am in the chip business myself), Logitech probably has one or more older families of products based on earlier CCDs (such as the QuickCam chat) that appear to have Linux support through the gspca driver but have relatively poor image quality (just because of older technology).  Then there is the 0.3 megapixel CCDs with "RightLight Technology" that also work with Linux and have very good image quality, and then there are the newest products with 1.3 megapixel CCDs that may not be well supported in Linux.

Your Mileage May Vary.

---

### Post by gatman3 on 2007-08-20
Just as an update, I have come to learn in the last few days that Logitech has released multiple products under the same name.  To clarify, here are the usb IDs referenced in my post above:

[FONT="Courier New"]Logitech Quickcam for Notebooks Pro    = 046d:08cb
Logitech Quickam Chat                  = 046d:092c
Logitech Quickcam Communicate STX      = 046d:08ad 
Logitech QuickCam for Notebooks Deluxe = 046d:08d8
[/FONT]

And here are some links to pictures with these products (sorry, these are US links to CompUSA, most convenient for me but may not be valid for too long;  logitech.com actually shows different pictures and presumably different products for some of these):

Logitech QuickCam for Notebooks Deluxe Webcam, 0.3 Megapixels
[http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200061+400054&Ne=400000&product_code=328756](http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200061+400054&Ne=400000&product_code=328756)

Logitech QuickCam for Notebooks Pro Webcam, 1.3 Megapixels
[http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200061+400054&Ne=400000&product_code=334529](http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200061+400054&Ne=400000&product_code=334529)

Logitech Quickcam Chat Webcam, 0.3 Megapixels
[http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200061+400054&Ne=400000&product_code=340909](http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200061+400054&Ne=400000&product_code=340909)

Logitech QuickCam Communicate STX Webcam, 0.3 Megapixels
[http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200061+400054&Ne=400000&product_code=342934](http://www.compusa.com/products/product_info.asp?pfp=BROWSE&N=200061+400054&Ne=400000&product_code=342934)

Yes, it's a big, scary world out there when it comes to webcams and linux.

---

### Post by Grigorius on 2007-08-20
Hi, have you tried this webcam: Logitech QuickCam Communicate Deluxe? (1.3 megapixel) ... I've been searching for a whie now but I can't get any reviews ...

---

### Post by buntunub on 2007-08-20
Hi, did you try luvcview out with any of those? The newer one probably would have worked well with that app using the right cli switches. Also, im sure it would have worked fine using ffmpeg for record. Uvc should work out of box under Feisty, especially with Ekiga, but I guess you tried something even poor Ekiga cant handle.

---

### Post by gatman3 on 2007-08-21
> **Grigorius said:**
> Hi, have you tried this webcam: Logitech QuickCam Communicate Deluxe? (1.3 megapixel) ... I've been searching for a whie now but I can't get any reviews ...

Nope, just the ones listed in my post.

I have come to learn that Logitech webcams with Linux are a VERY hit-and-miss world.  My best advice to everyone is to buy something from a big-box store with a no questions asked return policy (assuming you have that available to you where you live) and then keep trying different models until you get one that works with Feisty more or less out-of-the-box.  It's a hassle, but there doesn't seem to be any better way because Logitech has done its best to make this about as difficult on Linux people as possible by producing multiple models with the same name but with different chips... and no vendor supported linux drivers.

---

### Post by gatman3 on 2007-08-21
> **buntunub said:**
> Hi, did you try luvcview out with any of those? The newer one probably would have worked well with that app using the right cli switches. Also, im sure it would have worked fine using ffmpeg for record. Uvc should work out of box under Feisty, especially with Ekiga, but I guess you tried something even poor Ekiga cant handle.

 I tried the UVC drivers but had no success with any of those models.  Perhaps it would have if I knew the magic switches to throw.

The other thing I find odd about UVC is that I read all these posts where people say "Eureka!  I got it to work in luvcview!"  Yet, most of the good applications (Kopete, VLC) do not support Video4Linux2 yet with the UVC drivers.  So what's the point?  I'm sure Ekiga is a great application, but all of my friends have Yahoo accounts.

On a lighter note...  For grins, I installed the Logitech drivers in Windows XP running under VMware, and it worked great.  I guess VMware is always an option (I guess I could also gouge my eyes out...)  Of course it also loaded all kinds of crapware (yahoo desktop search junk), etc.  And THAT's why I prefer Linux even with all of these driver headaches.  :)

---

### Post by buntunub on 2007-08-21
> **gatman3 said:**
> 
The other thing I find odd about UVC is that I read all these posts where people say "Eureka!  I got it to work in luvcview!"  Yet, most of the good applications (Kopete, VLC) do not support Video4Linux2 yet with the UVC drivers.  So what's the point?  I'm sure Ekiga is a great application, but all of my friends have Yahoo accounts.



True,  but not everyone uses a webcam for video chatting. Alot of folks use webcams for security setups and for making recordings. Luvcview and ffmpeg do the trick quite nicely there. For voice chatting, Ekiga fulfills most peoples needs. I find that if I cant use one particular protocal (yahoo, aim, whatever) then I simply sign up for (and have my family/friends sign up) a protocall that my working stuff can handle. It does not take but a few seconds to do.

---

### Post by gatman3 on 2007-08-21
> **buntunub said:**
> True,  but not everyone uses a webcam for video chatting. Alot of folks use webcams for security setups and for making recordings. Luvcview and ffmpeg do the trick quite nicely there. For voice chatting, Ekiga fulfills most peoples needs. I find that if I cant use one particular protocal (yahoo, aim, whatever) then I simply sign up for (and have my family/friends sign up) a protocall that my working stuff can handle. It does not take but a few seconds to do.

All good points.  It would be nice, though, if this were documented well somewhere instead of piecemeal in 15 different sites spread across the web.  What the linux/ubuntu world needs is a database of webcam names, USB IDs and which driver supports them.  And documentation on which applications are supported by which drivers.  I'm not an extreme newbie (linux user for 8 years, Solaris user before that) but I can see how this would be extremely daunting to the novices trying to come over from Windows.

---

### Post by buntunub on 2007-08-21
> **gatman3 said:**
>  What the linux/ubuntu world needs is a database of webcam names, USB IDs and which driver supports them.  And documentation on which applications are supported by which drivers.  I'm not an extreme newbie (linux user for 8 years, Solaris user before that) but I can see how this would be extremely daunting to the novices trying to come over from Windows.

This already exists and has for quite some time. Try the linux webcam projects website out for more info.

---

### Post by gatman3 on 2007-08-22
> **buntunub said:**
> This already exists and has for quite some time. Try the linux webcam projects website out for more info.

I'm reading a little bit of "what, are you stupid?" in this.

Please educate me.  Can you provide a link?  When I google on "linux webcam projects" or "linux webcam projects website" nothing obvious pops out at me.

Here are the most useful links I did find:

[http://www.qbik.ch/usb/devices/devices.php](http://www.qbik.ch/usb/devices/devices.php)

This looks like a great site cataloging USB devices, whether or not they are supported  and the drivers that support them.  I wish I had found it a week or two ago.  Must have been buried after the first several dozen hits in google whenever I searched.

Unfortunately, though, of the 4 webcams that I tried in the last week, this database gets it all almost completely wrong compared with my experiences with Feisty.

1.  Logitech Quickcam for Notebooks Pro = 046d:08cb
qbik.ch doesn't have an entry for this USB ID.
Me, I couldn't get it to work.  But then I also didn't stumble across the magic luvcview switches to throw with it.
Score: 1-out-of-1 (I'll generously give them the benefit of the doubt for not knowing anything about this device)

2.  Logitech Quickam Chat = 046d:092c
qbik.ch gives this one a green check mark, works with spca5xx.
Maybe so, but when I used it with Feisty it worked but required annoying manual brightness and contrast tweaking every single time I started it up, as if the driver and/or camera didn't remember the last settings used.  In my book, that's pretty marginal.
Score: 1-out-of-2  (Sorry, but if I spend an hour or two screwing with something and can't make it work, it doesn't deserve a green checkmark).

3. Logitech Quickcam Communicate STX = 046d:08ad
gbik.ch give this one a red x, "no driver available".
I plugged it in and it worked perfectly out of the box with Feisty.  Once I figured out that the microphone was at /dev/dsp2, I got that working too (wouldn't expect a novice to figure that out, though).
Score: 1-out-of-3 (perhaps the database is just out of date with regard to this device, but I'm not giving it to them)

4. Logitech QuickCam for Notebooks Deluxe = 046d:08d8
qbik.ch doesn't have an entry for this one.
For me, it worked perfectly out of the box, same as #3.
Score: 2-out-of-4 (I guess I'll give them the benefit of the doubt on this one, and chalk it up to the database not being up to date with the current product offerings.  But that's a little bit of a weak argument, too).

Yep, we're batting a thousand here, kids.  Actually 2-out-of-4 is pretty good... in baseball.

Now, I did find another web site:

[http://www.exploits.org/v4l/](http://www.exploits.org/v4l/)

This one has links to information on lots of different V4L applications.  This would have been very helpful for me in understanding the webcam application landscape but, again, I unfortunately didn't stumble across it previously.  Now, I just need to visit and study each of the 106 (yes, I counted them) links provided and I'll be an expert.

OK, so this is what we geeks do, waste tons of time trying to figure things out, and enjoying every minute of it.  But linux still has a long, long way to go to crack the mainstream.

Maybe what Ubuntu needs is a massive hardware compatibility lab funded by some idealist like Mark Shuttleworth.  I mean, even if the hardware developers aren't willing to actually write linux drivers for their products, perhaps they'd at least donate one of every device for compatibility testing so they could be tested with the existing (and mostly excellent) efforts to write open source drivers.  Then, instead of googling all over creation to find mish-mosh about what's supported and what isn't, ubuntu could have an accurate, centralized database already available.

I'm dreaming again.

---

### Post by gatman3 on 2007-08-22
THE HOLY GRAIL OF WEBCAM INFO:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Good god, this needs to be indexed better!  Somehow we need to get Google to make this a sticky as the first page always listed whenever anyone searches for "linux webcam" or "linux webcam drivers".

---

### Post by buntunub on 2007-08-22
> **gatman3 said:**
> THE HOLY GRAIL OF WEBCAM INFO:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Good god, this needs to be indexed better!  Somehow we need to get Google to make this a sticky as the first page always listed whenever anyone searches for "linux webcam" or "linux webcam drivers".

Glad you found it! And you are 100% correct when you say that this is indeed what we geeks do for entertainment. I got my webcam working using that site (and many, many, many, many others including the ubuntu forums which were of most help), even though I will never use it, nor ever intend to use it, nor will anyone in my family ever use it.. Does not matter! It did not work at first, and so it became my one and only mission to get it working in Linux. Surprisingly, it was amazingly simple and easy to get up and running and was exceptionally well supported in Linux. So, I wholeheartedly DISSAGREE with your statement that linux has a long way to go for the prime time. It is just fine as is now and will only get better.

Btw, for luvcview the magic switches are not so magic. The info for it is plainly available via searches.

luvcview -f yuvy 

use -S for saving streams and use an mplayer script to run it (also available via searches).

---

### Post by gatman3 on 2007-08-22
> **buntunub said:**
> Glad you found it! And you are 100% correct when you say that this is indeed what we geeks do for entertainment. I got my webcam working using that site (and many, many, many, many others including the ubuntu forums which were of most help), even though I will never use it, nor ever intend to use it, nor will anyone in my family ever use it.. Does not matter! It did not work at first, and so it became my one and only mission to get it working in Linux. Surprisingly, it was amazingly simple and easy to get up and running and was exceptionally well supported in Linux. So, I wholeheartedly DISSAGREE with your statement that linux has a long way to go for the prime time. It is just fine as is now and will only get better.

Btw, for luvcview the magic switches are not so magic. The info for it is plainly available via searches.

luvcview -f yuvy 

use -S for saving streams and use an mplayer script to run it (also available via searches).

My, you are an argumentative one.  Linux is absolutely perfect, ubuntu even more so.

(Now it's your turn to tell me that I'm an idiot, and that Linux has a long way to go...)

Thank you for the help... I think...

---

### Post by pyjamashark on 2007-08-23
I thought I'd add my experiences with Logitech Webcams on Ubuntu Feisty Fawn:

Logitech Quickcam Fusion - couldn't get it to work.

Logitech Quickcam Express Plus - worked perfectly, just plug it in and hey presto!

Cool
joe

---

### Post by buntunub on 2007-08-23
> **gatman3 said:**
> My, you are an argumentative one.  Linux is absolutely perfect, ubuntu even more so.

(Now it's your turn to tell me that I'm an idiot, and that Linux has a long way to go...)

Thank you for the help... I think...

Lets back up. You posted a long rant about your webcam experiences and how some worked, some didnt.  Thats great. It was fairly obvious to me (judging by the wording of your original post) that you did not research your purchases prior to, nor did it seem like you did much research after the fact either. Your not the first person to have issues with webcams, and there is a wealth of information available freely on the web (and quite alot right here on these forums), accessable via selective (and yes, very time consuming) searches. It is not very much fun to do that type of research for some, I know, but hey, this is Linux, not Windows, and so whatever issues we run into, cie la vie. We do what we have to do to fix it, which is to pay the dues and do those very time consuming web/forum searches, learn bash commands.. all of it. I love that about Linux, and I have tremendous respect for those who take the time to post their fixes/how-to's, but thats me. Linux will never, ever, be like Windows, but it certainly is ready for the big time, because it is not hard at all to get all your stuff up and running if its not preconfigured on install or first plugin -- so long as your willing to put the effort in to do the research that is necessary. Not saying you didn't, just that it appeared you didn't. Either way, you found the info you needed  easily, so all is well.

---

### Post by gatman3 on 2007-08-24
> **buntunub said:**
> Lets back up. You posted a long rant about your webcam experiences and how some worked, some didnt.  Thats great. It was fairly obvious to me (judging by the wording of your original post) that you did not research your purchases prior to, nor did it seem like you did much research after the fact either. Your not the first person to have issues with webcams, and there is a wealth of information available freely on the web (and quite alot right here on these forums), accessable via selective (and yes, very time consuming) searches. It is not very much fun to do that type of research for some, I know, but hey, this is Linux, not Windows, and so whatever issues we run into, cie la vie. We do what we have to do to fix it, which is to pay the dues and do those very time consuming web/forum searches, learn bash commands.. all of it. I love that about Linux, and I have tremendous respect for those who take the time to post their fixes/how-to's, but thats me. Linux will never, ever, be like Windows, but it certainly is ready for the big time, because it is not hard at all to get all your stuff up and running if its not preconfigured on install or first plugin -- so long as your willing to put the effort in to do the research that is necessary. Not saying you didn't, just that it appeared you didn't. Either way, you found the info you needed  easily, so all is well.

buntunub, I think that if you reread my first post, the only thing I really "ranted" about was the fact that the hardware vendors such as Logitech (and chip vendors like Sunplus) aren't even willing to provide the Linux device driver writers like the phenomenally gifted M. Xhaard some basic documentation on their products so that they can avoid having to rely on reverse engineering.  And as a result, the breadth and quality of device drivers for Linux is sorely lacking what is should be (I think you'll find that M. Xhaard probably feels the same way based on his published comments).  And... as a further result of that, "out-of-the-box" interoperability generally sucks. 

The purpose of my post was a meager attempt to help others by sharing my experience when I simply plugged in four real devices currently sold at a typical big-box store, and the fact that two of them worked "out-of-the-box" with Feisty, and two of them didn't.  And even though I had found M. Xhaard's website, I didn't really need to because I tried using the UVC driver as is also specified as the proper driver by him - both from the "out-of-the-box" Feisty installation, and from manually compiling and installing the latest UVC driver from scratch.  No, I did not try the switches that you suggested for luvcview before I returned the device, but the cameras didn't work when I tried them with Ekiga either.  And they didn't work with Ekiga after I recompiled and reinstalled the latest UVC driver either, as was suggested in several posts.  And based on the responses that i have received both publicly and privately, I am not alone in my frustration with webcam support in Linux.  That frustration is certainly NOT directed at the driver writers like M. Xhaard, but at the hardware vendors who are not providing information to help him.  And the last thing that the community of Ubuntu users needs, many of whom like myself are not experts in the field, is "hit and run" posts by folks like you that are not terribly helpful and seem purposed to simply boost your own ego or something.

What I find offensive about your tone in your posts is that you come across with the arrogant position that the world of Linux devices IS well documented and well supported and that anyone who doesn't agree with you must be a weak-minded fool who hasn't done their proper homework.  I guess we just differ in our philosophies on life; I believe that forums such as this one - and the Ubuntu philosophy in general - is to be a little more empathetic and supportive of the struggles of your peers.

Yes, I did spend a ton of time searching these forums and the web, and I didn't find the answers to getting my webcam working with the driver that was supposed to support it.  What I did learn is that I am not alone in my frustration.  But I persist... to a point.  No, the answers are not all there.  For example, I have no explanation for why my alternate AMD-64 boot of Feisty (and previously Edgy and Dapper) causes video tearing with my Radeon Express 200M integrated graphics chip... but only every 2rd or 3rd boot.  Or why I simply can NOT get my supposedly supported Ricoh firewire chip to work.  And yet I have had brilliant success getting ALSA setup for my USB audio and USB MIDI adapters, and also getting the fglrx driver working with my Radeon graphics chip in my i386 installation.  What I am griping about, by and large, is the fact that in many if not most cases the god danged chip vendors won't just provide documentation to the linux driver developers to give them basic help in these matters.  And sometimes the solutions are actually not well documented in web pages or forums.  No, really, sometimes they are not.  But yes, like you, I have paid my share of "dues".

It kind of makes me think, too, that Ubuntu isn't really the right distribution for you, either.  You seem like you are very bright.  Just not very empathetic or tolerant of those who are less skilled.  You might be better served by a more "bare-bones" distribution like Debian.  I'm sure there are more experts like yourself within that community and you wouldn't have to be troubled by the hordes of us Ubuntu users who are obviously less gifted.

---

### Post by gatman3 on 2007-08-24
> **pyjamashark said:**
> I thought I'd add my experiences with Logitech Webcams on Ubuntu Feisty Fawn:

Logitech Quickcam Fusion - couldn't get it to work.

Logitech Quickcam Express Plus - worked perfectly, just plug it in and hey presto!

Cool
joe

QC Fusion is apparently supported by the UVC driver.  I too had trouble (as have others) getting it to work with Feisty.  Which application did you try?  Seems like only V4L2 applications are supported by UVC.

I didn't see QuickCam Express Plus in the list of supported cameras on this web page:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

but it must be supported by the spca5xx or gspca driver which seem to work well in Feisty.

---

### Post by gatman3 on 2007-08-24
Sorry.  I was in a bad mood last night.  Didn't mean to rant yet again.  I have reread all of your comments and I think they can be taken much more constructively than I obviously have.  After a good night's sleep and a good cup of coffee, I sincerely apologize.  Let's bury it and move on.

---

### Post by buntunub on 2007-08-24
> **gatman3 said:**
> 

What I find offensive about your tone in your posts is that you come across with the arrogant position that the world of Linux devices IS well documented and well supported and that anyone who doesn't agree with you must be a weak-minded fool who hasn't done their proper homework.  I guess we just differ in our philosophies on life; I believe that forums such as this one - and the Ubuntu philosophy in general - is to be a little more empathetic and supportive of the struggles of your peers.


It kind of makes me think, too, that Ubuntu isn't really the right distribution for you, either.  You seem like you are very bright.  Just not very empathetic or tolerant of those who are less skilled.  You might be better served by a more "bare-bones" distribution like Debian.  I'm sure there are more experts like yourself within that community and you wouldn't have to be troubled by the hordes of us Ubuntu users who are obviously less gifted.

Sorry you were offended. You will generally find two types of Linux users -- Those who love cli and who just love to sit around and figure stuff out that does not work, or figuring out networking protocalls, etc, much like figuring out a really complex puzzle, and those who just want their stuff to work with no hassles. Fortunately (or not, depending on how you look at it), Linux is not Windows and so therefor, will never be a one click, no-brainer affair. Not everything is going to work in Linux -- just the way it is, and that is not the fault of linux, but the hardware vendors as you say, which in turn is the fault of consumers who do not generate the demand for it. And your right that many people have issues with usb webcams as I did as well, but got it working fairly easily with a little research and tinkering under the hood. My solutions wont work for everyone however, which is why I do not include any details in my posts generally unless im posting a wiki or guide which I have thoroughly tested first. 

We all were/are nubs gatman, and nobody has dibs on linux knowledge. I run several distro's including Gentoo (my first ever distro), Debian, Fedora, and Ubuntu/Xubuntu. Gentoo was a serious thorn in my side until I spent countless hours reading manuals/guides/wiki's, and trolling forums. Now, I simply could not be happier with its simplicity and unprecedented performance. When I went asking questions in forums I typically got "RTFM nub!", or something very much like that. I was offended by that at first, until I realized that they were right. I am very far from being an expert in Linux :lolflag:  I just know a thing or two, which I learned from doing research, reading manuals, trial and error, and wrecking my system a few times too. :)  Sorry I came across the wrong way. I guess us geek types just dont have much in the way of people skills.

---

### Post by dugh on 2007-08-25
Thanks for the helpful info gatman3.

Here's how I got the Logitech Quickcam for Notebooks Pro to sort of work, just for others' info.

Following instructions from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) and [https://answers.launchpad.net/ubuntu/+question/3743](https://answers.launchpad.net/ubuntu/+question/3743)
I got the latest svn version of UVC and installed it.

Instructions

Open the Terminal application and type the below commands.

```
##get required software
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential subversion

##make a folder for uvc files
cd
mkdir linux-uvc
cd linux-uvc

##fetch source code for UVC:
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

##now compile and install it:
cd trunk
make
sudo make install
```

Now plug in the webcam and run the command "dmesg" (no quotes) in the terminal and check for output similar to this at the bottom:

```

[ 1801.680000] usb 2-7: new high speed USB device using ehci_hcd and address 6
[ 1801.956000] usb 2-7: configuration #1 chosen from 1 choice
[ 1802.048000] Linux video capture interface: v2.00
[ 1802.052000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08cb)
[ 1802.100000] usbcore: registered new interface driver uvcvideo
[ 1802.100000] USB Video Class driver (v0.1.0)
[ 1802.128000] usbcore: registered new interface driver snd-usb-audio

```

Now you can test the webcam in various applications.

In Ekiga, I configured it to use video4linux2 and get audio input from the usb device (webcam) instead of a microphone.  I can see the video and can hear microphone input, so it is working.  But actually trying a call in Ekiga (to sip:500@ekiga.net for an echo test), I get "security check failed", which apparently has no solution at the moment:
[https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/120251](https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/120251)
After quitting and restarting Ekiga, I also notice that now the webcam image is very dark, and there is no way to adjust it.

Camorama does not work with video4linux2 devices like this one apparently.

Kopete does not work.  Doesn't show video.  Perhaps I need to try a newer version of Kopete or something.

I haven't tried luvcview (available for download at the bottom of this page:
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) ) but I assume it will work.

So the driver works, but no applications work.  I'm returning the webcam.

---

### Post by gatman3 on 2007-08-26
Thanks for the info, dugh.  Sounds like you had your own adventure with that camera, a little more successful than I did.

I think that there are some folks who have been able to get it to work better than you and I did, but it sounds like you were well on the right track.  Correct me if I'm wrong (anyone out there who knows more) but I think that the QC for Notebooks Pro is only supported by the UVC driver, which means that in theory it only works with applications that support Video4Linux2.  It does not appear that Kopete is one of those applications, but Ekiga, luvcview and ffmpeg appear to be the most popular ones that do support V4L2.  So... in the end, it all depends on what you want to use the camera for.

Some people like buntunub seem to be quite happy with the V4L2 supported applications.  It sounds like more advanced folks who use the cameras for pure video capture and security applications might even like the better quality UVC-supported cameras and the applications that support them.  But if you want to do webcam chat on a Yahoo, MSN or other network more popular in the Windows world, I think you need Kopete... and a camera that is supported by one of the V4L1 supported drivers such as the spca5xx/gspca driver.  In general, it appears that there is a broader range of supported applications for V4L1 supported cameras.

On the other hand, from the mxhaard driver website it seems like the cameras with the highest video quality (his highest rating appears to be 8 stars) are supported by the UVC driver.  Most of the spca5xx/gspca driver-supported cameras appear to top out at 4 stars (although I think there are a few 6 star models).  I have a couple of 4-star models (QC for Notebooks Deluxe and QC Communicate STX), and I am generally pleased with the quality for webcam chat, but I could see how others might think the quality is lacking for more advanced applications.

Thanks for sharing your experience.

---

### Post by buntunub on 2007-08-27
Fear not, im sure Kopete will not be long in producing v4l2 support, if there isnt already a backported patch available for it. IMO, Kopete rules the chat app world!

---

### Post by gatman3 on 2007-08-27
Yes, Kopete is a true gem, I couldn't agree more.

One thing I was wondering... with regard to this discussion on the UVC driver vs. the spca variants... and Kopete vs. Ekiga, or even other chat clients, is this:

How does the video quality compare for Kopete vs. Ekiga?  (desirably, an apples-to-apples comparison with the same webcam... if that's possible for someone).  If there are differences, is it related more to V4L1 vs. V4L2?  Since I wasn't able to get Ekiga working with my webcam, and I was wondering if anyone (buntunub?) can share their experience with it, or post any good links about it.

Similarly... How do the different chat networks supported by Kopete compare in terms of video quality?  I have only used Yahoo, since that's where my friends/colleagues are.  There are a moderate to high level of compression artifacts, in my opinion, using Yahoo vs. the raw video stream shown locally.  Any networks that do a better job?

My interest is in webcam chat for work purposes.  I have had pretty good success showing a small portion of a whiteboard over video chat using Kopete/Yahoo.  It's usable, but the quality could definitely be better.  Just wondering if it's worth migrating to a different network or client.

---

### Post by winterhighland on 2007-08-30
My first post!

I have got a Logitech Quickcam Fusion working in Fiesty, using ffmpeg to record short video clips and also extract still images from it. I can view it live using a app called videoview, but it will not work in Camorama for example.

Camera (when laptop on): [www.winterhighland.info/testcam/fusion-txt.jpeg](www.winterhighland.info/testcam/fusion-txt.jpeg)

The reason I am messing about with this is that I am looking to develop an automated webcam system for setting up mountain webcams in Scotland, mainly at the ski areas for our website ([www.winterhighland.info](www.winterhighland.info)).

A couple of the ski areas have tried out various network cameras for this, including axis cameras and stardot netcams, but these come in at a hefty price and have various problems.

I decided to have a look at a cheaper option, to use a usb webcam and old PIII computers, so we can get more cameras live for our budget, but also as we can source PIII computers for next to nothing (possibly even nothing in some cases)  we're not to bothered if they sometimes fail due to fairly harsh conditions in some of the mountain lift huts where we will put them.

The reason for choosing linux is the hope that they can be left alone for extended periods of time and will keep taking pictures.

At present the test camera is being run by a shell script which is running every couple of minutes as a cron job. All is well with the basic theory, but after a period of time between 1 and 2 hours, /dev/video0 vanishes, and ffmpeg can't find the camera and the whole thing stops. 

 Is there a way to 'reboot' the usb devices automatically? At present either unplugging and plugging in again or starting up a gui interface program such as videoview is required for the webcam to be found again. Would (bit extreme) issuing a shutdown -r now when ffmpeg fails to find the camera solve the problem? 

Thanks for your time for anyone who reads this essay of a first post!

---

### Post by alinuxfan on 2007-09-02
i am getting security check failed with ekiga now too.  
I searched google, and i haven't found a fix but there is another program in the repos that did the trick for me.
It is twinkle.  It is a kde app but it works for my purposes on this machine

---

### Post by keithrennie on 2007-09-08
Gatman3, I really appreciate your efforts, and your approach.  We dont need anybody's condescension.  But I do need somebody's advice on how to approach getting my webcam to work on Linux, because I havent yet found a solution - or rather I've found too many partial solutions that you "could try" scattered all over the place as you say, and I dont want to start experimenting until I see a clear strategic approach to this.  I'm trying to get my Logitech quickcam fusion working  on Feisty (I use Kubuntu desktop).  I really just got the model because it was available and I was in a hurry). Anybody managed to get a driver to work on this confguration? what is the best logical order to try different solutions? I'm fairly new to Linux, having just recently liberated myself from Windoze and reformatted my hard disk to avoid Vista. I'm getting devices to work one by one, but webcams seem an issue.  Should I just park the quickcam until somebody finds a decent solution, and try to find and dust off my old model webcam (which is probably also a Logitech but I imagine by now it has a driver somewhere that works)?  or do I just barge in on a trial and error basis and load and try different drivers to see what works on the quickcam, and remove them when they dont?  I have a demanding job, so I dont have all the time in the world. (its ID is 046d:08ca).
Meanwhile I'm exploring Google.com/linux which seems promising. A search on the device ID gets quite a few hits. And since I read French, I'm also looking at the french sites seem to have done quite a bit of work on this issue.  
And a final thought.  Hardware manufacturers respond to the market.  When enough of us tell Logitech that we are switching away from their product because they dont pay attention to our needs, they will start to notice. There are not enough of us yet to make any impact, but the trend is encouraging. Same story with the internet wireless gizmos that plug into the USB (T-mobile and the like).

---

### Post by gatman3 on 2007-09-09
keithrennie,

Yes, it would be nice if a true expert out there could provide a more thorough general strategy for bringing up webcams in linux and/or ubuntu.  I sympathize with you, but I'm afraid you probably are going to have to resort to some experimentation.

Your QC Fusion webcam is listed with the UVC driver, which appears to be causing the most problems for ubuntu/feisty users.  I was unable to get a similar logitech webcam to work using the UVC driver even after moderate experimentation.  Some others have been more fortunate (or are more capable, perhaps), but there is some definite frustration out there with UVC-based webcams under ubuntu.  The carrot for UVC seems to be that the webcams are mostly reported on the mxhaard website to have the highest quality of the bunch (your yet-to-function 0x08ca camera is listed at 8 stars; my QC Communicate STX and QC for Notebooks Deluxe are supported by gspca but only received 4 stars in the mxhaard rankings).

Do be aware that UVC does not appear to support VideoForLinux1, so several of the most popular applications such as Kopete will not work with your camera (although support will probably be coming soon, if you're willing to wait).

Hopefully somebody more experienced with UVC will post a more comprehensive strategy for you to try bringing up your camera.  But in the meantime you're stuck with my advice.  Here is what I would try (unfortunately... just experimentation):

1. Plug in the camera
2. Check to see if the /dev/video0 device is created automatically by the driver (ls /dev/video*).
3. If it is... you're probably in business and you can try to capture video using ffmpeg.  Try:

ffmpeg -an -y -vd /dev/video0 -sameq -t 5 test.avi

4. If steps 2/3 are not successful, check to see if the UVC driver is loaded. Try something like this:

lsmod | grep uvc

5. If the UVC driver is loaded but the camera still isn't working properly, then you probably need more of an expert to help.  If it isn't loaded, try:

sudo modprobe uvcvideo

and then repeat steps 2 and 3.  If that fixes it, you may just need to add uvcvideo to your /etc/modules file.  If not, then...

6. Download the linuxuvc driver, compile it and load it.  I think you can get the source code from [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) (this step is beyond the scope of how much I want to type here, not to mention the fact that I wasn't successful doing this anyway, so I won't presume to try to tell you how to do it...)

7. If all else fails...  (don't smack me...)  Give up, return the camera and buy one that works with the gspca driver (reference the mxhaard website); gspca supported cameras seem to work better "out of the box" under feisty.

Good luck, and please share your results.  And please don't give up yet.  Linux has its frustrations, but the rewards are substantial (and, dare I also mention that Vista has its own driver support issues as well, and I wouldn't be surprised if some other peripheral you own won't work with Vista anyway).

---

### Post by gatman3 on 2007-09-09
Some more info from the web on your particular webcam in conjunction with the UVC driver (perhaps you already saw this, but anyway...)

If you read through the banter at [http://lists.berlios.de/pipermail/linux-uvc-devel/2007-May/001759.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2007-May/001759.html) it appears that there may be some problems with Ekiga in conjunction with ATI drivers.  Perhaps this was my problem as well, since I tried it on a machine with the ATI Radeon 200M chip.  In any case, it is also suggested that you try the luvcview and kdetv applications and see if they work with your camera (assuming the driver is working and creates the /dev/video0 device properly).

I have no idea if this is relevant or not, but you might also experiment with installing the libpt-plugins-v4l2 package using synaptic or adept.

Also, please refer to the solution posted earlier in this thread by dugh for getting the UVC driver working.  I forgot about that one in my last post.

---

### Post by gatman3 on 2007-09-09
winterhighland - To "reboot" the webcam, perhaps you could try using rmmod and modprobe to remove and reload the driver associated with your webcam?  Cool website, by the way, I can't wait to ski in Scotland someday!

---

### Post by keithrennie on 2007-09-09
Problems getting Logitech Quickcam to work on Feisty
This was written before helpful suggestions from gatman and others.  I will try their suggestions and certainly post the results on this thread.  But since my last post I have been busy (it was a weekend). 


I'm very new to Linux and what little I know is self taught.  I need help getting my Logitech Quickcam Fusion (2006) to work.  I ve got several other devices to work (like my Palm), but Quickcam is a stubborn problem and beyond my knowledge and experience.  Of course Logitech is of no help whatsoever.  I read various helpful threads and postings in English and French, visited BerliOS (but couldnt access their OpenFacts page); compiled a uvc driver, and (I think) added the module in the kernel successfully, but the device is still not being recognized.  What do I try next?  Did I mess up the installation, or miss a key step?

Here's my whole Fusion-Feisty story to date, with lots more info.

Actions. I installed Linux essentials and subversion before I started, and later installed aMSN, Ekiga, Kopete, xawtv and camorama using Kubuntu Feisty's Adept Manager.  Of course camorama doesnt work.  But I totally failed to compile luvcview.  I just got lots of error messages on the make command so I left it for now although I think there s a workaround. .  The kernel is 2.6.20-16-generic. I connected the camera to my USB.  It was fully tested and works fine on Windoze.

Using the command line  lsusb the device identifies itself  046d:08ca Logitech Inc.  This is a 2006 Quickcam Fusion.  (Sunplus SPCA525A controller chip, they say.)

This device is supported by the uvc driver according to the following two tests:
sudo lsusb -d 046d:08ca -v | grep &#8220;14 Video&#8221; returns 
bFunctionClass 	 14 Video 
bInterfaceClass 	14 Video (repeated 12 times)
I cant remember where I found this test but I believe the response is considered positive.  The device is also listed among the uvc-supported models on the BerliOS site [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/).  However, the driver is still in development and not free of problems.

I downloaded the latest version of the uvc driver files from BerliOS using the following command (its one line):

svn checkout svn://svn berlios.de/linux-uvc/ linux-uvc/trunk

This command put the package files including MakeFile in a folder /trunk which it created in my home directory.

I installed the linux headers:

sudo apt-get install linux-headers-2.6.20-16-generic

I then made and compiled the driver and installed it:
make
sudo make install

When nothing seemed to work (e.g. camorama did not recognize the device) I tried 

sudo mknod /dev/video0 c 81 0 (This was redundant, it was already there)
sudo mknod /dev/video1 c 81 1
sudo chmod n+rw /dev/video0
sudo ln -s  /dev/video0 /dev/video

and then finally 
sudo modprobe uvcvideo

Behavior:  When I boot with the camera connected to the usb  it does not seem to be recognized.  I cant switch it on.  Camorama refuses to recognize the webcam but it looks as though this is a limitation of the application. Xawtv causes it to flash on and off briefly so at least there's a flicker of life there.  I totally failed to install luvcview.  Skype is turned off for now. 

The hardware listing for USB devices has at EHCI controller 5 the following lines:
Serial #: 9B9DE3B3	
Class 239 	 	subclass 0 		protocol 0 	USB version 2.00
Vendor ID 0x46d 	Product ID  0x46d  	Revision 0.05
Speed 480 Mbits  	Channels 0  		Max. Packet Size 0

When I run dmesg piped to file I get the following relevant lines (no other lines refer to this device or the driver) 

[   37.836000] cs: IO port probe 0xa00-0xaff: clean.
[   38.008000] usbcore: registered new interface driver snd-usb-audio
[   38.008000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ca)
[   38.024000] usbcore: registered new interface driver uvcvideo
[   38.024000] USB Video Class driver (v0.1.0)
[   38.568000] fuse init (API version 7.8)
[   39.096000] lp:  etc etc 

I dont know where to go from here.  Help, please!!!!  Actually, I;ve been given a few tips in the responses just in, so if you guys will look at my new info and I'll try out your various suggestions then we can see where we are at the end of the week.
  
And no, I wont give up, although I might just give the webcam to my daughter and get another one.  Liked this cam a lot tho, the quality and response using Skype on Windoze made me the envy of my friends. And totally sold on Linux.  I remember twenty years ago we were begging for this solution to come.

Keith

---

### Post by keithrennie on 2007-09-09
Winterhighland, 

you're just about the first person I've seen who actually said they got Fusion to work on Feisty.  (there's a Swiss fellow on Swisslinux who got it going on Gutsy eventually I think, but then they have Roger Federer to inspire them).  And you didnt tell us how you performed this marvellous feat.  Did you just plug it in cold and run ffmpeg or did you have to install something, or did you run the installation disk on a Windows emulator? (I failed to do it on wine because it wanted Windows explorer on the dreaded SP2, which I had happily murdered, and then windows explorer had other dependencies . . .

So please come clean and tell us in your second-ever post just what you did to actually get the camera recognized and functional?  Fame could be waiting just around the corner . . .  

Keith

---

### Post by gatman3 on 2007-09-10
Keith,

I'm stumped.  I think I had problems getting luvcview to compile as well, but I can't remember the details.  A few more thoughts:

1. V4L2 support seems to be pretty sketchy in the linux video application universe, so maybe you are fighting V4L2 problems, not UVC problems.  You did not list ffmpeg or ekiga as applications you tried, both of which are known to support V4L2.  I'm not sure if xawtv does, pretty sure camorama does not.  I know that I had no luck wth those apps, or with Ekiga (although that may have been due to ATI fglrx compatibility problems for me, who knows for sure) but I didn't actually try ffmpeg before returning the camera (I'm still learning too).

2. Instead of compiling luvcview, since the compile is broken with feisty dependencies, you could try to find a binary package and install it with dpkg.  Try [http://ftp.cica.es/debian/pool/main/l/luvcview/](http://ftp.cica.es/debian/pool/main/l/luvcview/) although I'm not sure this is the latest or also if it's compatible with the feisty library versions.  You may have to google some more to find a good binary

3. Less of a quick fix, but... send your compile log for luvcview... and your other relevant logs...  to the UVC/luvcview developers or the ubuntu package maintainer (you'll have to do some leg work to figure out who that is, of course).  They should be interested in fixing it, and they may have insight into why your camera (and everyone else's for that matter) isn't working in feisty.

Furthermore, maybe with the help of someone more experienced with the ubuntu project we should get a formal bug filed relating to UVC camera support and see if it can be fixed in gutsy.  Maybe someone reading this would know how to do that.

Keep us posted, the community is pulling for you (well, I am at least...)

---

### Post by josefcarel on 2007-09-13
> **gatman3 said:**
> I just wanted to share my recent experiences with selecting webcams to use with Feisty, since I could only find sketchy information on up-to-date Feisty webcam support when I searched on my own.  It appears from my searches that Edgy had some serious problems with webcams, and that Feisty works better, but there still isn't much up-to-date information (that I could find, anyway) on Feisty support for specific webcams.  Hopefully this will be helpful to others who may be trying to get webcams going (this info would have saved me a lot of time had it been available).

Note that this is purely based on trial-and-error experience, and is limited to the specific Logitech webcams that I experimented with; I am not an expert in the drivers associated with the various webcams, and mostly tried to get something to just work "out-of-the-box".  I'm also not sure that my machines are representative of "typical", whatever that might be.

The first webcam I purchased was a "Logitech QuickCam or Notebooks Deluxe" not to be confused with the "Logitech QuickCam Deluxe for Notebooks" which appears to be a different and perhaps older product (a sarcastic thank-you to Logitech, although not unlike most computer peripheral vendors, for using confusing marketing names and little or no real technical info about the differentiation of their products). The QuickCam for Notebooks Deluxe advertised 640x480 resolution with 1.3 megapixel stills.   In any case, I plugged this webcam into my MSI 1013 notebook (yes, it's an unusual but oddly sexy little diy notebook) running Ubuntu Feisty, fired up Camorama, and found that it "just worked"... although, the colors were messed up in Camorama (I think the blues and yellow or greens were swapped, so my blue shirt looked yellow, and my skin looked blue).  In Kopete, it worked perfectly and with correct colors, and the picture quality was quite good in my opinion.  After searching for more info on the web, it appears that others have experienced this blue/yellow swap in Camorama, and can be fixed by adding a "color adjustment" effect in Camorama.  Picture quality with Kopete is good enough to even use to share whiteboard drawings with remote coworkers.

Emboldened by my first easy success, I decided to try to trade up to the "Logitech QuickCam for Notebooks Pro" which advertises higher resolution (a "True 1.3 Megapixel Sensor") and was only $20 more.  So, I took advantage of the no questions asked return policy where I bought my first camera and traded up.  This turned out to be a big mistake.  This camera did not work at all out-of-the-box and, in fact, I never got it working at all in any capacity.  After researching on the web, I learned that there -may- be some support for this camera... or perhaps older versions of it... using Video4Linux2, and I compiled and installed the latest linux-uvc driver which was my only hope to get it to work.  Nothing.  I also tried the, apparently now abandoned, PWC (Philips WebCam) driver which was also hinted at as a possibility, but nothing.  Even if I could have gotten it to work, I don't think that Kopete supports Video4Linux2 (I could be wrong about this) and it looked like I may have had to switch to Ekiga.

So... I returned that one and went back to the first QuickCam for Notebooks Deluxe.

Now on to my home desktop, which is an older Athlon XP 2600 also running Feisty.  After reading some favorable testimonials about the Logitech QuickCam Chat (half the price of the QuickCam for Notebooks Deluxe) I took the plunge.  This one worked out-of-the-box with Kopete, sort of.  Two problems: (1) image quality is significantly inferior to the QuickCam for Notebooks Deluxe, which advertises "RightLight" technology, and (2) the image would always start in Kopete in a very washed out state, but after pulling up the "Settings->Configure->Devices" menu it would correct itself.  I decided I could probably live with the lesser image quality, but I figured my wife wasn't going to be real happy using it if I told her that she had to jump through this goofy configuration hoop every time I asked her to bring up the webcam (we use Yahoo IM with Kopete, which works GREAT, by the way).  So I returned it and traded up to a "Logitech QuickCam Communicate STX".

My rationale with choosing the QuickCam Communicate STX was that, like the QuickCam for Notebooks Deluxe, it advertised the exact same resolution and the exact same "RightLight Technology" and "RightSound Technology", so I guessed (hoped) that it used the same chip as the one that I previously had such good success with.  Sure enough, I got it home, plugged it in and it "just worked", and looked and behaved identically to the excellent QuickCam for Notebooks Deluxe that I use on my laptop.  Plus, it mounts much better to my flat panel monitor than the QuickCam Chat, and it has a shutter to cover the lense which, although technically unnecessary, was something that I figured would raise my wife's comfort level with having a camera sitting on top of the home computer monitor pointed at her whenever she was using it.

I wish that Logitech would publish better technical specs, perhaps even list the specific chips used in their products.  Why do these computer peripheral vendors treat the whole world like a bunch of idiots that can't understand anything more than phrases like "RightLight technology" or arbitrary descriptions like "sharper video even in dim lighting".  Sharper than what?  Which other inferior product of yours is it sharper than, do tell?!  I had to deduce that the QC for Notebooks Deluxe and the QC Communicate STX use the same chip - and therefore have the same level of compatibility - because of certain shared marketing terms such as "RightLight" and "RightSound".  You wouldn't guess from the names that they share much in common.

To summarize (hopefully this will save others the hassles that I went through):

1. Logitech QuickCam Chat
Price = $
Worked out of the box, but had relatively poor image quality (compared with options #2 and #3 below) and required manually hitting the Kopete configuration every time it was initialized.  Also did not mount very well on my flat panel monitor, kept slipping off.

2. Logitech QuickCam Communicate STX
Price = $$
Worked out of the box very well, good image quality (for a webcam).  Worked perfectly with Kopete.  Works with Camorama, but need the "color correction" effect.  Mounted very well on my flat panel monitor (Samsung 931B).  Nice black color and black cord, blends well on my black monitor and in my dimly lit home office.

3. Logitech QuickCam for Notebooks Deluxe
Price = $$
Identical to #2 Logitech QuickCam Communicate STX (must use the same chip, just constructed for mounting on a notebook instead of on a desktop monitor).

4. Logitech QuickCam for Notebooks Pro
Price = $$$
Could not get it to work at all.  Yes I did try the uvc and the pwc drivers.  No joy.  Maybe some Linux guru could get it to work, but not me.  My guess is that it has a newer chip (it is supposedly a true 1.3 megapixel CCD, compared with the 0.3 megapixel CCDs in the options #2 and #3 above that worked well for me) and the Linux drivers probably haven't caught up to it yet (aside from the fact that uvc seems to have very limited application support, and pwc development seems to have been abandoned).

Both Logitech webcams that I settled on (QC for Laptops Deluxe and QC Communicate STX) appear to use the gspca driver, which was loaded automatically for me by my vanilla Feisty i386 installation (my gratitude to the fabulous Ubuntu developers).

I'm also not sure if this means that all Logitech webcams with true 1.3 megapixel CCDs (QuickCam Fusion, QuickCam Orbit, etc.) will not work well with Feisty (web searching suggested that there may be some success with other drivers like the linux_uvc driver... but not for me), but based on my experiences I'd be wary.  If I had to guess (and I can make at least an educated guess, since I am in the chip business myself), Logitech probably has one or more older families of products based on earlier CCDs (such as the QuickCam chat) that appear to have Linux support through the gspca driver but have relatively poor image quality (just because of older technology).  Then there is the 0.3 megapixel CCDs with "RightLight Technology" that also work with Linux and have very good image quality, and then there are the newest products with 1.3 megapixel CCDs that may not be well supported in Linux.

Your Mileage May Vary.

**Hello, Im very confused with that** I was trying the Logitech QuickCam for Notebooks Deluxe in my Dell laptop with Ubuntu Feisty and at the beginning the image is great in Kopete, and blue in Camorama, but after a few minutes the image freezes totally and nothing to do. I tried Easycam2 but it is not defined there.  
An other question, what do you know about Logitech quickcam 3000 and 4000 Pro? 
Thanks in advance
Josef :confused:

---

### Post by keithrennie on 2007-09-14
Thanks gatman.  We move ahead a step at a time. No luck yet with luvcview.  Dependency failure.  Now I need to find a repository for libc6 2..6.x.  Help! and any tips, tricks or warnings from anyone? (like, do you first have to uninstall 2.5? can I uninstall it properly if it causes too many problems, without having to reinstall the whole kit and caboodle?).    

BACKGROUND -  I tried installing the compiled luvcview from the spanish site you recommended, and dpkg complained of an unsatisfied dependency, libc6>=2.6-1.  This is an unsupported version of lib6 (my kubuntu installation including all avalable updates is 2.5 -0.)  I searched for 2.6 experiences and repositories.  I'm prepared to give 2.6 a try although there may be some risk (that may well be why the berliOS luvcview package failed to compile in the first place) but I cant find a recent version of libc6 anywhere.  Not much helpful correspondence on it has come to light so far (a bit on amd64, a couple of references to gutsy, little on feisty.  I think there is a repository search facility but I cant find that either, forgot to make a note of it.

Meanwhile I have found a correspondence between two berliOS guys on fusion, feisty and the uvc driver, and I will try contacting them personally as well as the swiss who was using gutsy since my french is still passable.  BTW does gutsy come with the 2.6 version of lbc6?

Yes I like the idea of filing a bug report but we dont have the necessary prerequisites yet, like replicabilty and tests under different conditions.  We can work towards that. 

On a more philosophical/hstorical note.  I was amused by the exchange between you and buntunub on the difference between windows and ubuntu users.  Hmm.  I've been with various kinds of computers on and off casually (not a professional, just a tinkerer, but my first wife was a real pro) for close on 40 years now.  I used to have to do a bit of programming in DOS about twenty years ago, when windoze didnt exist and we thought Ashton Tate's Framework or the Borland suites were going to take over (and perhaps the world would be a better place if they had, especially Borland which had a vision) and we dreamed that we might even get a PC-based unix version which we eventually did.  When windoze came along, it was incredibly buggy - all the way up to 2000ME - and exposed to viruses and hackers.  Still is.  So installing devices on IBM DOS or windoze then, getting on for twenty years ago, was a bit like installing devices on ubuntu now only much slower - trial and error, get somebody's tweaked driver of a 5.5 inch floppy in the mail etc.  but with the added problem that windoze kept crashing esp 2.1, 3.1 - like two or three times a week.  It was really inferior, and we couldnt understand why the world was buyng into it.  (Clever marketing strategy, plus astute use of force, perhaps?).  No internet, modems were abysmally slow, living outside europe and US, you had to have lttle self help clubs and networks, and your bag of tricks to rewrite your boot sector or edit drivers or remove viruses by hand, and most of it experiment and self-education, quite time consuming.  That context was one of the reasons btw why south africans indians iranians and russians got so innovative and good at fixing computa things and reverse engineering, along with needing to coax the very best performance possible from very limited hardware capability.  So what has changed since then is not, in my view, that windoze has got better - it's got a lot more complex and a bit more crash proof, but the big change in windoze IMO has been the relatvely recent arrival of accessible internet-based support plus the rise of the big corporate-based professional support systems,  whcih means that ordinary users can - are forced to - sit back and let the boffins fix it for them because they are not allowed by their company to even think of touching the installation.  I work in retirement for an organization with several thousand employees, a creaky leaky windoze-based intranet system and a whole company dedicated to keeping the thing working and users happy - sorta.  Ubuntu is fine, I think it is on the cusp of a big expansiion, thanks in part to Mark Shuttleworth, and it feels now quite like the old do it yourself days, but like gatman I wish there was a way to keep the systematic information more organized, structured and up to date.   Life is too short to spend so much of it fixing things, when there are other important things you want to do with it when it works.  Forgive the reminiscing rant, but it's fun to look back and see how things have developed.:)

---

### Post by keithrennie on 2007-09-15
GOT IT!!

solution

Igot the fusion webcam to work on kubuntu feisty using the Ekiga app with the v4l2 video plugin.  I also have the uvc driver working, but not luvcview which I removed using dpkg as it did not complete installation.   I will try  luvcview later.

I did a lot of research on fusion, drivers, and webcam apps, on ubuntu, linux, berliOS, google linux, linux-fr, google-fr/linux, and swisslinux - about 25 useful sites.  for the european ones, you have to use french, the swiss site also uses german and italian. They can cope with English but prefer not to.  You have to pay something to join the swiss site but you can read their posts.  The french wiki is good, better than ours here I thought, and well maintained, like mxhaard they have devices, ids and drivers updated almost to the day.  Their moderators also answer posts pretty promptly, and they are not verbose.  

But the final solution came from another ubuntu thread [http://ubuntuforums.org/showthread.php?t=194793](http://ubuntuforums.org/showthread.php?t=194793). This thread has been running sporadically for over a year, but often when somebody gets their webcam up they run away, so information accumulates slowly.   

The first response on the ubuntu thread, from macman, gave very helpful basic instructions  but the final solution that worked for me was mfulgo posting on June 14, 2007 re v4l2 for Ekiga which I set up with a yahoo account just for testing. 

First, I got a lot of reassurance from my console that the the camera was actually recognized by the system.  Here were two positive diagnostics: 

$ caminfo (this is usr/bin/caminfo) generates: 

CVideoDeviceInput: Warning: no channel info available.
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "USB Video Class device"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 0x0
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

This is fine. 

dmesg also identifies the webcam and in this case the last two lines showed that the system recognized that I had switched the webcam on and off a couple of times: 

$dmesg 
. . . .
[ 1635.196000] uvcvideo: Button event (1).
[ 1635.548000] uvcvideo: Button event (0).
[ 1636.092000] uvcvideo: Button event (1).
[ 1636.508000] uvcvideo: Button event (0).

I loaded the ekiga library libpt-plugins-v4l2 using my package manager
I switched on Ekiga to video 
Then Edit | preferences | Devices | Video Devices | Video plugin  and selected v4l2.
Nothing happened until I rebooted, and then it worked immediately.  Not sure how well it works &#8211; I think switching the cam icon off and on again loses the connection, but now I have something to test.

Thanks to all, and especially gatman3 for encouragement and tips.

---

### Post by keithrennie on 2007-09-16
:lolflag:I have now managed to get luvcview to install/compile on feisty:
Here's how:

I cleaned up the earlier failed installation.

I tried and failed to install the compiled debian version of luvcview from this site: 
 [http://ftp.cica.es/debian/pool/main/l/luvcview/](http://ftp.cica.es/debian/pool/main/l/luvcview/) 

As gatman3 suspected, the reason is that this version is not compatible with the feisty library versions.  It looks for a recent version of libc6 which I couldn't find and which might have had issues anyway.

So I went back to the french webcam site for the installation package:
[http://mxhaard.free.fr/spca50x/Investigation/uvc/](http://mxhaard.free.fr/spca50x/Investigation/uvc/) and downloaded the 20070512 i386 Gzip luvcview package.

I discovered from the other ubuntu thread (see previous post) that the reason that this package did not compile before is that it had failed to find the development debian library.  So I used my package manager to install two more libraries
libsdl1.2-dev
libsdl1.2debian-all
With these available: 
$make
$sudo make install
This installed the Gzip luvcview i386 package without complaint 

To test: 
$type luvcview
luvcview is /usr/local/bin/luvcview
$luvcview
and the app window loads successfully.

Thanks again all for tips and encouragement.

---

### Post by gatman3 on 2007-09-20
Outstanding work, Keith.  Thanks also for posting your solution!  Kind of makes me wish I had stuck with UVC a little longer to get an 8-star webcam up and running.

I also enjoyed your reminiscences.  My early days in computers were playing adventure and spacewar on the univac mainframes were my dad worked, and hacking my trash-80 in various ways.  It's been a fun ride.  I too loved the old Borland products.  In hindsight, I think I actually enjoyed the old DOS days (remember DOS TSRs and the high memory drivers, and all that good stuff?) better than the days of Microsoft domination.  I can remember reading an article about Bill gates in the old US-80 magazine back around 1982 or 1983, and I remember thinking about what a nice little company he had.  Now I feel like MS has everyone injected into the Matrix, and Linux is the red pill... which despite an undetermined outcome... but has the potential to set us free.

Thanks again for your correspondence, and enjoy your webcam!

---

### Post by keithrennie on 2007-09-21
Here is a list of the sites I found most useful.  I did not include French and Swiss sites and wikis but there are several good ones.

1.  Ubuntu websites and threads

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
Ubuntu community documentation on installing webcam drivers, software and troubleshooting.  Written for Edgy, needs to be updated.

[https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy](https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy)
Ubuntu community documentation on installing Logitech Quickcam Pro 5000 on Edgy. 

[http://ubuntuforums.org/showthread.php?t=53755&highlight=quickcam+driver](http://ubuntuforums.org/showthread.php?t=53755&highlight=quickcam+driver) 
Ubuntu tutorial on how to install qc-usb driver.

[https://help.ubuntu.com/community/Ov51x](https://help.ubuntu.com/community/Ov51x)
Ubuntu community documentation on Ov51x driver

Some helpful forum threads on getting webcams to work, some have more links
[http://ubuntuforums.org/showthread.php?t=194793](http://ubuntuforums.org/showthread.php?t=194793)
31 postings, June 2006 &#8211; September 2007
[http://ubuntuforums.org/showthread.php?t=321862](http://ubuntuforums.org/showthread.php?t=321862)
15 postings, December 2006 &#8211; June 2006
[http://ubuntuforums.org/showthread.php?t=194793](http://ubuntuforums.org/showthread.php?t=194793)
37 postings, August &#8211; September 2007
[http://ubuntuforums.org/showthread.php?t=551231](http://ubuntuforums.org/showthread.php?t=551231)
5 posts, September 2007.  Smplayer media repository

2.  Some other sites, drivers and repositories

[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)
The Linux qc-usb project originally developed a driver for the Logitech Quickcam Express, but now has expanded to other models.  
&#8220;The current version of the qc-usb driver is 0.6.5. This release fixes a compilation problem on kernel version 2.6.18 (and probably on 2.6.17, too)
The site has a list of cameras known to work with this driver, another list of cameras know not to work. However, more complete listings of webcams and drivers are available.

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
USB Video Class (UVC) drivers, focusing on webcams - V4l2 driver

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
Probably the authoritative site for cameras, ID codes, drivers, regularly updated
[http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/)
Philips USB webcam driver for Linux

---

### Post by swudee on 2007-10-01
The other problem with the webcams is that they change them during production.
I got a Quickcam Communicate  STX because people said it worked with Feisty.
Well I found it sort of worked with Ekiga, and didn't work with aMSN.
But then the device ID on the one I have is differant. 
Bus 001 Device 002: ID 046d:08d7 Logitech, Inc.
How do you tell that when it is packaged up in the shop?
Anyway the camera is working on Gutsy using Kopete.
The microphone does not seem to be detected, Not listed,no adjustments etc
But that is for tomorrow night

David

---

