---
title: "Understanding sshfs working !"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by siddukirk on 2010-03-30
Hello everyone,

I am curious to know how the sshfs works !

Here is the scenario on my comp i am trying to understand 

1. I have minix operating system running on qemu (it has sshd running within it)
2. its root directory is mounted on my host(ubuntu 9.10) using the below command 
   sshfs -p2002 root@localhost:/ ~/minix
3. now i am able to edit files and run all the linux commands (which most of them minix doesnt have for ex : du -sh # h is not supported) on that folder(~/minix) seamlessly

my question is ...

how is it that remote server (sshd) able to answer all of my commands ?
or if not remote sshd what else is that which comes into play ?

Please help me understand

---

