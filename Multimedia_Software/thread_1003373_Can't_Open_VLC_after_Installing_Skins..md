---
title: "Can't Open VLC after Installing Skins."
date: 2008-12-06
forum: Multimedia Software
---

### Post by adredz on 2008-12-06
Can't Open VLC after Installing Skins.
Hi, I am having trouble reverting the defaults of my vlc settings. After I installed a skin I download from gnome-look I can't switch to any skins anymore. I searched for a .vlc/something in my home directory to delete it but I didn't find it so I decided to delete the vlc directory in /usr/share/. Then, when I launch vlc it doesn't open up anymore and prompts me for a skin instead. However, if I leave the .vlt skin that I download on the 'desktop'(where it shouldn't be installed there in the first place) it runs fine. But I want the default skin and I don't know how to set it back.. It is really ruining my video experience on my desktop. Damn! Any help pls.. When I run vlc via terminal here's what I get:

note: I also get prompted for a skin after getting this error:
> 
[00000001] main libvlc debug: translation test: code is "C"
[00000413] access_directory access error: /home/adred/Desktop/87928-hx_milky_1.1_0.8.6.vlt: No such file or directory
[00000413] access_file access error: cannot open file /home/adred/Desktop/87928-hx_milky_1.1_0.8.6.vlt (No such file or directory)
[00000404] main interface error: no suitable access module for `/home/adred/Desktop/87928-hx_milky_1.1_0.8.6.vlt'
[00000404] skins2 interface error: failed to open /home/adred/Desktop/87928-hx_milky_1.1_0.8.6.vlt for reading
[00000404] skins2 interface error: failed to parse /home/adred/Desktop/87928-hx_milky_1.1_0.8.6.vlt
[00000418] xml xml error: XML parser error (line 1) : failed to load external entity "skin.dtd"

[00000418] xml xml error: XML parser error (line 2) : Validation failed: no DTD found !
[00000404] skins2 interface error: failed to parse /tmp/vltmOFbUW/default/theme.xml
[00000404] skins2 interface error: error while parsing /tmp/vltmOFbUW/default/theme.xml
[00000421] xml xml error: XML parser error (line 1) : Document is empty

[00000404] skins2 interface error: failed to parse /usr/share/vlc/skins2/default.vlt

If I open up a different skin or the default skin via the prompt dialog that pops up after launching vlc, i get this error:
> 
[00000424] xml xml error: XML parser error (line 1) : failed to load external entity "skin.dtd"

[00000424] xml xml error: XML parser error (line 2) : Validation failed: no DTD found !
[00000404] skins2 interface error: failed to parse /tmp/vltTtDR09/default/theme.xml
[00000404] skins2 interface error: error while parsing /tmp/vltTtDR09/default/theme.xml
[00000427] xml xml error: XML parser error (line 1) : Document is empty

[00000404] skins2 interface error: failed to parse /usr/share/vlc/skins2/default.vlt
[00000404] skins2 interface error: cannot load the theme, aborting
[00000408] main generic error: object is not attached

P.S. I am using Ubuntu Intrepid btw..
Thanks in advance..

---

### Post by mc4man on 2008-12-06
The config files are in your home dir. -> .config/vlc. Try deleting the vlc folder and doing a complete removal or purge of vlc and reinstall.

---

### Post by adredz on 2008-12-06
it works.. thanks you!

---

