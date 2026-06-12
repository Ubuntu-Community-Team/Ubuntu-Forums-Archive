---
title: "myth 8.04 boot up issue help"
date: 2008-11-14
forum: Mythbuntu
---

### Post by zf3636 on 2008-11-14
I get this message when i turn my pc on /dev/sda1/ Routine check of drives Press Esc to skip/dev/sda1/. I also updated the system prior to this without restarting the pc,I transferred some music aswell as installed a program through supnaptic manager.
after 30 sec i get the following result Checking drive /dev/sda1:60% (stage 1 to 5,246/288)
(Attempt to read block from file system resulted in short read) while reading indirect blocks of inode 2017665.Error reading block 8093031.
/dev/sda1/:UNEXPECTED INCONSISTENCY RUN fsck MANUALLY. 
fsck died with exit status 4 fail
(ie,without -a or -p options)
An automatic file system check (fsck) of the root file system failed
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root file system mounted in read only mode.
The root file system is currently mounted in read only mode
A maintenance shell will now be started 
After performing system maintenance, press CONTROL -D to terminate shell
and restart the system.
bash:no job control in this shell
bash:groups:command not found
bash:lesspipe:command not found
bash:Command:Command not found 
bash:The:command not found
bash:dircolours:command not found
bash:Command:command not found. 
please can any one help, or ideas thx zf3636.

---

### Post by anonymousdog on 2008-11-14
You will probably be able to fix it with a standard 'fsck /dev/sda1' once in the maintenance shell.  The default mode asks you questions about how to fix the file system.

Overall, though, unless you had a loss of power, you probably have a failing hard drive, power supply or drive controller.

---

### Post by zf3636 on 2008-11-15
thanks for reply, will check this out mythbuntu works when i press Esc

---

### Post by zf3636 on 2008-11-15
Thanks anonymousdog did the following fsck/dev/sda1 and then followed the prompts y/n and then restarted my pc and loaded up as normal Thanks again for your help zf3636.

---

