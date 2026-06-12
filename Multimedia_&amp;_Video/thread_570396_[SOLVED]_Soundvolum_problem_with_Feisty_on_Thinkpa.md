---
title: "[SOLVED] Sound/volum problem with Feisty on Thinkpad R60"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by CrazyChip on 2007-10-08
I have seen alot of threds about not getting the sound to work, but that is strictly speaking not my problem. I have sound, but the volum is not so good. The volume is "good" when it's at max and i can hear sounds, although when i turn it down some it almost immidietly disappear. The "soundbar" is still at around 80%, and i should still be hearing some sound.

Any thoughts?

---

### Post by k@zp3r on 2007-10-11
I have the exact same problem on my R60 running Kubuntu.
If I start a Gnome session, the volume gets a lot louder, so I'm guessing it's a problem with Kde or Kmix or something.
Are you running Kde or Gnome?
The only guess I have so far is that is has something to do with the hardware volume control not being properly supported. As far as I have understood there are two main volume controls and you usually control the hardware volume with the volume controls left of the ThinkVantage button, but KDE or kmix somehow grabs these keys. I could be completely wrong though, since I don't really know what I'm talking about. :-)
Maybe someone else could give some input on that thought?

Thanks.

---

### Post by CrazyChip on 2007-10-12
im running Gnome, and i haven't done anything to try to fix it(i have no idee where to begin).

Edit:
i have added a picture of my volum "bar" when i  no longer can hear any sound.
[http://filer.skogsrud.net/bilete/Volume-in-Ubuntu.png]("http://filer.skogsrud.net/bilete/Volume-in-Ubuntu.png")

---

### Post by CrazyChip on 2007-10-16
I think i found the answer to the problem :)
As explaind in the bug report, the Thinkpad need's no software to control volume. But Alsa mixer(Gnome), and whatever it's called on KDE(kmilo i think) captures the up, down and mute commands to preform them in the software. This means that the volum is beeing lowerd or rasied twice. bla bla bla, you get where this is going...

The fix i use is to disable the capture of the volume control, thereby eliminating the use og alsa mixer and only using the hardware controls. (as explained in the bug report #51537)

Bug reports:
#51537 [Wrong handling of volume buttons on IBM Thinkpad notebooks]("https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/51537")
#61822 [IBM Thinkpad volume keys handled wrong and made partly unusable]("https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/61822")

---

