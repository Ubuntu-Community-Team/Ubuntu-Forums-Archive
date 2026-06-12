---
title: "How: Nautilus/Nemo Action or Gnome/KDE Open With Command to Burn Selected ISO to DVD?"
date: 2013-12-22
forum: Multimedia Software
---

### Post by OzzyFrank on 2013-12-22
Hi. I'm wanting to either create an "**Open With**" option (in Gnome and KDE) or a Nautilus (or preferably Nemo) ***Action*** to **burn a selected ISO disc image** using the command-line. For me, the default option in Nautilus to burn with Brasero hasn't worked in the last few years, but the "Write to Disc" Brasero extension near the bottom of the context menu has been fine. However, due to the dedicated efforts of the Nautilus team to keep losing users (now in 13.10 it's auto-open folders on hover??), I've finally given up and gone to Nemo - and unfortunately Nemo does not share this extension.

I've successfully created some Actions for things I used to be able to do in Nautilus (till they dumped "Open With" for folders), like open the selected folder in Image Viewer, so was wondering if there was a way to make one using the **growisofs** command (or any other that works). I know a command like **growisofs -dvd-compat -Z /dev/sg1=disc.iso** will burn an ISO image, but obviously you need to specify the ISO's name each time. So what kind of option can I use to supply the file name from that which is selected? (Obviously, I don't need to actually make an Action for Nautilus, because that extension works fine if I was still happy using Nautilus, but if someone knows how to do this, I should be able to nut out how to make it work in Nemo).

And besides making a usable Nautilus and/or Nemo Action, can I do this for a custom "Open With" command, in both Gnome and KDE? (I've been using the latter since upgrading to 13.10, as all my Gnome Classic settings were wiped, and Nautilus became unusable - so, preferably for KDE, as I could then make it work with Dolphin too). Also, in case it matters, often I would be using this for a rewritable disc, so if there is any difference between burning to those and normal blank write-once discs, I'd like to know both methods. Many thanks in advance.

---

