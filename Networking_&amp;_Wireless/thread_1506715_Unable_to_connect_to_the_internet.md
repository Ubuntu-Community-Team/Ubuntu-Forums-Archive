---
title: "Unable to connect to the internet"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by Admiral1234 on 2010-06-10
Currently I have an Acer Aspire One netbook with Windows XP on it. I want to switch to Ubuntu, so I have the OS on a flash drive and I can run it fine. The only problem is, I cant see any wireless networks in range. I know the router is working because I can connect with Windows fine. A notification also pops up telling me i have to install missing drivers. But when i click on install, the progress gets to 99% and fails. It says i need the Broadcom B43 driver, but i don't know how to get it. If someone could give me a link to it so i could put it on a flashdrive then my computer, I think that might work. But then again, I am a beginner at this, so anything will help! Also I am putting Ubuntu netbook remix 10.04 on it if that helps.

Thanks!

---

### Post by mikewhatever on 2010-06-10
Are you running the Remix iso from the flash drive, or is it a proper installation?

---

### Post by Admiral1234 on 2010-06-10
> **mikewhatever said:**
> Are you running the Remix iso from the flash drive, or is it a proper installation?

 I am running it on a flashdrive, I want to be sure everything will work before I really install it.

---

### Post by mikewhatever on 2010-06-10
> **Admiral1234 said:**
> I am running it on a flashdrive, I want to be sure everything will work before I really install it.

That's not what I asked. Is it a proper installation on the flash drive, or is it just a bootable iso?

---

### Post by Admiral1234 on 2010-06-10
> **mikewhatever said:**
> That's not what I asked. Is it a proper installation on the flash drive, or is it just a bootable iso?

 Sorry, I'm 14 years old and don't know much yet. But its a bootable iso file on the flashdrive.

---

### Post by pastalavista on 2010-06-10
You need a network connection to install the wireless driver, so best bet would be to connect via ethernet and download/install it. Not knowing which variation of the Broadcom driver means trial and error until you pick the right one. With an internet connection, the Hardware Drivers tool in the System/Administration menu will be able to automatically install the one your system needs.

edit: By "connect via ethernet" I mean use cat5 ethernet cable to plug directly into the router, even running from the USB drive, it can install the driver and wireless will work, only problem is, you'll need to do it again when you actually install it to the HD.

---

### Post by Stancel on 2010-06-10
> **Admiral1234 said:**
> Currently I have an Acer Aspire One netbook with Windows XP on it. I want to switch to Ubuntu, so I have the OS on a flash drive and I can run it fine. The only problem is, I cant see any wireless networks in range. I know the router is working because I can connect with Windows fine. A notification also pops up telling me i have to install missing drivers. But when i click on install, the progress gets to 99% and fails. It says i need the Broadcom B43 driver, but i don't know how to get it. If someone could give me a link to it so i could put it on a flashdrive then my computer, I think that might work. But then again, I am a beginner at this, so anything will help! Also I am putting Ubuntu netbook remix 10.04 on it if that helps.

Thanks!


Have you tried clicking on "Connect to Hidden Wireless Network" or rebooting and checking again?

Keep in mind plenty of people are having wireless connection issues with 10.04. when I upgraded to Lucid I had no problem finding the network, I just couldn't connect to it.  I think you should try 9.10 for the time being and see how that works for you.

edit: Is this because you're experiencing problems with Ubuntu? Your post makes it sound like you haven't installed Ubuntu yet.

---

### Post by Admiral1234 on 2010-06-10
> **Stancel said:**
> Have you tried clicking on &quot;Connect to Hidden Wireless Network&quot; or rebooting and checking again?

Keep in mind plenty of people are having wireless connection issues with 10.04. when I upgraded to Lucid I had no problem finding the network, I just couldn't connect to it.  I think you should try 9.10 for the time being and see how that works for you.

edit: Is this because you're experiencing problems with Ubuntu? Your post makes it sound like you haven't installed Ubuntu yet.

 I have ubuntu on a flashdrive right now and i am booting it from there. If you mean haven't permanently installed it, then no i haven't.

---

### Post by mikewhatever on 2010-06-11
I don't know if you can install a wireless driver while running from Live usb. I am afraid this particular one may require installing Ubuntu properly first.
The output of **lspci | grep -t network** should show the model of the wireless card, and if you post it here, people can tell you if they had any problems.

---

