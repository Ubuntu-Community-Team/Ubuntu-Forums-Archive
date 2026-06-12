---
title: "[SOLVED] installing restricted nvidia driver from command line"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by dooglex on 2007-11-08
Hi 
i want to use the command line to install the nvidia restricted drivers so i can bypass the power connector check on my graphics card, can anyone help?

Thanks,

---

### Post by Fire_Chief on 2007-11-08
If you have a newer Nvidia card```
sudo apt-get install nvidia-glx-new linux-restricted-modules
```Otherwise, if it's an older card```
sudo apt-get install nvidia-legacy linux-restricted-modules
```After you finish the install run```
sudo nvidia-settings
```Reboot and you *should* be good to go

---

### Post by dooglex on 2007-11-08
brilliant, many thanks! i have a 7900gs so im guessing i use the newer one? and simply add 

--power-connector-check/--no-power-connector-check
Disable or enable the "NoPowerConnectorCheck" X configuration option.

to the end of the line as appropriate?

---

### Post by Fire_Chief on 2007-11-08
Yes, use the newer one. I don't have a card w/ external power so I don't know about the power check option during the config. I know the option is not specified during the install but you may want to check the options available for nvidia-settings```
sudo nvidia-settings --help
```

---

