---
title: "Got a new Geforce 8600 GT, still jerky?"
date: 2009-12-19
forum: Multimedia Software
---

### Post by Don Scapp on 2009-12-19
Hi there,

I recently upgraded my old Nvidia Geforce 6150 SE to a Geforce 8600 GT (still old, but should be fine) and I'm still experiencing slow fps compiz and SuperTux2. I am comparing my performace with Mandriva 2010, and although I realize it is a different distro, I am very impressed with the speed and their grpahics, and would desperatly like my Ubuntu to benefit from the same speed. Is there anything I can try that might make things work smoother, in particular, the desktop spinning cube is really smooth on mandriva, but is very jerky on ubuntu, and the wobbly windows aren't as fluid looking. SuperTux is also quite jerky and just doesn't seem as smooth as it should be.

Thanks in advance,

Don.

---

### Post by jerrrys on 2009-12-19
hope you didnt get stuck with a made in china 8600, they are known for problems...

---

### Post by Don Scapp on 2009-12-19
Yes, I think it might be made in china, but I'm quite suprised that I'm having the exact same problem as I was before, unless nvidia cards generally function like this? What kind of performance should compiz usually function at under ubuntu?

---

### Post by jerrrys on 2009-12-19
i have an older computer with a 5200 pci card in it.  although compiz runs on it, the results were poor and i stopped using it.  could be pci-e is the way to go with compiz...

---

### Post by Don Scapp on 2009-12-19
Yeh, this is a PCI-E card, but what I don't understand is why Mandriva is absolutly fine with both the old geforce6 and the slightly newer geforce8. I'm not trying to mention mandriva for any reason other than it works perfectly, and I would LOVE it if Ubuntu could be just as smooth, responsive and work as well. I tried the backfill hack, and even thou I think I installed it right, everything went white, I could only access the menus by wildly clicking around, and it didn't even seem quicker. Had to reinstall after that, and Im not aware if there are any other methods for fixing slow compiz/games that rely on fast graphics. SuperTuxKarts and ExtremeTuxRacer seem fine, but SuperTux2 is just not very smooth.

---

### Post by jerrrys on 2009-12-19
ok, theirs an old program floating around that may pin down the problem.  it will check compiz settings a generate a report.  it will not work on all computers, but would be worth a shot if i could remember the name of it.  im not on my computer right now or i could look it up in my files.  maybe someone reading this knows the name

also, simon and g fan?  so are we...

---

### Post by jerrrys on 2009-12-19
found it, first one

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=check+compiz+settings&as_qdr=all&sa=Google+Search&lang=en#998](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=check+compiz+settings&as_qdr=all&sa=Google+Search&lang=en#998)

---

### Post by Don Scapp on 2009-12-19
Thankyou, I shall give it a run and report back!

---

### Post by Don Scapp on 2009-12-19
Hi, I ran the checker, and it gave me this output:

> Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]



So, everything looks okay. Should I try and build compiz on my installation, or will that not make any difference? I also have and am using compiz fusion icon, but that didn't make any difference.

---

### Post by jerrrys on 2009-12-19
my limited knowledge of compiz is now exhausted.  i would suggest letting this thread die and starting a new one with **compiz settings** in the title and see if that draws the attention of a compiz wizard...could even give it a link to this one...good luck

---

### Post by Don Scapp on 2009-12-20
Thanks for your help, I'll give that a go and see if someone can help!

---

### Post by Don Scapp on 2009-12-30
I found, the whole thing is caused by the default drivers Display settings being 65hz, and is simply fixed by adjusting the settings under Compiz refresh rate/detect refresh rate section!

Thanks to all who helped!

(I've also used posted this solution on my other older threads in case anyone stumbles across them in the future.)

---

