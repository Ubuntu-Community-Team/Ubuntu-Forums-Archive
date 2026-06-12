---
title: "why no mythfrontend lirc debugger?"
date: 2009-01-29
forum: Mythbuntu
---

### Post by mathog on 2009-01-29
I just spent 20 minutes trying to figure out why this ~/.lirc/mythtv entry:

```
begin
    remote = RM-VL600_8201
    prog = mythtv
    button = ok
    config = space
    repeat = 0
    delay = 0
end

```
wasn't working, and finally figured out that it should have been **Space** instead of **space**.  Sigh.  Ok, that was my mistake, but an incredibly easy (and common) one to make. The hard part is that I didn't know when the changes I was making to the .lirc/mythtv file were taking effect. To test this I had to be watching a recording, fast forward it to get to 3X, and then press the "ok" button.  In the end, to be sure that the changes would "take", I was stopping the frontend, the backend, and lirc, and then restarting them all.  How much of that was actually necessary?

Dear developers, please add this mode:

  Utilies/Setup -> Setup -> lirc debug

Once in that mode, it would echo lirc events and find potential problems, as in the present case:

(press "1" on remote)
in lirc debug
received "1" - valid key
(press "ok" on remote)
in lirc debug
received "space" - unknown key

This would be a lot more user friendly than the present system, which 
tosses a warning message into /var/log/mythtv/mythfrontend.log.

lirc debug would also have options to show all the keys that have a defined meaning somewhere in Mythtv, and to reload whatever needs to be reloaded to pick up .lirc/mythtv changes.

Yes, I know about:

 cd ~/.lirc
 cp mythtv lirc_test
 nedit lirc_test #change all mythtv -> lirc_test
 ircat --config=.lirc_test lirc_test

In this case it wasn't helpful, because I wasn't picking up on the
case sensitivity.  It just said "space", which was right (according
to the lirc_test file) but wrong (according to mythtv, and probably every other application.)

Thanks

---

