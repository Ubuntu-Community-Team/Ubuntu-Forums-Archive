---
title: "How to get Mic working on Creative Labs SB X-Fi"
date: 2011-01-10
forum: Multimedia Software
---

### Post by BugBuster on 2011-01-10
Hello All,

Just a quick how-to, to get mic working with Creative Labs SB X-Fi on Ubuntu 10.10 64bit.

This is a result of my conversation with a 'friend' I met on #ubuntu on irc.freenode.net, whom I was trying to help.

To begin, this is the card we are talking about:
```

$lspci | grep audio
05:01.0 Multimedia audio controller: Creative Labs SB X-Fi

```

This card uses "snd-ctxfi" module for the audio output.

And this is how he got the mic to work using alsamixer...


[IMG]http://i.imgur.com/7uoUj.png[/IMG]

I have seen many thread/posts on the internet about this issue..and thought this could help someone.

---

### Post by MrPok on 2011-02-02
> **BugBuster said:**
> Hello All,

Just a quick how-to, to get mic working with Creative Labs SB X-Fi on Ubuntu 10.10 64bit.

..

I have seen many thread/posts on the internet about this issue..and thought this could help someone.
Unfortunately, this didn't get my microphone working. :( 
Indeed there are tons of pages on this, but after spending lots of hours today I can't find how to fix this. :](*,)
I have a X-Fi Titanium (which I believe is a PCI-express version).

- sliders or settings that aren't saved for some alsa settings, when using *alsamixer* or *GNOME Alsa Mixer*,
- no mic input signal whatsoever in the *PulseAudio Volume Control*,
- ..gremlin sounds eminating from my headphones..



Any ideas?

Kind regards


[SIZE="1"]btw the grep is case-sensitive, so you need "Audio" instead of "audio".[/SIZE]

---

### Post by Another Monkey on 2011-03-19
I've been trying to get the mic working with an X-Fi as well, I've given up.  Whenever I try to use the X-Fi all  get is a recording of whatever the sound card happens to be playing.
lspci:
```
04:04.0 Multimedia audio controller: Creative Labs SB X-Fi

```I did find a solution that worked for me on my Dell Dimension 9200.  It has an on-board sound card (Intel SigmaTel STAC9227) and if I connect the mic to the rear jack on the case and tell Ubuntu to use the internal sound for input and not the creative, I can record sound.  The front jack does not work, it appears to be wired to the X-Fi.  I think Ubuntu doesn't support Creative sound cards fully, and I am sure that I have read that the fornt jacks are not supported at all on Creative cards.
Obviously this will only work if your motherboard happens to have an on-board sound card (something I wish Dell had made clear when I bought the PC, I could have saved a few £s).
Some people may be lucky depending on the exact model of X-Fi and how it is connected.
As for case sensitivity in grep, the command should actually be:
```
me@my_pc:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
04:04.0 Multimedia audio controller: Creative Labs SB X-Fi
```

---

