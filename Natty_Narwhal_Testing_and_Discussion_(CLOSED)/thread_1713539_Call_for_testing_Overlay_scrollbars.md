---
title: "Call for testing: Overlay scrollbars"
date: 2011-03-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jibel on 2011-03-24
Mark recently blogged about the overlay scrollbars [1]. Now, you can test it for real and report your feedback.   

**How can you help ?**  
We need people running Natty, then follow the the instructions below:  
1. Install the overlay scrollbar from the PPA

 [FONT=Courier New]$ sudo add-apt-repository ppa:ayatana-scrollbar-team/release     
 $ sudo apt-get update     
 $ sudo apt-get install liboverlay-scrollbar-0.1-0 [/FONT]

2. You have to have an account in our tracking system. Go to       
  [http://desktop.qa.ubuntu.com]("http://desktop.qa.ubuntu.com/")  
and click on “Log In” and “Create New Account”   

3. Run the 5 tests described on the tracker (when you click on "Overlay Scrollbars) with as many applications as you can and post the results of the tests to the Tracker [2]. 

Add the applications you've tested in the comment area of the result.   

To enable the overlay scrollbars for an application, run the following command:     
[FONT=Courier New] $ LIBOVERLAY_SCROLLBAR=foo <command> [/FONT]
 
for example
[FONT=Courier New] $ LIBOVERLAY_SCROLLBAR=foo gedit [/FONT]

Before starting to test the scrollbar, read the detailed instructions on [https://wiki.ubuntu.com/Ayatana/ScrollBars](https://wiki.ubuntu.com/Ayatana/ScrollBars)   

**How to file bugs ?  **
In case you find bugs, please report them at: [https://bugs.launchpad.net/ayatana-scrollbar/+filebug](https://bugs.launchpad.net/ayatana-scrollbar/+filebug)  
Don't forget to mention the version of the overlay library tested, and of the application that exposes the problem. 
If the application crashed, apport should have captured a crash file which can help narrow down the issue more quickly.  

In particular, report:

[LIST]
[*] Any kind of crashers, like when the application starts and tries to display the window(s) containing scrollbars
[*] Slowdowns in using scrollable areas; measurements can help judge how much the scrollbar really impacts the application, or whether the application is just slow due to other circumstances
[*] Any other kind of anomaly obviously due to the scrollbars that impacts the user experience
[/LIST]

You can join us in #ubuntu-testing on Freenode where we are coordinating this effort and we'll be happy to help you in testing this feature.   

[1] [http://www.markshuttleworth.com/archives/615](http://www.markshuttleworth.com/archives/615) 
[2] [http://desktop.qa.ubuntu.com]("http://desktop.qa.ubuntu.com/")

---

### Post by kansasnoob on 2011-03-24
Thanks for getting ahead of me :)

I received the same notice in my email this AM. But I'm such a dummy when it comes to Unity, and I'm under tight time constraints, that I'll probably have to sit this one out :(

That does sound like an interesting concept though.

---

### Post by VMC on 2011-03-24
For some reason I deleted my email from ayatana. Thanks for the info. I will install as soon as I catch up on reading this forum.

Also, yesterday I read about the new backgrounds and there already here as of todays daily-live-iso.

---

### Post by go7Ul1ai on 2011-03-24
Can't get it installed even with following instructions, I must be dumb!

---

### Post by snlzkn on 2011-03-24
I guess I am too late for this testing it says
We are not testing at the moment

on the page however I installed it and I quite liked them :)

---

### Post by cariboo on 2011-03-24
> **snlzkn said:**
> I guess I am too late for this testing it says
We are not testing at the moment

on the page however I installed it and I quite liked them :)

There apparently is a bug that needs to be fixed.

> Early testing of the overlay scrollbars revealed that a latest update of GTK in Natty made it non functional. A fix has been provided and will be released soon. But for the moment we are holding on the testing and we will send a notification to ubuntu-qa mailing list when the fix is available.


So keep an eye on the QA mailing list for notification.

---

### Post by bluenova on 2011-03-26
It looks really nice! Don't have time to test now but I will when I can.

I do feel though that it would be more athletically pleasing if the scrollbar appeared over the red line, not next to it. It just seems a bit odd off to the side.

---

### Post by tjeremiah on 2011-03-26
wish it will work with browsers (Chromium/Firefox). Overall I like it and dont notice much problems when using it with windows that do support te scrollbar .

---

### Post by Atermoon on 2011-03-27
To be honest I find it very weird and visually unpleasant that they appear outside the window. I like the idea, but I think they should be inside.

---

### Post by Handle123 on 2011-03-27
Should really appear inside the window, it doesn't make sense outside.

---

### Post by Nickedynick on 2011-03-27
I like the concept - it seems to be intuitive and work well. The one gripe I have, however, is that the zone around which you can grab the scrollbar is too small. At the very least the orange scroll indicator should be grabbable, if not a few more pixels around the edges. At the moment you have to be too precise with your actions.

---

### Post by tanari on 2011-03-28
only one problem! 
With "normal" scrollbars in maximized windows I can just move mouse to the right edge of monitor and start dragging scrollbar, but now I must AIM at scrollbar thumb!

I like to see them in final version, looks really nice!

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-03
The wiki says this is supposed to work with gnome-terminal and chromium-browser. Doesn't work with either for me, and I've got chromium-browser set to use the GTK theme.

Also, causes nautilus to crash on close.

---

### Post by kahping on 2011-04-03
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> The wiki says this is supposed to work with gnome-terminal and chromium-browser. Doesn't work with either for me, and I've got chromium-browser set to use the GTK theme.

Also, causes nautilus to crash on close.

Just to be sure, did you set LIBOVERLAY_SCROLLBAR=1?

---

### Post by mc4man on 2011-04-03
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> The wiki says this is supposed to work with gnome-terminal and chromium-browser. Doesn't work with either for me, and I've got chromium-browser set to use the GTK theme.

Also, causes nautilus to crash on close.
Don't use chromium, doesn't work on gnome-terminal and atm certainly does crash nautilus, sometimes when opening, always when closing 

> Just to be sure, did you set LIBOVERLAY_SCROLLBAR=1? 
With the upgrade of the gtk libs don't see that's needed anymore - it works on some windows, doesn't on others

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-03
> **mc4man said:**
> Don't use chromium, doesn't work on gnome-terminal and atm certainly does crash nautilus, sometimes when opening, always when closing

Because it works so much better on Firefox? Or is your next suggestion "don't use a browser"?

---

### Post by mc4man on 2011-04-03
> Because it works so much better on Firefox? Or is your next suggestion "don't use a browser"?
I don't recollect it working on firefox either, I've removed the liboverlay... package, no use for it till it stops crashing nautilus.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/748552](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/748552)

(and never have had any thoughts/comments on what people use as a browser, whatever they like is what they should use..

---

### Post by kahping on 2011-04-04
> **mc4man said:**
> With the upgrade of the gtk libs don't see that's needed anymore - it works on some windows, doesn't on others

Really? Didn't know that. Guess I'll give it a try and see. Thanks :)

---

### Post by mc4man on 2011-04-04
> **kahping said:**
> Really? Didn't know that. Guess I'll give it a try and see. Thanks :)
You can ck. out, it does work - though keep in mind the bug linked above -

---

### Post by MacUntu on 2011-04-04
Gedit does seems to get slower if the document is large. Not yet tested enough to report it.

It also feels a bit strange in file choosers, when you have to move the pointer inside the location pane on the right to grab the handle.

---

### Post by juancarlospaco on 2011-04-04
Works perfectly.

With this and the global menu theres a lot of space avaliable on screen.

---

### Post by mc4man on 2011-04-04
See no more nautilus crashes with the 0.1.5 version, scrolling works fine in all supported apps

There is a new package - overlay-scrollbar (0.1.5-0ubuntu1), is built and pending approval to go into ubuntu repo (universe
So likely will show in near future or here (pick arch on right under Builds

[https://launchpad.net/ubuntu/+source/overlay-scrollbar/0.1.5-0ubuntu1](https://launchpad.net/ubuntu/+source/overlay-scrollbar/0.1.5-0ubuntu1)

(while many times use scroll wheel or scroll area instead of grab bar it makes sense to have on outside w/ un maxed windows

---

### Post by mc4man on 2011-04-06
the liboverlay-scrollbar has been released into natty so is avail. thru package manager
(probably no need for a testing sticky anymore

---

### Post by cariboo on 2011-04-06
I'll leave it up for another day or so, then unstick it.

---

### Post by PaulW2U on 2011-04-06
> **mc4man said:**
> the liboverlay-scrollbar has been released into natty so is avail. thru package manager
(probably no need for a testing sticky anymore
As I haven't installed this yet, it is now being show as a Missing Recommended package in Synaptic.

---

### Post by go7Ul1ai on 2011-04-06
Yeah, I really like the overlay scrollbars and I'm glad they've been pushed through updates.. Just wish that more applications would be supported..

Do you reckon it would ever work in Firefox?

---

### Post by Anduu on 2011-04-07
> **tanari said:**
> only one problem! 
With "normal" scrollbars in maximized windows I can just move mouse to the right edge of monitor and start dragging scrollbar, but now I must AIM at scrollbar thumb!

I like to see them in final version, looks really nice!

I didn't realise people still dragged scrollbars these days....

---

### Post by Harry33 on 2011-04-07
> **PaulW2U said:**
> As I haven't installed this yet, it is now being show as a Missing Recommended package in Synaptic.

This is because the new meta package ubuntu-desktop_1.219 recommends overlay-scrollbar.

---

### Post by mc4man on 2011-04-08
There were some interesting additions to latest upgrade though one - scroll on thumb icon seems to have some issues
[https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/754306](https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/754306)

---

### Post by hugmenot on 2011-04-08
Myself, as a keyboard use I never grab the scrollbar, but this is ********: [http://pad.lv/754605](http://pad.lv/754605)

---

### Post by kansasnoob on 2011-04-08
> **hugmenot said:**
> Myself, as a keyboard use I never grab the scrollbar, but this is ********: [http://pad.lv/754605](http://pad.lv/754605)

I needed to get rid of them for a different reason, my poor vision, but ATM I just had to remove both:

overlay-scrollbar
liboverlay-scrollbar-0.1-0

I just thought to add, it most recently messed with me while viewing the .manifest file for the current daily build. I do so frequently enough that I do "drag" the scrollbar to the approximate point of the page before using the scroll wheel, so yes it is important to be able to see the "length" of the page.

---

### Post by r-senior on 2011-04-08
> **kansasnoob said:**
> so yes it is important to be able to see the "length" of the page.
Doesn't the orange bar do that though, just like a "normal" scrollbar? The less there is to scroll, the longer it is.

Admittedly it is very narrow, which needs to be tempered with an accessibility option, but I don't think the fundamental principle has disappeared has it?

---

### Post by mc4man on 2011-04-08
> **hugmenot said:**
> Myself, as a keyboard use I never grab the scrollbar, but this is ********: [http://pad.lv/754605](http://pad.lv/754605)

The fading of the scroll line is a bit weird and doesn't happen in a consistent manner here on 2 installs
(time to do fresh installs tonight.
It may be better if it doesn't go to white (or whatever it's fading to), almost impossible to see on a white window background
(the fade shows clearly on my text editor where i use a colored scheme

Anyway there will be another release next week so still some time for some adjustments

---

### Post by hugmenot on 2011-04-08
The problem is twofold 

[LIST=1]
[*]The fading doesn’t react to the keyboard, onyl to mouse hover events
[*] You need to see where a window is scrolled even if it is inactive. You always need to see at a glance how long a document is and where you are in that document. So there should be no fading at all.
[/LIST]

---

### Post by seeker5528 on 2011-04-09
> **r-senior said:**
> Admittedly it is very narrow, which needs to be tempered with an accessibility option, but I don't think the fundamental principle has disappeared has it?

Accessibility isn't the issue. It's the difference between....

Mouse over the window....

[img]http://home.comcast.net/~seeker5528/Screenshot-Scrollbars1.png[/img]

Mouse not over the window.....

[img]http://home.comcast.net/~seeker5528/Screenshot-Scrollbars2.png[/img]

Personally I don't have too difficult of a time with that as it is in these screenshots, where the background is white, but it's not great either, but in the list view with alternating white and gray lines, not so easy. So depending on the colors of the theme versus the color of whatever happens to be behind the scroll indicator, visibility when the mouse cursor is not in an area that causes the scroll indicator to light up ranges from 'not so good' to 'impossible to see'.

Which is not *all* about width, it's also due to the fact that the overlayed scroll indicator area sits inside the window boarder, hanging out over the top of the window contents potentially allowing it to disappear in the contents of the window, even if the scroll indicator is in it's lit up state. 

Later, Seeker

---

### Post by mc4man on 2011-04-10
> **hugmenot said:**
> The problem is twofold 

[LIST=1]
[*]The fading doesn&#8217;t react to the keyboard, onyl to mouse hover events
[*] You need to see where a window is scrolled even if it is inactive. You always need to see at a glance how long a document is and where you are in that document. So there should be no fading at all.
[/LIST]
I also see a 3rd issue with the active window - if not using the thumb to scroll then the current behavior is fade on scroll, (about 1 sec).
A slight hassle w/ a mouse/scrollwhell, very inconvenient w/ a touchpad/scroll area

Edit: it turns out the above behavior - fade on scroll is only if desktop based viewport switching is enabled, affects very few
There are a few senarios that can temp cause it, no big deal.

Reedit - a recent rev (250), has fixed all possible instances where the pager will fade when scrolling, inc. allowing it to remain visible when scrolling on an unfocused window. - hopefully will be in the 0ubuntu3 release

---

### Post by Bufke on 2011-04-13
It doesn't seem possible to middle click to scroll instantly with this. This is a problem for anyone with a lot to scroll through and a vague idea of where they want to go. Personally this is the only way I interact with scroll bars, everything else can be done via keyboard.

Could a middle click in the nothingness above or below the overlay scrollbar be made to scroll there instantly?

---

### Post by lucazade on 2011-04-13
> **Bufke said:**
> It doesn't seem possible to middle click to scroll instantly with this. This is a problem for anyone with a lot to scroll through and a vague idea of where they want to go. Personally this is the only way I interact with scroll bars, everything else can be done via keyboard.

Could a middle click in the nothingness above or below the overlay scrollbar be made to scroll there instantly?

Agree with you, middle click on scrollbar is a must.
Have you checked if there is an open bug report ?

---

### Post by Bufke on 2011-04-13
Doesn't seem to be. I just [reported it here]("https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/760226").

---

### Post by cometdog on 2011-04-16
I can't afford to test this right now on my work laptop, but I wonder if anyone with this installed could comment.

I'm concerned about a potential problem with a specific scenario with multiple monitors, which is a frequent occurrence when hooking up a laptop to a projector.

Imagine the internal display at some high resolution (1600x1200 or 1920x1200) and a desktop which is extended to the right over an external display at 800x600 or 1024x768.  What happens when you move a window against the right side of the internal display and try to scroll it?

1. Does the scroll thumb appear on the external display / projector, or does it know to switch to overlaying on the inside of the window so that it remains on the internal display?
2. If it ends up on the external display, what happens when it goes beyond the vertical display limit of the external display?  Can you keep scrolling, but you simply end up with a scroll thumb that you can't see or find easily once you let go of it?
3. Does this behavior change depending on Metacity / Compiz or with display driver?

---

