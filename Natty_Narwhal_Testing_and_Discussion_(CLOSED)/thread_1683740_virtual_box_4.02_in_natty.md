---
title: "virtual box 4.02 in natty"
date: 2011-02-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by xgt001 on 2011-02-08
hello everyone

i can install virtual box succesfully.. but when i start a virtual machine it shows an error telling kernel drivers not installed ... can anybody help please???

thanks in advance

---

### Post by Tompalaz on 2011-02-08
If you are using the 2.6.38 kernel, run this in the terminal:
```
sudo find /usr/share/virtualbox/src/vboxhost -name *.h -exec perl -pi -w -e 's/linux\/autoconf/generated\/autoconf/g;' {} \;
```
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by xgt001 on 2011-02-08
hey thanks for the reply
i ran both the commands but both dint work :confused:
 
upon executing the first command i got this

"find: `/usr/share/virtualbox/src/vboxhost': No such file or directory"


and after running the second command i got this 

"

Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)
"

pls help thanks

---

### Post by rebootme on 2011-02-09
FWIW, I'm running 4.02 fine.  All I did was install the virtualbox-ose package with synaptic.

---

### Post by recluce on 2011-02-11
According to the guys over at the virtualbox.org forum, VBox 4.02 does **not** work with the 2.6.38 kernel at this time - this has nothing to do with Natty.

Solutions:

1.) Try the code posted by Tompalaz. Be aware that, according to the other forum, you can no longer run VBox with a kernel <2.6.38 after this

2.) Use a 2.6.37 series kernel

3.) Wait until VBox supports 2.6.38 kernel


BTW: I have the same errors with a 2.6.38 kernel under Lucid

---

### Post by xgt001 on 2011-02-11
thanks for that info recluce :-k i dint knw that

---

### Post by rebootme on 2011-02-11
I'm running 2.6.38-2-generic and VirtualBox 4.0.2 just fine...

---

### Post by recluce on 2011-02-11
> **rebootme said:**
> I'm running 2.6.38-2-generic and VirtualBox 4.0.2 just fine...

Good for you!

But since you did not give us a shred of additional information, why did you post at all?

---

### Post by xgt001 on 2011-02-12
is it something like the virtual box in synaptic(or USC) is tested on natty ??? .. i downloaded a .run file from virtualbox.org so that i can install in any distro... is it the probleM?????

---

### Post by dino99 on 2011-02-12
work with kernel > = 2.6.38 but dont with the others, be aware

ln -s /usr/src/linux-headers-`uname -r`/include/generated/autoconf.h /usr/src/linux-headers-`uname -r`/include/linux/autoconf.h

---

### Post by vishalrao on 2011-02-12
This worked for me:

```

sudo find /usr/src/virtualbox-ose-4.0.2/vboxdrv -name *.h -exec perl -pi -w -e 's/linux\/autoconf/generated\/autoconf/g;' {} \;

sudo aptitude reinstall virtualbox-ose

```

I had it installed already first of course...

---

