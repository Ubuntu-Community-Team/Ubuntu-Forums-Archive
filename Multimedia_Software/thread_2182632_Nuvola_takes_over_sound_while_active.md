---
title: "Nuvola takes over sound while active?"
date: 2013-10-21
forum: Multimedia Software
---

### Post by malenkylizards on 2013-10-21
I'm crossposting from askubuntu.com, just as a heads up.

I just installed Nuvola Music Player on a just-today reinstallation of Ubuntu 13.10. I was having issues on the previous installation, which was 13.04, and reinstalled the OS.

I was having sound issues before, and I'm having them now as well. Basically, sound works as expected when Nuvola is closed. When it's open, sound plays in Nuvola, but any other application is silent, until I close Nuvola, at which point it works again. It seems to "take over" the sound while it's open.

Anybody else have experience with this problem, or able to offer tips? Alternately (I'm not expecting you to...I've googled it pretty extensively), do you know of another piece of software that will provide a window for Google Play Music?

Relevant info: I'm just using the onboard sound output on my motherboard. It's configured as 5.1, with the appropriate speakers. Regardless of whether Nuvola is active or not, I get sound out of all speakers as expected.

---

### Post by malenkylizards on 2013-10-22
20 hour bump.  Any advice?  Any information I could offer that might help narrow down the source of this problem?

---

### Post by malenkylizards on 2013-10-22
Okay, I finally fixed this.  Responding so anyone in the future can hopefully find this.  A fix was found here: [http://choffee.co.uk/thoughtsplurge/posts/2012/11/16/Nuvola_Cloud_music_player__flash__and_amd64/](http://choffee.co.uk/thoughtsplurge/posts/2012/11/16/Nuvola_Cloud_music_player__flash__and_amd64/)

It's probably a hacky solution, but installing libasound2-plugins:i386 seems to have solved the problem.  I can now have Nuvola open and play sounds from multiple sources.  Thanks, unknown blogger from a year ago!!!!

---

