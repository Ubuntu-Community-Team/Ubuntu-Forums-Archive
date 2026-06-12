---
title: "Radeon HD 7850M and HP Envy 17 3200"
date: 2013-02-09
forum: Multimedia Software
---

### Post by jwhirl06 on 2013-02-09
I am having issues with the kernel updates breaking the radeon drivers on my HP Envy 17T-3200 series. I tried the open sourced ones, as well as directly from AMD. Every time I take a linux-headers update my compiz crashes leaving me with a blank screen and no unity. Is there a fix for this?

---

### Post by jwhirl06 on 2013-02-11
bump, anyone? When I take updates for kernel headers, it crashes compiz and I have no unity. Is there anyway I can backlist the ATI card and just use intel??

---

### Post by Bucky Ball on 2013-02-11
*Thread moved to **Multimedia & Video**.*

You might have more luck here.

---

### Post by jwhirl06 on 2013-02-11
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video**.*

You might have more luck here.

Oh sorry! I appreciate it. Thanks!!!

---

### Post by jwhirl06 on 2013-02-12
bump! anyone?!

---

### Post by Yellow Pasque on 2013-02-12
So which driver are you using (and if it's fglrx/Catalyst, how did you install it)?

---

### Post by jwhirl06 on 2013-02-12
> **Temüjin said:**
> So which driver are you using (and if it's fglrx/Catalyst, how did you install it)?

I tried the built in open source, fglrx and every time it takes a kernel update it breaks my install. Then I tried using the Catalyst drivers from AMD, works great until I take a kernel update then it breaks them again. To fix I have to purge fglrx and the amd stuff.

---

### Post by Yellow Pasque on 2013-02-12
> Then I tried using the Catalyst drivers from AMD
How did you install these? If you just ran the file downloaded from AMD, you did it wrong. You need to follow procedure here to build the kernel module with dkms so that it doesn't break every time you install a new kernel: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)
and then: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file_2](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file_2)

---

### Post by jwhirl06 on 2013-02-12
> **Temüjin said:**
> How did you install these? If you just ran the file downloaded from AMD, you did it wrong. You need to follow procedure here to build the kernel module with dkms so that it doesn't break every time you install a new kernel: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)
and then: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file_2](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file_2)

Thank you! will try now...

---

### Post by jwhirl06 on 2013-02-12
No, followed the instructions to a T, no unity.

Ubuntu starts with "This system is running in low-graphics mode"

---

### Post by Yellow Pasque on 2013-02-12
Did you get any errors while installing? Perhaps posting /var/log/Xorg.0.log would be helpful

---

### Post by jwhirl06 on 2013-02-12
> **Temüjin said:**
> Did you get any errors while installing? Perhaps posting /var/log/Xorg.0.log would be helpful

No errors during install, will get you xorg log in a moment, currently doing updates via shell lol

---

### Post by jwhirl06 on 2013-02-12
since I am only in terminal, I can't copy the whole thing to somewhere where I can forward it. In the log I read a warning about how this was a muxless system and at the end it said "Fatal server: no screens found"

Also, it is saying its falling back on old probe method for fglrx

---

### Post by Yellow Pasque on 2013-02-12
Sorry, I didn't realize this was a hybrid graphics setup with an Intel GPU and a Radeon GPU.
See: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Intel.2FATI_Hybrids](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Intel.2FATI_Hybrids)

---

### Post by jwhirl06 on 2013-02-12
> **Temüjin said:**
> Sorry, I didn't realize this was a hybrid graphics setup with an Intel GPU and a Radeon GPU.
See: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Intel.2FATI_Hybrids](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Intel.2FATI_Hybrids)

I can't stand these damn hybrid graphics, I came from a Nvidia optimus GT525m rig before this. Trying now. If this fails, is there a way for me to just use the intel graphics?

---

### Post by Yellow Pasque on 2013-02-12
If you're lucky, your BIOS has a switch to shut off the AMD card to save power. You can probably accomplish that with vgaswitcheroo utility if not.

---

### Post by jwhirl06 on 2013-02-12
> **Temüjin said:**
> If you're lucky, your BIOS has a switch to shut off the AMD card to save power. You can probably accomplish that with vgaswitcheroo utility if not.

How would I go about doing that? The laptop is plugged in at all times, and I don't do any gaming, the ivybridge intel should suffice.

---

