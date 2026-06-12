---
title: "Very weird audio feedback issue"
date: 2009-04-07
forum: Multimedia Software
---

### Post by Midnightsun on 2009-04-07
Hi guys

Just installed Ubuntu on my new machine and am having a very strange audio problem.

I'm getting a kind of buzzing feedback through my speakers that appears to respond to what's going on on the screen.

For instance, just leaving the computer to idle or typing like now and they are totally silent.  However it appears the more I make happen on the screen, the more pronounced the buzzing becomes.  e.g Moving a window around produces a constant buzz until I stop.

It's not my monitor interfering with the speakers as the problem persists after it's turned off.

It's a brand new system, so I'd be suprised if the board was faulty.

The hardware is all on board the Gigabyte motherboard:
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)

I've got no idea how to even begin trouble shooting this issue.  I've got no headphones on hand to see if the problem persists, but like the computer the speakers are brand new so I doubt they're faulty.  I will find some headphones to test tomorrow, though.  

In the meantime, I'd really appreciate any suggestions people can give.

EDIT:  Hey guys - found some headphones and it appears the problem only happens with the speakers.  I don't know if this means the speakers are faulty but it seems a really weird fault to have - to give feedback based on what's happening on the screen...anyway - advice would be appreciated :)  I'll try and borrow some other speakers tomorrow

---

### Post by ErroneousBosch on 2009-11-14
I was having this same issue (video playback SUCKED)
I installed Gnome alsa mixer, and played with the LFE level, even returning it back to high and it seems to have fixed the problem. Hope that helps!

---

