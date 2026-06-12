---
title: "My only real problem w/ Unity: It destroys my focus-follows-mouse kung fu"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by msp3k on 2011-04-08
There is only one really important thing that will stop me from using Unity:
It completely destroys my focus-follows-mouse workflow that I have relied on
for increased speed and productivity since the early 1990's:

[IMG]http://i.imgur.com/8qKXQ.png[/IMG]

A typical situation: I have two (and often many more) windows open on the
desktop. Window A is on the top, partially obscuring window B. I read from
window A while typing in window B. A typical example: Following a set of
instructions that involve typing in a series of commands in the terminal.

[IMG]http://i.imgur.com/9w9JF.png[/IMG]

(Yeah, yeah, I know. That find command is going to fail when I press RETURN.
Please keep in mind that this is only an example, you nitpickers out there!)

As you can see in this example, with the mouse in the Firefox window, Firefox
has the focus, and the global menu now shows the application menu for Firefox.
Let's say that I want to use 'File' > 'Open...' in Firefox...

[IMG]http://i.imgur.com/rGHVE.png[/IMG]

...So I begin to move my mouse from the Firefox window up toward the global
menu. But wait! As soon as my mouse touches the terminal window, the global
menu changes!

[IMG]http://i.imgur.com/i9VqF.png[/IMG]

Now when I click on File, what I get is not Firefox's File menu, but
Terminal's File menu!

[IMG]http://i.imgur.com/VIlQM.png[/IMG]

I have lost count on the number of times that I have accidentally
done the wrong thing in the wrong application amidst the heat of my 
daily battles against the forces of evil.  While a global menu works great if 
you use a click-to-focus workflow, it's disastrous for 
a focus-follows-mouse workflow.

I understand the desire to save some screen real estate by consolidating the
application menus to a shared space at the top of the screen, but the ability
to overlap windows and focus on one that is partially obscured ALSO saves
screen space; and I might argue: if the goal is to save screen space, a
focus-follows-mouse workflow with overlapping windows can save you a lot more
space than simply a global menu can!

This is serious enough that I have already decided that unless Unity includes
an option to turn off the global menu, I will find another desktop program.

There have been several posts online about how to disable Unity's global menu.
Since there is no settings option, all of these solutions involve a terminal
and root privileges:

1) Edit /etc/X11/Xsession.d/80appmenu, and comment out the line that reads
"export UBUNTU_MENUPROXY=...".

2) Another option is to create an extra file in /etc/X11/Xsession.d/, with a
number greater than 80 (ex: 81disableappmenu), that contains the single line:
"export UBUNTU_MENUPROXY=", with no value following the equals sign.  This
effectively wipes out the environment variable value set in 80appmenu.

The problem with both of the above approaches is that it does not work for ALL
programs.  While this will result in some programs getting their application
menus back, it doesn't seem to work for all applications.

[IMG]http://i.imgur.com/ovIkI.png[/IMG]

The best solution that I have found so far is this:

3) cd /usr/lib/indicators/5 ; mv libappmenu.so libappmenu.so.old

This removes the library file libappmenu.so from commission all together.
This will result in ALL applications getting their menus back, restoring
zen-like peace to us focus-follows-mouse workers around the globe.

DEAR CANONICAL: *PLEASE* include an option to TURN OFF the global menus!
Restore my workflow zen!



There is only one more gripe that I have concerning Unity, and it's a minor
one that should be easy to fix.  I often begin a task by starting multiple
applications at once.  For example: A terminal window, my email client, and a
web browser being the bare minimum that I need to even begin to be productive.
So here goes: I have stuck the Terminal application icon to the Launcher, so
I'll click it first...

[IMG]http://i.imgur.com/KLY4V.png[/IMG]

...And up comes the terminal.  But wait!  Where did the Launcher go?  It's
auto-hidden itself so as not to conflict with the Terminal for screen space.
That's nice, except if the default location of a new application were just a
few scant pixels over to the right, then I would still be able to quickly and
easily start the other applications that I need.

[IMG]http://i.imgur.com/7KMrI.jpg[/IMG]

Like I said, a minor issue, and one that should be easily fixed.  But
Canonical, there are a few tweaks you could make that would make my workflow
go faster:

1) The auto-hide feature is nice, but an auto-unhide feature, triggered
perhaps by my mouse hitting the left edge of the screen, would also be nice.

2) The ability to disable auto-hide would also be nice.

My only other gripe about Unity is that Canonical has removed my ability to
add apps and launchers to the top panel.  I can now create a launcher on the
desktop.  That's nice.  But the whole point of putting launchers and
applications on a panel is that they are always available, regardless of how
many windows I may have open and cluttering up my screen.

