---
title: "Playing videos in VLC over Samba?"
date: 2009-02-20
forum: Multimedia Software
---

### Post by skullmunky on 2009-02-20
I've seen a bunch of threads about this problem, but I'm not clear on what the best solution is.  

The setup:  have a windows box, (let's call it "winbox"), which has some video files on it.  I want to watch them on my Ubuntu laptop.  I'm running Kubuntu Intrepid, but I imagine the underlying issues are the same for gnome, kde, what-have-you.  

What Works: 

1. connecting by going to Start->Computer->Network and browsing the samba shares.  I can open up the share on winbox, browse through the folders, double-click or r-click the file and open it in VLC.  But instead of playing it, it starts copying it to somewhere, and then crashes.

2. I can get this to work by mounting the share manually, like so:

```

sudo mount -t cifs //winbox/users/me -o username=XXXX,password=XXXX /mnt/winbox

```

then in Dolphin, I can go to /mnt/winbox and open the file in VLC and it plays fine.

I can ONLY do this if I first edit /etc/nsswitch.conf like so:

```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins

```

3. I figured I should be able to just put this in fstab, and if so then use automount, but when i try to mount it it just says that /mnt/winbox isn't in fstab.  

4. so, how do you get this to work?  And how come you have to manually fiddle with mounting from the command line instead of just opening it out of Dolphin/Konqeror/Nautilus?

---

