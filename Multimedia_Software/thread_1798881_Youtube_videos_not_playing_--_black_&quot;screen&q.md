---
title: "Youtube videos not playing -- black &quot;screen&quot; but flash works elsewhere"
date: 2011-07-06
forum: Multimedia Software
---

### Post by harfooz on 2011-07-06
The title pretty much explains it all. I'm running 10.10 and as of July 6, 2011, youtube videos will not play on Firefox, showing only a black screen. Flash is playing elsewhere (pandora, etc.) without incident. 

Several others on IRC are indicating the same behavior. Any ideas to try?

Thanks,
'fooz

---

### Post by chrisod on 2011-07-06
I came to report this same problem. Everything works fine on my desktop but my son's PC can't get any YouTube video to load at YouTube.com. Bizarrely, some YouTubes videos embedded at my blog work fine for him. Viddler, Pandora, and other flash sites all work normally. We both are 10.04 / Firefox 5 / latest Flash. It was all working fine this morning.

I checked both Epiphany and Chrome on his box and get the same problem in both. I dumped his cache too.

---

### Post by HeadHunter00 on 2011-07-06
well, that happens to me too. however, if i refresh the page 3 times in a row, the problem goes away. i am using ubuntu 10.10 with firefox 4. if none works for you, you can use html5 for youtube: [http://www.youtube.com/html5](http://www.youtube.com/html5)
but make sure you got atleast ff4 or higher.

---

### Post by sween1911 on 2011-07-06
I've got the same exact problem and I'm still on 8.04.4. Refreshing multiple times does nothing.

---

### Post by chrisod on 2011-07-06
My son reports that YouTube is working for him again. Must just be a YouTube glitch.

---

### Post by sween1911 on 2011-07-06
After some googling "youtube won't work", I found that putting an S after http fixed the problem!

So [https://youtube.com](https://youtube.com) works fine now! I agree with chrisod, must be some kind of glitch with them.

---

### Post by epadget1 on 2011-07-06
Same problem in Mint Katya, although only in Chromium.  Firefox works fine.

@sween1911, it's baffling, but that https trick worked for me too.  I have no idea why, but telling the browser that it's a secure connection seems to fix it.

(Edit: A friend told me that it's possible that https youtube is actually somewhat different from regular youtube.  That means that this is really more of a workaround than a solution, but also that it's probably youtube's problem to fix.)

A friend of mine also had a similar problem, and discovered that he had two identical copies of the Flash Player plugin installed and disabling one fixed the problem for him.  That was not the case for me, but it would be worth checking if that's happening for you.

---

### Post by lovinglinux on 2011-07-07
Is another YouTube glitch. Deleting cookies and blocking YouTube from creating new cookies in the preferences might solve the problem.

---

### Post by Alfagulf on 2011-07-07
I have the same problem with both Chrome and FF.
Using HTTPS does help, however, when I switch to full screen mode, the video disappears (Black screen) but the audio continues!!

Can you confirm if you all have the same behavior?

Thanks

---

### Post by lovinglinux on 2011-07-07
> **Alfagulf said:**
> I have the same problem with both Chrome and FF.
Using HTTPS does help, however, when I switch to full screen mode, the video disappears (Black screen) but the audio continues!!

Can you confirm if you all have the same behavior?

Thanks

Now that you asked, I went to YouTube to test and I also have the same problem. Video disappears in fullscreen. Blocking the cookies doesn't seem to help. I will try to figure out a solution.

---

### Post by lovinglinux on 2011-07-07
> **Alfagulf said:**
> I have the same problem with both Chrome and FF.
Using HTTPS does help, however, when I switch to full screen mode, the video disappears (Black screen) but the audio continues!!

Can you confirm if you all have the same behavior?

Thanks

> **lovinglinux said:**
> Now that you asked, I went to YouTube to test and I also have the same problem. Video disappears in fullscreen. Blocking the cookies doesn't seem to help. I will try to figure out a solution.

See [YouTube Problems Mega Thread]("http://ubuntuforums.org/showthread.php?t=1799217")

---

### Post by Alfagulf on 2011-07-07
Confirming that disabling hardware acceleration enables full screen viewing.

Now back to the same original question: Why doesn't youtube works with HTTP as usual?

---

### Post by Mr Wobbly on 2011-07-07
Same phenomena found here. Youtube worked fine yesterday, not today. All other flash sites working fine.

Https connection however makes it work. how annoying... must be a Youtube software change...

---

### Post by nexx on 2011-07-07
> **lovinglinux said:**
> Is another YouTube glitch. Deleting cookies and blocking YouTube from creating new cookies in the preferences might solve the problem.

On natty flash stopped working on chrome only (still working on firefox). Deleting the cookies did the trick, now flash work in chrome.:popcorn:

---

### Post by Alfagulf on 2011-07-07
Could the problem be related to Nvidia driver for GeForce FX5600 ?
I am using this old graphic card on Ubuntu 11.04 which is also having compatibility problem with Unity!!
Are you by any chance using the same or similar graphic card?

---

### Post by Mr Wobbly on 2011-07-07
no, I don't think it has anything to do with nvidia drivers, i'm on intel and i'm suffering :

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

EDIT
Actually I have now found the same issue now at another site - please see if you get the same black screen at this link

[http://www.telegraph.co.uk/news/newstopics/howaboutthat/ufo/8619831/Fiery-UFO-filmed-over-Mexico.html](http://www.telegraph.co.uk/news/newstopics/howaboutthat/ufo/8619831/Fiery-UFO-filmed-over-Mexico.html)

---

### Post by Alfagulf on 2011-07-07
I tried it and I was able to see the video!

---

### Post by chrisod on 2011-07-07
YouTube just rolled out a new user interface - I suspect that is the source of all our issues. It is working with https for me.

---

### Post by Chris58 on 2011-07-07
This has happened to me today. Youtube not playing, only a black screen, however when I use https:// it works ok!
Is this a known bug with Ubuntu? (I'm a very new Ubuntu user of only 2 days)

Chris

---

### Post by Chris58 on 2011-07-07
> **chrisod said:**
> YouTube just rolled out a new user interface - I suspect that is the source of all our issues. It is working with https for me.

Sorry, posted before I read this.

Chris

---

### Post by chrisod on 2011-07-07
YouTube just started working normally for me, and I've heard from a couple of other Linux users that it's working for them too. Looks like YOuTube might be working it out.

---

### Post by beew on 2011-07-07
If you use the FlashVideoReplacer then you don't even need flash for Youtube (and a few other sites).

---

### Post by Mr Wobbly on 2011-07-07
yup http now working... panic over!

---

### Post by sween1911 on 2011-07-07
Working fine with regular http now!

---

### Post by Alfagulf on 2011-07-08
Today morning after I cold booted my machine, I noticed that youtube is working as usual with http!!

I did not remember doing any update, however I did uninstall an unneeded tscleint(Remote desktop client), but I don't think this is related!!

---

### Post by lovinglinux on 2011-07-08
There are still users experiencing problems and asking for help. Here it only works with hardware acceleration disabled.

---

### Post by Alfagulf on 2011-08-26
Now I am using Natty x64, I recently noticed that some times youtube will not play, I can only hear the sound!!
However, if I press F5 to refresh the screen, I may or may not recover!
Even if the refresh fix the problem, if I press F5 again, the video may or may not start again!!!

I have Flash 10,3,183,5 installed.

Someone had reported similar problem at the beginning of this thread, However I could find a solution yet!!

Are you having such problem?

---

### Post by lovinglinux on 2011-08-26
> **Alfagulf said:**
> Now I am using Natty x64, I recently noticed that some times youtube will not play, I can only hear the sound!!
However, if I press F5 to refresh the screen, I may or may not recover!
Even if the refresh fix the problem, if I press F5 again, the video may or may not start again!!!

I have Flash 10,3,183,5 installed.

Someone had reported similar problem at the beginning of this thread, However I could find a solution yet!!

Are you having such problem?

See [http://ubuntuforums.org/showthread.php?t=1799217](http://ubuntuforums.org/showthread.php?t=1799217)

---

