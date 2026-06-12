---
title: "How to get quicktime movies, .avi, .mpg to play?"
date: 2009-09-22
forum: Multimedia Software
---

### Post by mjp29 on 2009-09-22
I've installed the ubuntu-retricted-extras-package.

However, I can not play .mov files or .avi files that I email from my mac that were taken on digital cameras.  Also, mpg files won't play.

Movieplayer & VLC simply open and quickly quit and disapear.  Dragonplayer will atleast play the movie but there is no video (all black) and I can hear the sound of the movie.

Also, Firefox will not play quicktime movies online.

At the link [https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html)  I don't understand the statement "If you try to play an unsupported video file, you will be asked if you would like to search for a suitable codec. Click Search and, when the Install multimedia codecs window appears, select one of the codecs displayed in the list and click Install."

I don't understand [from above] when I'm asked to search for a suitable codec because I never get to a point where I can click "Search" at anytime.

I would like to make this work without typing in code, (unless it is code on a page on the ubuntu site I know is official) because I had major problems typing in code that users suggested previously and did a full reinstall of ubuntu (no offense to anyone please).

---

### Post by Wlerin on 2009-09-22
To be clear, your problem is that VLC and Movieplayer just die when you open up these videos? As in, a black window appears for a split second, then the entire program crashes?

I had the same problem, and eventually found a site that mentioned a bug in the current version of the Xvideo output layer that both programs use. A workaround is to use X11 or SDL to output video instead.

For vlc, you could type:
```
vlc --vout x11
```or ```
vlc --vout sdl
```There is probably also a way to change this in the configuration, but I just replaced all references to the program with these.

Then again, you could have an entirely different problem.

---

### Post by mjp29 on 2009-09-22
> **Wlerin said:**
> To be clear, your problem is that VLC and Movieplayer just die when you open up these videos? As in, a black window appears for a split second, then the entire program crashes?

I had the same problem, and eventually found a site that mentioned a bug in the current version of the Xvideo output layer that both programs use. A workaround is to use X11 or SDL to output video instead.

For vlc, you could type:
```
vlc --vout x11
```or ```
vlc --vout sdl
```There is probably also a way to change this in the configuration, but I just replaced all references to the program with these.

Then again, you could have an entirely different problem.

Yes, my problem is that VLC and Movieplayer just die when they open these videos and a black window appears for a split second and then the entire program crashes (vanishes away).

Is this a common problem?  Is the code you suggest to enter to be entered into terminal.  If others can reply that your code is the fix to the problem then I'll enter it.  Please don't take it personally, but I entered a lot of code into terminal (from forum members)to try to fix a problem and ended up screwing up my cache (somehow).   I'm sure your code is good but I'd like other members to chime in first and verify before I enter code into terminal again.

---

### Post by Wlerin on 2009-09-22
The "code" I suggested isn't really enough to be called a 'code', just a command with options. But then, I guess so are certain variations on rm...

You can run it from a terminal, or in the Custom Command box for Open with Other Application, or even in place of the VLC button in your program menu.

