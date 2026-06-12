---
title: "Followed instructions, now I've NO sound OR sound drivers....can't fix."
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by Soglad on 2007-11-07
I followed this poster's instruction on how to get a microphone working on a HDA Intel audio chipset and it completely removed all my sounds and I can't seem to re-install it!!

I get the Gnome Volume Manager in the top right...but it has the muted sign on it. When I try to click on it, it give me a big error message of:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I got no sounds from anything.

Here's the instructions I followed....

[QUOTE=Fraz]Yes, it does exist!

Here is my hardware, same as the original posters:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

The laptop in question is an Asus S96J.

Okay here is how you "fix" this, it's not a 100% great solution but it gives you the functionality you need.

I noticed two problems with snd-hda-intel after installing Ubuntu 6.10 (Edgy).

1) Microphone refused to work. The internal one was always garbage and never worked, even in Windows, but my external headset microphone refused to work whatever amxier settings I used.

2) The volume control would change the "Headphone" volume which does nothing.

How to fix:

1) You need the latest ALSA driver. Do this:

1. Get build-essential and linux-headers packages.
2. Get alsa-driver package from alsa-project.org
3. Unpack it.
4. Run "./configure --with-cards=hda-intel"
5. Run "sudo make"
6. Run "sudo make install"
7. Edit /etc/modules and add "snd-hda-intel"
8. Reboot.

You will now notice new options in the Gnome Volume Manager. For me the front microphone input is labeled "Microphone" (Not FRONT microphone, that is the busted internal mic). It now works.

If you don't see it, add "options snd-hda-intel model=ref position_fix=0"
to /etc/modprobe.d/alsa-base and reboot again.

Now, for problem number 2, the Volume Control keys.

Basically unless we can either hardcode gnome-volume-manager to adjust FRONT instead of HEADPHONE or merge the two in ALSA we have to use the following work around:

1) Edit /etc/acpi/mutebtn.sh to read:

#!/bin/bash
. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_MUTE
amixer sset Front toggle

2) Edit /etc/acpi/volupbtn.sh to read:

#!/bin/bash
. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_VOLUMEUP
amixer sset Front 1+ unmute;

3) Edit /etc/acpi/voldown.sh to read:

#!/bin/bash
. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_VOLUMEDOWN
amixer sset Front 1-;


Done!!

The only drawback is you lose the visual notification gnome-volume-manager gives you.

If there is a way to merge headphone & front please tell me!

Thanks.[/quote]

Anyone know how to fix this?

Thanks!

Dav.

---

### Post by Soglad on 2007-11-11
Bump!

---

### Post by Soglad on 2007-11-11
Bump!

---

### Post by Soglad on 2007-11-12
Ah c'mon please! I've got no sound here!!

---

### Post by Soglad on 2007-11-12
...........................................

---

### Post by Soglad on 2007-11-12
Dum-di-dum-dum

---

### Post by Soglad on 2007-11-12
Bbbbuuuuummmmmpppppp!!!!

---

### Post by Soglad on 2007-11-13
Bump...

---

### Post by lik on 2007-11-13
same problem but my sound never worked.
have you tried the comprehensive sound post?

---

### Post by Soglad on 2007-11-13
> **lik said:**
> same problem but my sound never worked.
have you tried the comprehensive sound post?

I have, and strangely when I try removing all the lib files and re-installing them, my pc freezes and I can only recover by restarting...it's very odd....

---

### Post by lik on 2007-11-13
My problem just went away like magic! its really odd... didn't do anything! I'm begining to love ubunto lol

---

### Post by Soglad on 2007-11-13
Can anyone tell me how to install HDA Intel drivers properly? I've tried the comprehensive sound thingy and it make my pc crash!

Please help! I'm crippled without sound being a musician and all!

---

### Post by Soglad on 2007-11-13
bump

---

### Post by frodon on 2007-11-13
Too much bump kill the bump !

Please take the time to read our code of conduct :
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

thread closed.

---

### Post by frodon on 2007-11-14
Soglad, your thread is re-open.

Maybe you should give some details about how "crashed" your system using the instruction you followed. Try to provide some error log and explain clearly what step failed.
I think you should try to figure out first what when wrong exactly using the instructions detailed in your first post.

---

### Post by Soglad on 2007-11-14
I backtracked all my steps and nothing came of it. I shall supply and info anyone wants if they can give me and commands to put into a terminal.

When I try and follow the comprehensive sound guide thread and uninstall and reinstall all the sounds things, my pc screen goes black without warning and won't go out of it. Don't know what's going on.

---

### Post by Yellow Pasque on 2007-11-14
See my reply about using OSSv4 in the other thread you posted to.

---

