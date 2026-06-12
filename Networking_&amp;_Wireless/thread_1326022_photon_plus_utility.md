---
title: "photon plus utility"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by rizwanhudda on 2009-11-14
I m using Tata indicom photon plus connection [ its wireless broadband service], to use it one has to do the following
1) The USB modem is detected as a memory device in the beginning [it contains the manuals and setups], so i have to eject that memory device.
2)I have to go to the terminal 
```

sudo wvdial

``` type this to connect to web.
and then press 
```

CTRL + C

``` to disconnect the connection.

I want to create a shell script, clicking on which it gives me options to connect/disconnect etc..if possible i also want to track the no of MB downloaded uploaded through this shell script.

Thanks in advance.

---

### Post by nirmalraj on 2010-02-23
let me know how to eject/remove the memory module apart from using rmmod usb_storage

---

### Post by 7raTEYdCql on 2010-05-18
Hello rizwanhudda.
If you want to track the amount of mb uploaded and downloaded read about this utility vnstat. Pretty cool. I use it to track my mtnl download/upload amounts.

You from BITS rite. I'm from the Goa counterpart, and heard about your coding skills, keep it up!!

---

