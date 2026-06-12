---
title: "displayconfig-gtk for multi-monitors (2nd is a TV) lost"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by bohsocks on 2007-06-25
Hey guys.  I am very new to Linux.....

I am running the Gutsy pre-release and using displayconfig-gtk to use two monitors, the 2nd being a TV that connects through a box that uses my laptop's VGA out and a composite (yellow) input in the back of my CRT TV.

As everyone always says... this is so easy and straightforward to do in XP.  I had been using several methods to get this to work until I stumbled upon displayconfig-gtk.  Being the n00b I am when it comes to Linux, and also to graphics cards, this seemed pretty painless.

Well I have the utility open, and am trying to get dualhead to work.  I selected Screen 2 to be (brace yourself) my secondary screen, and to extend the desktop to the bottom.  When I go to select the "screen" it gives me a bunch of options.  But it's just a... TV, so I don't know what to pick.  So I pick Generic/Plug n' Play.  When I test it, I get this output from the terminal:

> 
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 933, in on_button_apply_clicked
    self.apply_changes()
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 964, in apply_changes
    if self.xsetup.isLiveResolutionConfigChanged() and \
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 807, in isLiveResolutionConfigChanged
    if screen.isLive() and screen.isResolutionSettingsChanged():
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 2092, in isResolutionSettingsChanged
    current_size = self.getAvailableResolutions()[self.currentsizeindex]
IndexError: list index out of range


And it doesn't work.  When I turn my box (VGA to Composite) on and off, it flickers my screen (exactly the same thing I see on my laptop monitor) for a second then goes to a [test pattern]("http://ubuntuforums.org/attachment.php?attachmentid=36470&stc=1&d=1182822332").  But it was doing this even before I was using displayconfig-gtk, so it has nothing to do with this package I don't think.

Any ideas on how to fix this problem?  This is the one of the few hurdles that keeps me from using Linux full-time.

---

