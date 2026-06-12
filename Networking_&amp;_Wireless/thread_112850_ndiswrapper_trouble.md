---
title: "ndiswrapper trouble"
date: 2006-01-05
forum: Networking &amp; Wireless
---

### Post by Jammy_Stuff on 2006-01-05
I'm currently setting up my Belkin F5D7050 USB wireless adapter and I'm having a problem with ndiswrapper. So far I've installed the drivers with:

```
ndiswrapper -i rt2500usb.inf
```

which gave no errors. Then I assigned an alias with:

```
ndiswrappper -m
```

which also seemed to work. Then I did:

```
modprobe ndiswrapper
```

which gave no errors. If at this point I type:

```
ndiswrapper -l
```

it says the drivers are installed correctly. However, when I plug in the adapter and type:

```
ndiswrapper -l
```

it just doesn't do anything. There is no output shown and I just get a blank line in the terminal (no james@ubuntu thing either). It stays like this no matter how long I leave it. Anyone know what's happened?

---

