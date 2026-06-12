---
title: "Have to enter keyring password twice"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2010-09-12
After recently upgrading to the Maverick beta, I am now prompted for my keyring password TWICE each time I boot.  I have automatic login enabled, and I am used to being prompted to enter my keyring password each time I boot.  Having to enter it twice in a row every time I boot is a bit frustrating though.  Anyone else have this problem and know how to fix it? I don't mind entering it once, so I just want to get back to that.

---

### Post by cariboo on 2010-09-12
Do you still have to enter a keyring password if you enable login?

---

### Post by awam66 on 2010-09-12
> **jblackhall said:**
> After recently upgrading to the Maverick beta, I am now prompted for my keyring password TWICE each time I boot.  I have automatic login enabled, and I am used to being prompted to enter my keyring password each time I boot.  Having to enter it twice in a row every time I boot is a bit frustrating though.  Anyone else have this problem and know how to fix it? I don't mind entering it once, so I just want to get back to that.

Yes I got the same, but if I go back to manual log in it no longer occurs. I haven't yet tried auto login again though. Not on the right machine at the moment.

---

### Post by jblackhall on 2010-09-12
> **cariboo907 said:**
> Do you still have to enter a keyring password if you enable login?

Yes, still twice.

---

### Post by cariboo on 2010-09-12
@jblackhall, it looks like something went seriously wrong with your update, have you tried purging gnome-keyring, then re-installing it?

---

### Post by smoosh on 2010-09-12
I have the same issue, and when I did a ```
sudo apt-get purge gnome-keyring
``` it gives me this: ```
lolo@smoosh:~$ sudo apt-get purge gnome-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  liblash2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  akonadi-server apturl-kde docbook-xsl
  docbook-xsl-doc-html kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins
  kdesudo kdoctools kubuntu-debug-installer
  libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4
  libakonadi-kmime4 libakonadiprivate1 libattica0
  libboost-program-options1.42.0 libclucene0ldbl
  libdbusmenu-qt2 libiodbc2 libkabc4
  libkatepartinterfaces4 libkcal4 libkdecore5 libkdesu5
  libkdeui5 libkdewebkit5 libkdnssd4 libkfile4 libkhtml5
  libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4
  libkmediaplayer4 libkmime4 libknewstuff2-4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4
  libkpimutils4 libkpty4 libkresources4 libkrosscore4
  libkrossui4 libktexteditor4 libkutils4 libmailtransport4
  libmicroblog4 libnepomuk4 libnepomukquery4a libplasma3
  libpolkit-qt-1-0 libqapt-runtime libqapt1 libqca2
  libsolid4 libsoprano4 libssh-4 libstreamanalyzer0
  libstreams0 libthreadweaver4 libvirtodbc0
  mysql-client-core-5.1 mysql-server-core-5.1 odbcinst
  odbcinst1debian2 oxygen-icon-theme
  plasma-scriptengine-javascript python-kde4 qapt-batch
  shared-desktop-ontologies software-properties-kde
  soprano-daemon ttf-dejavu virtuoso-minimal
  virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common
Suggested packages:
  libsaxon-java libxalan2-java docbook-xsl-saxon fop xalan
  dbtoepub djvulibre-bin hspell libqca2-plugin-cyrus-sasl
  libqca2-plugin-gnupg libqca2-plugin-ossl
  libqca2-plugin-pkcs11
The following packages will be REMOVED:
  apturl* checkbox-gtk* computer-janitor-gtk*
  desktopcouch* gdebi* gksu* gnome-codec-install*
  gnome-keyring* nautilus-gksu* network-manager-gnome*
  python-desktopcouch* python-desktopcouch-records*
  software-properties-gtk* ubuntu-desktop* update-manager*
  update-notifier* xul-ext-bindwood*
The following NEW packages will be installed:
  akonadi-server apturl-kde docbook-xsl
  docbook-xsl-doc-html kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins
  kdesudo kdoctools kubuntu-debug-installer
  libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4
  libakonadi-kmime4 libakonadiprivate1 libattica0
  libboost-program-options1.42.0 libclucene0ldbl
  libdbusmenu-qt2 libiodbc2 libkabc4
  libkatepartinterfaces4 libkcal4 libkdecore5 libkdesu5
  libkdeui5 libkdewebkit5 libkdnssd4 libkfile4 libkhtml5
  libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4
  libkmediaplayer4 libkmime4 libknewstuff2-4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4
  libkpimutils4 libkpty4 libkresources4 libkrosscore4
  libkrossui4 libktexteditor4 libkutils4 libmailtransport4
  libmicroblog4 libnepomuk4 libnepomukquery4a libplasma3
  libpolkit-qt-1-0 libqapt-runtime libqapt1 libqca2
  libsolid4 libsoprano4 libssh-4 libstreamanalyzer0
  libstreams0 libthreadweaver4 libvirtodbc0
  mysql-client-core-5.1 mysql-server-core-5.1 odbcinst
  odbcinst1debian2 oxygen-icon-theme
  plasma-scriptengine-javascript python-kde4 qapt-batch
  shared-desktop-ontologies software-properties-kde
  soprano-daemon ttf-dejavu virtuoso-minimal
  virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common
0 upgraded, 84 newly installed, 17 to remove and 0 not upgraded.
Need to get 60.0MB of archives.
After this operation, 212MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
lolo@smoosh:~$ 

```

Why on earth would it install a whole bunch of KDE packages???

---

### Post by VMC on 2010-09-13
Not sure what happened. Here's simulation run, that mine shows:


