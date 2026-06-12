---
title: "Getting Frostwire to work on Mandriva Linux?"
date: 2008-12-21
forum: Mandriva/Mageia
---

### Post by Pascal11110 on 2008-12-21
I have never used Mandriva Linux, but a friend of mine is trying to install frostwire on it. Can someone give me a step by step instruction, like where to download it, which version to download, and then instructions on how to install it if it goes as planned? I'll have him post any problems he has if he has problems during the installation. Thanks a lot.

---

### Post by TeaAge on 2008-12-22
I think this should be the latest version:
[http://hermes.frostwire.com/frostwire/4.17.1/frostwire-4.17.1.noarch.rpm](http://hermes.frostwire.com/frostwire/4.17.1/frostwire-4.17.1.noarch.rpm)

Just download it and install it with a double-click on it.

You also have to install java (if it isn't). I have the following packages installed:

```

java-1.6.0-sun-plugin-1.6.0.10-1mdv2009.0
rootcerts-java-20080503.00-2mdv2009.0
java-1.6.0-sun-alsa-1.6.0.10-1mdv2009.0
java-1.6.0-sun-fonts-1.6.0.10-1mdv2009.0
timezone-java-2008i-1mdv2009.0
java-1.6.0-sun-1.6.0.10-1mdv2009.0
java-access-bridge-1.24.0-1mdv2009.0
java-1.6.0-sun-jdbc-1.6.0.10-1mdv2009.0
java-1.6.0-openjdk-1.6.0.0-0.16.b11.4mdv2009.0

```

Then it should work.

Regards,
TeaAge

---

### Post by Pascal11110 on 2008-12-24
thanks a lot

---

### Post by bartos on 2008-12-24
This is what I had to do to get Frostwire 4.17.1 to run without errors on Mandriva 2009



```
Move the frostwire-<version> file to the /opt directory

su -
mv frostwire-<version>.tar.gz /opt

Uncompress and Extract

cd /opt
tar zxvf <frostwire version>.tar.gz


Next, test start FROSTWIRE, as your NORMAL USER


From Command Line:

/opt/frostwire<version>/runFrostwire.sh

```

---

### Post by TeaAge on 2008-12-24
> **bartos said:**
> This is what I had to do to get Frostwire 4.17.1 to run without errors on Mandriva 2009


Why didn't you use the rpm?

Regards,
TeaAge

---

### Post by bartos on 2008-12-24
The rpm seems to have a install error that doesn't set up properly and sudo update-alternatives --config java doesn't fix it. Seems to be a common problem that I had also, so this is an alternative.

---

