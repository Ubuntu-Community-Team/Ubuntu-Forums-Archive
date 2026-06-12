---
title: "no AppleTalk?"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by integerpoet on 2010-07-10
I've installed netatalk onto Lucid Lynx.

It works over IP, or at least it works well enough that I can mount my Ubuntu home directory as a volume on a Mac via ASIP (AFP). This isn't what I installed netatalk for, but this tells me the package has installed properly, or anyway nearly so.

However, any time I try to work with AppleTalk (say "getzones -m"), I get:

[INDENT][FONT="Courier New"]atp_open: Cannot assign requested address[/FONT][/INDENT]

Given that I didn't specify an address, I can only assume getzones used some generic address or this error message indicates something else.

And when I look in the system log, I see afpd make the same complaint as it starts, just before it talks about bringing up IP services.

What I'm really trying to do is set up an AppleTalk printer. I get the same error message from the pap command.

I know AppleTalk requires kernel support which may or may not be compiled in, so one theory is that it's not there on Ubuntu. I've found [a web page]("http://manpages.ubuntu.com/manpages/lucid/man7/ddp.7.html") which suggests Ubuntu does have AppleTalk support, but I'm not sure how to prove or disprove it.

Any ideas?

---

