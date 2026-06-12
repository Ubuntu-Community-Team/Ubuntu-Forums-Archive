---
title: "How can I change how firefox handles audio stream?"
date: 2009-05-16
forum: Multimedia Software
---

### Post by TomX19 on 2009-05-16
Using Ubuntu Jaunty 64-bit I have a problem listening to radio streams using BBC iPlayer (through Firefox, not desktop).

Video streams play as per the first screen shot below, with no problems and allow you to click to a different point in the programme:

Audio streams used to behave in the same way, and streams of past radio shows would also allow you to click at any point in the show.  However, recently the audio-only stuff is being handled in a different way.  It looks as per the second screen shot, and has a cache progress bar.  Often playing an audio stream causes Firefox to freeze and has to have a 'force quit' done.  Anybody have any ideas how I get the audio stuff handled by the same plugin that's doing the video?

Many thanks in advance

Tom

EDIT: More on this.  Appears that the 'lower bandwidth version' which is an option on audio streams uses a different plugin (RP9?) to handle the audio, and actually performs worse (i.e., media often interrupted).  Clicking back to 'Use normal version' crashes Firefox every time.  I know the obvious answer is "don't use the lower bandwidth version then!" but still it's an issue....

---

### Post by gandaran on 2009-05-16
> **TomX19 said:**
> Using Ubuntu Jaunty 64-bit I have a problem listening to radio streams using BBC iPlayer (through Firefox, not desktop).

Video streams play as per the first screen shot below, with no problems and allow you to click to a different point in the programme:

Audio streams used to behave in the same way, and streams of past radio shows would also allow you to click at any point in the show.  However, recently the audio-only stuff is being handled in a different way.  It looks as per the second screen shot, and has a cache progress bar.  Often playing an audio stream causes Firefox to freeze and has to have a 'force quit' done.  Anybody have any ideas how I get the audio stuff handled by the same plugin that's doing the video?

Many thanks in advance
Tom

is the problem with the iplayer videos or the radio service?
the bbc iplayer videos are flash videos and firefox uses adobe flash if it is installed, I dont think you can do anthing about the flash videos only ensure adobe flash is installed and not any other flash.
for the radio service firefox uses a player plugin, which one do you have installed? mplayer-plugin is probably the best for the radio service but if it doesn't work fine you can remove it and install another real video/audio compatible player.

---

### Post by TomX19 on 2009-05-16
The problem is the radio service in iPlayer.  I'm not sure how to check what plugins are being used.  I've got flash-plugin-nonfree which I assume is handling the video streams and the normal-bandwidth audio but I'm not sure what player is called for when I click 'use lower bandwidth version'

I don't (and won't) have Realplayer installed.

---

### Post by gandaran on 2009-05-16
> **TomX19 said:**
> The problem is the radio service in iPlayer.  I'm not sure how to check what plugins are being used.  I've got flash-plugin-nonfree which I assume is handling the video streams and the normal-bandwidth audio but I'm not sure what player is called for when I click 'use lower bandwidth version'

I don't (and won't) have Realplayer installed.
from the look of your shot I could say firefox is using vlc plugin (mplayer isn't for sure) but I could be wrong, check in synaptic, type mozilla in search box you should find which mozilla plugin are installed, I would recommend to have only totem and mplayer plugin installed, these two are nearly perfect setup for firefox web streaming but there are many other player plugins if you are not satisfied with these.
I think  the use of lower bandwidth version as nothing to do with the problem if you have a fast bandwidth (broadband) internet connection.

---

