---
title: "Flash CPU 100%"
date: 2008-05-02
forum: Multimedia Software
---

### Post by towersoft on 2008-05-02
HI,
    I have seen others ask about this but have never seen a fix for the problem. I am begining to think that its just purely down to my Latop not beeing fast enough. Although it used to cope fine under Windows XP but I am not going back. Whenever I run flash content my cpu usage remains high, up to 100%. This after time causes the computer to shut itself down due to overheating. With 7 and 7.04 the computer would just turn off and I would get a message at boot that it had been turned off to protect itself. In hardy it properly shuts itself down with no warnings and startup messages. It mainly occurs if I play flash games such as the slots at Virgin Casino but Utube etc will overheat the computer as well.
    The Laptop is a Dell Latitude D410 1.86Ghz Centrino, 2GB Ram and plenty of Hdd space. Should I just dump this machine and get a new one?. Have been looking at the Macbooks. Any help greatly appreciated.

---

### Post by Zorael on 2008-05-02
There might be a way to solve this, but to be grim, there *are* computers that flash simply won't cooperate with. My brother has an Acer laptop a few years old, 2200 series or something like that (off the top of my head), and flash *always* berserks, regardless of whether he's running Windows or Linux. I can't think of anything else but there being some hardware incompatibility between flash itself and the system, because those are the only two common denominators between OS installations.

His workaround was to install a flash blocker; that way you can control when you want it to run. With Adobe now open-sourcing the flash SDK, hopefully flash itself (or other alternatives) will benefit from Linus' Law and work better across the board.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200611/110706Mozilla.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200611/110706Mozilla.html)
[http://en.wikipedia.org/wiki/Linus'_law](http://en.wikipedia.org/wiki/Linus'_law)

---

### Post by gsiliceo on 2008-05-04
I recommend you to install the 9,048 flash player, it is a LOT less cpu intensive.
First test your current version of flash here
[COLOR="Blue"][SHow my flash player version]("http://www.mediacollege.com/adobe/flash/player/version/show.html")[/COLOR]
Then normally you'd have to download a 94 meg package that adobe provides with lots of flash player version but i'd make it easier for you uploading just the recommended 9.048.
[COLOR="Blue"][Download it here 2.5 megs to your desktop]("http://www.mediafire.com/?znhecmwx0j4")[/COLOR]

Close firefox.

Then extract it, right click on the package and *"extract here"*
Open the folder and copy the file libflashplayer.so 
Now open a terminal and do this
> sudo nautilus
Once is opened go to /usr/lib/flashplugin-nonfree/
And paste the file you just copied, replace when asked. 
Then go back to the extracted folder in your desktop and double click the flashplayer-installer, and choose execute in terminal, then hit enter and you are done.

Test your new version of flash

---

### Post by darkshado on 2008-05-17
Same problem here and i try with the versions 9.048 and 10 of flashplayer almost 100% of CPU charge! 

my browser:
firefox 3 beta 5

ubuntu:

Hardy Heron

---

### Post by poctob on 2009-06-10
Since I just stumbled upon this post this issue is still a problem.  I edited firefox start up script:

[CENTER]**sudo gedit /usr/lib/firefox-3.0.10/firefox.sh**[/CENTER]


And added the following line to the end:

[CENTER]**export XLIB_SKIP_ARGB_VISUALS=1**[/CENTER]

Worked like a charm since.

---

### Post by McYaballow on 2009-12-29
> **poctob said:**
> Since I just stumbled upon this post this issue is still a problem.  I edited firefox start up script:

[CENTER]**sudo gedit /usr/lib/firefox-3.0.10/firefox.sh**[/CENTER]


And added the following line to the end:

[CENTER]**export XLIB_SKIP_ARGB_VISUALS=1**[/CENTER]

Worked like a charm since.
Didn't work for me :(

---

### Post by sportsdude81 on 2010-02-05
> **poctob said:**
> Since I just stumbled upon this post this issue is still a problem.  I edited firefox start up script:

[CENTER]**sudo gedit /usr/lib/firefox-3.0.10/firefox.sh**[/CENTER]


And added the following line to the end:

[CENTER]**export XLIB_SKIP_ARGB_VISUALS=1**[/CENTER]

Worked like a charm since.

What does this code do?  what does change? does it hinder flash in any way?

---

### Post by sportsdude81 on 2010-02-05
> **sportsdude81 said:**
> What does this code do?  what does change? does it hinder flash in any way?

Well despite all my questions I added the one line of code to the end of start up script and it worked!!!!  Normally if i watch/play anything flash my cpu shoots up and stays up until i close firefox.  No as soon as i close the web page my cpu drops.  I am on a HP Pavillion dv6000.  Running 64bit Karmic and Firefox 3.5.7

---

### Post by umutert on 2010-04-23
> **poctob said:**
> Since I just stumbled upon this post this issue is still a problem.  I edited firefox start up script:

[CENTER]**sudo gedit /usr/lib/firefox-3.0.10/firefox.sh**[/CENTER]


And added the following line to the end:

[CENTER]**export XLIB_SKIP_ARGB_VISUALS=1**[/CENTER]

Worked like a charm since.


Worked for me too
saved up about %33 cpu time, used to be working 100%, now %66,
I also recommend a flash ad blocker, I am using [adblock]("https://addons.mozilla.org/en-US/firefox/addon/1865") and it works real good

by the way I have ubuntu 9.10 on a single core intel m with 512MB shared memory.

---

### Post by sportsdude81 on 2010-05-11
for Lucid Lynx or any other build with any other Firefox version you have to change the firefox version number accordingly.  firefox-3.6.3 in Lucid.

---

### Post by rsscwb on 2010-06-13
I had the same problem and solved it by using the swfdec instead of Adobe plugin:

apt-get remove flashplugin-installer flashplugin-nonfree
apt-get install swfdec-mozilla

It worked very fine here.. I tried the gnash plugin too, but unfortunately the result was not satisfactory in some sites.

---

### Post by chris1379 on 2010-06-13
My problem is with youtube videos. If I try any player other than Adobe Flash Player  10, I get a black screen telling me I need to upgrade my Adobe Flash Player. Why can't Adobe give us options to reduce postprocessing and such so it will at least play on lower spec systems? For now I use Download Helper and DL the video to the desktop. The resulting files play in any player I have but I usually use VLC.

---

### Post by GaaraOfDSand on 2010-06-17
I tried what rsscwb said, and that player is even worse than Adobe's.. At least that's how it was for me, not saying it can't work for others.

---

### Post by allanfelipe on 2011-02-20
this is a lack of respect
2 years after the problem and it is not solved.
i am a adobe flex developer and I am given up from ubuntu and linux.
sorry but my softwsare will only run into MS or apple.
Flash player is the worst thing on linux.
sorry ubuntu, but I cant go forward..
and Ubuntu + Flash will always SUCKS
I am with ubuntu 10.04 and tried with all flash player versions available. If someone has a complete and final answer for this problem please answer here.
good bye linux and ubuntu.

---

