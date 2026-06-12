---
title: "Amarok output to freebob device (internal streaming?)"
date: 2007-09-16
forum: Multimedia Production
---

### Post by Stochastic on 2007-09-16
Hi, so I've got my Focusrite Saffire soundcard up and running in Jack with freebob and it's working great for all applications that can output to jack.  I'm looking for a way to get Amarok to output to jack.  So far, I've been able to get Xmms to output to Jack so I think the easy next step to finish the chain off would be to send Amarok's output to a stream and to read that stream with Xmms (I know, pretty complicated chain just to play an ogg vorbis file, but hey, I'd like to hear a better solution if you've got it).  So I'm looking to the Amarok gurus on how to setup a stream of Amarok's output that can be read by xmms.  Thanks.

---

### Post by stmiller on 2007-09-16
Edit: Looks like in Amarok's prefs there is not option to output jack. You can always just take the pcm alsa output in qjackctl and pipe it somewhere else.
[URL="http://bugs.kde.org/show_bug.cgi?id=134767"]
See this bug report.[/URL]

---

### Post by Stochastic on 2007-09-16
I'm not really sure what you mean by the alsa_pcm output piping suggestion, is it that you're suggesting I take the output of the alsa software and pipe it to an input in jack?  How would I do that?

I solved my issue with Amarok by looking into it's internal engine Xine.  It turns out that upcoming versions have built in Jack support so I merely compiled a newer Xine driver and now Amarok config has an option of Jack output.  That being said, it'd be nice to get all apps that normally use alsa to get directly piped to Jack (such as videos on Youtube and totem).

---

