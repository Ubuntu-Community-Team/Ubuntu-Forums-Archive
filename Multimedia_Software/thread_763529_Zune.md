---
title: "Zune"
date: 2008-04-23
forum: Multimedia Software
---

### Post by abeeeeee on 2008-04-23
how do u sync your zune through amarok? my windows is completely gone, so i can't do anything with that. :[

running on gutsy gibbon 7.10

---

### Post by aparigraha on 2008-04-23
haven't really tried with zune, but a few other microsoft issues.
try: settings-> configre amarok-> media devices
try "autodetect devices". if that doesn't work, "add device".
select "MTP media device" and find out where your zune is connected if you need to:

sudo fdisk -l

good luck

---

### Post by Just-trevor on 2008-05-31
```
root@Trevor2:/home/trevor-max# sudo fdisk -|
> 

```

what do i need to type in?
I added the device but it won't show up

I have 8.04 by the way

---

### Post by Just-trevor on 2008-05-31
I did a little more research and found  [http://www.zune-online.com/news/zune/zune-on-linux-via-vmware.html]("http://www.zune-online.com/news/zune/zune-on-linux-via-vmware.html")

I tried to unload the 2.0 usb with ```
sudo rmmod ehci_hcd
```  but nothing happened
what is the command for hardy?

---

