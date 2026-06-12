---
title: "AGAIN: Lirc with mceusb2 driving me insane :("
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by mael on 2008-02-14
i know, this falls in the category of "just another user with the same problem again" but it's different. i've read many forum posts and googled my *** off but didn't find any solution.

i have a "Windows Media Center Remotes (new version Philips et al.)" which is nicely recognized at the installation of lirc. it worked even for some month. now all over a sudden it's not working anymore. this is with ubuntu gutsy and lirc 0.8.2. as far as i remember there were no updates from ubuntu regarding lirc.

all drivers/modules are loaded perfectly:

```
lsmod|grep lirc
lirc_mceusb2           13828  0 
lirc_dev               14564  1 lirc_mceusb2
usbcore               143340  6 lirc_mceusb2,cdc_acm,usbhid,ehci_hcd,ohci_hcd

```

```
mode2 -d /dev/lirc0
```
shows a lot of output if i press any keys on the remote, so the driver is fine, it's lircd which makes trouble.

lirc is running:
```
 
ps auxfww
root     31299  0.0  0.0   2952   488 ?        Ss   22:53   0:00 /usr/sbin/lircd --device=/dev/lirc0

```

 the /dev/lircd socket is there and accessible.
```
la /dev/lirc*
crw-rw---- 1 root root 61, 0 2008-02-14 22:38 /dev/lirc0
srw-rw-rw- 1 root root     0 2008-02-14 22:53 /dev/lircd

```
but irw doesn't deliver any output when i press a key (this worked a while ago). it just waits there and doesn't show a error message - not connection refused, not anything. in fact, strace shows, it reads the socket but there isn't any output at all.

now i've upgraded to the latest hardy alpha release and lirc 0.8.3 but the problem remains the same.

i've tried to purge lirc and created new config files, tried different settings, whatever i could find, but none of it worked.

ANY ideas? ANY help would be appreciated!


PS: completely different story: if anybody has the problem, that the mceusb2 remote is dead - it doesn't light up on keypress and doesn't sent any IR signals - take the batteries out for 30 min and try again ;)

---

