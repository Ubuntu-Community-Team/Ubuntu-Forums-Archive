---
title: "glxgears: high fps, gears spin slowly ?"
date: 2005-11-01
forum: Multimedia &amp; Video
---

### Post by Biased turkey on 2005-11-01
I have 2 rigs with Ubuntu 5.10
rig 1 has an ATI Radeon 9600 and Athlon XP
rig 2 has a Geforce 6600 and AMD64.
On both systems I installed the hardware 3D acceleration drivers by following the ubuntu documentation  BinaryDriverHowto
glxgears -printfps returns respectively 3400 and 3900 fps but the gears are spinning so slooooowly that I thought something was rong with the drivers.
Then I installed UT on both systems and UT runs nicely ( I don't know how to enable fps display in UT )
Gentoo on rig 2 give the same value for glxgears ( 3900 ) but the gears are spinning **a lot faster**
Does anyone has an explaination ? Is it because by default the Ubuntu drivers enable vertical sync ?
tia for any info.

B.T.

---

### Post by Joh_ on 2005-11-01
They simply just don't spin the gears as much per frame. For example, instead of making it spin 1 degree per frame, they might've made it spin 20 degrees a minute or similar. It still writes with the fps it states, just doesn't spin faster that way, but the smoothness of higher fps still remains.

---

### Post by Biased turkey on 2005-11-01
[QUOTE=Joh_]They simply just don't spin the gears as much per frame. For example, instead of making it spin 1 degree per frame, they might've made it spin 20 degrees a minute or similar. It still writes with the fps it states, just doesn't spin faster that way, but the smoothness of higher fps still remains.[/QUOTE]

Your wise answer is so  simple that  ...  I never thought of that.
I was already suspecting a hidden bug or some hidden default values in xorg.conf  lol
Now I'm reassured.
And of course, the most important is that real  3D applications like UT  run nicely

Thanks.

---

