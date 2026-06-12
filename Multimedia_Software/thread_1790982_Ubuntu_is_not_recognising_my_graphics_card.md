---
title: "Ubuntu is not recognising my graphics card"
date: 2011-06-25
forum: Multimedia Software
---

### Post by pauloz on 2011-06-25
I know this issue has been raised before, both here and on other websites and forums, but I keep running into a brick wall because I can't understand the responses (please excuse my ignorance - I've only a few months' experience with Ubuntu). 

Ubuntu does not appear to be recognising my graphics card, which is a Galaxy GeForce 8400GS 512MB DDR2 64-bit. I run Ubuntu 10.04 LTS alongside Windows 7 (dual boot) and I first suspected something was not right when I tried to upgrade my Visual Effects from "None" to "Normal". Ubuntu searches for available drivers but bombs out with the message, "Desktop effects could not be enabled". Videos are often "jittery" as well.

I hope someone can help me and would appreciate basic, step by step instructions, particularly if I have to use the terminal. Thanks.

---

### Post by BicyclerBoy on 2011-06-25
Have you tried the System-->Administration-->Hardware Drivers ?

This should find nvidia proprietary driver 173 or 195 etc..

---

### Post by pauloz on 2011-06-26
> **BicyclerBoy said:**
> Have you tried the System-->Administration-->Hardware Drivers ?

This should find nvidia proprietary driver 173 or 195 etc..
I've tried that and it results in a message, "No proprietary drivers are in use on this system".

---

### Post by andrea000 on 2011-06-26
You could try to installing the nvidia drivers with synaptic
I have problems with the 173 driver saying driver installed
but not in use I found a workaround for it by installing the
nvidia-glx-173-kernel-source but I have not had time to try
it so I'm running the open source driver for now.

---

### Post by BicyclerBoy on 2011-06-26
@OP
In synaptic package manager, on the Ubuntu software tab,  do you have "ticked"

proprietary drivers for devices ?

You can install the 
"nvidia-current"       (195 at present)
"nvidia-current-modaliases"
"nvidia-settings"
"libvdpau1"

 packages from in synaptic

I run 260 on 10.04 from a mythtv ppa..

@andrea
There is no way 173 is the latest version for 11.04. It is up to version 260.

I think you should purge all nvidia & then reinstall via synaptic
[sudo] apt-get -purge remove nvidia-*

---

### Post by pauloz on 2011-06-26
> **BicyclerBoy said:**
> @OP
In synaptic package manager, on the Ubuntu software tab,  do you have "ticked"

proprietary drivers for devices ?

You can install the 
"nvidia-current"       (195 at present)
"nvidia-current-modaliases"
"nvidia-settings"
"libvdpau1"

 packages from in synaptic

I run 260 on 10.04 from a mythtv ppa..

@andrea
There is no way 173 is the latest version for 11.04. It is up to version 260.

I think you should purge all nvidia & then reinstall via synaptic
[sudo] apt-get -purge remove nvidia-*
Success! Thanks BicyclerBoy - I installed all four that you suggested and already can see a significant improvement. Cheers!

---

### Post by BicyclerBoy on 2011-06-26
@Andrea

Do you have a package called 
dh-modaliases
installed ? (check in synaptic package manager)

Install if you don't..

Can you run
nvidia-settings 
Does it complain/give errors ?
Does it report the driver version ?

---

