---
title: "K3b,flac and debugging"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by nidfix on 2008-03-29
Hi all,

I would need some help on K3b.
In addition to mp3, I woudl like to rip in flac.
So I installed flac package and I defined an entry into the k3b external audio encoder similar to lame for mp3:
flac - -s --endian=little -6 -o "%f"
as well as
flac - -s -6 -o "%f"

Unfortunately, it always generates an error "command failed" at the beginning.

In order to confirm the command, I tried from the command line without any problem:
cat "try.wav" | flac - -s -6 -o "try.flac"

There is no indication of the error in the debug window nor at the console if k3b is launched from it.

Anyone has any idea ?

Is there a way to start a real debug mode on k3b to see the reason why it fails ?

Thank you in advance for your help.

---

### Post by nidfix on 2008-04-05
After some additional investigations I found that k3b does not like to have quote around its variables.
So instead of:
flac - -s --endian=little -6 -o "%f"
I should have used:
flac - -s --endian=little -6 -o %f

By the way it appears that on contrary to the text display in the window to define the command, the stream is in big endian and not in little.
So to actually rip something usable:
flac - -s --endian=big -6 -o %f

---

