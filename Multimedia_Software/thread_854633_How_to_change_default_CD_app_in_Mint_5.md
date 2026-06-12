---
title: "How to change default CD app in Mint 5?"
date: 2008-07-09
forum: Multimedia Software
---

### Post by iceportal on 2008-07-09
Hey everyone. I'm using Linux Mint 5 (Elyssa) and when I pop in an audio CD it automatically starts Rhythmbox to play/rip/whatever.

Personally, I prefer Amarok, but I'd actually prefer that it start sound-juicer instead.

I've tried using Preferences->Preferred Applications, and I've tried using Preferences->Removable Drives and Media, but neither work. In Preferred Applications, no matter what I change the multimedia settings to, it still opens Rhythmbox. It completely ignores my preferences. And in the Removable Drives and Media system, there's no entry for multimedia or CD drives.

I've searched all over the internet trying to find a solution to this, and I'm stuck.

Can anyone here help me? How do I change my preferred CD player to sound-juicer in Linux Mint 5 (Elyssa)?

---

### Post by awshidahak on 2008-08-30
From your message it sounds like you don't care to use Rhythmbox at all (same way i feel).  I had the same issue for quite a while on my mint5 machine and if you don't care to have Rhythmbox, this solution should work.

To install Sound Juicer:

1. Click Elyssa > Software Portal
2. Click APT
3. In the box type: sound-juicer
4. Click install and click install again at next box
5. Once you get the success box click close.
6. Click Ok.
7. Close mintInstall

To set as Sound Juicer as the default for CD:

1. Click Elyssa > Preferences > Preferred applications
2. Click Multimedia
3. Select Custom from the list
4. In the command box type: sound-juicer
5. Click close

now

1. Click Elyssa > Sound & Video
2. Right Click Rhythmbox and select uninstall
3. Follow the prompts to remove Rhythmbox

i hope this works.  If anyone (with Mint 5) has a solution that doesn't involve removing rhythmbox, please let me know.  I'm dying of curiosity.

---

