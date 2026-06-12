---
title: "Bizzare problems with video card/GUI"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by chejrw on 2007-06-20
I just picked up a machine from a garage sale that I intended to use as a fileserver.  It had WinME on it (shudder) on a whopping 8 GB hard drive, so I just pulled that out, plopped in a 120 GB drive I had in a drawer and installed Feisty on it.  It worked beutifully on the live session, so I expected no problems.  However, when I rebooted to get out of the live session and start normally, things started going wrong.

OK.  It starts to boot normally (Black Ubuntu splash screen w/orange progress bar.)  No problems here.  After that disappears, I am expecting the login screen.  I am greeted with this:

[IMG]http://i206.photobucket.com/albums/bb161/chejrw/IMG_0216.jpg[/IMG]

It stays like that for a good... 4 minutes or so.  Then finally loads the login screen.

[IMG]http://i206.photobucket.com/albums/bb161/chejrw/IMG_0217.jpg[/IMG]

A little weird, I though, but whatever.  I log in.  After entering my password, the screen doesn't change.  The black circles in the password field turn grey, and the screen just stays like that.  After about 5 minutes, the icons that normally appear on the Gnome splashbar (like, for Nautilus and stuff) appear on top of the login screen - not the bar, mind you, just the 3-4 square icons.  (sorry, I didn't get a pic of this).  Shortly thereafter, my monitor goes blank and presents me with the following message:

[IMG]http://i206.photobucket.com/albums/bb161/chejrw/IMG_0218.jpg[/IMG]

I try the usual Ctrl Alt - to resize, but it doesn't do anything (after trying it a few times, I try the capslock key and discover that they computer has, indeed, frozen.)

So I restart the machine, to go to text-only mode.  This time between the loading splash and the login screen, I get a slightly different bizzare screen

[IMG]http://i206.photobucket.com/albums/bb161/chejrw/IMG_0219.jpg[/IMG]

You can sort of see the login with the gnome splash icons superimposed here - it seems that my video card is somehow remembering textures, even between reboots.

Anyway, as I say, it worked flawlessly on the Live session, so I know the hardware can handle Ubuntu, I just need to figure out what the heck to do to get it working.  I tried using the fglrx driver instead of the regular ATI, but that just caused X to crash.  The video card is an ATI Rage 128 (AGP).

Help!

---

