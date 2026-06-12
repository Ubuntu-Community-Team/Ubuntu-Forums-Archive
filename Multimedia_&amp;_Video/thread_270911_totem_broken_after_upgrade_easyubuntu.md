---
title: "totem broken after upgrade easyubuntu"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by dgermann on 2006-10-03
Hi--

A few months ago I got easyubuntu and first time out managed to finally (after years) get sound and video on my computer.

Update manager has been bugging me to upgrade totem, so tonight I did.

Now it does not work. When I go to play a video on a website I get "You don't have latest flash player" (from video.yahoo.com) or "totem could not play 'fd://0'" (from a local TV station website).

What I did: 1. used synaptic to upgrade totem. It replaced xine with gstreamer (I don't know the difference). The local TV station site wanted to install a plugin after that--took me to a Windows site!

2. I then used easyubuntu to install totem--it said there was a broken package.

3. I used synaptic to uninstall totem-gstreamer--it also removed totem.

4. I then used easyubuntu to install totem again--I got the fd://0 error message above.

5. I used easy ubuntu to install all codecs and other items on its Multimedia tab. Still no go.

So what's next?

Thanks, folks!

:- Doug. Germann

---

### Post by croak77 on 2006-10-04
What browser are you using? Do you have flash plugin installed?

---

### Post by dgermann on 2006-10-04
croak77--

Thanks for your reply.

I have Firefox 1.5.0.7. Synaptic reports I have installed /etc/init.d/flashplugin-nonfree

As far as I know, flash was working previously. At least a couple months ago I was able to view videos.yahoo.com.

I did manage to get the local TV station streaming video working. I used synaptic to install totem-xine--it uninstalled totem-gstreamer and then installed totem-xine and that seems to be working.

So do I need to do something with Synaptic, or go to the flash site and install from there?

Thanks, croak77!

:- Doug.

---

