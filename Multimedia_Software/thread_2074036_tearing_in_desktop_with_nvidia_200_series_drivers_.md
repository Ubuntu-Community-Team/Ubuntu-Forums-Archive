---
title: "tearing in desktop with nvidia 200 series drivers and 660ti"
date: 2012-10-20
forum: Multimedia Software
---

### Post by manorba on 2012-10-20
Hi all,

since upgrading kubuntu 64bit to 12.10 i have tearing on the upper part of the desktop. i have vsync enabled both on nvidia panel and in system settings->desktop effects, in fact the same configuration was working fine up till now.
i have the same problem with video on vlc (which was ok before, too) but not with kmplayer so i guess this is somethign i should ask on vlc forums... btw both are using vdpau naturally.

these are my relevant specs:
660TI, kubuntu 64bit 12.10 with kde 4.9.2, nvidia drivers 310.14 from xorg-edgers.

any help would be appreciated,
manorba

---

### Post by fooman on 2012-10-20
best results for me are to always uncheck/disable *sync to vblank* in the nvidia-settings... but keep it enabled in the compiz-config-settings-manager.

---

### Post by manorba on 2012-10-21
thnx for the reply,

well i tried every combination of vsync on system-settings and nvidia-settings, and both on is my best one. with every other combination i have let's say "regular" tearing on the whole desktop, while with this setting the tearing happens only on 1 line on the upper 1/5th of the screen approximately. 
i'll try to explain it better: if you move a small window on the upper part of the screen you see this noticeable tear... funny thing if you do the same thing on the lower part of the screen there's no tearing at all.

---

