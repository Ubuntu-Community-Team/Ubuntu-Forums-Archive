---
title: "flash stoped working???"
date: 2009-02-25
forum: Multimedia Software
---

### Post by keithg67 on 2009-02-25
I have Xumbuntu and when i installed it the flash worked great then all of a sudden it stoped working and the only thing diffrent is i got the last set of updates. anyone know what went wrong???

---

### Post by Steve H on 2009-02-25
Have you tried reinstalling it?

```
sudo apt-get install flashplugin-nonfree
```

Which updates were they?

---

### Post by keithg67 on 2009-02-25
> **Steve H said:**
> Have you tried reinstalling it?

```
sudo apt-get install flashplugin-nonfree
```

Which updates were they?

I did try to reinstall it but it didnt work also i dont remember what updates they were there were alot of them. i am thinking about reinstalling xumbuntu and installing the updates 1 by 1 to see which one is affecting it doesnt help me much lol but i can at least post it and help everyone else out.

---

### Post by Steve H on 2009-02-25
It might be easier to remove firefox, ubufox (config files), firefox branding, flashplugin-nonfree in that order using Synaptic. Synaptic should then automatically remove the dependencies. Then install firefox and the rest with Synaptic installing dependencies. BUT the last install was flashplugin-nonfree. Reboot after each install and after flash install.

Good luck!!

:p

---

