---
title: "Of Wine, Fink, x11, and Apps on a Mac 10.4 G3 PPC"
date: 2008-04-16
forum: Mac OSX
---

### Post by Truefire on 2008-04-16
I just got a refurb Mac so that I could help friends/family with Mac tech probs.

After I got a feel for it, I want to do a bit more.

I installed Fink and Darwine, only to find that both need some obscure version of X11.

Does anyone know where I can get this?

I tried this one:
[http://www.apple.com/support/downloads/x11formacosx.html](http://www.apple.com/support/downloads/x11formacosx.html)

But it says,"Newer Version installed"

Honestly, I like installing things on Ubuntu better :)

Any ideas? 

PS: I don't have a Tiger installation cd, but I can borrow one if necessary.I'm comfortable enough with the Terminal, and feel free to ask for screenshots.


Specs: Mac OSX Tiger  Power Mac G3 (PPC CPU, 400Mhz)
512mb RAM, 128mb GPU, CD Drive and Zip drive.

---

### Post by Truefire on 2008-04-18
Well, I installed x11 and fink, now it's just noit working with WINE.
Here's all the stuff I found, including the x11 found on the Tiger DVD.

Peter
July 22, 2006 at 5:14 pm
1) insert Tiger install DVD.&#8232;2) scroll window that appears down slightly&#8232;3) double click “optional installs” package icon&#8232;4) click continue on installer welcome pane&#8232;5) click continue and agree on installer license pane&#8232;6) select your boot volume and click continue on installer target pane&#8232;7) click disclosure triangle on “Applications” at top of custom install pane&#8232; select “X11&#8243;&#8232;9) click install
[http://cjmart.in/2006/12/01/install-x11-on-tiger-without-the-tiger-install-dvd/#comment-79770](http://cjmart.in/2006/12/01/install-x11-on-tiger-without-the-tiger-install-dvd/#comment-79770)
Peter
July 23, 2006 at 8:56 pm
Put the Tiger DVD in, scroll down and open the “System” folder, then open the “Installation” folder, and then the “Packages” folder. You will see X11User.pkg, which you can use to install X11 and nothing else.
[http://developer.apple.com/tools/xcode/](http://developer.apple.com/tools/xcode/)
[http://lists.apple.com/archives/x11-users/2007/Nov/msg00005.html](http://lists.apple.com/archives/x11-users/2007/Nov/msg00005.html)

[http://www.macgimp.org/comment.php?mode=display&order=ASC&pid=6984](http://www.macgimp.org/comment.php?mode=display&order=ASC&pid=6984)
[http://xanana.ucsc.edu/~wgscott/xtal/wiki/index.php/X11](http://xanana.ucsc.edu/~wgscott/xtal/wiki/index.php/X11)
Quick Description of what you need to do
[edit]
On 10.5
	•	Install the X11 SDK. (This gets installed by default when you install Xcode.)
then ...
	•	Install X11.app from the OS X installation DVD. It is an optional package in 10.4 but a default installation in 10.5. Run software update to make sure you have the latest version.
or, to be compatible with what I have compiled, get the most recent version of X11 from here:
	•	X11-2.2.0.1.pkg (or newer) from [http://xquartz.macosforge.org/downloads/](http://xquartz.macosforge.org/downloads/)
Install the X11-2.2.0.1.pkg unless something more recent appears between now and when you read this.
	•	10.5 only: DO NOT set the $DISPLAY variable
[edit]
On 10.4
	•	Install the X11 SDK. (This gets installed by default when you install Xcode.)
then ...
	•	Install X11.app from the OS X installation DVD. It is an optional package in 10.4. Run software update to make sure you have the latest version.
	•	10.4 only: Set the $DISPLAY variable (for users of Terminal.app or iTerm.app) in 10.4, but do not set DISPLAY in 10.5.
	•	10.4 only: Add X11.app to your Login Items if you want it to launch before you need it in 10.4. Do not do this in 10.5; it launches automatically when needed.
&#8232;

---

