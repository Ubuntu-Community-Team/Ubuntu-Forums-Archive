---
title: "No multithreading on ARM CPU (python, tar..)"
date: 2019-05-09
forum: Mobile Technology Discussions (CLOSED)
---

### Post by postcd on 2019-05-09
Hello, i am running Ubuntu 16.04.

[system] Platform: linux
[system] Arch: arm
[system] OS Release: 4.9.160-armada375
[system] CPU: ARMv7 Processor rev 1 (v7l)
[system] CPU Logic cores: 2
[system] Total memory: 2019.60 MB

I am using htop and top to monitor CPU usage of the running processes.

I see that my python script is utiliting like around 100% of the CPU. htop visualize only one thread fully utilized and other only sporadically utilized (probably by other processes).
Same for tar (tr -czf) it also used only one CPU thread. I have not tested any other utilities.

Please what i should try to change so processes utilizing multiple CPU threads? Thank you in advance.

---

### Post by TheFu on 2019-05-12
Each process is scheduled to run on a CPU.

If you want a single process to use multiple CPUs, then you'll need to write a multi-threaded application. It is non-trivial and brings all sorts of other complexities into coding like data protection.  Never allow more than 1 thread to write to the same memory or disk file without using a locking mechanism first.  [https://www.toptal.com/python/beginners-guide-to-concurrency-and-parallelism-in-python](https://www.toptal.com/python/beginners-guide-to-concurrency-and-parallelism-in-python) is what google found for writing multi-threaded python.

A common way to see multi-threaded apps work is to calculate pi. Back in the 1990s, when I got my first dual-CPU computer, I also wanted to see it work. Since you don't care about the result, just seeing both cores used, [https://gist.github.com/skeeto/212715](https://gist.github.com/skeeto/212715)

I doubt tar is multi-threaded, since it is either reading from or writing to a file.  A quick google says that libbzip2 is multi-threaded, so if you use that compression, multiple threads should be used.  That would be **tar cjf** options according to the manpage. I didn't test it.  Tar is of limited use these days. I only use tar like I would use ZIP, which is pretty much never.

---

