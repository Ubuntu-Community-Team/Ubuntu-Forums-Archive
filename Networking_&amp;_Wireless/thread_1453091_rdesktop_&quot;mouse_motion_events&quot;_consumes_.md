---
title: "rdesktop &quot;mouse motion events&quot; consumes lots of upload bandwidth"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by fermulator on 2010-04-12
Client (running rdesktop) = Ubuntu 9.04 Jaunty
Host (running terminal services) = WinXP SP3

So rdesktop has the "-m" flag to control whether or not it sends "mouse motion events".

An excerpt from the man page:
>        -m     Do not send mouse motion events.  This saves bandwidth, although some Windows applications may rely on receiving mouse motion.

My remote desktop machine has "show windows contents while dragging" box unchecked:
[IMG]http://img198.imageshack.us/img198/9890/donotshowwindowcontents.gif[/IMG]

This allows moving windows around to be bearable.

If it is checked, moving windows around on the remote machine is very painful, so enabling it isn't really an option.

If I disable mouse motion events w/ the "-m" flag, then I can no longer see where I'm moving windows to.  It would seem that the "don't show window contents" relies on mouse motion events to redraw the "gray border window" that is displayed.

If mouse motion events are enabled, the bandwidth it consumes is crazy (fills my 60KB/s upload pipe).

Any thoughts on how I can have the best of both worlds?  I need:
 A) Mouse motion events disabled, and modify Windows somehow to not rely on motion events..., OR,
 B) Mouse motion events enabled, and figure out how to throttle the frequency at which rdesktop sends motion events.

---

### Post by romulis on 2012-01-16
Don't know if the problem still actual.
Try using an option -x 0x02 (which means RDP5_NO_FULLWINDOWDRAG):
like
rdesktop -f -d mydomain -k en-us -x 0x02 servername
i found it here (i hope puting links to original is legal here):
[http://katastrophos.net/andre/blog/2008/03/10/rdesktop-connect-to-windows-vista-with-cleartype-font-smoothing-enabled/](http://katastrophos.net/andre/blog/2008/03/10/rdesktop-connect-to-windows-vista-with-cleartype-font-smoothing-enabled/)

---

