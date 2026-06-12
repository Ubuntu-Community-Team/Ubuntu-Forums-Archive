---
title: "fglrx disabled Unity, how to re-enable?"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by fett2k on 2011-04-21
Actually this isn's just about reenabling it, if you can help me more than that.

I have a HP g62 a40SP, with a ATI Mobility Radeon HD 5470. Since I installed Ubuntu, it overheats as hell (first intalled here was Maverick). Updated yesterday to Natty, and I read somewhere that fglrx was already working relatively fine with Natty and 30º below my 75-80º, so I installed fglrx... Resulting in disabling Unity with a message telling me I don't have the hardware needed to Unity.

I tried to disable fglrx, disabled and reenabled Unity on compiz, and nothing, I'm in Ubuntu session (supposed to run Unity, right?) running gnome-panel, and still on 75º.

How to reenable Unity? Still kind of noob on linux, so...
Thanks for all/any help!

EDIT: i'm on 32bit, and if I try to run Unity from the terminal it ends with segmentation fault...

---

### Post by fett2k on 2011-04-21
er... Uninstalled fglrx through "sudo aptitude remove --purge fglrx" and I'm on Unity again. Weird stuff going on.

---

### Post by screaminj3sus on 2011-04-21
hmm, what method did you use to install fglrx? Was it the one from the repos? Did you use Jockey?


try:

sudo apt-get install fglrx
sudo update-alternatives --config gl_conf (and select the line with fglrx)
sudo update-initramfs -u

---

### Post by fett2k on 2011-04-21
It's exactly what I did...
Was I supposed to install Jockey?

---

### Post by screaminj3sus on 2011-04-21
Either way *should* work

Jockey is preinstalled its the "additional drivers" tool.

---

### Post by xgt001 on 2011-04-21
> **fett2k said:**
> Actually this isn's just about reenabling it, if you can help me more than that.

I have a HP g62 a40SP, with a ATI Mobility Radeon HD 5470. Since I installed Ubuntu, it overheats as hell (first intalled here was Maverick). Updated yesterday to Natty, and I read somewhere that fglrx was already working relatively fine with Natty and 30º below my 75-80º, so I installed fglrx... Resulting in disabling Unity with a message telling me I don't have the hardware needed to Unity.

I tried to disable fglrx, disabled and reenabled Unity on compiz, and nothing, I'm in Ubuntu session (supposed to run Unity, right?) running gnome-panel, and still on 75º.

How to reenable Unity? Still kind of noob on linux, so...
Thanks for all/any help!

EDIT: i'm on 32bit, and if I try to run Unity from the terminal it ends with segmentation fault...
same problem here mate... unity working with fglrx but too sluggish..
i have hp g42 which has ati radeon hd 6370m
to get unity with fglrx i downloaded the drivers through additional driver app and then rebooted... worked.. but extremely sluggish compared to the fast open source drivers
regarding the heating well the main reason i installed fglrx was because natty's oss drivers were pretty bad at power management, and cooling..but i must agree that it dint fix the issue completely ...

---

### Post by fett2k on 2011-04-21
well, without fglrx it worked for me, though the temperature problem. but now i can't boot ubuntu :S
i already had this problem several times, never understood what the problem was. stopped trying to solve it since i needed ubuntu to work - now i dont for another week or so, so i updated... and now i can't boot.
well, i suspect it has to do with the graphics card - without fglrx. going to open another topic, since this isnt about unity anymore for me.

but well if i find how to solve that problem (wich i doubt) ill keep you updated :)

thanks for the help!

---

### Post by el_koraco on 2011-04-21
Don't wanna get you down, but the last two times I tried to enable and subsequently purge fglrx on my Mobility Radeon 4200 with Maverick (lol for the temperature handling, and lol for fglrx causing my system to go into memory overload), I ended up having every third boot end up in a broken screen. 

The only option that seemed usable was to reinstall (and install Kubuntu the last time that happened). Now i just leave it alone.

---

### Post by fett2k on 2011-04-21
after digging and digging for a solution i found nothing too understandble by me at this point... i removed the quiet splash option from grub to see if i got something telling me it was ATI, and it just booted o_O ill try to leave it alone...

time for me and tux get to know each other a lot better than till now.

sry about this going off topic

---

### Post by aeronutt on 2011-04-21
> **el_koraco said:**
> Don't wanna get you down, but the last two times I tried to enable and subsequently purge fglrx on my Mobility Radeon 4200 with Maverick (lol for the temperature handling, and lol for fglrx causing my system to go into memory overload), I ended up having every third boot end up in a broken screen. 

The only option that seemed usable was to reinstall (and install Kubuntu the last time that happened). Now i just leave it alone.

I've had the same experience trying to install fglrx for a mobile AMD HD6630 GPU.  I'm getting poor compiz performance as is.

---

### Post by screaminj3sus on 2011-04-21
> **xgt001 said:**
> same problem here mate... unity working with fglrx but too sluggish..
i have hp g42 which has ati radeon hd 6370m
to get unity with fglrx i downloaded the drivers through additional driver app and then rebooted... worked.. but extremely sluggish compared to the fast open source drivers
regarding the heating well the main reason i installed fglrx was because natty's oss drivers were pretty bad at power management, and cooling..but i must agree that it dint fix the issue completely ...

> **aeronutt said:**
> I've had the same experience trying to install fglrx for a mobile AMD HD6630 GPU.  I'm getting poor compiz performance as is.

Make sure to disable sync to vblnak in ccsm or unity will be very slow with fglrx. It seems to be enabled by default.

---

