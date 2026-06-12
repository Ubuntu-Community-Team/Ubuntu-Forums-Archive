---
title: "Update issues"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2010-09-02
Tried to update 10:04 this morning and kept getting an error with the "lock file". I tried with both the update manager and the synaptic package manager and got the same error.

I have attached a copy of the error.

Does anyone know whats happening and how to fix it?

---

### Post by BkkBonanza on 2010-09-02
A lock file like that is generally used to prevent multiple similar programs from making concurrent changes to their files. It could be left locked if one of the programs was terminated abruptly and didn't unlock (remove the file).

You could try **ls -ls /var/cache/apt/archives/lock** to see the details of the file and when it was last created/changed.

If you are sure that no other process is still manipulating the apt cache archive then you might try removing that file (or renaming it). I think it would be safer to reboot first to be sure something isn't lingering.

You may also want to browse the process list and see if some process related to updating is still running.

---

### Post by Jonny87 on 2010-09-05
> **BkkBonaza said:**
> A lock file like that is generally used to prevent multiple similar programs from making concurrent changes to their files. It could be left locked if one of the programs was terminated abruptly and didn't unlock (remove the file).

You could try **ls -ls /var/cache/apt/archives/lock** to see the details of the file and when it was last created/changed.

If you are sure that no other process is still manipulating the apt cache archive then you might try removing that file (or renaming it). I think it would be safer to reboot first to be sure something isn't lingering.

You may also want to browse the process list and see if some process related to updating is still running.

Thanks for the info, that must have been what it was as I tried it agian once I got home (before I had seen your reply) and it worked fine and has done since. Thanks for filling me in though, good to learn these things.

---

