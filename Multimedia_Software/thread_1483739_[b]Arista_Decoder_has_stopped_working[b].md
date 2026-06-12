---
title: "[b]Arista Decoder has stopped working[/b]"
date: 2010-05-14
forum: Multimedia Software
---

### Post by wired99 on 2010-05-14
Arista Decoder has decided to simply not open.
When called from the menu it shows a window in the Panel but will not open and then disappear.
When called from the terminal I get the following:

> 
myself@ubuntu:~$ arista-gtk
Traceback (most recent call last):
  File "/usr/bin/arista-gtk", line 1417, in <module>
    main = MainWindow()
  File "/usr/bin/arista-gtk", line 398, in __init__
    image = _get_icon_pixbuf(device.icon, width, height)
  File "/usr/bin/arista-gtk", line 109, in _get_icon_pixbuf
    path = arista.utils.get_path("presets", uri[7:])
  File "/usr/share/arista/arista/utils.py", line 75, in get_path
    "path": path,
IOError: Can't find presets/droid.png in any known prefix!
[highlight]What should I do?[/highlight]
It did work before, I've used it many times, it's a great program.
I'm using Ubuntu 10.04 with Gnome 2.30.0

---

### Post by xc3RnbFO8P on 2010-05-15
Go to /home/your foler/**.arista**/present (hidden folder, use Ctrl-H) 
and rename **droid.xlm** to **droid.png**
or contact the Administrators, [http://programmer-art.org/services/](http://programmer-art.org/services/)

---

### Post by BigAndy on 2010-05-15
I also got it to work by going to this location in a terminal:

/usr/share/arista/presets

and riunning this command:

sudo cp pda.png droid.png

This creates a copy of the pda picture to replace the missing picture that is stopping Arista from starting up

---

### Post by wired99 on 2010-05-15
Thank you, thank you!

I decided to try a combination of both suggestions.

I went to ~/.arista/presets and copied droid.xml to droid.png (in case I needed the original back) then I renamed droid.xml to droid.xml.old.

It worked once - it asked to install my devices, to which I said yes.

It did not work the second time.

I looked back on the /preset folder and Arista had made a new droid.xml file.

I simply deleted this new file and it now works again. I guess I'll have to keep an eye on this folder.

Thanks again for both suggestions.

---

### Post by wired99 on 2010-05-15
I kept wondering about the droid.xml file and how it was automatically created by Arista.

I decided to to go back and do exactly as [email]feline@mindless.com[/email] suggested.

It works like a charm. Thanks again.

---

### Post by Wagnarok on 2010-05-23
This worked for me as well with a slight variation on the above solutions.  I copied droid.xml to droid.png, and tried keeping a copy of droid.xml renamed to old.droid.xml just in case.  Arista still wouldn't open until I removed old.droid.xml from ~/.arista/presets altogether.

---

