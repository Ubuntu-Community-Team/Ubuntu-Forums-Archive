---
title: "How does (will) Wayland cope with switchable graphics?"
date: 2010-11-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by warnec on 2010-11-17
Hi. A main reason why I don't use Linux on my laptop is very poor support for switchable graphics (PC needs to be rebooted). AFAIK, it is caused by some X server limitations.


Do You perchance know how does (or will) Wayland cope with switchable graphics? (of course, as long as the drivers are open for both integrated and discrete GPUs, which is the case of my laptop)

---

### Post by bash on 2010-11-17
> On Tue, Nov 9, 2010 at 8:53 AM, nerdopolis
<bluescreen_avenger at verizon.net> wrote:
> A feature that seems to be in some laptops, and is being worked into the Linux
> kernel.
>
> Would Wayland ever be able to handle this, when the feature comes into Linux,
> or would the display server always need to be reset?

Outcome of discussion between Dave, Kristian, Jesse and me while ridding a bus
is that we should add a way for wayland to ask its client to redraw
their surface
using a another EGL driver and that wayland server should be able to handle
client reporting failure doing so. Maybe i did get this wrong, feel
free to correct me :)

I think to cover all use case Dave presented we should have somethings
like this:
-wayland provide a list of EGL driver it can texture from (optimus case where we
can migrate texture from nvidia to intel)
-wayland can ask to it's client to switch GL driver and report if they
can switch or
not (i think this should happen in 2 step first ask and gather answer
from all client
if one client says it can't then forbid the switch, otherwise ask to
all client to redraw
with new driver)

All this wouldn't need restart from wayland.

Cheers,
Jerome

Source: [http://lists.freedesktop.org/archives/wayland-devel/2010-November/000100.html](http://lists.freedesktop.org/archives/wayland-devel/2010-November/000100.html)

---

### Post by warnec on 2010-11-18
So it's planned, the way I see it. Hope they don't abandon their  plans. Would love to see a GPU switch with no PC/system reboot :)


Thanks for the info. I guess it could help some other people Googling for this information (searching and exploring mailing lists is a little bit harder)

---

### Post by benjamimgois on 2010-11-18
That would be great, the current state of vga switching on X isn't very usefull, the proprietary drivers like FGLRX and Nvidia doesn't work and the opensource alternatives still have huge performance problems. Hope to see wayland solving this.

---

