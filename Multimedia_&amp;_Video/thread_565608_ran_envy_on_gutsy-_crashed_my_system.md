---
title: "ran envy on gutsy- crashed my system"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by thorezzz on 2007-10-02
I was ofcourse tempted to update my X with envy, and since I'm running Gutsy I followed this guide [http://albertomilone.com/wordpress/?p=107](http://albertomilone.com/wordpress/?p=107) , and ofcourse it had to go wrong. Envy installed fine and told me to reboot the computer, and I did.

At startup, i see the usual ubuntu progress bar and when its done loading, the screen goes black, almost sounds like the monitor just switches off. I tried running it without splash, but nothing really out of the ordinary. I tried both generic and 386 kernels, and to switch to another log in thingy without X or gdm, like (ctrl+alt+F1)- I got a Geforce fx 5200.

dont know what else to say...I'm a noob :(

---

### Post by thorezzz on 2007-10-02
I fixed it by removing nvidia-glx (the old version) with apt-get and rebooting :)

i feel good now

---

