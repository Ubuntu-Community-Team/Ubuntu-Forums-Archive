---
title: "fglrx driver not installing on Intrepid 8.10 / ATI X2300"
date: 2009-01-10
forum: Multimedia Software
---

### Post by jommoner on 2009-01-10
I have an ASUS Z99J laptop, with a A8JR motherboard, and have just put Ubuntu on it as I am fed up with Vista. The difference in speed and stability is amazing!.

However, I want to go windows-free, and therefore I need proper 3D support. The built-in Free 3D graphics drivers do quite a good job, but cause many glitches on the icons and menus (as well as 3D graphics) on games, especially World of Warcraft :)

I therefore want to try ATIs own closed-source fglrx drivers.

If I click on System -> Administration -> Hardware drivers, it tells me :

No proprietary drivers are in use on this system

And it then has a grey LED next to 'ATI/AMD proprietary FGLRX graphics driver'

At the bottom of the hardware drivers window it says 'This driver is not activated', and there is a button which says 'Activate'.

Clicking on 'Activate' gives a window 'Downloading and installing driver...' which stays at 0%. The hard drive light then flickers for a while, but the window always stays at 0%. Eventually the 0% window disappears, and the Hardware drivers window remains unchanged (telling me the driver is not installed, and so on).

If I click activate again, this time the 'Downloading and installing driver...' window doesn't come up, but the hard drive is active again.

When the hard drive light is active for the above two examples, it is flickering on and off so fast that you can't quite see it, but it looks about half as bright as normal (presumably looking through some internal indexes or something?)

This is a fresh install of Ubuntu by the way - nothing extra added to it as of yet.

I would be grateful for ideas of what to do next - I can type commands into the terminal to get results if that would help!

Thanks for your help :)

---

### Post by markbuntu on 2009-01-10
You need to get all the updates and reboot before installing the restricted driver.

---

### Post by jommoner on 2009-01-10
Thanks for the reply!

I have just got it working fortunately! I managed to install all the updates, but it still wouldn't install. It still did the thing of stayin at 0% then the window vanishing a few minutes later.

I eventually found this thread:

[http://ubuntuforums.org/showthread.php?t=1024846&highlight=X2300](http://ubuntuforums.org/showthread.php?t=1024846&highlight=X2300)

The text it shows at the beginning :
>
>Re: ATI Mobility Radeon X2300 problems
>
>I had excact the same problem when I just changed my laptop to HP 6910p
>but I just solved this probelem.
>
>steps below:
>
>sudo apt-get update
>sudo apt-get dist-upgrade
>sudo apt-get install linux-restricted-modules-$(uname -r)
>sudo apt-get install xorg-driver-fglrx
>sudo depmod -a
>sudo aticonfig --initial
>sudo aticonfig --overlay-type=Xv
>sudo /etc/init.d/gdm restart
>
>(This solution was form [http://terenzioberni.blogspot.com/20...53jr-f3jr.html](http://terenzioberni.blogspot.com/20...53jr-f3jr.html))
>
>-ckh





I typed in those commands, and after the one which says 'restart' at the end, it logged out, but then just hung there. I waited a few minutes, then shut down by pressing the power button briefly (so Linux could do its shutdown process).

On reboot I now seem to have fully functioning 3D, so the above seems to have been a good solution for now :)

Still no idea why the neat GUI install from the Hardware Drivers window wouldn't work though!

Can someone mark this as [Solved]? :)

---

### Post by markbuntu on 2009-01-10
You need to do that yourself with the thread tools at the top of the page.

---

