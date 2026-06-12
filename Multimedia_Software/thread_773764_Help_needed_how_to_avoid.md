---
title: "Help needed: how to avoid"
date: 2008-04-29
forum: Multimedia Software
---

### Post by maansson on 2008-04-29
How is it possible to disable the new screen resolution tool and go back to the old way (6.10) where if a laptop is attached with a CRT attached this one will be used?

I have a physical setup where it doesn't make sense to use both screens.

I've been trying to make it work using nvidia-settings and the new screen resolution tool with no success.


Help will be appreciated!


System specifics:
* Laptop: Dell D620
* Graphics: interal NVdia card
* screen: Dell FPW205
* Ubuntu: latest intel desktop version

---

### Post by Vermind on 2008-04-29
Hello,
So, do You have an intel GMA or an nvidia card?
for nvidia cards, nvidia-settings allows disabling the other screen and doing other neat tricks. For intel, to disable the other screen, look for a "CRT" button on the keyboard, or a picture of a display. These are usually activated by a Fn button. If those buttons don't work, [here]("http://ubuntuforums.org/showpost.php?p=4003194&postcount=584") is a howto written by someone with an intel card.

---

### Post by maansson on 2008-04-29
As I wrote in my original post it is a nvidia card - but your solution did help.

Although it seems a bit strange that by disabling the internal screen the system will again "autodetect" which screen is present and use the CRT if present.

Thank you very much for pointing out the right way!

---

