---
title: "Amarok, Gnome and the iPod"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by mikesena on 2007-11-12
Hi,

I am trying to use Amarok to:

1.  Connect automatically with my iPod (rather than manually having to click connect)
2.  Submit plays to last.fm
3.  Be able to disconnect, without having to unmount via rightclicking the ipod icon and saying unmount.

How do I do all this?  I know it can be done, I just can't get my settings right.

Can someone please be detailed in explaining?
I saw this, but it didn't work: [http://ubuntuforums.org/showthread.php?t=497201&page=2](http://ubuntuforums.org/showthread.php?t=497201&page=2)

My iPod is mounting after I used the device setting in gnome (i.e. in properties) and specified a mount location.

I would really appreciate any help,
thanks

Michael

---

### Post by Vaz on 2008-02-18
This response is pretty late, but here's what I've done:

In System->Preferences->Removable Devices and Media:
In the Multimedia tab, you can replace rhythmbox (or whatever) with amarok so it will open automatically when you connect your ipod.

In Amarok settings under Media Devices, click add device, use the ipod plugin, pick a name and the full mount point (eg /media/ipod).

When I plug in my ipod, amarok opens and it's already connected.. if there's more to it, I can't remember what else I would have done.


For last.fm:
In amarok settings under last.fm, I just filled out the settings and it worked.  Sometimes it doesn't seem to work right, and sometimes it does...  it didn't work for me for a long time, but lately it's been submitting okay.


For automatically unmounting:

In gnome you can set the post-disconnect command to:
gnome-eject -p %m

%m refers to the mountpoint rather than the device (%d).  This seems to be more reliable.

Let me know if anything doesn't work right for you.

---

