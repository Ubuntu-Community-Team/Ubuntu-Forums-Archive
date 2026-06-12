---
title: "Hostname in router?"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by ManyBeers on 2009-11-30
Sony Vaio laptop:Dual-boot Ubuntu/WindowsXP

I use Ubuntu8.04 with a D-link DWLG630 pcmcia
wireless card and WICD as the network manager.
When I am connected to my router (ActiontecGT701WG) while in Ununtu the PC name
field shows "unknown" yet the computer name is Ubuntu. The name correctly displays when I am
booted in to WindowsXP. How come Ubuntu doesn't show correctly?

---

### Post by fancypiper on 2009-11-30
Post the contents of /etc/hostname

---

### Post by ManyBeers on 2009-11-30
> **fancypiper said:**
> Post the contents of /etc/hostname

"ubuntu"...thanks for posting. Sorry it took me so long to report back but I had gone to bad shortly after making this thread.

---

### Post by Iowan on 2009-11-30
If you get your address via DHCP, you can edit */etc/dhcp3/dhclient.conf* and include the hostname on the "send host-name" line. Sometimes the DHCP server also serves as DNS, sometimes not...

---

### Post by ManyBeers on 2009-11-30
> **Iowan said:**
> If you get your address via DHCP, you can edit */etc/dhcp3/dhclient.conf* and include the hostname on the "send host-name" line. Sometimes the DHCP server also serves as DNS, sometimes not...
It doesn't look like there is much to edit.

---

### Post by SteveHillier on 2009-11-30
> **ManyBeers said:**
> Sony Vaio laptop:Dual-boot Ubuntu/WindowsXP

I use Ubuntu8.04 with a D-link DWLG630 pcmcia
wireless card and WICD as the network manager.
When I am connected to my router (ActiontecGT701WG) while in Ununtu the PC name
field shows "unknown" yet the computer name is Ubuntu. The name correctly displays when I am
booted in to WindowsXP. How come Ubuntu doesn't show correctly?

In my experience this is not necessarily an issue with the OS.  I have seen this behaviour in all sorts of situations and in Windows OSs.  Network printers are a real pain.  Sometimes you just have to map it out the hard way.

---

### Post by Iowan on 2009-11-30
> **ManyBeers said:**
> It doesn't look like there is much to edit.You got me there - my 8.04 server file looks almost identical. This workstation file is much more involved. Add the following line above the "request" line - change <hostname> to your hostname:```
send host-name "<hostname>";

``` On this machine, the line looks like:```
send host-name "DELL4100";
```

---

### Post by ManyBeers on 2009-11-30
> **Iowan said:**
> You got me there - my 8.04 server file looks almost identical. This workstation file is much more involved. Add the following line above the "request" line - change <hostname> to your hostname:```
send host-name "<hostname>";

``` On this machine, the line looks like:```
send host-name "DELL4100";
```

   I think the reason the file looks that way is because I'm not using Network Manager but WICD instead and it might have it's own config file. In other words I don't think that file is being used. I posted the same question over at WICD's forum and hopefully somebody there can help. The fact that my wireless works at all is great so a hiccup like this is small potatoes.
But if I can fix it I will.

---

### Post by Iowan on 2009-11-30
I haven't used WICD, so I'm not sure how it does DHCP, or if it uses **dhclient**. Good luck - keep the thread updated...  :p

---

### Post by ManyBeers on 2009-11-30
> **Iowan said:**
> I haven't used WICD, so I'm not sure how it does DHCP, or if it uses **dhclient**. Good luck - keep the thread updated...  :p

I will. In it's preferences ..dhcp client field.. Automatic is checked.
These are unchecked
dhclient
dhcpcd
pump
Oh If you noticed my avatar has been changed to yours but the white has been removed. If you want it copy it and then I'll put mine back. I prefer them without the white background, no offense intended

---

### Post by Iowan on 2009-12-01
> **ManyBeers said:**
> Oh If you noticed my avatar has been changed to yours but the white has been removed. If you want it copy it and then I'll put mine back. I prefer them without the white background, no offense intendedOn my system, the background is the same as the forum background... but I've been intending to make it transparent. Thanks - copied.

---

### Post by ManyBeers on 2009-12-01
> **Iowan said:**
> On my system, the background is the same as the forum background... but I've been intending to make it transparent. Thanks - copied.

I was wondering if you would notice it. Your welcome.

---

