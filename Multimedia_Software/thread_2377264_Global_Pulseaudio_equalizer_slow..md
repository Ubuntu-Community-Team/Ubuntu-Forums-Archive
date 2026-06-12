---
title: "Global Pulseaudio equalizer slow."
date: 2017-11-11
forum: Multimedia Software
---

### Post by YuiDaoren on 2017-11-11
[FONT=franklin gothic medium]Kubuntu 17.10[/FONT]

I installed and set up the global equalizer in Pulseaudio. It works quite fine for music, system sounds, and video playing.

However, it's too slow and gets choppy when used with games like Second Life and Descent 2. I don't want to just bypass the equalizer for these, because I use the equalizer to handle my high-frequency hearing problems. In Second Life especially I need it.

The only thing I could think to try was adding [FONT=lucida console]tsched=0[/FONT] when loading [FONT=lucida console][COLOR=#111111]module-udev-detect[/COLOR][/FONT] as it helped with choppiness for Minecraft way back when[FONT=lucida console][COLOR=#111111].[/COLOR][/FONT] It had no effect. I can't think of anything else to tweak. Any ideas?

---

