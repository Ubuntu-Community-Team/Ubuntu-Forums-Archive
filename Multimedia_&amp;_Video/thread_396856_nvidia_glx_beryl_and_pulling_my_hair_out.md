---
title: "nvidia glx beryl and pulling my hair out"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by sgtkwol on 2007-03-29
I'm gonna keep this really basic, because I could fill a book with logs and error messages.  I've googled, and browsed the inter-web for a solid week and cant find anything that helps me.  I'm using feisty fawn and have an nvidia geforce 6200 le.  I'm running from the nvidia drivers and I get the nvidia splash screen, so that much works, but glxgears and all other glx info shows me that glx is hosed right now.  I'm sorry if this is posted somewhere else on this forum, but more than likely I have actually already tried it.  thanks in advance.

---

### Post by dreadlord_chris on 2007-03-30
> **sgtkwol said:**
> I'm gonna keep this really basic, because I could fill a book with logs and error messages.  I've googled, and browsed the inter-web for a solid week and cant find anything that helps me.  I'm using feisty fawn and have an nvidia geforce 6200 le.  I'm running from the nvidia drivers and I get the nvidia splash screen, so that much works, but glxgears and all other glx info shows me that glx is hosed right now.  I'm sorry if this is posted somewhere else on this forum, but more than likely I have actually already tried it.  thanks in advance.

I'm using the 7300LE and I was able to get all the eye-candy goodness by following this guide: [CompositeManager/AIGLXOnEdgy]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy") with one change:

```

Section "ServerLayout"
        Option         "AIGLX" "true"
EndSection

```

left me with a blinking cursor & black screen - without that line in my **/etc/X11/xorg.conf** everything works.

While I *was* able to get straight GLX to work with my NVIDIA card (after much frustration & hair pulling ](*,) ) - it was very unstable for me.

I then tried the AIGLX method - and it worked!

---

