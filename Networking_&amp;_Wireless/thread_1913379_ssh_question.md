---
title: "ssh question"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by Sonicgoo on 2012-01-22
so how do check if the video is working on a second computer via SSH?

I know can look at the logs but how do I know that everything is working?

I am working on a video issue on my families computer in another in another state.

---

### Post by 2F4U on 2012-01-22
SSH alone may not be the right tool if you want to actually watch the video on your local machine. VNC or some other remote desktop software may be more appropriate.

---

### Post by CharlesA on 2012-01-22
> **2F4U said:**
> SSH alone may not be the right tool if you want to actually watch the video on your local machine. VNC or some other remote desktop software may be more appropriate.
Please don't use VNC over the internet.

Teamviewer would probably be a better solution.

---

### Post by Sonicgoo on 2012-01-22
I don't want to watch video I just want to know if the user can see ubuntu and that screen is working without calling them up.

---

### Post by CharlesA on 2012-01-22
If you can SSH in, doesn't that mean that Ubuntu is up and running?

---

### Post by Sonicgoo on 2012-01-22
Well the computer can be running and still not have a monitor/video that is not working. So I was wondering how can you tell via ssh if everything is running appropriately?

This is my parents computer running Ubuntu 11.04 and I just need to make sure that it's functional with a reasonable interface. It has had some issues with stalling on the boot. So when I reboot it after working on it I would like to be sure that the screen/video card is working. I think I solved the stalling problems with this line in the boot.

"GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

It is a Dell, running Ubuntu 11.04 with following: 
82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device

-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2666MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 533MHz

---

### Post by CharlesA on 2012-01-23
It would probably be easier to just call them. I think you can check to see if X is running, but it would depend on where it stalled in the boot process before.

---

### Post by azmyth on 2012-01-24
You could use NX client 4.0 (3.5 won't work). Basically, it grabs the screen remotely so if it doesn't login you know the computer is down and if it logs in and the screen is black you know there's an issue with video out on the server.

With this said though, for some reason NX 4.0 just stopped working on my computer so I've been using x2go but this won't work for you since it starts a new session.

---

### Post by CharlesA on 2012-01-25
NX creates it's own "virtual" display from what I have seen. If you log in with it and then look at the console of the machine you just logged into, you'll still be on the login screen/where ever you were.

---

### Post by azmyth on 2012-01-26
That's how NX 3.5 worked. They changed this in 4.0. Whatever you change on the remote screen will change whatever is on the server and vice versa. If you install it, you'll see what I mean.

---

### Post by CharlesA on 2012-01-26
> **azmyth said:**
> That's how NX 3.5 worked. They changed this in 4.0. Whatever you change on the remote screen will change whatever is on the server and vice versa. If you install it, you'll see what I mean.
Interesting. The machine I have running NX is on 3.5.

Thanks!

---

