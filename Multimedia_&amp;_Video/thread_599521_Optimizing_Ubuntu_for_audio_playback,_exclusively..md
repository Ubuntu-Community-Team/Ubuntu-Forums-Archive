---
title: "Optimizing Ubuntu for audio playback, exclusively."
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by Mojo McCracken on 2007-11-01
I am in the middle of transforming an old laptop into a digital jukebox. I have for 6 months just used a basic Ubuntu 7.04 installation, With Rhythmbox as the music manager. In this time i realized that the machine wasn't capable of playing music optimal. It's an old computer and because of that, the output had a tendency to lag.

So, i hooked it up to the internet, updated it, uninstalled a few applications and disabled some background services. At this point the machine seemed to work perfectly, and even capable of using the nice new crossfade feature. I was able to clear about 70% of the available RAM and 80% of the available MHz by disabling *bluetooth*, *klogd*, *sysklogd*, *powernowd*, *anacron*, *atd*, *hotkey-setup*, *cupsys*, *dbus*, and *apport*. Life was sweet.

But, of course, things wasn't supposed to work out. At some point of the testing, disabling, unistalling etc. i probably managed to throw something important out the window. Suddenly it shrieked *"Failed to initialize HAL"*. I have since looked into this and tried to repair it. Nothing worked. It's probably because i disabled *dbus* (?). I tried to re-enable *dbus* to fix it, but suddenly my password didn't seem to work. Anyone knows why? 
Another possibility could be that I disconnected the external audio harddisk during playback. But is that really possible and if so: How do i fix this problem?

Well no harm done. I decided to reinstall Ubuntu and here i am, with a fresh standard version 7.10. I will be delighted to know which applications i can safely uninstall, disable etc. without inhibiting the machine's ability to play music (and just function), flawlessly. (IE: Do i actually need *ubuntu-desktop*? And is *acpid*, *apmd*, *avahi-daemon* and *gdm* required to run?). Is there anything else i can do to optimize playback?

I have a 700 MHz CPU, 128 MB RAM and a standard on-board sound card to fiddle with. The music database is stored in an external harddisk, connected via USB. Not much, but since my testing i am confident that it can be worked out.

Thanks in advance. And thank you for the lovely OS. :)

---

### Post by geoff123 on 2008-03-15
ran across your post.  it's been awhile, but I'll answer anyway.
most of those you uninstalled are okay.  you definitely want to keep dbus and this likely caused your problems. 
you should probably keep anacron and atd also. 
you could probably disable the apmd service, but it could affect your laptop powersaving modes.

you do not need ubuntu-desktop, but it's nice to keep for upgrades and such.   it is a meta-package that keeps track of many other installed programs. 

you could try using a lighter-weight audio player such as xmms?
you could try installing enlightenment and logging into that instead of gnome?

good luck.

---

