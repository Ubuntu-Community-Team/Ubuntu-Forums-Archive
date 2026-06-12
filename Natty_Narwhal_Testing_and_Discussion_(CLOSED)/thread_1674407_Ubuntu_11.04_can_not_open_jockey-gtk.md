---
title: "Ubuntu 11.04 can not open jockey-gtk"
date: 2011-01-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sinanaykut on 2011-01-23
Hello guys,

I wanted to try Natty Narwhal, so upgraded my 10.10 to 11.04

Anyway, my system can not connect to the wireless network at my home. I tried to run jockey-gtk but it gave that error

Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 421, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 450, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 79, in ui_show_main
    col_icon.set_sizing(Gtk.TreeViewColumnSizing.AUTOSIZE)
AttributeError: type object 'GtkTreeViewColumnSizing' has no attribute 'AUTOSIZE'

I use a netbook and this is my wireless chipset (I suppose)

Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

How can I enable the driver for my network card? Is there any possiblity to enable it except jockey-gtk way?

Thanks.

---

### Post by overdrank on 2011-01-23
Moved to Natty Narwhal Testing and Discussion

---

### Post by cariboo on 2011-01-23
Did you try jockey-text? To find the recommended driver at the prompt type:

```
sudo jockey-text --list
```

then to install it:

```
sudo jockey-text -e <driver> 
```

<driver> = the driver shown when running the first command.

---

### Post by sinanaykut on 2011-01-23
Ow guys, i resolved the problem. I ve just searched 'broadcom' on Ubuntu Software Center, then installed the related module and thats it. Rebooted the system and my wireless is working :)

---

