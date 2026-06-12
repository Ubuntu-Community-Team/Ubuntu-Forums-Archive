---
title: "LIRC double keypresses in 10.04"
date: 2011-11-26
forum: Multimedia Software
---

### Post by mrming on 2011-11-26
I've got a script set up to launch XBMC with my MCE (usb) remote's green button, as detailed here:

[http://noods.wordpress.com/2010/06/16/how-launch-xbmc-with-mce-remote-home-button-on-ubuntu/](http://noods.wordpress.com/2010/06/16/how-launch-xbmc-with-mce-remote-home-button-on-ubuntu/)

The problem I've got is that when I run irw each press of a button on the MCE remote gives two keypress events.

I've tried pretty much everything suggested online about how to stop this but nothing has worked.

Can anyone give me some advice on how to supress the repeat? I'm running 10.04 with kernel 2.6.32-33.

Any help would be greatly appreciated as this problem is driving me mad! :D

---

### Post by Bonster on 2011-11-27
This is what i did to stop the repeat. it depends how many times it repeats, so use irw to count it for each button.

For example my remote button repeats 5 times, so to balance it out i use the
repeat = 5, this somehow cancel it out. Hope that helps, took me a while to figure that out also =)

```
begin
	prog = vlc
	button = volup
	config = key-vol-up
	repeat = 5
	delay = 0
end
begin
	prog = vlc
	button = voldown
	config = key-vol-down
	repeat = 5
	delay = 0
end
```

---

