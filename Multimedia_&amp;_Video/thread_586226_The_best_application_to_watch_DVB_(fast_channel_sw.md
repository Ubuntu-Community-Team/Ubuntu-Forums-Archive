---
title: "The best application to watch DVB (fast channel switching, ir support...)"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by vemon on 2007-10-22
Hi!

I have spent a few days trying to find a nice application to watch digital television (DVB) in Ubuntu Gutsy. I have a simple budget DVB-T card without a hardware mpeg decoder so the whole job of transforming a dvb stream to human watchable form in my tv is left to the player app.

My criteria included:

- DVB support using channels.conf
- Fast DVB channel switching
- Full screen, and "zoom" (fill the screen with the picture) capabilities
- De-interlace and crop (my tv is 4:3) filters
- Controllable with a remote (either native lirc support or some other remote interface / api that can be called with irexec)
- Option to disable gui completely (only rely on the remote and/or keyboard shortcuts)
- Stable (don't want to restart the app in the middle of my favourite tv show)
- And last but not least: All the settings should be definable from from the command line (startup command)

Trial #1 - Mplayer:

I first tried to use mplayer since it's been my player of choice for a long time. It almost meets the criteria but a very important feature is missing: Fast channel switching. When changing a channel the whole application seems to "restart" and it takes a long time (many seconds) for the next channel to pop up. So it was a no-go for mplayer.

Trial #2 - Xine:

My next candidate was xine (actually gxine). It also had the problem of slow channel switching so I ditched it pretty fast without even checking if it would meet the other criteria.

Trial #3 - VLC:

The first thing I tried with VLC was of course the channel switching and it worked MUCH faster (0,5 - 1 second) than with mplayer or xine. I was already convinced that I had found my dvb player :). After a bit (a lot) of digging I managed to get all the stuff from my wish list (criteria) working. I'll post my working VLC command line here as soon as I get back home :)

Conclusion:

I'm now a happy VLC user when it comes to watching DVB streams in Ubuntu :). The next thing I'm planning is making it transcode the dvb stream to mp4 on the fly and stream it so I can watch TV from any computer in my WLAN network.

Question to Ubuntu users:

What is your DVB player of choice in Ubuntu and why?

---

