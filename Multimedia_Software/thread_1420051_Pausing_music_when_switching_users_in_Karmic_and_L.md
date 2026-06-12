---
title: "Pausing music when switching users in Karmic and Lucid"
date: 2010-03-02
forum: Multimedia Software
---

### Post by wojnicki on 2010-03-02
In Jaunty, if a user A plays music and switches to another user (user B) the sound is paused and the B user is able to play his sounds at will. When B switches back to A, B's sounds are paused, and A's sounds are resumed. By default this behavior is not available in Karmic and Lucid as of 3.2.2010 any more. :(

If you want to have it back you need to uncheck 'Use audio devices' privileges for your users (System->User Settings->Advanced->User Priviledges), or remove the users from audio group.

These privileges are very confusing then. I guess their proper interpretation is that if:
- checked: the user locks the audio device as long as he wants, no sound pausing upon user switching,
- unchecked: the user which currently uses the display has access to the audio device, sound pausing takes place upon user switching.

The problem is more general and it regards permissions to access certain devices (and files in /dev directory). Historically if a user needs access to particular device he is assigned to a group which group-owns the device file. It has worked for ages in the unix world i.e. access to an audio device, cdrom, cd burner etc.

This group based approach has several well known limitations. Now it seems that such an access is controlled by consolekit/udev, which makes some sense, at least because of the dynamic nature of /dev directory. The gnome-system-tools and especially users-admin seem not to know anything about acl. I'm not sure whether it's good or bad - it depends, especially that gnome is cross platform - on other systems /dev might be static or there might be no acl at all.

See  [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433654) for more details.

Mind that the sound pausing worked fine in the previous Ubuntu release (Jaunty). 

Anyway I hope it helps, have fun!

---

### Post by JHAx86 on 2010-11-06
This problem is still present in Ubuntu 10.04, and workaround is still working.

If you have did a distro upgrade from previous versions. The "playing audio not stopping when changing user" problem is still present. Read the bug report and this forum post helped me to solve it.

A user really do not need to have permissions to access audio directly, because be default we are members of the groups running the needed daemons to have audio playing correctly and behave correctly in multi user environments.

Thank you.

---

