---
title: "help choosing a upnp media server"
date: 2010-02-14
forum: Multimedia Software
---

### Post by Chrisoldinho on 2010-02-14
Hi all,

Tomorrow i get my hands on an old dell optiplex gx620 that i plan to use as a media server. i have tried in a vmware environment freenas and openfiler however neither will allow me to create a dual boot environment for occassional browning on Ubuntu.

Therefore I am going to install Ubuntu and some form of media server inside. I will be sharing media to a PS3 and an Xbox 360.

I understand that mediatomb is freeware and supports the ps3 but not the 360. i understand twonkyvision supports both and i am prepared to pay for this however is it the only option that supports both the 360 and the PS3? 

Also as this is new to me how do you manage the shares using twonkyvision and is it fully supported in ubuntu 9.10 x86/x64?

Sorry for so many questions, just want to make the right choice!!

Chris.

---

### Post by Jose Catre-Vandis on 2010-02-14
Try ushare - in the repos, light and simple, AFAIK, works with both.

---

### Post by sondo2121 on 2010-02-15
I have had very good luck with PMS (PS3 Media Server).  I did have to compile it for my system, but it works well.

I have a PS3 where I stream all of my content from my Ubuntu Server.  I just recently (1 week ago) converted from Windows Server 2003 to Ubuntu on my server.

Let me know if you have any questions as I just went through all of that.

---

### Post by Chrisoldinho on 2010-02-15
Thanks for the advice.

I will try ushare, failing that I will go for twonkymedia - any guides on how to install this? (i'm new to linux).

---

### Post by Jose Catre-Vandis on 2010-02-15
> **Chrisoldinho said:**
> Thanks for the advice.

I will try ushare, failing that I will go for twonkymedia - any guides on how to install this? (i'm new to linux).


[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

You need to enable Xbox and DNLA in the config file

---

### Post by Xkutzy on 2010-02-15
Just a quick word of warning about the Optiplex GX620. I have the small form factor version (not the ultra small) and the thermal design of the case isn't great. The CPU fan blows the hot air straight over the HDD. The result is that in standard configuration the HDD runs hot, >50 celcius on a mild day. I haven't found a good way to control the fan in Windows or Linux, but stangely i8kutils does increase the minimum fan speed by enough to drop the HDD temp about 10 degrees. The increased noise may be an issue if you are planning on installing your media server near the TV/HiFi.
Other than that the GX620 is a nice bit of kit that runs Ubuntu just fine.

---

### Post by Chrisoldinho on 2010-02-15
thanks everyone for the responses so far. ill let you know how i get on...

---

