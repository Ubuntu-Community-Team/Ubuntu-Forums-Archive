---
title: "Ubuntu freezes  after installing any nvidia driver"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by Amorphous_Snake on 2006-07-10
I have a GeForce 4 MX 440. Whenever I install any driver for it, from any source: Automatix, Easy Ubuntu, legacy driver or the latest normal driver, the system would then freeze when I use some programs like Firefox.

I have seen people complaining about this problem when they run a screesaver or something graphical, but this didn't happen to me. I tried running screesavers and they worked fine.

The nvidia driver was the only thing that I installed, so I don't thing it's a conflict from any other program.

The freezing happen on visiting web sites.

The problem happened when I was trying another distro: OpenSUSE 10.1, again after installing the drivers.

I am a Linux newbie and I have asked this question many times under the Beginners' forum, but no one could help me.

I have Ubuntu 5.10.

---

### Post by tseliot on 2006-07-10
Try point 4 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Breezy#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Breezy#PROBLEMS_SECTION)

---

### Post by Amorphous_Snake on 2006-07-12
Thanks a lot TSELIOT. IT WORKED! My Linux future is safe! I can now upgrade to 6.06.

But I have a few questions:
1- What was the cause of the problem?
2- How did you solve it?
3- Will the lines that I enterd reduce the 3D rendering abilities of my card, and will it affect the TV-out connection (I did spot the word "Composite")?

Thanks you again, and God bless you.

---

### Post by tseliot on 2006-07-12
> **Amorphous_Snake said:**
> Thanks a lot TSELIOT. IT WORKED! My Linux future is safe! I can now upgrade to 6.06.

But I have a few questions:
1- What was the cause of the problem?
2- How did you solve it?
3- Will the lines that I enterd reduce the 3D rendering abilities of my card, and will it affect the TV-out connection (I did spot the word "Composite")?

Thanks you again, and God bliss you.

It's a bug in the driver, I suppose. I didn't fix it. Nvidia's staff suggests this fix on their forums

---

### Post by Amorphous_Snake on 2006-07-12
Thanks, but what about the rest of the questions?

Also, if I install the new Ubuntu, and decided to install the latest nvidia driver, will I have to change the gcc and all that stuff in your Method 2? And what's gcc by the way?

I guess by now, you have guessed that I am a complete Linux newbie!

---

### Post by tseliot on 2006-07-12
> **Amorphous_Snake said:**
> Thanks, but what about the rest of the questions?

Also, if I install the new Ubuntu, and decided to install the latest nvidia driver, will I have to change the gcc and all that stuff in your Method 2?
Only if Method 2 suggests it. Using my script will save you much time

> **Amorphous_Snake said:**
> And what's gcc by the way?
a compiler (for further information look it up in google)

> 3- Will the lines that I enterd reduce the 3D rendering abilities of my card, and will it affect the TV-out connection (I did spot the word "Composite")?

No

---

### Post by Amorphous_Snake on 2006-07-18
I installed Ubuntu 6.06 and downloaded the latest driver through your Method 1 (I didn't know it was that easy!!!). Then when the freezing happened again, I tried the lines you told me to use.

> BusID "PCI:1:0:0" 
Option "NvAGP" "0" 
Option "RenderAccel" "Off" 
Option "IgnoreDisplayDevices" "DFP,TV" 
Option "NoRenderExtension" "Off" 
Option "AllowGLXWithComposite" &#8220;Off&#8221;

But then I couldn't log into the graphical interface and Xorg crashed. I discovered the problem was due to the line BusID, which I also discovered that I didn't write in my first attempt in message 3 above. I removed the line, and everything worked.

I then tried to connect to my TV and I got nothing. So, I decided to play a little with the lines and found that the freezing problem can be fixed just by adding the line **Option "NvAGP" "0"** and you don't need the rest of the lines. but I didn't try the TV yet. But I am pretty sure that it will work.

I will let you know whem I try it.

Again: THANKS Tseliot, without a solution to the freezing problem, my Linux "expedition" would have come to an end!

---

