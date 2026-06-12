---
title: "Remote screen usage with Mythfrontend"
date: 2007-10-23
forum: Mythbuntu
---

### Post by mungewell on 2007-10-23
Hi,
Been playing around with Xinerama and VNC module in an attempt to build a system which would allow for a remote screen/PDA to control an instance of MythTV via VNC over wireless networking. Think of this as a funky touch screen remote control.

Mythbuntu can viewed over VNC, but when a video is played the screen blanks out as mplayer is attempting to display video. If you use '-vo x11' the video is seen over VNC but the frame rate is bad.

I would actually not like any motion video displayed on the remote, only on the main display. With the remote only displaying the mythfrontend screens to enable navigation, I see a future where the playing/position of the active video can be control via the page in mythfrontend on the remote.

Q. Does anyone know of a way that I can get mythfrontend to display/duplicate the UI on multiple screens, but only display video on the main screen?

The option in the 'setup/appearance' allows screens 0, 1, or All. Where 'All' is actually spanned across 0 and 1, ie a very wide screen. I would like 'Each' option, where the screen is duplicated on each Xinerama screen.

[I also noted that the entry in the database for the 'All' setting is '-1'.]

Cheers,
Simon.

---

### Post by mungewell on 2007-10-24
I possibly have a lead in this case.

TightVNC (windows version) lets you select a specific window (or area of the screen) to export, there is a old (May 2006) project called SharedAppVnc which allows the same thing.

[http://shared-app-vnc.sourceforge.net/](http://shared-app-vnc.sourceforge.net/)

It's basically (yet another) Xvnc server with a small application which enables to selection of the item to share. It can set sharing to either whole screen, single application window, or turn it off.

Unfortunately my build-foo wasn't good enough to get it working under Ubuntu Gutsy, any takers?

Simon

---

