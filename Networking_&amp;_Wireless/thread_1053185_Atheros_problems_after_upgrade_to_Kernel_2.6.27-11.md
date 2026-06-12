---
title: "Atheros problems after upgrade to Kernel 2.6.27-11"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by Racer-X on 2009-01-28
Looks like there are some problems with some Atheros wireless cards after updating to kernel 2.6.27-11.

Here's a thread I saw and posted to regarding this problem, but wanted to draw attention more to the kernel in the posting title rather than security upgrade.

[http://ubuntuforums.org/showthread.php?t=1052932](http://ubuntuforums.org/showthread.php?t=1052932)

Can someone detail what the differences are between the kernels?  I noted that in the modules directory on the 2.6.27-11 kernel, ath_pci doesn't exist (nor do any others really), but solely cfg80211.ko.

In the previous kernels, the modules directory contained a whole list of driver modules.

Does a different driver need to be enabled?  NetworkManager isn't loading up wireless at all when I boot into 2.6.27-11, but I can get things back working in 2.6.27-9.

Many thanks in advance!

---

### Post by Post Monkeh on 2009-01-28
my atheros 928x worked ok straight away.

i'm fairly new to linux so i don't know exactly what settings a new kernel changes, but is it possible people have blacklisted their ath9k driver and that's what's causing the problem?

---

### Post by Racer-X on 2009-01-28
Bump.

---

### Post by stathis21 on 2009-02-11
same problem here:(:(:(

---

### Post by botao on 2009-02-17
ya2c ( yet another 2 cents ) :

=> Assuming there is an active wired web connection :

1) if checking for atheros :

      ```
lspci | grep Wireless
```

   failed (that is, returned nothing) , then

2) get the latest (current.tar.gz) madwifi-hal at [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) , possibly with :

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz

```

3) then 'explode' the tar ball :

   ```
tar xvf madwifi-hal-0.10.5.6-current.tar.gz
```

4) now go into the package directory , and 'build' it :

```

   cd madwifi*[0-9]
   make
   sudo make install

```

5) now check if atheros shows up :

   ```
sudo modprobe ath_pci
```

6) now make sure the module will be loaded at the next boot :

   ```
grep ath_pci /etc/modules || sudo echo ath_pci >> /etc/modules
```

well, now a reboot is in order ...:popcorn:
_______________________________________________________________

Good Luck , and success !

Alexandre Botao ( [http://www.botao.org](http://www.botao.org) )

---

