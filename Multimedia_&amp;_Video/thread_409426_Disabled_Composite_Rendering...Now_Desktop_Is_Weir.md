---
title: "Disabled Composite Rendering...Now Desktop Is Weird!"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by Extrapolation on 2007-04-14
Help!

I recently updated my drivers with a new ATI X1650 card, using Envy.  It all worked great as far as installation, and I booted into Gnome, but now I'm having bizarre display problems.  They ONLY happen when I disable composite rendering.

Windows do not refresh.  When I scroll down, only a few horizontal "bars" change.  I literally had to guess where the text box was in this form.  I continually have to highlight and scroll down, because just scrolling down, in any window, produces this problem.  It's like the display is refusing to refresh!

As soon as I remove the Composite Rendering section from my xorg.conf, it's fine again, but I have no 3D acceleration.  Please help!  I'm seriously handicapped here!

---

### Post by Extrapolation on 2007-04-14
Come on; could someone please help?!  This is the second thread I've posted about this, and no one has any advice at all.  I've usually had good responses from the forums, but I'm really getting frustrated here.

---

### Post by FlatulentFox on 2007-04-19
I just found out a possible solution from another thread.  The trick is to change your "AGP Aperture" size to something above 64MB.  Everything in the guides works fine, even the Composite Rendering part.  I was having the same problem as you: when I would drag a window, or scroll down in a window, it would get all jarbled up; as if it wasn't refreshing.  

To change your "AGP Aperture" size, you have to get into your bios (usually by pressing the DEL key on startup) and try and find the option where you can change the AGP aperature amount.  Mine was set at 64MB, and when I changed it to 256MB, all those problems dissappeared!!!  I really hope this works for you; I know how frustrating it can be trying to work on a desktop that doesn't refresh itself!!!

---

