---
title: "XUbuntu 24.04 Is there a way to set device aliases within Pulseaudio Panel Plugin?"
date: 2024-08-24
forum: Multimedia Software
---

### Post by Adam_GUI on 2024-08-24
I recently purchased an HP Omen 40L.
Computer is fine, overall, but the audio jack's audio is garbage -- Speakers sound as if they're blown.

So, fully embracing the sunken cost fallacy, and not wanting to return the computer as I needed to get work done, I purchased a set of two USBA to Headphone jack devices from Amazon.

The devices work great.
Unfortunately, they have the exact same name identifier in Pulseaudio Panel Plugin in XFCE.

Is there a way to assign user-friendly aliases, so that I don't confuse the front and rear audio devices?

Thanks.

[ATTACH=CONFIG]294129[/ATTACH]

---

### Post by Adam_GUI on 2024-08-25
I guess this is my 24 hour bump.
I'll accept an RTFM for a man page.

i've tried searching for "Pulseaudio alias" with no luck for me with the forums.  Maybe I've done something wrong.

---

### Post by Adam_GUI on 2024-08-27
Obligatory thread bump.
Ideas?

---

### Post by Yellow Pasque on 2024-08-29
Maybe something like this: [https://unix.stackexchange.com/questions/648666/rename-devices-in-pipewire](https://unix.stackexchange.com/questions/648666/rename-devices-in-pipewire)
X/ubuntu 24.04 is using Wireplumber 0.4.x, so I think the first answer using Lua is what you want, rather than the second answer using JSON, but don't quote me on that.

---

