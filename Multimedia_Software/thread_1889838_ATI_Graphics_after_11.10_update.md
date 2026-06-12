---
title: "ATI Graphics after 11.10 update"
date: 2011-12-02
forum: Multimedia Software
---

### Post by christophski on 2011-12-02
I have a fanless ATI graphics card running two 1920x1080 monitors. Before the update, graphics were a dream, smooth and quick but now after the update the graphics are very choppy, even when scrolling in firebox. I can't run ardour properly because the ui is too slow and if I want to watch 1080p video I have to disable one of the screens or the frame rate is so bad it is unwatchable. I have always used the open source drivers and in ubuntu 11.04 I could do all these things fine. Has anybody got an idea of how to fix it?

---

### Post by christophski on 2011-12-04
nobody?

---

### Post by collisionystm on 2011-12-04
Install the catalyst 11.11 drivers


[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

---

### Post by kaldor on 2011-12-04
Not a solution, but I reported a similar issue on Launchpad a couple of days ago. Using a 12.04 daily build is very broken. Since 12.04 uses the same version of Unity as 11.10, our issues might be identical. Which graphics card are you using?

Link to my report [_here_]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/898963"). If it's the same problem, then add yourself to the "affected" list.

---

### Post by MoreOrLess on 2011-12-04
Pastebin your /var/log/Xorg.0.log

---

### Post by christophski on 2011-12-06
@collisionystm: I will give it a go, but I have never had luck with closed drivers.

@kaldor: I have this graphics card: [http://www.aria.co.uk/Products/Components/Graphics+Cards/ATI+4000+Series/Asus+ATI+Radeon+HD+4350+512MB+DDR2+PCI-Express+Graphics+Card+?productId=37477](http://www.aria.co.uk/Products/Components/Graphics+Cards/ATI+4000+Series/Asus+ATI+Radeon+HD+4350+512MB+DDR2+PCI-Express+Graphics+Card+?productId=37477)

It is driving 2 1920x1080 monitors. it used to be able to do this fine under 11.04 with Gnome 2, but now with 11.10 and unity performance is far worse. My computer is Intel Core i7 2.8GHz with 6GB RAM and unity is very slow, I expect more from a computer like this.

For the moment I have switch to unity-2D and I am finding it far far more responsive and has a much quicker log-in time too (another problem I've had with 11.10, long log-in time).

We had a discussion about this on reddit and somebody pointed me towards this bug which I think my be contributing to what I am experiencing: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/861061](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/861061)

@MoreOrLess: [http://pastebin.com/5gRgY93D](http://pastebin.com/5gRgY93D)

---

