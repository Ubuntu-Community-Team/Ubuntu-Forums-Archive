---
title: "No Network Connection with Ubuntu 10.04"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by drstove on 2012-11-01
Going back to Windows XP and Ubuntu 6 through Windows Vista and Ubuntu 10.04 I have run a dual boot system. I have never had to do anything except install Ubuntu to have it automatically connect to my router through Ethernet. Now when trying to install a dual boot with Win 7 and Ubuntu 10.04, Ubuntu cannot find either the Ethernet or wireless network. If I pull down the network icon at the top of the screen is says that it cannot detect any network. It does offer to set up a VPN connection, about which I haven't a clue. I have tried to set up both wired and wireless networks using addresses etc. that I find in Win 7 but nothing works. How can I get 10.04 to find either network. Is this another game that Microsoft is playing? Like I said, I have never had to do anything in the past to have Ubuntu automatically find and connect with Ethernet.

---

### Post by ahallubuntu on 2012-11-01
I'd venture to guess this is relatively new hardware?  If so, don't bother with 10.04 LTS.  The kernel just won't have automatic support for the newer chipsets.  Try 12.04 LTS instead.

If this isn't new hardware, use the sticky thread at the top of this section for troubleshooting wireless issues (will largely apply to wired too) and provide the results requested there.

---

### Post by dannyboy79 on 2012-11-01
first post back the results of this command entered in a terminal

```
lspci -v
```

I want to see what sort of ethernet chipset you have. You say you previously ran Ubuntu on this same hardware, what version what you using? Its my understanding now you're trying to get version 10.04 working.

---

### Post by drstove on 2012-11-01
> **dannyboy79 said:**
> first post back the results of this command entered in a terminal

```
lspci -v
```

I want to see what sort of ethernet chipset you have. You say you previously ran Ubuntu on this same hardware, what version what you using? Its my understanding now you're trying to get version 10.04 working.

I have used the same router from XP through Win 7, and from Ubuntu 6 through 10.04 on previous machines. Ubuntu can't find a network on my new Win 7.0 machine.

---

### Post by drstove on 2012-11-01
> **ahallubuntu said:**
> I'd venture to guess this is relatively new hardware?  If so, don't bother with 10.04 LTS.  The kernel just won't have automatic support for the newer chipsets.  Try 12.04 LTS instead.

If this isn't new hardware, use the sticky thread at the top of this section for troubleshooting wireless issues (will largely apply to wired too) and provide the results requested there.

Thanks for the response. I have used a live version of 12.04 on disk and don't like the interface. That is why I am trying to install 10.04.

---

### Post by dannyboy79 on 2012-11-01
> **drstove said:**
> I have used the same router from XP through Win 7, and from Ubuntu 6 through 10.04 on previous machines. Ubuntu can't find a network on my new Win 7.0 machine.I already asked once for this information, if you don't give it no one can help you get Ubuntu 10.04 and networking working, whether it be WIFI or Ethernet.

```
lspci -v
```

---

### Post by dannyboy79 on 2012-11-01
> **drstove said:**
> Thanks for the response. I have used a live version of 12.04 on disk and don't like the interface. That is why I am trying to install 10.04.Just to point out, there are ways of NOT using Unity (new interface) within 12.04. It's called Gnome Classic

---

