---
title: "Access Ubuntu 9 share in Win 7"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by gohargod on 2011-02-21
Any tips on getting Ubuntu 9.0.4 to:

1. Mount a secondary drive at bootup
2. Share the drive - or a folder on the drive - with a Windows 7 PC

I've been playing for some time and not having much success. Latest issues:
  - I now have a mount working at boot, but Nautilus won't let me share it because it's owned by root. when I try to chown in terminal or Nautilus, I receive an "Operation not permitted" error in terminal and the GUI just doesn't really do anything.
  - When I actually had the Ubuntu mount/share working and tried to access it from Windows, I had a few issues:
     - Windows could ping by ip or name, but when I did "net view" it would say "access denied"
     - every time I tried to map/access the ubuntu share from within Win 7, Windows tried to use my Windows domain. I have a feeling this isn't the main issue, but thought I would mention this since I'm using my work laptop and don't think I want (or will be able to) change the domain/workgroup on my laptop.

There is a lot of conflicting information and false leads in getting this to work. I expected this to be much easier than it has been and would appreciate any thoughts/suggestions.

Thanks!

---

### Post by BHEJU on 2011-02-21
It depends on your format of the drive (Ext,ntfs,fat)..
If you have ntfs drive like me.. you can try what I have done.. very simple.
install ntfs config manager (to auto-mount drive at log-in)
samba config (to share the folder)

Nothing else to do. just shows up on win.
Hope this helps.

Cheers

---

### Post by gohargod on 2011-02-21
Bheju,

That was great, thanks! I had to do some finagling, but was able to get it to work. This is what I did based on your instructions in case there are others with similar probs.

1. I re-formatted the drive using NTFS (I used Synaptic Package manager to install the NTFSprogs package) and then it showed up ok in the gparted->format menu.
2. I used this link ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) to help with my Samba setup
3. Connected from Win 7 with no problems.

Thank you!

---

