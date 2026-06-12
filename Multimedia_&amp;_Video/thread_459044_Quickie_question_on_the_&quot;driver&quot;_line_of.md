---
title: "Quickie question on the &quot;driver&quot; line of xorg.conf"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by baconstrip on 2007-05-30
Well I'm currently in the process of trying to figure out how to get my dual screens working with a Nvidia card -and- an ATI card.  My current plan is to use each card separately as the main card and copy the xorg.conf's to merge them together.

So Ill backup my current xorg.conf on the nvidia card (which is using the latest nvidia driver), and then I'll boot up from the ATI PCI card, use "dkpg -reconfigure xserver-xorg" line to set up the ATI card and install the ATI driver once I get booted into X.   My question is, is the "driver" line under device the sole thing that controls which driver my card is using?   

For instance, after I get the xorg.conf from the setup ATI card,   and I want to revert back to my nvidia card using the nvidia driver to start setting things up... all I have to do is put the proper device and driver "nvidia" back into the xorg.conf?  The actual driver information will stay installed and Ill essentially have both the nvidia and ati driver installed and useable via the "DRIVER" line, right?

Thanks for any help guys.. trying to get the dual screens set up has been a big lesson in editing xorg.conf.. and I have mucho  more to learn :)  Im hoping I can figure this out as I cannot use an OS on my mainbox without the dual widescreen LCD's (once you have them, it's incredibly hard to go back to just one!)

---

### Post by kidders on 2007-05-31
Hi there,

xorg.conf can be finicky and irritating ... but I doubt I need to tell *you* that! Basically, I'm not sure your plan of "merging" two xorg.conf files will necessarily work out as cleanly as you might think.

The short answer to your question is yes ... the "Driver" directive is pretty much the only thing that dictates what driver gets used. There are however additional directives that control things like which device gets which driver.

If I were you, I would regard auto-generated xorg.confs as guides, rather than finished products, and experiment with creating my own xorg.conf from scratch, with a little help from the man pages. Some suggestions...[LIST]
[*]Try not to put anything into xorg.conf that you don't quite understand, and keep unnecessary stuff to a minimum (eg unused input devices).
[*]Start with something unambitious & ugly (ie low resolutions, colour depths, etc.), being careful to use things like PCI IDs to ensure that the correct driver gets applied to the appropriate card.
[*]Take a look at some of the xorg.conf directives that control how multiple monitors are managed, bearing in mind that inconsistency between what your BIOS & X each consider your "primary" monitor can sometimes cause trouble.
[*]Don't forget that you can start X without starting any display manager (eg kdm, gdm), for the sake of a quick test. In my experience, tweaking xorg.conf requires an awful lot of starting and restarting (CTRL+ALT+Backspace), which gets boring very quickly!
[*]X's system logs are also very handy for identifying problems.[/LIST]Then, once you have the basics right, and X starts up reliably, you can look into hardware-specific optimisations, so both your cards end up using exactly the right sets of options, and both your cards work as optimally as possible.

Thankfully, you'll only ever have to get xorg.conf right once. Barring any major developments, the same file should work pretty much indefinitely, on any version of Linux you ever install on your computer. :-)

With luck, there's something here that you didn't know already!

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

