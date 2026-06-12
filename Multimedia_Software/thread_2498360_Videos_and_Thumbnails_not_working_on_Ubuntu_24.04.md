---
title: "Videos and Thumbnails not working on Ubuntu 24.04"
date: 2024-06-10
forum: Multimedia Software
---

### Post by MaximB on 2024-06-10
Today I did an installation of Ubuntu 24.04, kept my home folder that was used by Linux Mint.
I did have some desktop crashing issues, but I solved it by removing the .gnome related dirs.

Now I have a new issue,
I cannot view any thumbnails in 'files',
There were old threads that it's somehow related to apparmor, but I have the latest version in which it was fixed.

Also a somehow related issue, I cannot play any videos, not in VLC or on any other player.
dmesg shows:

audit: type=1400 audit(1718040850.090:5237030): **apparmor="DENIED" operation="symlink" class="file" profile="snap.vlc.vlc"** name="/dev/char/195:255" pid=107301 comm="glxinfo" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000
And many other apparmor="DENIED"  lines for other apps,

I noticed that I don't have this file (dunno if I should)
/etc/apparmor.d/usr.bin.snap

I've run:
sudo dpkg-reconfigure apparmor

and even:
sudo apt reinstall snapd

But still the same issue.

---

### Post by deadflowr on 2024-06-10
As far as snaps go,
snaps don't handle symlinks or understand what they even are.
The expected behavior is to bind mount the source and the destination.

As far as not seeing thumbnails in Files try deleting the "fail" folder in ~/.cache/thumbnails.
I've seen that work myself.

---

### Post by MaximB on 2024-06-10
I didn't understand what I should do in the first part,
And if I use flatpak vlc the videos will run? or should I try to get a .deb package?

I already removed the "fail" folder in ~/.cache/thumbnails, but it didn't resolve the issue.

---

### Post by deadflowr on 2024-06-10
> And if I use flatpak vlc the videos will run? or should I try to get a .deb package?
Sure. Either should work, I would think.
Snaps are weird. Sorry.
> I already removed the "fail" folder in ~/.cache/thumbnails, but it didn't resolve the issue.

Yep, I don't know what's gong on with some users and thumbnails.
Might have some common thing/setup that not everyone else has or does.
???:confused:](*,)

---

### Post by MaximB on 2024-06-10
After removing the default vlc and installing vlc with apt - the videos started running again....
Also when I installed Steam via the software manager it had bugs (couldn't add a third dist to storage and it didn't recognize my ~/.steam/root/compatibilitytools.d/ dir, so no Proton-GE), but after installing Steam via the Steam website .deb method - those bugs were gone.

The thumbnails issue I solved by:
sudo apt install ffmpegthumbnailer
and also running this (not sure if the second command is mandatory as I run it first and it didn't work)
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0

Why ho why do they insist on shipping a LTS release with broken snaps? it's supposed to be stable... :(

---

### Post by bloozguy on 2024-09-07
Had these problems "upgrading" to 24.04.1

The vlc solution worked but the thumbnail problem persists.

Sorry as hell that I "upgraded".

---

### Post by neilbt478 on 2024-10-08
Had no music or video thumbnails on 24.04 install. Did the "ffmpegthumbnailer" thing and got video thumbnails but still no music thumbnails. After head scratching and hair pulling and trying everything the internet suggested (which just caused more hair pulling) I ended up installing Thunar file manager and even Nautilus has music thumbnails now. The world is weird...

---

