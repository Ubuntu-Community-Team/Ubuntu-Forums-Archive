---
title: "Bait and Switch"
date: 2009-11-18
forum: Multimedia Software
---

### Post by DeadlyOats on 2009-11-18
Hello, all!

The "[COLOR="Red"]Sticky:   [all variants]   Comprehensive Multimedia & Video Howto[/COLOR]"  ([http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")) does not seem to apply to ver. 9.10.  It seems the stuff written there all says "Jaunty" which is ver. 9.04, and does not say "Karmic" which is ver. 9.10.

I looked at "gksudo gedit /etc/apt/sources.list", and there is nothing but Karmic stuff in there, and it all points to multiverse, not medibuntu.

If I replaced each word, "Jaunty", with the word, "Karmic", and each word, "medibuntu", with the word, "multiverse", will that work to install all of the codecs, and packages needed to have the full range of multimedia running in Karmic, or is there more to it than that?  I'm talking about editing the instructions that were written for Jaunty, to make it work for Karmic in that howto.

---

### Post by wilee-nilee on 2009-11-18
Basically you don't want to rewrite the apt/sources list. If you want all media possibilities install the Ubuntu restricted extras in synaptic. type w32 in the search in synaptic and tick the non free codes then check if you have libdvdvdcss2 in synaptic. You can also install vlc and smplayer for more media coverage.

I assume your using Ubuntu if it's xubuntu or kubuntu use those restricted extras. The restricted extras I believe adds the medibuntu but you should post the apt source list so people can see what you have on and off.

Here is a link to load medibuntu to your apt list and set the key.
[http://digitizor.com/2009/10/26/install-useful-software-codecs-ubuntu-karmic-medibuntu-repository/](http://digitizor.com/2009/10/26/install-useful-software-codecs-ubuntu-karmic-medibuntu-repository/)

---

### Post by DeadlyOats on 2009-11-18
Thank you for your reply.  I'll get to work and let you all know how it all turned out.

---

### Post by DeadlyOats on 2009-11-19
I apologize for double posting, but I wanted to give an update to anyone that may have been following this thread.

I opened synaptic package manager and, after entering my password, clicked on settings, and then clicked on repositories.  In the software sources dialog box, I clicked on the other software tab, and there I confirmed that medibuntu - Ubuntu 9.10 "Karmic Koala" repositories was installed and selected.

I don't know if that is by default, or if it's because I copied and pasted the first instructions in the "[COLOR="Red"]Sticky: [all variants] Comprehensive Multimedia & Video Howto[/COLOR]" [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683"), which describes how to install medibuntu repositories (it's the very first instructions).  I did that before I posted for help, because I did not realize that the sticky did not cover ver. 9.10 "Karmic".

So, it may be that if medibuntu repositories were not installed by default, then perhaps following that first instruction added those repositories to my software sources.

Next, I searched for and installed the codecs and other stuff that wilee-nilee talked about.  Typing w32 in the search box brought up w32codecs, which I selected and installed.  Typing 'restricted', brought up the restricted extras, which I selected and installed.  Typing 'libdvd' brought up a bunch of stuff, but I was able to locate, select and install libdvdcss2.  Then I typed 'vlc' and 'smplayer', I selected and installed them.

I did each search and install separately, not all at once in one big install.  Synaptic automatically selected dependencies and installed them too.  When it was all done.  I rebooted.  It wasn't required, but I did it anyway - just in case.

Everything works perfectly.  I see that smplayer really brings mplayer to being a very user friendly and feature-rific media player.  It now rivals vlc in usability, stability, and a couple of other ility's to boot.  The improvements on vlc are also quite refreshing as well.  Firefox was a champion, with all of its plugins installed and perfectly running.  I was able to watch streaming video from youtube.com and animeseed.com (favorite site for streaming anime) with excellent video and audio quality.

In otherwords.  Thanks, wilee-nilee, your advice hit the spot.

P.S.  I listed the stuff I installed in the order I actually did them.  I don't know if that has any bearing on anything, but I thought, I'd point it out.

---

