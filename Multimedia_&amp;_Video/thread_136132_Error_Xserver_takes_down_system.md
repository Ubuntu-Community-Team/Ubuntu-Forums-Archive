---
title: "Error Xserver takes down system"
date: 2006-02-25
forum: Multimedia &amp; Video
---

### Post by dcostelloe on 2006-02-25
Well as luck would have it I have had to replace my video card on my production server. The following events are now in play:

I have no graphical support as xserver-xorg will not configure using sudo dpkg-reconfigure xserver-xorg

The configuration menu steps through ok when I select my new card and save configuring and re-boot the xserver reports it has failed.
I following up with a search of the forums and try everyting suggested including the suggestion to remove xserver and re-install. This is the point I'm at now.
Removal of xserver worked smooth..problem now  I can't re-install as although I can boot to my cdrom for some reason or other ubuntu can no longer find the cdrom.
Tried mounting the cdrom - Failed

Now I'm stuck with a production server with no graphics and no way to backup the server to my writable Cdrom.

I need to be able to change a device and not have to re-install the OS. 

Tried to mount a windows share so I could back up my sql database and other required files... seems that there is an issue as the desktop used to mount the share ok?


So I tried to use the boot cd to do something other than wipe out my server. Used the rescue command no luck mounting anything there.

So here I am 3 weeks later still trying to get xserver re-installed to try and get this server working in graphic mode or any mode would be nice. So I can mount the cdrom 

This should not happen on a simple hardware replacement?

Is there any way I can have the boot cd fix the xserver or any option other than losing all my OS?

:confused:

---

### Post by dcostelloe on 2006-03-01
Update:

Fixed CDrom issue I can now re-install xserver-xorg.

Still same problem with xserver failure?

:-({|= :-({|=

---

