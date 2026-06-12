---
title: "Issues with irexec and LIRC"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by rsidle on 2008-02-03
I am using Gusty with up-to-date LIRC and am sucessfuly using a MCE remote. What I am trying to do is blast codes to my TV and receiver to change inputs, volume, channels etc. I'm about 90% there. My issue is that when I have Elisa or some other program running, my mappings in .lircrc don't run. When I exit the program, all of the codes that should've been sent get sent all in a burst. Is there some way that LIRC will run commands to irexec regardless of other program that's running? Here's how my whole .lircrc file is written:

begin
prog = irexec
button = mute
config = irsend SEND_ONCE sonyreciever rcvmuting
end

It works perfectly unless some other program is running in the foreground. Thanks in advance!

---

### Post by rsidle on 2008-02-11
bump

---

