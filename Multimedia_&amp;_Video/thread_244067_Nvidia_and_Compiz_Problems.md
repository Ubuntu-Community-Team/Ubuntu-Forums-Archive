---
title: "Nvidia and Compiz Problems"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by justing1319 on 2006-08-25
I'm thoroughly confused here and I'm hoping someone can shine some light on this for me. I switched from an ATI 8500 to an Nvidia 7600 and I'm having a variety of problems. At first i used the envy script to get the newest Nvidia drivers and all seemed well so i went ahead and tried installing XGL/Compiz. After a lot of tweaking this is where i am:

1.In the Nvidia settings the only thing i can change is “nvidia-settings Configuration” all the other tabs are gone.
2.When i restart compiz wont load until i run “sudo apt-get install libgl1-mesa –reinstall”

Any help or suggestions of things I can try short of clearing Ubuntu would be much appreciated.

---

### Post by tseliot on 2006-08-26
If you changed your card you might want to do:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then:
```
sudo dpkg-reconfigure xserver-xorg
```
select the "nvidia" driver, your keyboard, etc., and press ENTER whenever you don't know the answer to the questions


I can't help you with compiz since I don't use it.

If you have any problem after you follow what I suggested, reinstall the driver (get the latest "envy", the one which I released yesterday)

---

