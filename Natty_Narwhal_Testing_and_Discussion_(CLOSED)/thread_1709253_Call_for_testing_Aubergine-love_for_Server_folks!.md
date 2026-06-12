---
title: "Call for testing: Aubergine-love for Server folks!"
date: 2011-03-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-03-17
Here's another call for testing from Dustin Kirkland:

> Howdy Ubuntu-devel and Ubuntu-server,

We just uploaded a couple of small patches a week ahead of
UserInterfaceFreeze to five packages that affect the console tty and
vt interface.  We're hoping you can help test this on your hardware
and let us know if you find any adverse affects (please subscribe me
to the bug reports, if you do!) :-)

The end goals were (Bug #730672):
 1) Improve the virtual terminal color palette
 2) Modernize the visual experience on Ubuntu servers

To solve (1), we wrote a small C program that you should now find in
/sbin/setvtrgb.  You can refer to the manpage for the full
documentation.  It's a handy utility that reads a set of well-formed
RGB values from file and then uses an ioctl to dynamically apply them
to all consoles.  This utility is currently provided in the kbd
package, and I'm working on getting that upstream into Debian.

The default colors used by the Linux kernel are quite simply the
traditional 16 VGA colors, which you can find at:
 * [http://en.wikipedia.org/wiki/ANSI_escape_code#Colors](http://en.wikipedia.org/wiki/ANSI_escape_code#Colors)

While perhaps mathematically symmetric, some of those colors are a
pretty hard on the eyes.  The Ubuntu Design Team has put quite a bit
of effort into selecting a distinctive color scheme for the Ubuntu
Desktop, and they have now carefully selected an 16 color palette for
server consoles too!

So the next three pieces of (1) are solved by a series of uploads to:
 * console-setup -- add a conffile at /etc/vtrgb (so that you can
customize your own console colors, if you don't like the ones Ubuntu
provides!), and an upstart job that applies them on boot with
'setvtrgb /etc/vtrgb'
 * rootskel -- call 'setvtrgb /etc/vtrgb' early in the Server and
Alternate installer for its virtual terminals
 * bogl -- update the colors in the bterm palette used by
debian-installer (it happens to hard code them)

After upgrading your local system's kbd and console-setup packages,
you should now have a crisp, new, clean color scheme in your tty.
There should be no affect whatsoever in [X, Gnome, KDE, XFCE,
gnome-terminal, konsole] or even SSH sessions to your server.
However, if you drop to a command prompt with ctrl-alt-F1, you should
see a nice difference.  Note that if for some reason perhaps you
prefer the legacy VGA colors, you can revert the change simply with:
 $ sudo setvtrgb vga
And if you want to make that permanent, follow with:
 $ cat /sys/module/vt/parameters/default_{red,grn,blu} | sudo tee /etc/vtrgb

And as soon as the daily cdimage builder picks up the changes to
rootskel and bogl (within a day or two?), you should see the same
color improvements in the Natty Server and Alternate installer
screens.

Now to address (2), we've made one minor change to the newt library,
which defines the color scheme for most curses-based utilities -- most
importantly, debconf and in turn, the debian-installer.  If you've
ever installed an Ubuntu server, and in staring at the screen thought,
"That blue sure looks a lot like MS-DOS circa 1988," we're right there
with you.  So we've swapped that aged "Microsoft blue" out for some
modern "Ubuntu aubergine"!

So what does all of this look like?  Here are some screen shots!
 * On the console
  * before: [http://bit.ly/fvm16s](http://bit.ly/fvm16s)
  * after: [http://bit.ly/dRF9yi](http://bit.ly/dRF9yi)
 * And in the installer
  * msdos6: [http://bit.ly/gyQgJL](http://bit.ly/gyQgJL)
  * before: [http://bit.ly/i1cc5Q](http://bit.ly/i1cc5Q)
  * after: [http://bit.ly/hRLDDI](http://bit.ly/hRLDDI)

Spiffy, huh?  Thanks to everyone who help spread some Aubergine-love
to Ubuntu Server folks!

Enjoy,
-- :-Dustin 

---

### Post by ikt on 2011-03-18
I noticed this has been included in the main desktop updates, looks so good, well done :)

---

### Post by VMC on 2011-03-18
Wow, it does look great! I thought I needed to do something, and probably do, but just opening a VT and listing files/folders are now in living color! Great job.

---

### Post by RJ12 on 2011-04-17
> **ikt said:**
> I noticed this has been included in the main desktop updates, looks so good, well done :)

You can use this on the desktop?

---

### Post by ikt on 2011-04-17
> **RJ12 said:**
> You can use this on the desktop?

seems so, the colours are a lot more vibrant, very noticeable.

---

### Post by RJ12 on 2011-04-17
> **ikt said:**
> seems so, the colours are a lot more vibrant, very noticeable.

How do I activate it :)?

---

### Post by ikt on 2011-04-18
> **RJ12 said:**
> How do I activate it :)?

Reboot into the recovery console. (hold shift on bootup)

And now I realise that the new colours are only activated in recovery mode not in the desktop.

---

### Post by Rasa1111 on 2011-04-18
Looks very nice for sure!
Nice work! <3

---

