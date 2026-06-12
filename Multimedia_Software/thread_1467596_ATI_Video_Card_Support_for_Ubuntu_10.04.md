---
title: "ATI Video Card Support for Ubuntu 10.04?"
date: 2010-04-30
forum: Multimedia Software
---

### Post by h3x22 on 2010-04-30
Ok so I just downloaded the new Ubuntu 10.04 and I have an ATI 4890 Graphics Card The last time I tried downloading the drivers of the little Ubuntu Hardware finder it gave me a black screen and I didn't know what to do so I deleted the partition. This time I researcher up on it a little and found this app called "EnvyNG". It's supposed to download the drivers for me in a easy and safe way. I have been having problems with download the app from the Ubuntu Universe suppository (Example)- 

```
“sudo apt-get install envyng-core envyng-qt”
why it shows the message:
Reading package list…Done
Building dependency tree
Reading state information…Done
E: Couldn’t find package envyng-core
```


even though the repository won't work I found people who did get it still had the black screen problem. From all the reading up I did on it, it seemed very confusing-

[https://wiki.ubuntu....ithRadeonDriver](https://wiki.ubuntu....ithRadeonDriver)

Also I do have the Ubuntu Universe suppository checked off and working so I really don't know what to do. I would just like to know what the most easy way is to make my ati 4890 driver to work in Ubuntu, I don't care how it's done I just need to know in a simple and easy fashion (maybe screenshots).

Anyways please I'm new to Linux an would love to use it if it only worked for me 

Thanks. :(

---

### Post by alphacrucis2 on 2010-04-30
> **h3x22 said:**
> Ok so I just downloaded the new Ubuntu 10.04 and I have an ATI 4890 Graphics Card The last time I tried downloading the drivers of the little Ubuntu Hardware finder it gave me a black screen and I didn't know what to do so I deleted the partition. This time I researcher up on it a little and found this app called "EnvyNG". It's supposed to download the drivers for me in a easy and safe way. I have been having problems with download the app from the Ubuntu Universe suppository (Example)- 




Either use the administration/hardware drivers method (strongly recommended), or install the Catalyst 10.4 driver from AMD's website which they released a couple of days ago (carefully following their instructions). Forget what happened in earlier versions.

---

### Post by h3x22 on 2010-04-30
Thanks it worked.

---

