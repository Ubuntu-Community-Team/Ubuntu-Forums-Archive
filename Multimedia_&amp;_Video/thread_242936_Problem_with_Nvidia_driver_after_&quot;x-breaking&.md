---
title: "Problem with Nvidia driver after &quot;x-breaking&quot;"
date: 2006-08-24
forum: Multimedia &amp; Video
---

### Post by Eleka on 2006-08-24
Hello all!

I have the famous Xorg break a days ago.

After read all the forums and fix my problem, I find that I have no hardware acceleration on my nvidia card.

My config is the same as three days ago when it works all correctly and I had 8000-9000 FPS ... but now, I only have 3000 FPs and I can't run compiz :(

My device section on my xorg.conf is that:
```
Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    Option         "NoLogo"
EndSection
```

And I attach my glxinfo output, I try to reinstall the driver (uninstalling and installing agains the packages nvidia-glx and nvidia-kernel-common with all its dependancies and my running kernel restricted modules ...

---

### Post by Eleka on 2006-08-24
Well, I'm working on fix that problem.

Now, I changed only one thing: from the /etc/gdm/gdm.conf-custom I commented the lines about Xgl with # and now, when I start my Gdm, it have hardware acceleration and about 7500 FPS, but I have not possibility of run Xgl or compiz ...

How can I fix it?

---

### Post by Eleka on 2006-08-25
I saw that my problem is not very popular, because I don't find anybody with the same problem ...

Today I have tried to do a fresh install of Ubuntu in other partition and I obtained the same result as in my original Ubuntu: when I don't run Xgl, I have a well hardware acceleration, but when I run Xgl, I have not direct rendering, my FPS went down to 3500 and my Compiz don't work :(

Anybody have a solution or is in the same situation?

---

### Post by Eleka on 2006-08-25
Well, I have a solution ... the answer is: I'm a stupid man! 

I didn't saw the changes necessaries on the startup script for compiz and I were running it with more options that it needed ... and then make me broken my head

Excuse me for the post (I don't know how delete it)

---

