---
title: "Video Problem: Scrolling and Cursor Traces on Screen"
date: 2008-10-16
forum: Multimedia Software
---

### Post by viniciusandre on 2008-10-16
Hi People,

I don't exactly know how to describe this problem, so I'll put some screenshots. It happens often with scrollable texts or continently changing outputs as the ones in the terminal or web pages on Firefox.

When I scroll the text or select the problematic area with the mouse, it comes back to normal as a mouse selection could 'reveal' the real content. But it don't take long until it happen again.

Here for example, I moved the OpenOffice cursor from left to right with the keyboard, and at some positions it leaves the cursor trace:
[http://img300.imageshack.us/img300/2479/capturadetelanu1.jpg](http://img300.imageshack.us/img300/2479/capturadetelanu1.jpg)

It started happening when I upgraded to Intrepid, it was quite ok on Hardy.

What could it be?

---

### Post by duffiana on 2008-10-21
I think that I noticed the same issue, but with different configurations.
I have a laptop running Hardy, with ATI restricted drivers, for which the problem does not apply.
And a desktop pc, also running Hardy, but with NVIDIA binary drivers (manual install, 177.80 - GPU is 9800GT): this shows the same traces you see.

The differences between the two installs are:
- the laptop is ATI and the desktop is NVIDIA
- the laptop packages are less up-to-date than the desktop ones (didn't do an update for a while)

Considering the problem came for you with Intrepid, the cause may be a package update, as you seem to suggest.
But I'm also wandering if you're using NVIDIA drivers ?

Could you add some details, so we can open a bug report with enough information.

regards,
chris.

---

### Post by viniciusandre on 2008-10-21
It is, indeed, a NVIDIA card, wich drivers were updated with intrepid.
I believe this was caused by it.

I don't know as well how much the Ubuntu community can help us on binary drivers issues like these ones.

Thanks!

---

