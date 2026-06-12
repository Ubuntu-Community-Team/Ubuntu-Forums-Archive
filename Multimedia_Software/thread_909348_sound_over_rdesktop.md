---
title: "sound over rdesktop"
date: 2008-09-03
forum: Multimedia Software
---

### Post by akahige on 2008-09-03
I'm running rdesktop from the command line. This seems to be less problematic than using the TS Client.

When I have sound enabled -- bringing the remote XP machine to the local Ubuntu client -- all of the sound events on the linux desktop are disabled.

There certainly seem to be no shortage of linux multimedia apps that will happily overlap their audio output over each other. Is there a way to get both local AND remote sound with rdesktop?

---

### Post by ConSeannery on 2009-01-02
Hello there,

You could try using the -r switch for rdesktop, it lets you define sound playback location. Copied from the man page for rdesktop:

 -r sound:[local|off|remote]
Redirects  sound generated on the server to the client. "remote"
only has any effect when you connect to the console with the  -0
option. (Requires Windows XP or newer).

You would likely use (replacing the IP with your remote machines):
rdesktop -r sound:local 192.168.0.10

---

### Post by akahige on 2009-01-02
Thanks for posting back.

Your suggestion doesn't actually address the problem as described, but near as I've been able to determine in the intervening months, it's a case of rdesktop not being a PulseAudio compliant app. (VMware has similar issues.)

Oh well... as time passes, hopefully all these things will start playing nice with each other...

---

