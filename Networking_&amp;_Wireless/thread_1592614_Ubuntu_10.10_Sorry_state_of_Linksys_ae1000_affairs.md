---
title: "Ubuntu 10.10: Sorry state of Linksys ae1000 affairs"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by Questioneer on 2010-10-10
Today I installed a fresh install of 10.10 on my hard drive.

My wireless N Linksys ae1000 USB card never worked by default with ubuntu, but by downloading the ralink drivers and compiling them with some modifications it would always work, up to 10.04.

Now, it doesn't.

I downloaded the RT3572USB drivers from ralinktech's website(also tried the RT2870USB, which gave a similar error, but the first driver is the updated version anyways which should work), and unpacked it.

I then ran:

```
sed -ir -e 's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e 's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/' ./os/linux/config.mk
```

and then

```
sed -ir -e 's!^#endif // RT2870 //!        {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870 //!' ./common/rtusb_dev_id.c
```

and then:

```
make && sudo make install
```

However, the source did not compile, and make gave me an error.

Here's my lsusb line: [http://www.pastie.org/1212005](http://www.pastie.org/1212005)

Here's the make error output: [http://www.pastie.org/1212000](http://www.pastie.org/1212000)

Here's my iwconfig: [http://www.pastie.org/1212003](http://www.pastie.org/1212003)

As far as I remember, doing this exact process worked perfectly on 10.04, on two computers. What should I do? I kind of need help on this asap.

---

### Post by Shaythong on 2010-10-10
This is exactly the problem I'm having. I've been trying to look up solutions for this problem for a couple days and haven't found anything myself. :( By the way, does your installation of 10.10 ever stutter or freeze up sometimes?

---

### Post by chough42 on 2010-10-11
I have the exact same problem.  This adapter has been nothing but trouble.  I'm thinking about replacing it.

---

### Post by thonuz on 2010-10-12
I also have been trying this for a while. I heard attempting to run another version of ubuntu or debian in virtualbox might work.
Has anyone tried wrapper?

Anyway here is my error
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/thomas/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make: *** /lib/modules/2.6.35-22-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

---

### Post by leafboy214 on 2010-10-15
I just installed my newly purchased AE1000 driver after fighting with for awhile. If noone has yet located this link, it details what needs to be done to the downloaded driver in order to compile it on Maverick Meerkat. 

[http://www.reddit.com/r/linux4noobs/comments/dphdy/so_my_wireless_card_broke_with_ubuntu_1010/](http://www.reddit.com/r/linux4noobs/comments/dphdy/so_my_wireless_card_broke_with_ubuntu_1010/)

---

### Post by jdonbook86 on 2010-10-25
I think I finally got the AE1000 working. However, I have to keep my internal wireless card on to keep the connection going. If I kill off the internal card, both connections go away. I think the card actually is choking the bandwidth of the USB dongle back to 802.11 b/g speeds (11Mbps) instead of the n rate of 56 Mbps. Many thanks to the fellow over on the Fedora posting for his recipe to get this thing going. The magic was getting inside one of the install files to rename a couple usb references.

---

### Post by jdonbook86 on 2010-10-25
By the way, the Fedora post is here: [http://forums.fedoraforum.org/showthread.php?t=244215](http://forums.fedoraforum.org/showthread.php?t=244215)

---

