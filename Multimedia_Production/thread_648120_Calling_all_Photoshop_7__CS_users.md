---
title: "Calling all Photoshop 7 / CS users"
date: 2007-12-23
forum: Multimedia Production
---

### Post by dankegel on 2007-12-23
The Wine project is looking for hardcore Photoshop 7 or CS
users who use Photoshop professionally, all day, every day,
and who are willing to tell us why they can't do that in Linux
using Wine yet.

We know everybody would like Photoshop CS3 or at least
CS2 support, but support for CS2 and CS3 isn't quite
ready, so we'd like to focus on our strengths, and support
Photoshop 7 and CS excellently.  Don't worry, we're also
working on the CS2 and CS3 issues.  Getting all the 7 and CS
issues taken care of builds a stronger foundation for CS2 and CS3.

If something doesn't work in Photoshop 7 or CS itself,
or your favorite plugin works in Windows with 7 or CS
but not in Wine, please let us know how to reproduce
the problem.  To do that, just reply to this post, or leave 
a comment in the wine appdb for Photoshop 7 or CS, 
or file a bug in the Wine Bugzilla, whichever you're more
comfortable with.
We'll take it from there; if we can reproduce it, we'll
file a bug and see if we can get a wine developer to fix it.

Ideally you'd test with the latest release of Wine
(currently 0.9.51), but if you're still on a slightly older
version, don't sweat it, we'll retest on the latest for you.

Thanks!
Dan Kegel
Wine 1.0 Release Manager

---

### Post by splintercellguy on 2007-12-27
I think this would get a better response in the Wine subforum.

---

### Post by Gomorrah on 2007-12-28
Hello.

No Wacom pressure support through Wine on Photoshop 7 has stopped me from moving to Linux; everything else seems to work beautifully.


Step 1. Install Ubuntu 7.10

---

Step 2. sudo gedit /etc/X11/xorg.conf

