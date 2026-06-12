---
title: "muse sequncer works in 16.04, crashes in 18.04 upgrade - anyone succesful? &quot;SOLVED&quot;"
date: 2019-02-07
forum: Multimedia Software
---

### Post by RobertoRecordo on 2019-02-07
I was in the process of learning to use the muse-sequencer [http://www.muse-sequencer.org/](http://www.muse-sequencer.org/)
I think it is easier to use than Ardour or Qtractor for the midi editing that I need. I was having no problems with it until I upgraded from Ubuntu Studio 16.04 to 18.04
Now it is crashes ( core dump) and never gets beyond the start up splash screen unless I disable loading plugins.

I am getting good help with this on the  muse-sequencer forum, 
        [https://linuxmusicians.com/viewtopic.php?f=61&t=19546&p=102127#p102127](https://linuxmusicians.com/viewtopic.php?f=61&t=19546&p=102127#p102127)
 but they can not tell me if this is generally a problem with 18.04

I would like to know if anyone in this group has been able to run MusE on Ubuntu Studio 18.04 without problems. It may help me decide what to do next

Thanks!

---

### Post by RobertoRecordo on 2019-02-28
This "known problem" was solved by downloading a newer version.

I got help on the muse-sequencer forum
> Please try the git master version of MusE.
[https://github.com/muse-sequencer/muse](https://github.com/muse-sequencer/muse)
As shown on that page, it is typically pulled from a command line while in some desired source folder with this command:
"git clone [https://github.com/muse-sequencer/muse.git](https://github.com/muse-sequencer/muse.git)"


Muse-Sequencer is working well now.

---

