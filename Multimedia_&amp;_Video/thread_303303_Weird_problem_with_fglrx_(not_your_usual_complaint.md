---
title: "Weird problem with fglrx (not your usual complaint)"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by poebae on 2006-11-20
Hey guys,I need some help. I'm new to Ubuntu, so please bear with me.

I (thought) I got my ATI card working properly, but there's a problem:

I was fiddling around with my xorg.conf, and when I tried rebooting I got the error message that my GUI session couldn't be started.

I fiddled around with my xorg.conf again and typed 'startx', then pulled up a terminal, and my fglrxinfo output showed the correct ATI stuff instead of MESA. Then I realised that I wasn't logged in 'properly', in that when I pressed "Quit", the 'shut down' and 'restart' options weren't available to me.

When I rebooted my system and logged in again, I was given the "Couldn't open screen 0" message.

I've read that it's got something to do with being logged in as root, though that didn't make much sense to me, since you're not normally logged in as root anyway...

Why does my card work properly only when my Ubuntu doesn't boot up correctly and I have to type 'startx' manually?
Reply With Quote

---

