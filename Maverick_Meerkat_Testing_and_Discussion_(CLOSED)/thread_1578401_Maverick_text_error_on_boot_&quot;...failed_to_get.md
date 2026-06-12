---
title: "Maverick text error on boot: &quot;...failed to get i915 symbols, graphics turbo disabled&quot;"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by shuttleworthwannabe on 2010-09-20
I have Dell vostro 3700 running Maverick beta 10.10 updated daily. It has nvidea GForce 330m card with turbo mode; I have notice this error message on boot up (after the grub menu). I initially thought it would go away with every update, but since 14 Sept 2010 dailyinstall, it has been there. Any way to resolve this problem, if it is a problem at all. Also note, the screen works fine and drivers are installed through the restricted extras hardware settings.

Thanks
S

---

### Post by emanuelgreisen on 2010-09-20
I have a Macbook Pro6,1 with the same graphics chip and see the same message.

At first I followed the instructions on the Mactel Ubuntu Wiki telling me to set the following:

```
        Option  "Coolbits" "1"
        Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x3; PowerMizerDefaultAC=0x3"
```

This in effect resulted in the all graphics in X to be so infinitely slow. Disabling and re-enabling nvidia (thus getting rid of the xorg.conf file) I now have excellent graphics and according to nvidia-settings the GPU is now adaptive and changes frequency.

So what ever this is it is not keeping the NVidia driver from scaling the frequency of the GPU.

---

### Post by shuttleworthwannabe on 2010-09-20
> **emanuelgreisen said:**
> I have a Macbook Pro6,1 with the same graphics chip and see the same message.

At first I followed the instructions on the Mactel Ubuntu Wiki telling me to set the following:

```
        Option  "Coolbits" "1"
        Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x3; PowerMizerDefaultAC=0x3"
```

This in effect resulted in the all graphics in X to be so infinitely slow. Disabling and re-enabling nvidia (thus getting rid of the xorg.conf file) I now have excellent graphics and according to nvidia-settings the GPU is now adaptive and changes frequency.

So what ever this is it is not keeping the NVidia driver from scaling the frequency of the GPU.

Thanks for the response--but, what do I do with the code? and also do you have direct link to the wiki?

I am assuming we add the code to xorg.conf file???

S

---

