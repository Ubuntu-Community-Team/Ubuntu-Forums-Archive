---
title: "Getting Wifi to work correctly"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by CaptainMorgan on 2005-12-11
I attempted Mad-Wifi, but then got lost. 

In System/Administration/Networking, Im using DHCP, says it's configured and active, I set it to default... I even use Kwifimanager which states that the signal is strong at times, switching to no access point, then switching to a reall access point. Kwifimanager says Im connected, signal strength, on the correct network. Everything considered, I still cannot get online. No browser or other net app will connect.

Where do I begin? 
Any info you can provide is grealty appreciated. 

Thank you

---

### Post by John.Michael.Kane on 2005-12-11
have you looked this over [https://wiki.ubuntu.com/MoreRecentMadwifiHowto?highlight=%28wifi%29](https://wiki.ubuntu.com/MoreRecentMadwifiHowto?highlight=%28wifi%29)
[https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29](https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29)

---

### Post by CaptainMorgan on 2005-12-12
thank you for the link...
After step 2, because I don't have the latest kernel, I attempted the command there. Here is what I received:
```

root:/etc/apt # sudo aptitude install madwifi-source gcc-3.4 linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
[B]1Couldn't find any package whose name or description matched "madwifi-source"
The following packages have been kept back:
  libdvdcss2 linux-image-386 linux-restricted-modules-386[/B]
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

```

Which evidently caused a proble because at step three:
```

root:/etc/apt # sudo module-assistant build madwifi
**sudo: module-assistant: command not found**

```

So I went into Synaptic to search for the madwifi source and it's not there. I have every madwifi package installed concerning the i386. I did not install ones such as AMD, etc. I also attempted updates in Synaptic.. but still nothing.......

---

