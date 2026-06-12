---
title: "3D rage lt pro AKA Mach64"
date: 2006-05-27
forum: Multimedia &amp; Video
---

### Post by asalford on 2006-05-27
Thanks in advance for reading this post and any help provided is greatly appreciated :) 

I read the post mach64 howto:

[http://www.ubuntuforums.org/showthread.php?t=7200](http://www.ubuntuforums.org/showthread.php?t=7200)

my issue is related to this post, but the issue i'm having is somewhat different.

this is an older laptop (toshiba satellite 1625cdt) & the 686 kernel simply reboots continually thus I can't resolve the issue:

*** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.

The above is the relative output from the dri.log

the common files installed without incident.

I am running X.org, ubuntu 5.10, uname -r output is 2.6.12-10-386

build essential, the headers are installed, & gcc 4.0 & gcc 3.4 are installed.

in the above post, I am showing others with this issue with no posts on a solution

Again, thanks for any help

---

### Post by az on 2006-05-27
[QUOTE=asalford]Thanks in advance for reading this post and any help provided is greatly appreciated :) 

I read the post mach64 howto:

[http://www.ubuntuforums.org/showthread.php?t=7200](http://www.ubuntuforums.org/showthread.php?t=7200)

my issue is related to this post, but the issue i'm having is somewhat different.

this is an older laptop (toshiba satellite 1625cdt) & the 686 kernel simply reboots continually thus I can't resolve the issue:

*** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.

The above is the relative output from the dri.log

the common files installed without incident.

I am running X.org, ubuntu 5.10, uname -r output is 2.6.12-10-386

build essential, the headers are installed, & gcc 4.0 & gcc 3.4 are installed.

in the above post, I am showing others with this issue with no posts on a solution

Again, thanks for any help[/QUOTE]


First of all, install Dapper on that box and it should work out-of-the box.

If it doesn't, you may want to boot into recovery mode and run
dpkg-reconfigure xserver-xorg

and configure X to use a lower screen resolution and color depth.  Depending on how much video ram you have, you may need to go down to 800x600 at 16-bit to get 3d acceleration.

I got 3d acceleration on an ati mach64 out-of-the-box on breezy, without using updated xorg driver.

---

### Post by asalford on 2006-05-28
[QUOTE=azz]First of all, install Dapper on that box and it should work out-of-the box.

If it doesn't, you may want to boot into recovery mode and run
dpkg-reconfigure xserver-xorg

and configure X to use a lower screen resolution and color depth.  Depending on how much video ram you have, you may need to go down to 800x600 at 16-bit to get 3d acceleration.

I got 3d acceleration on an ati mach64 out-of-the-box on breezy, without using updated xorg driver.[/QUOTE]

the max the screen supports is 800x600.  I reduced from 24 to 16.  no effect.  it is an integrated video card that shares system ram.  shows me it is stealing about 8meg of system ram

I am interested in how you were able to enable 3d on breezy which is what I am running.

Also note, glxgears runs flicker free for about 5 seconds then gets jerky.

glxinfo:

glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

I would prefer not to use a stable release on this laptop since it is a production system.

---

### Post by asalford on 2006-05-28
tried dapper as you suggested, made the system urinate on the dog.  ;)   just kidding.

It had not effect one way or the other.

I have browsed around and around and around.  Seems lots of people have a headache now from trying to get it working.

Any other suggestions?

---

