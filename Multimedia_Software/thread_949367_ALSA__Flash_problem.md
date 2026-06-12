---
title: "ALSA / Flash problem"
date: 2008-10-16
forum: Multimedia Software
---

### Post by RaverWild on 2008-10-16
Hello!

I have the folowing problem (up to date latest Ubuntu, desktop machine):

If I use my browser to watch videos from Youtube or similar service, which require a flash browser, after a period of time this constantly holds the control over the sound, thus preventing any other player (amarok, video players as well) to work (they just stick). 

I have workaround for this, but I am already sick of it. Am I the only one with this problem? Is there a permanent solution?

Please share experience.

Ok. let me share my workaround. First how to determine what holds the control over the sound:

lsof | grep pcm

but I really don't need to check this anymore - after few weeks of this problem realized that only application appearing is Firefox (Firefox 3! not tested with older versions). But Firefox itself is not guilty, think it's just about the Flash plugin (my opinion).

So second - I just kill -9 Firefox.

And final:

sudo /etc/init.d/alsa-utils restart

Then I am able to play everything, as it should be. But as I said I am already sick of killing and restarting. Is there a permanent solution for this?

Thanks.

---

### Post by eye208 on 2008-10-16
> **RaverWild said:**
> Is there a permanent solution?
Yes.

[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

