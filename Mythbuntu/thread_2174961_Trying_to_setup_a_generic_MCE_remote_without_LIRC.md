---
title: "Trying to setup a generic MCE remote without LIRC"
date: 2013-09-17
forum: Mythbuntu
---

### Post by Dan_Beaudet on 2013-09-17
Hi, I've pored over quite a few write-ups on how to setup an IR remote without LIRC using ir-keytable and custom keymaps. I can't get it to work properly. The remote *mostly* works but not all the keys are working, which I understand is not an uncommon problem which can be solved by creating a custom ir_keytable mapping (in my example, a table based off rc-rc6-mce). This isn't about how to setup a custom keymap, though.

What I'm finding odd is when I run "ir-keytable -t" the output from my remote doesn't look like I see in any of the write-ups I've seen.

Here is my sample:

ir-keytable -t
Testing events. Please, press CTRL-C to abort.
^[[A
^[[B^[[C^[[D
...

And on various write-ups I see that the output should look something like this:

ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1304995824.617619: event MSC: scancode = 7cb3
1304995825.030592: event MSC: scancode = 7cb4
1304995825.380603: event MSC: scancode = 7cb5
...

I've tried configuring the remote on mythbuntu 12.04.03 and on ubuntu 13.04. The ouput from the ir-keytable test is identical, which is key presses yielding [[B, the circle with the line through it when hitting the play button, and the numbers, which work fine. 

Here is what the remote looks like using ir-keytable:

Found /sys/class/rc/rc0/ (/dev/input/event9) with:
    Driver ene_ir, table rc-rc6-mce
    Supported protocols: NEC RC-5 RC-6 JVC SONY SANYO LIRC other 
    Enabled protocols: RC-6 
    Repeat delay = 500 ms, repeat period = 125 ms


I've spun my wheels for a while before deciding to post here. I'm new to linux so I wouldn't be surprised if I'm overlooking something.

Thanks for any assistance.

Dan

---

### Post by Dan_Beaudet on 2013-09-17
Strange that I had an epiphany after posting this...I discovered that event9 is actually my IR receiver, so no wonder I was getting strange output using ir-keytable -t. 

The generic MCE remote is actually being recognized as a keyboard, so I will now look at creating a custom keyboard map for the "usb keyboard" that is my MCE remote.

---

