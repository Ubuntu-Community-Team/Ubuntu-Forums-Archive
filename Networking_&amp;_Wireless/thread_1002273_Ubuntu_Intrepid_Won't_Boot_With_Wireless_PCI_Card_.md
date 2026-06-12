---
title: "Ubuntu Intrepid Won't Boot With Wireless PCI Card Installed"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by harpoonz on 2008-12-04
I'm new to Ubuntu and I'm having a problem installing a wireless card.  The card in question is a Belkin F5D7000 ver 7.000 that's plugged into a pci slot.  

I have Ubuntu already installed on the sytem and everything else is running great, the problem arose after I decided to pop in the wireless card.  After putting the card in,the boot process gets to the generic yellow/beige screen with the mouse cursor and then stalls.  I let it sit all night and I never got an error message just a complete lockup on boot. When I pull the card out, Ubuntu boots as normal. I can't run the Live CD either with the card plugged in.  The wireless card runs fine on the same system under Windows XP so I know its not a card or pci failure.  

Any help on this matter would be great.  Here are the specs on the system.

Ubuntu 8.10
IBM Netvista 6350
Pentium 4 1.8ghz
Intel 845 chipset
Integrated Sound/NIC
1gb RAM
Nvidia Vanta video card

---

### Post by IQRules on 2008-12-04
Maybe take out the PCI card and install the driver

[http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide](http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide)

You might want to add ndiswrapper to /etc/modules.

Could you boot into single user mode when PCI card is in the system?

---

### Post by harpoonz on 2008-12-04
Thanks for the response IQ.

I tried booting into single user mode with the card plugged in and boot still stalled.  

I installed ndiswrapper from synaptic and then tried following the directions on the link you gave me. After typing:

```
sudo ndiswrapper -i /home/username/drivers/r74092us/AR/bcmwl5a.inf
```

I got this error message:

```
couldn't open /home/username/drivers/r74092us/AR/bcmwl5a.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
```

I opened up the ndiswrapper-1.9 file and scrolled to line 219 and this is what is written:

```
    open(INF, $filename) or die "couldn't open $filename: $!";
```


I'm afraid I'm going to need a little more help as I have practically no Linux knowledge of my own to draw upon.

---

### Post by harpoonz on 2008-12-05
Anyone?

---

### Post by Ayuthia on 2008-12-05
> **harpoonz said:**
> Thanks for the response IQ.

I tried booting into single user mode with the card plugged in and boot still stalled.  

I installed ndiswrapper from synaptic and then tried following the directions on the link you gave me. After typing:

```
sudo ndiswrapper -i /home/username/drivers/r74092us/AR/bcmwl5a.inf
```

I got this error message:

```
couldn't open /home/username/drivers/r74092us/AR/bcmwl5a.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
```

I opened up the ndiswrapper-1.9 file and scrolled to line 219 and this is what is written:

```
    open(INF, $filename) or die "couldn't open $filename: $!";
```


I'm afraid I'm going to need a little more help as I have practically no Linux knowledge of my own to draw upon.

This means that the bcmwl5a.inf file was not found at that location.  Please check and see if the file is there:
```
ls /home/username/drivers/r74092us/AR/
```
This command will list out the files in that directory.  You will need to see if there is a bcmwl5a.inf and a bcmwl*.sys file there.

---

### Post by IQRules on 2008-12-05
ls /home/username/drivers/r74092us/AR/

Replace 'username' to YOUR account ID joe. Should be 1 of 'ls /home'.

---

### Post by earle79 on 2008-12-10
> **harpoonz said:**
> [SIZE="1"][COLOR="Gray"]I'm new to Ubuntu and I'm having a problem installing a wireless card.  The card in question is a Belkin F5D7000 ver 7.000 that's plugged into a pci slot.  

I have Ubuntu already installed on the sytem and everything else is running great, the problem arose after I decided to pop in the wireless card.  After putting the card in,the boot process gets to the generic yellow/beige screen with the mouse cursor and then stalls.  I let it sit all night and I never got an error message just a complete lockup on boot. When I pull the card out, Ubuntu boots as normal. I can't run the Live CD either with the card plugged in.  The wireless card runs fine on the same system under Windows XP so I know its not a card or pci failure.  

Any help on this matter would be great.  Here are the specs on the system.

Ubuntu 8.10
IBM Netvista 6350
Pentium 4 1.8ghz
Intel 845 chipset
Integrated Sound/NIC
1gb RAM
Nvidia Vanta video card[/COLOR][/SIZE]

I have this same issue, different computer specs but same thing.  I have the same exact wireless card too.

So did installing the driver first work for you?

---

### Post by harpoonz on 2008-12-11
Had a few distractions and it took awhile to try this again.  So, I tried to install the Dell driver again...still said there was no file to be found even though I could see it in the specified place with file browser.  I unpacked the file to my desktop, ran the commands, and this time it worked and I installed the driver.

The bad news however, is that I still can't boot into Intrepid with the card installed...it still stalls.  According to ndgtk, the driver is installed but my card still is not being recognized.  

I'm beginning to think that this is a irq or pci problem and not a problem with the OS recognizing the card.  I would think that even if the card wasn't recognized, Ubuntu would boot as normal.  

I tried booting with acpi turned off and the card in the pci slot and it still stalled.  I have an option in my bios for pci parity and switching that did nothing noticeable either.  

I'm pretty much at a loss here as to what to do next.

---

### Post by earle79 on 2008-12-11
well, I know how you feel.  I can't get this to work either.  but I do think its something PCI and IRQ related because I can't the computer to boot with ANY PCI card installed, so its not just this one card.  I too have tried all combinations of GRUB loader options.  I just don't get it.

---

### Post by harpoonz on 2008-12-11
Well I just booted my box up with Ultimate Boot CD to run some diagnostic tests on the motherboard.  I ran the PCI diagnostic and I get a "BUS ACCESS DISABLED!!" error. 

I have the latest bios installed and according to the diagnostics there does not seem to be an IRQ conflict.  

The strange thing is that when I swap out harddrives with a WinXP install everything works fine, wireless included, and this is with the exact same hardware setup.

Any ideas on how to enable bus access?

---

### Post by earle79 on 2008-12-12
hey harp, well just so you know, i pull a d-link card out of my other desktop and the computer boots just fine.  so i guess 8.10 really doesn't like this card.  i will see if i can get this card to work now.

---

### Post by earle79 on 2008-12-13
harp, just letting you know that i really think its that card.  cause i got my dlink card to work so far.  i just have to reinstall it everytime i reboot which i am working on that now.  if you get that card to work let me know.

---

