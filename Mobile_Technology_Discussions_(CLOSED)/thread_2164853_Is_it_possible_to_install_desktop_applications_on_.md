---
title: "Is it possible to install desktop applications on Ubuntu Touch?"
date: 2013-08-02
forum: Mobile Technology Discussions (CLOSED)
---

### Post by arapaho on 2013-08-02
Is it possible to install desktop applications on Ubuntu Touch? Will they work? Does Ubuntu Touch need special versions?

---

### Post by Copper Bezel on 2013-08-02
At the moment, [no, desktop apps don't work on Touch]("https://wiki.ubuntu.com/Touch/FAQ#Which_applications_do_run_on_Ubuntu_Touch.3F"). There's a set of core apps under development that are "native" to Ubuntu Phone, and the OS can't run existing desktop apps because it doesn't make use of X11. However, non-graphical apps apparently run just as they would on normal Ubuntu. 

I'm not sure whether desktop apps will be limited to the "convergence" system on phones, or whether Ubuntu Touch will use Mir (and XMir) in future iterations.

---

### Post by grahammechanical on 2013-08-02
May I quote from here?

[http://en.wikipedia.org/wiki/Ubuntu_Touch](http://en.wikipedia.org/wiki/Ubuntu_Touch)

> [COLOR=#000000][FONT=sans-serif]Ubuntu Touch utilizes the same core technologies as the Ubuntu Desktop, so applications designed for the latter platform run on the former and vice versa. Additionally, Ubuntu Desktop components come with the Ubuntu Touch system; allowing Ubuntu Touch devices to provide a full [/FONT][/COLOR][desktop]("http://en.wikipedia.org/wiki/Ubuntu_Desktop")[COLOR=#000000][FONT=sans-serif] experience when connected to an external monitor.[/FONT][/COLOR][SUP][[6]]("http://en.wikipedia.org/wiki/Ubuntu_Touch#cite_note-ecosys-6")[/SUP][COLOR=#000000][FONT=sans-serif] Ubuntu Touch devices can be equipped with a full Ubuntu session and may change into a full [/FONT][/COLOR][desktop operating system]("http://en.wikipedia.org/wiki/Desktop_operating_system")[COLOR=#000000][FONT=sans-serif] when plugged into a docking station.[/FONT][/COLOR][SUP][[4]]("http://en.wikipedia.org/wiki/Ubuntu_Touch#cite_note-ars1-4")[/SUP][COLOR=#000000][FONT=sans-serif] If plugged the device can use all the features of Ubuntu and user can perform office work or even play ARM-ready games on such device.[/FONT][/COLOR]

The intention is to have one Ubuntu platform that runs on a Desktop PC, a phone, a tablet and a TV. Personally, I do not think that there will be a good user experience running apps like Libreoffice on a phone size screen. The experience may get better on a tablet. I do think that the phone core apps will work well on the desktop size screen. But the Touch aspect will only work if the monitor is a touch screen.

I am at present running Saucy Salamander on Xmir and I have yet to find a Xserver application that does not work. I understand that support for Xserver will be dropped sometime during 2014. Developers are encouraged to use the Ubuntu Software Development Kit (SDK) as that will help them write apps that will scale from phone, through tablet up to desktop size.

It is possible to run a development version of Unity 8 in Saucy Salamander right now. I might just try it out and watch it grow.

[http://www.omgubuntu.co.uk/2013/08/unity-8-ubuntu-13-10-arrives?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2013/08/unity-8-ubuntu-13-10-arrives?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

You may want to watch the video that this page links to. It will show you how it all goes together.

[http://www.omgubuntu.co.uk/2013/07/ubuntu-edge-convergence-shown-off](http://www.omgubuntu.co.uk/2013/07/ubuntu-edge-convergence-shown-off)

Regards.

---

### Post by Copper Bezel on 2013-08-02
There's some speculative stuff left in there. Apparently, the "converged" mode for running a desktop from a Touch device is planned to be complete for 13.10, but that doesn't tell us whether or not existing desktop applications will be able to run on the phone screen at that time as well. Like you said, it's hard to see how that could be a very complete experience with most apps. That's particularly since GTK3 isn't resolution-independent; tiny, tiny buttons. = / 

The desktop apps Canonical is talking about when they say that apps written for the desktop will run on the phone might well be apps written for the desktop *using the Ubuntu SDK.*

---