See [http://wiki.videolan.org/VLC_command-line_help](http://wiki.videolan.org/VLC_command-line_help), at the "-V, --vout" entry if you want to verify that this does what I am saying it does (i.e. selects a different video output mode).

EDIT: I only vaguely remember the page that gave me the solution I am giving, you, but it was my impression that it is a recent, but common, problem. However, in a quick google search just now I couldn't find anything.

EDIT2: You could also try just typing "vlc [video name]" in a command-line and see what error you get. ("video name" being the path to one of these videos).

---

### Post by Wlerin on 2009-09-22
Also, video output modes are on this page, though no SDL is mentioned (I've only used x11 myself).

[http://wiki.videolan.org/Video_Output](http://wiki.videolan.org/Video_Output)

---

### Post by mjp29 on 2009-09-22
> **Wlerin said:**
> To be clear, your problem is that VLC and Movieplayer just die when you open up these videos? As in, a black window appears for a split second, then the entire program crashes?

I had the same problem, and eventually found a site that mentioned a bug in the current version of the Xvideo output layer that both programs use. A workaround is to use X11 or SDL to output video instead.

For vlc, you could type:
```
vlc --vout x11
```or ```
vlc --vout sdl
```There is probably also a way to change this in the configuration, but I just replaced all references to the program with these.

Then again, you could have an entirely different problem.

vlc --vout x11 would make all the videos play in vlc only (that command forced vlc to open, then i could open a video file and it would work).  However this appears to be a temporary fix where I have to enter this line into terminal each time I want to open a video file I've saved to my desktop.  It's not a permanent fix because later I can open vlc from the application menu and it won't work to open a video file (again the black screen and crash instantly).

I'd like to be able to view these videos instantly in emails (when received) or double click a .mov, .avi file and instantly view them (without entering the vlc --vout x11 into terminal).

Do you suppose this is a problem with the pc box i'm using (or its graphics card) or is this a very common problem in the latest release of ubuntu?

Just testing ubuntu now to see if its for me, but if I can't get things like this to work more flawlessly then it will be a more heavy consideration on whether or not I should do a total switch (from Mac os x).

---

### Post by Wlerin on 2009-09-22
Then it is a problem with your default output mode. You can configure VLC to automatically use the X11 output mode (or any other one that works) by going to Tools > Preferences, select the video tab, and choose something from the Output menu.

Also, what I've been doing (though changing the config would probably be simpler), is right-clicking any new video formats, choosing "Run with Other Application" (or whatever your file manager calls it) and using "vlc --vout x11", making sure to check "use this as the default".

There's probably a way to do this with Movieplayer. What program is your current default? Or which one do you prefer?

Edit: Also, what graphics card to you have? This is the first machine I've had this problem on, but it's also the only one I've used the newest versions of ubuntu on. 

Lastly... what errors do you get when you just run "vlc -vvvv" (super verbose mode) and open a video file?

---

### Post by mjp29 on 2009-09-22
When I enter "vlc -vvvv" a bunch of text spits back at me, but at the end it says "[00000404] qt4 interface debug: Error while initializing qt-specific localization"

I configured VLC to automatically use X11 output mode as you so easily suggested (thanks for making it easy!)

I'll also try to make vlc -vout x11 as my default

I really don't care if it's movieplayer or vlc (or any program by default as i have no preference).  If I can make vlc my default and get these movies to play from file (on desktop) or from email then it works and that workds for me - and it looks like i'm on the right path thanks to you

as far as my graphics card - how can i find that out (what command line in terminal?)  All I can tell you is this is an HP-Compaq dcs5000 sff  computer box


thank you so much for your help (you have me on the right path to loving ubuntu again!)

question still for you to help with:  I can now right click and choose to view a video file (from desktop) by clicking to view with vlc (by left clicking it) and both avi and mov will play.  however, if i double left click either it won't play (same vlc black screen and crash).  I suspect I need to make vlc x11 default as you suggested.  however, when I right click either movie file then left click to choose application i only get a list that has many choices on no x11 choice (the big list does have vlc as a choice) but no way to make x11 default (and if i choose make vlc default then i get the same crash from email or desktop file if i choose the movies).  however i can right click the attachment in the email and choose x11 and make them play in email attachment received.  curious thing though that right clicking the movies on desktop don't give x11 option but if i just choose vlc they do play now

thanks so much for your help and please keep helping me

---

### Post by Wlerin on 2009-09-23
Once you've configured vlc to use x11 as the default, you shouldn't need to use the vlc --vout x11 command anymore. It's either-or. Glad to hear it works, although I wish I knew why it wasn't fixed yet, or why it seems to be rather rare (still haven't found the original reference to it, though I suspect I found it by looking up the error message I received, which I'll reproduce shortly).

Edit: just read the last half of your post. Will get to it in a microt.

---

### Post by mjp29 on 2009-09-23
> **Wlerin said:**
> Once you've configured vlc to use x11 as the default, you shouldn't need to use the vlc --vout x11 command anymore. It's either-or. Glad to hear it works, although I wish I knew why it wasn't fixed yet, or why it seems to be rather rare (still haven't found the original reference to it, though I suspect I found it by looking up the error message I received, which I'll reproduce shortly).


update and more good news

i rebooted the computer and now in evolution email if i simply choose to open the attachment in vlc media player it plays great (so it is going to the x11 by default now)

also, a file on the desktop if i right click and choose vlc media player (x11 no longer an option but x11 must now be built into it) ... because by just choosing vlc media player from a file on desktop makes it play great too

now how do i just simply make vlc media player my default movie player - that should be simple, eh?  (so that it doesn't always try to open such files from movieplayer)

must be a bug in the graphics card in this box or something, because i don't see it widely reported as a problem (same with your computer, eh?)

thanks so much again for your help!


p.s. tell me what code to enter into terminal to tell me what video/graphic card i have and maybe that will tell something about the problem (perhaps it is the same card you have)

---

### Post by Wlerin on 2009-09-23
[COLOR=Red][s]> **mjp29 said:**
> When I enter "vlc -vvvv" a bunch of text spits back at me, but at the end it says "[00000404] qt4 interface debug: Error while initializing qt-specific localization"
Try to open a video file with the newly opened vlc, what error does it give when it quits? Or is that the error? What about when you open an avi or mpg?[/s]

Edit: vlc is working now, so you shouldn't get an error.[/COLOR]

> I configured VLC to automatically use X11 output mode as you so easily suggested (thanks for making it easy!)

I'll also try to make vlc -vout x11 as my defaultAs mentioned above, doing the former should make the latter unnecessary.

> I really don't care if it's movieplayer or vlc (or any program by default as i have no preference).  If I can make vlc my default and get these movies to play from file (on desktop) or from email then it works and that workds for me - and it looks like i'm on the right path thanks to youWhich desktop environment are you using? Gnome? KDE? Xfce? Also, see below about right-clicking.

> as far as my graphics card - how can i find that out (what command line in terminal?)  All I can tell you is this is an HP-Compaq dcs5000 sff  computer boxType
```
lshw -class display
```This will list all hardware you have in the display class. It advises you to run it as a super user but there aren't any differences, at least for this application (some of the other classes don't show as much info for a regular user).


> thank you so much for your help (you have me on the right path to loving ubuntu again!)Glad to help!

> question still for you to help with:  I can now right click and choose to view a video file (from desktop) by clicking to view with vlc (by left clicking it) and both avi and mov will play.  however, if i double left click either it won't play (same vlc black screen and crash).  I suspect I need to make vlc x11 default as you suggested.  however, when I right click either movie file then left click to choose application **i only get a list that has many choices** on no x11 choice (the big list does have vlc as a choice) but no way to make x11 default (and if i choose make vlc default then i get the same crash from email or desktop file if i choose the movies).  however i can right click the attachment in the email and choose x11 and make them play in email attachment received.There should be an option in that list to "pick another application" that will open up a dialog box with a list. On that box, there should be either an option to manually enter a command and/or always use the selected command for that type of file. If vlc by itself works now that you have changed the output settings, then you can just select VLC on that list, and tell it to always use that program when opening mpeg and avi video (and flv, mp4, etc.). 

There are other ways as well, but they depend a lot more on your desktop environment.

>   curious thing though that right clicking the movies on desktop don't give x11 option but if i just choose vlc they do play nowGood, that means changing the configuration worked.

---

### Post by mjp29 on 2009-09-23
Thanks so much for your help.  I marked this thread as solved.

---

### Post by mjp29 on 2009-09-23
After marking thread as solved I just wanted to follow up with answering some of your questions.

the desktop i'm using is gnome i suppose - using Ubuntu (not kubuntu when doing this)

Terminal tells me my hardware is (below) - perhaps our rare problem was caused by both of us having some hardware in common - ?  reply back if you find out so by looking at below

michael@michael-desktop:~$ lshw - class display
Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.13)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

michael@michael-desktop:~$

---

### Post by ajgreeny on 2009-09-23
```
lshw -C display
```is the command you need.

---

### Post by mjp29 on 2009-09-23
After marking thread as solved I just wanted to follow up with answering some of your questions.

the desktop i'm using is gnome i suppose - using Ubuntu (not kubuntu when doing this)

Terminal tells me my hardware is (below) - perhaps our rare problem was caused by both of us having some hardware in common - ? reply back if you find out so by looking at below


michael@michael-desktop:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
michael@michael-desktop:~$

---

### Post by mjp29 on 2009-09-23
thanks and by the way i like your avatar.  but i would like to know who that is in the avatar - actor, comedian, who ?

---

### Post by Wlerin on 2009-10-07
Sorry, I haven't really checked on this since you marked it solved. That said, if you are still looking at this thread:

1) lshw results (lshw -class display works too, but it needs no spaces)

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=nvidia latency=32 maxlatency=1 mingnt=5 module=nvidia

So we do have a virtually identical graphics card (the second one isn't actually working right now... though that may be the card's fault, rather than Ubuntu's). I seem to recall a sticky about Intel cards, maybe I should check it out.

2) I figured out how to set Totem/MoviePlayer to use x11 output, if you prefer a more native-looking application.

type 'gstreamer-properties' at the command line, and then, in the dialog that comes up, select the Video tab, and set it to X11 only (there's a dropdown menu with four options, the one that has only X11 in parentheses is the one you want).

---

