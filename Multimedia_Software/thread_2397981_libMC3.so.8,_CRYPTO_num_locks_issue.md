---
title: "libMC3.so.8, CRYPTO_num_locks issue"
date: 2018-08-06
forum: Multimedia Software
---

### Post by keerthirajp on 2018-08-06
Hello everyone,
I am really glad to join the world of linux. But rt now I am stuck with an error.

I installed Autodesk maya and tried to open it via terminal. Then i got the following error.. 

"/usr/autodesk/maya2015-x64/bin/maya.bin: symbol lookup error: /usr/autodesk/maya2015-x64/bin/../lib/libMC3.so.8: undefined symbol: CRYPTO_num_locks"

I am using Ubuntu 18.04.1 LTS

Can anyone please help....

---

### Post by mariano4ka555 on 2019-01-02
It works for me

 sudo ln -sf /usr/lib/x86_64-linux-gnu/libssl.so.1.0.0 /usr/autodesk/maya2015-x64/lib/libssl.so.10

---

