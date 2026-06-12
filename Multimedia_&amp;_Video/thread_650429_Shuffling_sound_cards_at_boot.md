---
title: "Shuffling sound cards at boot"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by henrik_daver on 2007-12-26
Hi!

I have encountered a problem while installing a new sound card on my xubuntu-gutsy-amd64-computer-thing. The card works great, approximately half of the times i turn the power on. The other times the system prefers to select the onboard sound device for sound, and I can't switch to the new sound card through xubuntu's graphical interface. It's visible there, but even if I choose to uncheck all boxes on the motherboard sound device and activates the new card nothing happens.

How do I do to always make the computer choose the new card as the #1 sound card? Can I deactivate the motherboard's sound device thing in some way?

Very grateful for help,
Henrik

---

### Post by icheyne on 2007-12-26
I would just go into your BIOS and disable your onboard soundcard. While the computer is booting up, hold down the delete key. You will be able to disable the onboard sound card there.

Otherwise, try this: [http://alsa.opensrc.org/index.php/FAQ#The_order_of_my_cards_changes_whenever_I_reboot_or_as_devices_are_plugged_and_unplugged._How_can_I_create_PCMs_that_refer_to_cards_by_name_instead_of_number.3F]("http://alsa.opensrc.org/index.php?title=FAQ026")

---

### Post by henrik_daver on 2007-12-26
Thanks! I'll try it as soon as I get home (at work now :)

---

