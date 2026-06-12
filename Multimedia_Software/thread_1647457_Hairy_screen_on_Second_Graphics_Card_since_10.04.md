---
title: "Hairy screen on Second Graphics Card since 10.04"
date: 2010-12-17
forum: Multimedia Software
---

### Post by alphasoup on 2010-12-17
Since upgrading from 9.10 to 10.04, and after a fresh install of 10.04.
My second graphics card (radeon) on PCI has become hairy and almost unusable.
(Picture attached :()

The issue is that the radeon card was unable to run as primary display since 10.04
while it ran perfectly as primary in 9.10 (or 8.x before that).
So this seems to point to improvements made on the radeon driver.

When booting from fresh install, the screen went black with no display, the
system sometimes halted on boot. The "fix" was to put AGP/PCI as display
order in BIOS. Then 10.04 was happy to bring the main screen on nvidia AGP, no blank
screen. Then adding the secondary screen adds pixel-ated horizontal hair that
seen to be noise from other area of display memory: the hair go away on refresh
(partially) then reappear over time and while typing.

This is an "improvement" from 9.10 for radeon support since PCI had to be primary
or the screen was even worse (flickered and right shifted from mouse by + 2 inches horizontally).
Now however it can only be used as secondary (reverse config 1 <-> 2) but hairy.

This order of display used to work best with FC a long while ago, I assumed it would
work on Ubuntu with the latest :(

See attached picture, it is hard to read letters while typing this!

---

