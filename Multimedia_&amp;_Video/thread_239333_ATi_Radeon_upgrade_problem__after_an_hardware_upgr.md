---
title: "ATi Radeon upgrade problem  after an hardware upgrade"
date: 2006-08-19
forum: Multimedia &amp; Video
---

### Post by lignito on 2006-08-19
How to configure an ATi Radeon card 9250 after I hardware upgraded it from an Nvidia card ?
Now I can't start ubuntu....I only have the command line acesse...how can I configure Xorg in this case? any help will be apreciated,Thanks .

---

### Post by kriding on 2006-08-19
run this from the command line

```
sudo dpkg-reconfigure xserver-xorg
```

and select 'nv' as the default adapter

Basically, what has happened, is your graphics have been set to use your ATI card, and now you don't have one, there is nothing to initialise, so you have to manually change it.

There are alot of other settings to change once you enter that command, just follow each step and make your choices based on your setup.

---

