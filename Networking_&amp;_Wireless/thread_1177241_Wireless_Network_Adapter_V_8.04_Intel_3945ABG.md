---
title: "Wireless Network Adapter V 8.04 Intel 3945ABG"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by hellfire8 on 2009-06-03
Hey there,

I am relatively new to Linux and Ubuntu,

I managed to get hold of a Acer Aspire 2920 laptop, relatively new and good for free (good bargain considering it isnt that old, it wouldn't run windows and I decided I would try a Linux based OS, a friend suggest Xubuntu, Got it installed and it runs fine, yay for me

Problem is, I cannot get the onboard wireless working, 

I tried the sudo lshw command to see if it could find the controler and it found it

Found the PCI bridge and PCIexpress port 1, and the device

Configuration: driver=pcieport-driver
network DISABLED
description: wireless interface
product: PRO/wireless 3945ABG Network connection
vendor: intel corporation
physical id: o
bus info: pci@0000:04:00.0
logical name: wmaster0
version: 02
serial 00:1c:bf:63:bf:d1
width 32bits
clock 33MHz
capabilities: pm msi pciexpress bus master cap list logical ethernet physical wireless
configuration: broadcast=yes driver iwl3945 latency=0 module iwl3945 multicast=yes wireless= IEEE802.11g

how do I enable it, sorry, I am new and this will be a relatively newbee question I am sure

Regards,

Graeme

---

### Post by chili555 on 2009-06-03
> network DISABLED
description: wireless interfaceDisabled often means the wireless switch on your notebook is in the 'off' position and that all you need to do is push it to 'on.' Verify in a terminal with:```
sudo cat /var/log/messages | grep -i kill
```

---

### Post by hellfire8 on 2009-06-03
That is what I thought, however when I hit the wireless button nothing happens

sorted i think i have it on,

now when trying to connect to a network do i manually have to put the ssid in or can i just select a network from a list found (if so how)

---

### Post by hellfire8 on 2009-06-03
ok, i tried what you said above and it says "kill switch must be turned off for wireless to work" 

how do I turn the killswitch off

---

### Post by chili555 on 2009-06-03
> how do I turn the killswitch offI believe there is a switch or pushbutton on the upper right of your notebook, above the keyboard. Open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open while you manipulate the button and let's see if the kernel recognizes the key and turns the wireless on.

---

### Post by hellfire8 on 2009-06-03
yeah sorry sorted it, this is my first post from my new notebook running Xubuntu,

I love the OS so much, its sleek, gorgeous and runs like a dream, software is brilliant and runs very well.

---

### Post by hellfire8 on 2009-06-03
Thank you Chili555, your advice was brilliant and helped me alot, loving the net on this thing,

Do i require Anti virus or spyware? stupid question I know but this is a whole new os.

---

### Post by chili555 on 2009-06-03
You do not require antivirus or spyware programs. There is a linux native antivirus program called clamav which you can obtain with:```
sudo apt-get install clamav
```In my opinion, it's more peace of mind, rather than a real need. Almost every virus ever written is for Windows. As well, virii need administrative rights to your base system, which it isn't going to get if you run as a normal user and don't give out your password unless you know ***you*** are installing software and not a virus.

I have run linux exclusively since 2001 and have never encountered a virus. I'm not saying it can't happen; just that it's highly unlikely.

---

