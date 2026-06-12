---
title: "&quot;Motorboating&quot; Sound"
date: 2008-05-02
forum: Multimedia Software
---

### Post by lawtech on 2008-05-02
I'm trying to understand something...Why sound sometimes breaks up in a simple Python program. Please tell me if I'm in the wrong forum.

The program is pTheremin.py. I'm not associated with development of the program. It's here: [http://ptheremin.sourceforge.net/]("http://ptheremin.sourceforge.net/")

On some machines, it runs flawlessly. On others, fast mouse movements will cause "gaps" in the sound, sometimes called "motorboating." All of the machines I've tried are running current Ubuntu 8.04 Desktop.

There is clearly a machine speed issue. Faster machines do better than slower ones, but that is not the only factor. Some slower machines do better than some much faster ones. I've found no machine slower than 2 GHz that works perfectly. I've found a couple of 3+ GHz machines that do not work well. Machines with cheap sound cards and chips often work better than machines with more expensive ones.

Conceptually, this is a simple program. It captures mouse events and generates a variable tone. Surely it should run fine on machines much slower than 2 GHz? Is there so much overhead in this program that it causes motorboating? Why is there so much hardware variability?

As I say, I'm just trying to understand.

---

