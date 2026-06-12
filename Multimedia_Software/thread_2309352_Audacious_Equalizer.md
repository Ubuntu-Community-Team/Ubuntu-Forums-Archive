---
title: "Audacious Equalizer"
date: 2016-01-09
forum: Multimedia Software
---

### Post by Evil Wayz on 2016-01-09
I finally got around to adding the winamp presets to audacious and they work great.  However, THe two boxes, the eq and the preset menu, won't close after I select a preset. Actually if I just open them and do anything they won't close.  I've tried hitting ctrl-j but it doesn't do anything.  It's not of supreme importance but it's annoying and I'd like it to go away.

Using 14.04, with gnome flashback, audacious 3.7.

---

### Post by Yellow Pasque on 2016-01-12
I use Debian (sid) and build my own audacious from git. If you have a link to these winamp presets, I'll give them a try and see if I can reproduce the behavior here.

---

### Post by mc4man on 2016-01-12
> **Temüjin said:**
> I use Debian (sid) and build my own audacious from git. If you have a link to these winamp presets, I'll give them a try and see if I can reproduce the behavior here.
One set here, I believe you should extract, open in text editor & remove everything above [Presets]
Then save to ~/.config/audacious as eq.preset

wget [http://www.beastwithin.org/users/wwwwolf/code/xmms/winamp_presets.gz](http://www.beastwithin.org/users/wwwwolf/code/xmms/winamp_presets.gz)

In 3.6.x here the winamp interface > preset button opens a drop down menu > window, in 3.7 it opens a separate window directly. In the former window closes upon selecting a preset, in the later selecting sets, then window can be closed manually (X)

(- there are also eqf files here though they need to be loaded by path each time.
[http://gnome-look.org/content/show.php/?content=120304](http://gnome-look.org/content/show.php/?content=120304)
What doesn't work in either case is the export function > save, just produces an empty eq.preset file

---

### Post by QDR06VV9 on 2016-01-12
> **mc4man said:**
> One set here, I believe you should extract, open in text editor & remove everything above [Presets]
Then save to ~/.config/audacious as eq.preset

wget [http://www.beastwithin.org/users/wwwwolf/code/xmms/winamp_presets.gz](http://www.beastwithin.org/users/wwwwolf/code/xmms/winamp_presets.gz)

In 3.6.x here the winamp interface > preset button opens a drop down menu > window, in 3.7 it opens a separate window directly. In the former window closes upon selecting a preset, in the later selecting sets, then window can be closed manually (X)

(- there are also eqf files here though they need to be loaded by path each time.
[http://gnome-look.org/content/show.php/?content=120304](http://gnome-look.org/content/show.php/?content=120304)
What doesn't work in either case is the export function > save, just produces an empty eq.preset file
Thanks mc4man works good..
I found by using the winamp skin I was able to save the presets and no lag in closing any of the windows..
Kind Regards

---

