---
title: "[SOLVED] no response from record button"
date: 2008-09-29
forum: Mythbuntu
---

### Post by iitywygms on 2008-09-29
When I press r on the keyboard, live tv start to record.
If I press rec on the remote, nothing happens.
Here is the relevant portion of my lircrc.

begin
remote = mceusb
prog = mythtv
button = RecTV
config = R
repeat = 0
delay = 0
end

here is output for irw

000000037ff07be8 00 Record mceusb

What gives?

mythbuntu with 8.04.01 latest updates

---

### Post by anonymousdog on 2008-09-29
The relevant portion of ~/.mythtv/lircrc needs to refer to the button as "Record" vs. "RecTV".  Other lirc configuration (like ~/.lirc/mythtv files may override that setting (IDK); so, you may need to modify those too.

---

### Post by iitywygms on 2008-09-29
button=Record

fixed.

Thank you.

---

