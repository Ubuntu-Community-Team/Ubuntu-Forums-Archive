---
title: "google earth very slow after beryl installation"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by f3nol on 2006-12-31
Hi everyone!

i'm quite new to Ubuntu as you can see. I've recenently installed aiglx and beryl with this tutorial [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX")
It works good but since the installation my google earth is very slow with Beryl on or off. I have ATI 9600 card and using Dapper. Does someone know how to fix it? I wouldn't mind to uninstall beryl as I only wanted to see how it works.

Thanks in advance!!

---

### Post by Dieg oTrazzi on 2007-02-06
I have the same problem.
I installed Ubuntu already 5 times in 10 days !!! 
I have a Mobility X300, and I was using Fglx drives with beryl until a couple of weeks ago it stopped working. So I went crazy trying to understand the reason of the error  "Checking for non power of two texture support : failed". Then finally somebody suggested to reinstall Ubuntu and use aiglx instead.
Conclusion. Beryl starts, but is incredibly slow, and Google earth, or any other sw is very slow.
Dam .... 

Please somebody haelp me. I am trying to stay away from WINDOWS and APPLE, but why there are always som many problems with linux ? 

P.s. On top of that, now I cant even Hibernate the laptop no more...

---

### Post by silvagroup on 2007-02-06
Check the Beryl forum. ATI will work, but it doesn't seem to be well favored by Beryl. Seems that it works best with Intel and nvidia. Pretty much the same as Linux overall form what I have read.
Also check [http://www.linux-laptop.net/]("http://www.linux-laptop.net/") for some help on setting up your laptops. It's a different world with *nix and laptops and not all distos work the same in that regard.

---

### Post by ffxr on 2007-02-06
i have had similar issues (with video capture software) and after reading about i think i understand why i have my problems..

the ATI open source driver (used by AIGLX) uses software for 3D acceleration, rather than moving the rendering to the GPU.. it uses the CPU.

So processor intensive tasks (like google earth & vidcap apps.) will put extra load on the CPU resulting in applications running slowly.. m guessing this is the root of the problem... in theory using XGL & the proprietary flgrx driver should move rendering back to the GPU and should allow other processor intensive tasks to run more comfortably..

however, i have found XGL a bitch to set up.. so m investing in a cheap nvidia 6 series card, which i hope will solve my problems... ( i dont know if you have this option )

---

