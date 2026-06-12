---
title: "Intel 945GME Drivers"
date: 2009-10-01
forum: Multimedia Software
---

### Post by jjachnik on 2009-10-01
I have just got a Lenovo S10e and I have put Ubuntu Netbook Remix 9.04 on it. I am having a few problems with the graphics. I can only assume it is a problem with the drivers. I do not know which i am using, i looked in xorg.conf but nothing was listed.

When i plug in an external monitor (LG 22" widescreen) I only have 4 resolution options and all of them are 4:3 aspect ratio with the highest being 1024*768. I know the graphics card on the s10e can handle 1980*1050 because i have read it on some other forums while looking for a solution (it may have been under windows but why should it matter).

Also, if i turn on any "visual effects" then the top status bar in UNR disappears and so do other windows and it is all very strange.

lspci | grep VGA returns:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

Any help would be most appreciated.

---

### Post by jjachnik on 2009-10-02
So i have made some progress. I changed my xorg.conf to have a virtual display and i could then get the full resolution on my monitor. However, it was unusably slow (about 5 second lag just changing sections on the UNR menu) I then reverted my xorg.conf and i can still get the full resolution but it is faster!

I think the difference may be that i logged out and back in with my monitor plugged in. Previously, i plugged the monitor in with Ubuntu logged in. It used to be recognized as '22" monitor' and now comes up as 'LG Electronics 23"' so i guess that is progress.

I still think there may be problems with the drivers. Running glxgears on the netbook screen (external off) gives 150fps and running on the external monitor (internal turned off) gives barely 50 fps.

I found this thread: [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=gma+950")

I am unsure about doing this as i havnt used ubuntu that much.

---

