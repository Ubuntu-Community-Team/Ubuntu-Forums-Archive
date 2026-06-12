---
title: "I've botched it up royally (plus some other questions)"
date: 2008-12-29
forum: Multimedia Software
---

### Post by jharadie on 2008-12-29
I've made a mess of things: at this point I can't get Totem, VLC or MPlayer to play anything at all.  Given I still am pretty much a noob, it's probably easier for me to wipe and reinstall and get it right.  Not really sure what I did to mess things up, but don't want to mess up again.

I'm looking for links, HOWTOs, suggestions and comments.

What I have: Hardware: Microtel/ASUS Intel Celeron 2.8G CPU, 2G RAM, 320G HD, vid is on the MB, as is sound.  Also have Bttv (bt878) card, generic.  Would like to afford better, but being disabled and low-income has its disadvantages.  Software: Dual-boot XP, Lightweight 8.04 Ubuntu (installed Xubuntu alternate, sudo apt-get install ubuntu-desktop, login GNOME safe-mode, synaptic remove all packages starting with "compiz").  Installed ubuntu-restricted-extras, Totem worked OK for most things at that point.

What I'd like, part 1: a media player that will play just about anything I throw at it (AVI, wmv, flv, mpg, mov, mp4).  What I'd like, part 2: something like xawtv to manually record with the bttv card.  Almost had it working in 7.10, but no sound.  Somebody said something about needing sox?  What I'd like, part 3: a video editor.  I've seen suggestions that Cinelerra is the best, but for installing would like to see a good HOWTO that a noob wouldn't freak out over.

What I'd like part3 can be tossed if it will interfere with part 1.  Same goes for part 2.  Part 1 is the most important.

Other things: I have a good HOWTO for installing VMserver 1.06 and it's working OK.  I see where 1.08 is out, also 2.0.  I understand 2.0 *only* works through the web browser, does that mean I can't activate it and minimize it and forget about it?  I use it mainly for a separate XP that runs PhoneTray, since there seems to be no equivalent in Linux (yet).

Lastly, a HOWTO to get sendmail to use my ISP (Comcast) for outbound email.  Please don't suggest Postfix, I want to install Hylafax, and haven't found a way to tell it to use anything other than sendmail.  If there is another way, I'd gladly use it.  However, Hylafax is low priority, can be easily scratched from my wish list.

I know this is a lot to ask, but Ubuntu has really rocked my world and when I can video events (it's not as hard as one would think from a wheelchair), it beats the heck out of watching "The View" or "Jerry Springer." (grin)  If I could get xawtv and cinelerra to work, and if I could find an equivalent to Phonetray (have seen a few things, especially something about PBX, but they're just not equivalent enough), and a program to print my checks (I write so few that paying $20 is a waste), I'd dump expee completely.

Any and all suggestions, links, HOWTOs and comments are welcome.  Thanks.

---

### Post by balaknair on 2008-12-29
Pretty much all I could think of to fix media playback is already in the how-to by ubuntu-freak.

Just some stuff I think you might find helpful-

**TVTuner:**
Are you looking for something like this?
[http://ubuntuforums.org/showthread.php?t=908421](http://ubuntuforums.org/showthread.php?t=908421)
[http://davidwinter.me.uk/articles/2008/02/10/me-tv-eyetv-for-ubuntu/](http://davidwinter.me.uk/articles/2008/02/10/me-tv-eyetv-for-ubuntu/)

**Cinelerra:**
[http://www.ubuntu-unleashed.com/2008/05/howto-install-cinerella-video-editor.html](http://www.ubuntu-unleashed.com/2008/05/howto-install-cinerella-video-editor.html)

Maybe you should also consider **Mythbuntu**
[http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)
---------------------------------------------------------------------------

**Sendmail:**
[http://rimuhosting.com/support/settingupemail.jsp?mta=sendmail](http://rimuhosting.com/support/settingupemail.jsp?mta=sendmail) 

Instead of Sendmail, give Exim a try
[http://newbiedoc.sourceforge.net/networking/exim.html](http://newbiedoc.sourceforge.net/networking/exim.html)


Hope you find this helpful.
All the best.

---

