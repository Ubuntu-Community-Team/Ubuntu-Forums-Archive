---
title: "Linux Mint 17.3 Rosa - HPProBook 6560b wifi driver"
date: 2020-01-13
forum: MINT
---

### Post by Kevin McCready on 2020-01-13
I have a new install of Linux Mint but the wifi doesn't work (the lan is fine).

The message on the menu says "wifi is disabled by hardware switch".

I think it needs a driver. So I downloaded sp52229.tar from 
[https://support.hp.com/us-en/drivers/selfservice/hp-ProBook-6560b-notebook-pc/5045605](https://support.hp.com/us-en/drivers/selfservice/hp-ProBook-6560b-notebook-pc/5045605)

Then I used alien to convert the rpm to deb because Linux Mint doesn't use rpm. During the conversion I got error such as
warning: iwlagn-kmp-pae-2.6.36_2.6.32.27_0.2-0.3.1.i586.rpm: Header V3 RSA/SHA256 Signature, key ID 307e3d54: NOKEY

This is the output from the diagnostic tool:
[https://pastebin.com/fNWZ86ZV](https://pastebin.com/fNWZ86ZV)

---

### Post by wildmanne39 on 2020-01-13
*Thread moved to **MINT a more appropriate sub-forum**.*

I do not know the specifics about Mint but the hardblock usually means the wifi is turned off and you need to physically turn it on, like with the wifi switch or a key combination, your driver is installed already and usually the intel drivers work out of the box.

---

### Post by Kevin McCready on 2020-01-13
I think it's a firmware issue. None of the other things I have tried work.

---

### Post by Kevin McCready on 2020-01-20
Does anyone know anyone who can tweak the rpm to make a driver work?

---

### Post by jeremy31 on 2020-01-20
Mint 17 went EOL about 8 months ago
In terminal do
```
echo "blacklist hp_wmi" | sudo tee /etc/modprobe.d/hp_wmi.conf
```
Reboot

---

### Post by Kevin McCready on 2020-01-20
Thanks, I'll try. It's a friends computer so it will take me a couple of days when I see then next.

---

### Post by Kevin McCready on 2020-01-22
So I tried it, but problem persists. Also the tee command seemed to hang  the terminal. I let it run for 4 hours and nothing happened. More help  would be appreciated.

---

### Post by CelticWarrior on 2020-01-27
> **Kevin McCready said:**
> So I tried it, but problem persists. Also the tee command seemed to hang  the terminal. I let it run for 4 hours and nothing happened. More help  would be appreciated.


The command isn't supposed to give any feedback. And you wouldn't see any "change" either. You may see a change like it's working now, after logging out and in or rebooting. But if it doesn't change a thing, you were already informed that the distro you're using is out of support and not even an official Ubuntu derivative. This forum is very permissive about this things. If I were to run it, the forum,  your whole thread would have been deleted a long time ago with a suggested redirect to Mint forums.

---

### Post by Kevin McCready on 2020-01-29
Thanks for your input. Do you know how to alter the code for the driver? The rpm needs to be changed to deb. I think the thread has been moved to MINT. (see 2nd post)

---

### Post by CelticWarrior on 2020-01-30
The command you were given should be enough. 

Generally there's no need to install foreign drivers. All the drivers available in RPM (RHEL, Fedora and derivatives) are natively available for Debian/Ubuntu.

Now, what you should do is to upgrade to a support release ASAP and maybe you won't need to manually install any driver and if it doean't work the same way try the command given to blacklist the module. That's all.

---

### Post by Kevin McCready on 2020-02-09
Problem solved. Thanks for the advice. I appreciate it. The solution was to upgrade to the latest version of linux.

---

