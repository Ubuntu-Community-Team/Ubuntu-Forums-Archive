---
title: "No Connection with my Linksys card"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by Jigzaw on 2006-07-02
I just installed Dapper Drake and I'm having problems getting online with my Linksys Wireless-G PCI Adapter WMP54G card. It's recognized as something completely different in the "Device Manager". 

And yes, I'm a total n00b. I know just about as much about linux as the pope knows kama sutra... So be gentle with me and give it to me slowly. What do I hafta do to get online?

Other than that I'm very pleased with what I'm seeing so far. My hope is that I will stand the distance this time and get rid of ol' Micro$oft once and for good.

Any help is good help. Tnx in advance :D

---

### Post by Jigzaw on 2006-07-10
*bump*

I have read many of the guides on the RT2500 chipsets, but can't seem to get it to work. Whenever I try to do the "sudo mkdir etc/wireless..." I get the reply that I can't cuz the file or dir don't exist. I'm getting veeery frustraded and would really be glad for any help. In baby steps please...

---

### Post by durableapostle on 2006-07-10
I had a similar problem, with the WPC54Gv2.  I needed to change my firmware.  Maybe your problem is similar--

[http://ubuntuforums.org/showthread.php?t=75448&highlight=linksys+wpc54g]("http://ubuntuforums.org/showthread.php?t=75448&highlight=linksys+wpc54g")

---

### Post by diepruis on 2006-07-11
> **Jigzaw said:**
> 
Whenever I try to do the "sudo mkdir etc/wireless..." I get the reply that I can't cuz the file or dir don't exist.


For some reason mkdir wants you to take creating directories in steps, like so:

```

sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT61STA

```

That should sort you out.

---