Uncomment 3 lines to enable Wacom support (btw, I'm using a Wacom 6x8 Intous 2 USB tablet)

---

Step 3. Wacom now works with gimp (after enabling in preferences) Yay!

---

Step 4. Install Wine 0.9.51 as instructed on WineHQ.

Install Photoshop 7: wine /blah/blah/Setup.exe

Install Photoshop 7 Update: wine /blah/blah/ps701up.exe

---

Step 5. Start Photoshop (Wow! It works, nice job Wine guys)

-New document

-Select Brush tool

-Open brush editor

-Shape dynamics > Size jitter > Control: Pen pressure (I see a yellow triangle telling me Photoshop hasn't detected a tablet)

-Tried anyway, but no pressure.

--------

Step 6. ?



Thanks.

---

### Post by Gomorrah on 2007-12-29
I just tried the new Wine 0.9.52 after formatting and reinstalling Ubuntu 7.10.
Repeating the actions from my previous post results in the same conclusion. Could this be an Ubuntu problem; is there another distribution that you recommend?

[[IMG]http://img341.imageshack.us/img341/9339/screenshotah1.th.png[/IMG]](http://img341.imageshack.us/my.php?image=screenshotah1.png)

---

### Post by Shay Stephens on 2007-12-29
I use Photoshop 7 in my work as a photographer.  For the work I do, PS7 is working perfectly for me with the latest version of wine.  I am opposed to online activation, so I am not going to be using any of the CS versions of Photoshop.

---

### Post by Gomorrah on 2007-12-29
Do you use a Wacom tablet? And if so, does it work?

I work as an Illustrator - sometimes digitally - without tablet support I'm stuck on windows. Besides this, everything works perfectly for me too.

---

### Post by Shay Stephens on 2007-12-29
> **Gomorrah said:**
> Do you use a Wacom tablet? And if so, does it work?

I work as an Illustrator - sometimes digitally - without tablet support I'm stuck on windows. Besides this, everything works perfectly for me too.

I don't use a tablet, just mouse work.  Sorry :-(

---

### Post by QOLIM on 2007-12-30
2 Problems I'm having in photoshop7:

The 'Slice' windows won't show up in imageready, you only see a black line.

The windows (like layers, tools,...) are being displayed on top of all the windows open (of native linux apps)

---

### Post by Shay Stephens on 2007-12-31
> **QOLIM said:**
> The windows (like layers, tools,...) are being displayed on top of all the windows open (of native linux apps)

I don't use imageready, so no help there, but your second problem sounds like you are using an older version of wine.  Try using the .9.52 version that just came out, it solves that problem.  

Uninstall wine via synaptic, download the .9.52 deb from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

right click on the deb file and run it with wine.  After install, run winecfg from the terminal to finish the setup.  Then run PS7 again and it should work much better for you.

---

### Post by QOLIM on 2007-12-31
> **Shay Stephens said:**
> I don't use imageready, so no help there, but your second problem sounds like you are using an older version of wine.  Try using the .9.52 version that just came out, it solves that problem.  

Uninstall wine via synaptic, download the .9.52 deb from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

right click on the deb file and run it with wine.  After install, run winecfg from the terminal to finish the setup.  Then run PS7 again and it should work much better for you.

No, I'm always using the latest version (59.52 now and still having the problem).

I'm running kubuntu 7.10 btw

---

### Post by Gomorrah on 2007-12-31
I'm not having your window problem either:

[[IMG]http://img168.imageshack.us/img168/1508/screenshotfq1.th.png[/IMG]](http://img168.imageshack.us/my.php?image=screenshotfq1.png)

Ubuntu 7.10 / Wine 0.9.52

---

### Post by Shay Stephens on 2007-12-31
> **QOLIM said:**
> No, I'm always using the latest version (59.52 now and still having the problem).

I'm running kubuntu 7.10 btw

Hmm, I am running gnome, I don't know if that makes a difference or not.

---

### Post by QOLIM on 2007-12-31
I knew it didn't happen all the time.
And you were right, it doesn't happen in ps.
I just found out it's another imageready bug

pic:
[[IMG]http://img166.imageshack.us/img166/7792/p1ve5.th.jpg[/IMG]](http://img166.imageshack.us/my.php?image=p1ve5.jpg)

You can also see another bug I'm having lately: only the left half of the tools windows is shown (again only in imageready). 

here a pic of the slices window not showing up:
[[IMG]http://img235.imageshack.us/img235/9797/p2ey2.th.jpg[/IMG]](http://img235.imageshack.us/my.php?image=p2ey2.jpg)

---

### Post by galvheim on 2008-01-03
No support for Wacom Tablet Pressure. It works with Gimp and is correctly installed, but in Photoshop it is not working.

Btw. I use CS2 portable without problems.

Does anyone have support for the tablets pen pressure at all?

---

### Post by Gomorrah on 2008-01-03
> **galvheim said:**
> No support for Wacom Tablet Pressure. It works with Gimp and is correctly installed, but in Photoshop it is not working.

Btw. I use CS2 portable without problems.

Does anyone have support for the tablets pen pressure at all?


[http://www.winehq.org/?issue=337#Tablet Pen/Eraser/Pressure support](http://www.winehq.org/?issue=337#Tablet Pen/Eraser/Pressure support)

---

### Post by 124c41 on 2008-01-08
@galvheim
pressure support didn't work for me with wine 0.9.52 downloaded from the Ubuntu repositories.
After downloading and compiling the source, I restarted my PC with the tablet plugged in and after that, pressure sensitivity worked perfectly in CS2 and Artrage. (OpenCanvas recognizes pressure too but crashes when the tilt angle reaches 90° with an "EZeroDivide in ntdll.dll" error message)

---

### Post by Gomorrah on 2008-01-09
> **124c41 said:**
> @galvheim
pressure support didn't work for me with wine 0.9.52 downloaded from the Ubuntu repositories.
After downloading and compiling the source, I restarted my PC with the tablet plugged in and after that, pressure sensitivity worked perfectly in CS2 and Artrage. (OpenCanvas recognizes pressure too but crashes when the tilt angle reaches 90° with an "EZeroDivide in ntdll.dll" error message)

Didn't work for me.

Did you use the development, or official source?

---

### Post by 124c41 on 2008-01-09
> **Gomorrah said:**
> Didn't work for me.

Did you use the development, or official source?

I used the offical source from [http://prdownloads.sourceforge.net/wine/wine-0.9.52.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-0.9.52.tar.bz2).

---

### Post by Gomorrah on 2008-01-09
> **124c41 said:**
> I used the offical source from [http://prdownloads.sourceforge.net/wine/wine-0.9.52.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-0.9.52.tar.bz2).

So did I.

But I'm a Linux noob, so it would be safe to assume that the problem lies with me.

---

### Post by Rowdy73 on 2008-01-10
Thanks for the motivation guys, i now have a fully functional, working version of photoshop cs 8.0 in my Ubuntu flavor of Linux. Woot! :guitar:

---

### Post by sYnOnYx on 2008-01-10
> **Rowdy73 said:**
> Thanks for the motivation guys, i now have a fully functional, working version of photoshop cs 8.0 in my Ubuntu flavor of Linux. Woot! :guitar:

i wish i was there.

i keep getting a "componet move data" error.

---

### Post by sYnOnYx on 2008-01-10
> **sYnOnYx said:**
> i wish i was there.

i keep getting a "componet move data" error.

also getting this error in the terminal

Xlib:  extension "XFree86-DRI" missing on display ":1.0".

---

### Post by Rowdy73 on 2008-01-12
> **sYnOnYx said:**
> i wish i was there.

i keep getting a "componet move data" error.


I wish it were true, unfortunately i don't have it working like i thought i did.

-Total fail

---

### Post by dankegel on 2008-01-18
Syonix, your missing extension problem might be a video driver problem,
see [http://www.linuxquestions.org/questions/linux-games-33/xlib-extension-xfree86-dri-missing-on-display-0.0.-277294/#post2748586](http://www.linuxquestions.org/questions/linux-games-33/xlib-extension-xfree86-dri-missing-on-display-0.0.-277294/#post2748586)

Rowdy73, what's going wrong?

BTW, activation in Photoshop CS seems to be working for me since yesterday,
and this change will be in wine-0.9.54, which will be released
around Jan 25th. Imageready CS still has one bug stopping it
on Wine ([http://bugs.winehq.org/show_bug.cgi?id=9802](http://bugs.winehq.org/show_bug.cgi?id=9802)).

---

### Post by Rowdy73 on 2008-01-18
> **dankegel said:**
> 
Rowdy73, what's going wrong?



I thought i had them working PS 7.0 and PS 8.0, but now they fail to load at all.

Edit:

All i needed to do was go to administration > Synaptic > Search for WINE > Then install WINE and WINE-DEV
7.0 seems to work fine, 8.0 has a few bugs though.

---

### Post by dankegel on 2008-01-20
Updates: 
As of wine-0.9.54, pressure sensitivity should work better.
Also as of wine-0.9.54, Photoshop CS2 should work.  
The only hitch is you have to install the Times32 font 
from corefonts before installing CS2.
See [http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop) for details.

---

### Post by | MM | on 2008-01-27
Hi,

I am running Hardy, wine-0.9.54, Adobe Photoshop CS2.
Installation was perfect and things seem mostly fine as far as tools are concerned, in fact i have yet to see an issue with PS tools.  

The biggest impediment to usability is the window manager issues.
Let me try and describe some of the instances of bad window behaviour i have seen thus far.

1) The actual canvas, i.e. the image(s) i am working on, is not nested within PS-CS2's parent window as it is on Windows.  This means if you maximise the canvas window, it obscures the tools and the parent window (Photoshop).  

2) Sometimes nested windows and dialogues can get 'lost' behind Photoshop or the canvas. I have seen this with Save dialogues and also the layer/history/navigation (etc...) nested windows. In the case of this issue happening with prompts, as well as being lost behind windows, the prompt loses focus. Whereas, the hovering 'tool window' is rendered on top of _all_ windows on the desktop.  In general the nested PS windows do not seem to behave as they do on Windows.

3) When using metacity, when you right click on a tool to select a different mode that is available, say, i want to switch from 'blur' to 'smudge,' the context menu does not get rendered on top but can be 'lost' beneath other windows.  Oddly this does not happen when using compiz (let me reiterate: i have seen this only with metacity so far).

4) Resizing/Maximising/Opening windows results in slow (re)drawing of affected/opened windows.

5) Open Photoshop > Open an image or blank canvas and on my system i witness a lot of CPU gets used when mousing-over Photoshop or any of its child windows.  At times i have seen greater than 70% CPU use reported in gnome-system-monitor from merely mousing-over PS-CS2.  Point to note is that i have my mouse sensitivity to high, in the motion tab of gnome's mouse preferences.  I have not had a look at the effect of using a lower sensitivity with PS-CS2.  It seems to me that this is specifically a PS problem, because both Picasa and utorrent do not report higher CPU use when simply mousing-over areas of these two other apps.

That's it for now.  If there's anything more i can do to provide you with further information, please do not hesitate to ask, i will try my best to keep an eye on this thread.

Anyways, despite the issues i have mentioned, i am excited to see PS CS2 running O.K. on Ubuntu!  Thank you so much for your efforts!  I cannot wait for wine 1.0!


Regards 
Matt

---

### Post by | MM | on 2008-01-27
The [first attachment ]("http://ubuntuforums.org/attachment.php?attachmentid=57802&stc=1&d=1201469820")depicts a 'lost' window, in this case the actual canvas has become lost!  Note the navigator is still displaying the image supposidly still being worked on.  Also losing the canvas results in PS non-responsiveness, hence the greying out of the parent window by compiz.

Also of note in the first attachment.  Notice the font rendering of the zoom percentage, in the navigator window.  Below a certain font size, font rendering becomes unattractive and hard to read in all win apps via wine.

The [second attachment]("http://ubuntuforums.org/attachment.php?attachmentid=57803&stc=1&d=1201469820") depicts a slow redraw of photoshop windows when using compiz as the window manager.

The [third screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=57804&stc=1&d=1201469820") shows some simple window manager wierdness, where compiz is drawing a window border around the hovering tool window.

[This attachment]("http://ubuntuforums.org/attachment.php?attachmentid=57807&stc=1&d=1201471870") shows some mis-drawing of the save as dialogue.

---

### Post by ArtInvent on 2008-01-27
My wife is a dedicated Photoshop and Illustrator user. She's a professional fabric designer for clothing. I almost got her over to Ubuntu but she is so sensitive to even the slightest change in keystrokes etc that it slows her down. Me, I'm happy to adapt. Right now the only way to run these two programs adequately is in a VM, we use VirtualBox.  I can't get full tablet pressure to work there either, but at least Ill. runs.

She uses a very large Intuos tablet so that's pretty important to get running flawlessy with pressure etc. 

Next would be Illustrator. There is a reason these two programs are bundled together. As far as I know there's not a single version of Ill. that runs worth a rat's pitooty on Wine. Anyone working on that? 

Right now in Wine 0.9.54 - CS2 finally will activate fully and it runs pretty well. The previously mentioned window problems are kind of a drag. I personally don't like all the way PS uses separate windows for the toolbox and the layers toolbars, so the way I minimize this hassle is by sizing the main program window so that these elements are outside of it. Then I can maximize a photo window within the PS main window and all is well. But maximizing a photo in Wine it disregards the main window and uses the whole desktop. It doesn't really use the main window to contain anything. Weird, and not good.

The other problem is that my other programs are not happy at all with 0.9.54. CorelDraw and Sketchup got screwed up somewhere in the last few versions of Wine. I have actually gone back to 0.9.51 so that I could install and run these. Now that CS2 is installed it runs pretty much the same in 0.9.51. 

I haven't tried the tablet lately. Until I can run a more recent version of Wine with all these apps it's seems a little pointless.

Next, sometimes when I hit the spacebar to use the 'hand' tool to pan around, it gets stuck on the hand tool and won't switch to any other tool. You pretty much have to quit and restart. The hand is pretty important so that's a pain.

I haven't had any of the 'slow' window problems or sucking on CPU usage. I don't use Compiz or anything because on my Gutsy system it just isn't stable at all.

This is pretty much all the same from 0.9.51 through .54. Other than the nasty activate bug being fixed, not a lot of change.

Other than that this great progress. Thanks for all the efforts.

---

### Post by Gomorrah on 2008-01-31
> **dankegel said:**
> Updates: 
As of wine-0.9.54, pressure sensitivity should work better.
Also as of wine-0.9.54, Photoshop CS2 should work.  
The only hitch is you have to install the Times32 font 
from corefonts before installing CS2.
See [http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop) for details.

Thank you very much wine guys; Photoshop 7 now works with pressure!

The pressure is a bit weak in Gutsy, so I  added this:

Option		"PressCurve"    "80,0,100,20"

To my xorg.conf 

I can ditch Windows now.

Thanks again.

---

### Post by | MM | on 2008-02-05
For me, Photoshop CS2 crashes on opening PNG files.

File > Open > *open a PNG file*

Crashes without error.

---