---

### Post by mc4man on 2011-04-08
As far as your autohide issues - 
the bumping ot the launcher while using the dodge mode (default) was fixed in latest unity updates - it should not be happening anymore (was not accounting for window border

You can change launcher modes (4 avail.),  in ccsm > unity (install compizconfig-settings-manager) or in gconf-editor - see screen
0 = never
1 = autohide
2 = dodge
3 = dodge active

---

### Post by ronacc on 2011-04-08
wheres the one that makes the launcher go away and NEVER EVER appear ?

---

### Post by castrojo on 2011-04-08
You can remove the indicator-appmenu package to remove the global menu without having to go in there and move libraries around.

---

### Post by msp3k on 2011-04-08
Excellent!  You guys have come to my rescue!  I can finally make peace with the new interface direction that Ubuntu is taking.  A PERFECT example of why I love Linux and the Linux community!

---

### Post by HuoMaKe on 2011-04-08
> **ronacc said:**
> wheres the one that makes the launcher go away and NEVER EVER appear ?

[Right here.]("http://gnome3.org")

---

### Post by ronparent on 2011-04-08
Pmsp3k I understand your pain. Arrange that crowd over two screens and the problems are compounded. I will probably never get comfortable with unity but it may appeal to the many who try to keep things simple. Meanwhile, good presentation of the problem for some of us.:popcorn:

---

### Post by msp3k on 2011-04-08
> **mc4man said:**
> As far as your autohide issues - 
the bumping ot the launcher while using the dodge mode (default) was fixed in latest unity updates - it should not be happening anymore (was not accounting for window border

You can change launcher modes (4 avail.),  in ccsm > unity (install compizconfig-settings-manager) or in gconf-editor - see screen
0 = never
1 = autohide
2 = dodge
3 = dodge active

For anyone wanting to know the command-line for this:

```
gconftool-2 --type int --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode X
```

Where X is one of the integer values above.

---

### Post by mpt on 2011-04-08
> **msp3k said:**
> I have lost count on the number of times that I have accidentally
done the wrong thing in the wrong application amidst the heat of my 
daily battles against the forces of evil.  While a global menu works great if 
you use a click-to-focus workflow, it's disastrous for 
a focus-follows-mouse workflow.

When designing the menu bar, I specified how someone could [make it compatible with focus-follows-mouse]("https://wiki.ubuntu.com/MenuBar#focus-follows-mouse"), if they were interested. But nobody has been interested enough to implement it yet.

---

### Post by DennyF on 2011-04-08
It destroys my focus, too which is the point I was trying to make in the post "If it ain't broke, don't fix it." All this discussion really re-enforces that. I finally gave up on the sidebar by turning off Unity in the CCSM and installing Cairo Dock. However, because of some bug in either the Beta or Cairo-dock, the workspace panel has disappeared and every time I try to turn it back on in Cairo-dock, it generates an error. I don't know if that's CD's fault or in this Beta. i use the workspaces a lot and find it the quickest way to get from one ap to another, considering all the multi-tasking i do as a writer/publisher. All I know is, what I had before worked really well, was very fast and suited my work flow. I think the switch to Unity is a regression and for those who would argue "well, why did you install this 11.04 in the first-place" I would only reply that I was looking to upgrade my Linux core system. Perhaps that was a mistake and I'll have to drop back to 10.10. Meanwhile, I'll at least give this a shot and see it through to it's final release at the end of the month.
Hope you get things working for you.

---

### Post by r-senior on 2011-04-08
> **mpt said:**
> When designing the menu bar, I specified how someone could [make it compatible with focus-follows-mouse]("https://wiki.ubuntu.com/MenuBar#focus-follows-mouse"), if they were interested. But nobody has been interested enough to implement it yet.
Is there a bug/issue we can subscribe to? 

I'm a die-hard focus-follows-mouser and much prefer that idiom. In fact I see it as a defining feature of X-based desktops. But with the global menu I've had to resort to what I see as a Windows 95 click-on-the-panel-or-window-to-focus mentality.

---

### Post by daengbo on 2011-04-08
I know that this doesn't really solve your problem, but I've always used "Always on Top" when in this situation. In Natty, you right-click the application's window decoration.

---

### Post by lckarssen on 2011-04-15
> **r-senior said:**
> Is there a bug/issue we can subscribe to? 

I'm a die-hard focus-follows-mouser and much prefer that idiom.

Me too!
The bug report can be found [here on launchpad](https://bugs.launchpad.net/unity/+bug/674138).

---

