---
title: "Best way to redirect sound output to a different PC on the LAN?"
date: 2009-03-27
forum: Multimedia Software
---

### Post by Jonadab on 2009-03-27
Okay, I've got my whole music collection (mostly FLAC) on the PC in the bedroom.  When I'm there, I play it there.  But there's also a PC in the living room, and sometimes I'm there...  and I want to listen to my music there.  

I'm particular about my playlist (wrote my own algorithm, which spreads each genre and artist evenly throughout the list, while also playing songs that I rated higher more often), so when I go from one room to the other I'd like to pick up in the list right where I left off.  Hence, rather than make the music dir a fileshare, I'd like to redirect the actual audio if possible.

They're networked together via bog-standard 100BaseT FastEthernet, and isolated from the rest of the world via a third system which is an IP Tables firewall and NAT gateway.  Shouldn't there be an easy way to do this?

The living room PC runs Ubuntu Hardy, and the bedroom PC, which has the music, runs Debian stable (Lenny) and is currently using xmms2 to play the music.  I can control xmms2 remotely, of course, but what's the easiest way to temporarily redirect its output to the living room?

---

### Post by markbuntu on 2009-03-27
Just turn on Multicast/RTP in Pulseaudio Preferences and direct xmms to the rtp sink. More on that here

[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio)

---

### Post by Jonadab on 2009-03-28
> **markbuntu said:**
> [http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio)

Okay, following that, I was able to send the sound from the bedroom PC to the living room PC.  Initial success.  However, now I can't figure out how to get sound output on the speakers in the bedroom (hooked up directly to the PC that's producing the sound in the first place).  I don't necessarily need both at once, but I need to be able to get either at any time, with minimal fuss, preferably from the command line.

---

### Post by markbuntu on 2009-03-28
Did you check the loopback audio to local speakers?

---

### Post by Jonadab on 2009-03-28
Ugh, nevermind.  The problem with getting output to the local speakers turned out to be totally unrelated.

What happened was, I had made the mistake of rebooting (for unrelated reasons) ad interim, and as it happens one of the updates that had been installed was a new kernel, so when I rebooted, I was running a different kernel than before.

And the new version of the kernel does not have the driver (cs46xx) for a fairly significant category of soundcards, including my Turtle Beach Santa Cruz, which I specifically purchased because it was a good card and known to work well with open-source software.  It's worked well for me over a number of years, with a variety of OSes, including FreeBSD and every Linux distro you care to name, until now.  Something about there being a file in the driver that doesn't have an explicit license statement, and a clause in the DFSG that does not allow this.

So for the time being I'm using the junk onboard sound that came on my motherboard.  This is a Tyan board, intended more for small servers than desktops, but the audio does work.

I'd like to get my Turtle Beach card working again, but that's another thread for another forum.

All of which is to say, the pulse thing is working great, thanks for the tip.

---