```
$ sudo apt-get -s purge gnome-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apturl* checkbox-gtk* computer-janitor-gtk* gdebi* gksu* gnome-codec-install* gnome-keyring* language-selector* network-manager-gnome*
  software-properties-gtk* update-manager* update-notifier*
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
Purg apturl [0.4.1ubuntu4]
Purg checkbox-gtk [0.9.1]
Purg computer-janitor-gtk [1.14.1-0ubuntu2]
Purg gdebi [0.6.0ubuntu2]
Purg update-notifier [0.99.3]
Purg update-manager [1:0.134.10]
Purg language-selector [0.5.8]
Purg software-properties-gtk [0.75.10]
Purg network-manager-gnome [0.8-0ubuntu3]
Purg gnome-codec-install [0.4.2ubuntu2]
Purg gksu [2.0.2-2ubuntu2]
Purg gnome-keyring [2.92.92.is.2.30.3-0ubuntu1.1]
```

Also keyrings depends:

```
$ apt-cache depends gnome-keyring
gnome-keyring
  Depends: gconf2
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libcairo2
  Depends: libdbus-1-3
  Depends: libfontconfig1
  Depends: libfreetype6
  Depends: libgcr0
  Depends: libgcrypt11
  Depends: libglib2.0-0
  Depends: libgp11-0
  Depends: libgtk2.0-0
  Depends: libpango1.0-0
  Depends: libtasn1-3
  Depends: dbus-x11
  Recommends: libpam-gnome-keyring
  Breaks: libgnome-keyring0

```

---

### Post by kahping on 2010-09-13
This is off topic but... isn't it supposed to be apt-get --purge remove <packagename>? rather than apt-get purge <packagename>? or, are they synonymous commands? Just curious here

---

### Post by ranch hand on 2010-09-13
remove is a command to just remove the package itself.

purge wipes out anything associated with with it.

To add remove to the purge command is not going to hurt but it will not do anything either.

Adding purge, however, to the remove command could cause as quite a shock.

---

### Post by smoosh on 2010-09-13
When I do a ```
sudo apt-get remove gnome-keyring
``` I get the exact same output as I posted above for ```
sudo apt-get purge gnome-keyring
```

Weird.

Anyone else seen this? It looks like me trying to purge or remove gnome-keyring results in a full (or almost full) KDE system being installed, which makes no sense to me.

---

### Post by VMC on 2010-09-13
> **kahping said:**
> This is off topic but... isn't it supposed to be apt-get --purge remove <packagename>? rather than apt-get purge <packagename>? or, are they synonymous commands? Just curious here

I was curious about the differences also. If you read man page of apt-get, it will give an explanation:

```
--purge
           Use purge instead of remove for anything that would be removed. An asterisk ("*") will be displayed next to packages which are scheduled to be
           purged.  **remove --purge** is equivalent to the **purge** command. Configuration Item: APT::Get::Purge.

```

---

### Post by cariboo on 2010-09-13
I hate having to type more then I have to, :) so I always just use the **purge** option only.

---

### Post by seeker5528 on 2010-09-13
> **cariboo907 said:**
> I hate having to type more then I have to, :) so I always just use the **purge** option only.

For the literal minded, just using the purge option:

```
apt-get --purge some-package
```

would result in an error. Using the purge apt-get command on the other hand....

```
apt-get purge some-package
```

and you have success.

:p:p:p

As for the earlier question, using the purge option with the apt-get remove command, is the same as using the apt-get purge command.

Later, Seeker

---

### Post by ktp on 2010-09-13
> **kahping said:**
> This is off topic but... isn't it supposed to be apt-get --purge remove <packagename>? rather than apt-get purge <packagename>? or, are they synonymous commands? Just curious here

no differences..."apt-get remove --purge" does same thing as "apt-get purge".  One is less typing =)

---

### Post by kahping on 2010-09-13
Thanks for all the replies. so I learnt something new today :D

---

### Post by Maupertus on 2010-09-14
Okay, after updating today, I now have to enter the key 3 to 4 times. Something is going wrong here.

---

### Post by awam66 on 2010-09-14
I am getting the same problem here, and the same messages if I try to purge gnome keyring. There is something not right. However disabling auto login solves the problem, or at least gets rid of it. Has anyone filed a bug report??

---

### Post by FFuser on 2010-09-14
I too have this problem (entering my keyring password twice, while the password should be autounlocked on login - that was what it did in 10.04)

I'm NOT using the auto-login GDM feature...

---

### Post by cariboo on 2010-09-14
Try going to System->Preferences->Startup Applications and look for Certificate and Key Storage, edit the command so it looks like this:

```
gnome-keyring-daemon
```

and reboot.

---

### Post by TunaCanTommy on 2010-09-14
I just looked at Startup Applications Preferences and there are four applications that use "gnome-keyring-daemon":
GPG Password Agent, SSH Key Agent, Certificate & Key Storage, and Secret Storage Service.

Should all of them be activated on start-up ? ?

---

### Post by coolman98 on 2010-09-14
yeah what should we do.

---

### Post by cariboo on 2010-09-14
I would suggest just editing the command I suggested, and see what happens, I found that *could be* solution on Launchpad. As for the rest, just leave them.

---

### Post by jblackhall on 2010-09-14
> **awam66 said:**
> Has anyone filed a bug report??

Yep: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/637702](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/637702)

---

### Post by jblackhall on 2010-09-14
> **smoosh said:**
> Why on earth would it install a whole bunch of KDE packages???

If you look closely, it uninstalls ubuntu-desktop and other key components. That's why I didn't do it.

---

