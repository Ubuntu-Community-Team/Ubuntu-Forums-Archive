---
title: "Firefox acting flakey, any one else?"
date: 2010-05-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dagrump on 2010-05-21
Firefox no longer has window borders, & it shows up on all desktops. If minimized it won't restore. 
Tried uninstall & deleted .mozilla from /home & reinstalled, no change.
I don't remember any updates to firefox & I doubt I was paying that close of attention.
Any one else seeing this?
********************
Launching from the terminal gives no errors, but the terminal window starts bouncing around the screen. I can't restore my bookmarks, highlight the saved file, hit open, & it opens some random folder in home. 
I have window decorations on everything else I've opened, it seems to be firefox for the windows decorations problem. Although it does cause the issue with the terminal.
I also tried going to an older kernel, still does the same thing.

---

### Post by dagrump on 2010-05-21
Well, if I enable effects & use emerald I have borders, can restore my bookmarks, & it stays on the desktop it was opened on. 
So where to look? I don't use effects normally.
Guess it's early I could always reinstall, but if I do I won't be able use my backed up apt cache as I'd probably just reproduce the issue.
Any one have any shots in the dark to offer.

---

### Post by gnomeuser on 2010-05-21
Could be because client side decorations was just enabled in the gtk package. I know a ton of my applications just started failing on launch.

---

### Post by wilee-nilee on 2010-05-21
I'm not using meerkat yet but I had to remove the Namaroka version it just was full of bugs and just reinstall 3.6.3 in Lucid.

---

### Post by dagrump on 2010-05-21
Well, I guess it will get ironed out shortly then, I just noticed firefox right off the bat. I was sure I hadn't messed with anything lately.
I'll just install my updates for a week or so, & see if it clears up.
I have other installs to play with, trying KDE again. KDE hates me & I don't like it that much but, I'd like to learn to work with it. So I am trying again.

---

### Post by ranch hand on 2010-05-21
I am very happy to read this.  I do not use effects either but it sounds like FF is behaving for you a little better than for me.

For me it flashes on and off and has no buttons for things like shutting down or minimizing.

I too tried, after saving my bookmarks, just purging it and deleting the .mozilla file and reinstalling.

Right now I am on 9.04 but before I came over here in installed epiphany.  It works.

---

### Post by wilee-nilee on 2010-05-21
> **ranch hand said:**
> I am very happy to read this.  I do not use effects either but it sounds like FF is behaving for you a little better than for me.

For me it flashes on and off and has no buttons for things like shutting down or minimizing.

I too tried, after saving my bookmarks, just purging it and deleting the .mozilla file and reinstalling.

Right now I am on 9.04 but before I came over here in installed epiphany.  It works.

I have Jaunty on one of my laptops that has ancient an radeon card, I just purged the Ubuntu FF and installed the FF mozilla 3.6.3 and just added it to the menu, also did the same with thunderbird. Runs great the fonts look fine. Also the xmarks addon is a great one for having your bookmarks linked to all your FF versions on multiple computers. xmarks encrypts up and down but the bookmarks are stored on their system.

---

### Post by dagrump on 2010-05-21
I think I would rather run effects than change browsers, the box has no problem running effects. I just normally turn them off from force of habit.
Back in the dark ages they caused issues with full screen video & some games. Those problems don't seem to raise their ugly heads any more, I guess the hardware has grown past those problems. 
I can always fire up a different box if one goes south on me, if not I wouldn't mess with dev versions. I figure we haven't even reached an alpha release, so why complain. Just wanted to know if I'd broke something, doesn't sound like I did it.
I got time, they'll get it straightened out, I have faith.

---

### Post by jppr on 2010-05-22
> **dagrump said:**
> Firefox no longer has window borders, & it shows up on all desktops. If minimized it won't restore. 
Tried uninstall & deleted .mozilla from /home & reinstalled, no change.
I don't remember any updates to firefox & I doubt I was paying that close of attention.
Any one else seeing this?
********************
Launching from the terminal gives no errors, but the terminal window starts bouncing around the screen. I can't restore my bookmarks, highlight the saved file, hit open, & it opens some random folder in home. 
I have window decorations on everything else I've opened, it seems to be firefox for the windows decorations problem. Although it does cause the issue with the terminal.
I also tried going to an older kernel, still does the same thing.

Same here... Downgrade libgtk2.0-0 to 2.20.0-0ubuntu4, 2.21.0-1ubuntu2 break window borders.

---

### Post by LKjell on 2010-05-22
> **gnomeuser said:**
> Could be because client side decorations was just enabled in the gtk package. I know a ton of my applications just started failing on launch.

I read the changelog and felt something fishy with gtk2-engines-pixbuf. Removed the patch and is compiling right now..

---

### Post by chrisccoulson on 2010-05-23
> **gnomeuser said:**
> Could be because client side decorations was just enabled in the gtk package. I know a ton of my applications just started failing on launch.

You're right, this is related to client-side decorations, which I will be disabling in firefox at some point this week

---

### Post by gnomeuser on 2010-05-23
> **chrisccoulson said:**
> You're right, this is related to client-side decorations, which I will be disabling in firefox at some point this week

What will we be using csd for?

---

### Post by bladerunner6 on 2010-05-25
ppa:portis25/ia32libs


this ppa fixes the issue for me

---

### Post by ChrisB111 on 2010-06-10
On my system is just does not display, the window appears in the window list but the browser is just not there! I am running gnome shell also by the way.

Chris

---

### Post by Jordanwb on 2010-06-10
I haven't had any issues on 10.10 besides my video card and mtpfs (I finally got that udev rule working).

---

