---
title: "Ubuntu 11.04 PCMCIA Linksys WPC100 not working"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by aboatwri on 2011-06-24
I have a WPC100 linksys network card. I have ubuntu 11.04 installed. My laptop is a D610. 

I have done a LOT of google searching and not seeing any solutions on how to successfully get it working. 

I have tried the ndiswrapper and it does install the driver but then says "no hardware present". 

I have also blacklisted the broadcom drivers. 

Any ideas? I am coming to the conclusion that it will never be possible to get the WPC100 to work. (note I also have been to the support page and do not see it there. )

Thank you in advance for any and all suggestions.

---

### Post by chili555 on 2011-06-24
Let's take a look at what you have. Please jam that card in the slot and open a terminal and run and post:```
sudo lspcmcia ident -vv
dmesg | grep ndis
```Thanks.

---

### Post by karlw1lk1ns on 2011-08-13
Hello,
I have the same issue you are encountering, that Windows Wireless says Hardware is not present. I know this card does work with 11.04, however since I put a fresh install of 11.04 back onto my laptop it appears to be no longer working, I have no records of my setup before. I am new to Ubuntu but I have followed the above steps and get this:

sudo lspcmcia ident -vv
[sudo] password for karl: 
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:00.0)
    Configuration:    state: on    ready: yes
            Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V
            Available IRQs: 3, 4, 5, 10
            Available ioports:    0x00000100 - 0x0000016f
                        0x00000178 - 0x000001ef
                        0x000001f8 - 0x000002f7
                        0x00000300 - 0x0000036f
                        0x00000378 - 0x000003af
                        0x000003e0 - 0x000003ef
                        0x00000400 - 0x000004cf
                        0x000004d8 - 0x000004ff
                        0x00000820 - 0x000008ff
                        0x00000a00 - 0x00000aff
                        0x00000c00 - 0x00000cf7
                        0x00004100 - 0x000043ff
                        0x00004500 - 0x000047ff
                        0x00004900 - 0x00004bff
                        0x00004d00 - 0x00007fff
                        0x00008040 - 0x00008fff
            Available iomem:    0x000d4000 - 0x000dbfff
                        0x60000000 - 0x60ffffff
                        0xa0000000 - 0xa0ffffff
                        0xc0a00000 - 0xc39fffff
                        0xcc200000 - 0xcf9fffff
  CardBus card -- see "lspci" for more information
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:00.1)
    Configuration:    state: on    ready: yes
            Available IRQs: 3, 4, 5, 10
            Available ioports:    0x00000100 - 0x0000016f
                        0x00000178 - 0x000001ef
                        0x000001f8 - 0x0000036f
                        0x00000378 - 0x000003af
                        0x000003e0 - 0x000003ef
                        0x00000400 - 0x000004cf
                        0x000004d8 - 0x000004ff
                        0x00000820 - 0x000008ff
                        0x00000a00 - 0x00000aff
                        0x00000c00 - 0x00000cf7
                        0x00004100 - 0x000043ff
                        0x00004500 - 0x000047ff
                        0x00004900 - 0x00004bff
                        0x00004d00 - 0x00007fff
                        0x00008040 - 0x00008fff
            Available iomem:    0x000d4000 - 0x000dbfff
                        0x60000000 - 0x60ffffff
                        0xa0000000 - 0xa0ffffff
                        0xc0a00000 - 0xc39fffff
                        0xcc200000 - 0xcf9fffff

dmesg | grep ndis
[  119.388680] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  119.441659] usbcore: registered new interface driver ndiswrapper
[  137.299425] usbcore: deregistering interface driver ndiswrapper
[  137.324950] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  137.333515] usbcore: registered new interface driver ndiswrapper

I have been looking for a solution all day, without any luck. Any help would be greatly appreciated.

---

### Post by chili555 on 2011-08-13
> Hardware is not present. That often means the wrong .inf file has been installed. Let's check. Please post:```
sudo pccardctl ident
ndiswrapper -l
```That's a lower-case L for 'list.'

---

### Post by karlw1lk1ns on 2011-08-14
```
karl@karl-linux:~$ ndiswrapper -l
net5416 : driver installed
karl@karl-linux:~$ sudo pccardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available
```

I installed the drivers from the CD, oddly, before when working, I inserted the card and it worked out the box no drivers, nothing.  I did notice when I do a dmseg I get:

```
[ 1065.737798] pcmcia_socket pcmcia_socket1: pccard: card ejected from slot 1
[ 1068.556167] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[ 1068.556207] pci 0000:03:00.0: [168e:0023] type 127 class 0x000280
[ 1068.556221] pci 0000:03:00.0: unknown header type 7f, ignoring device

```

Thanks for getting back to me

---

### Post by chili555 on 2011-08-14
> $ sudo pccardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info availableThat's bad news. Was the device actually inserted at the time? The operating system doesn't see it.> [ 1068.556221] pci 0000:03:00.0: unknown header type 7f, *[COLOR="Red"]ignoring device[/COLOR]*That's consistent with 'hardware not present.' Are you sure the card is not defective?

---

### Post by karlw1lk1ns on 2011-08-15
Thanks for your help Chili 555, your are right it is not good news! 

I tried this in my dell laptop with XP, it does not see it either. So I will be contacting Linksys support shortly as it has just been brought.

Thanks again

---

### Post by chili555 on 2011-08-15
Hopefully, they will send a new one and we can get started again. Post back and we'll be glad to help.

---

### Post by karlw1lk1ns on 2011-08-20
I have now receive a new card if you are able to give me more help :)

---

### Post by chili555 on 2011-08-20
Ready! Please post:
```
sudo pccardctl ident
```Thanks.

---

### Post by karlw1lk1ns on 2011-08-31
Duplicate post... how do I remove? (Or Mods please delete thanks)

---

### Post by karlw1lk1ns on 2011-08-31
Hello, apologies for my slow reply. 

I get the following output:

Socket 0:
  no product info available
Socket 1:
  no product info available

If this is any help;
Dmesg now gives:

[29289.410194] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
[29326.128153] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into

Before was giving '[29272.996192] pci 0000:03:00.0: unknown header type 7f, ignoring device' for my faulty card.

Thanks

EDIT:
I came across a project called Mad Wifi, which supports the wireless card I have, I tried to install it following the comprehensive instructions on the website, but without sucess. Maybe this could be a solution? Link is: [http://madwifi-project.org/](http://madwifi-project.org/)

---

### Post by ToxAtec on 2011-08-31
Hi,

I have a very similar problem with my CardBus slot, one card (a Linksys WG511) is physically detected but somehow doesn't make it's way to the driver. Output is exactly as yours in your last post, and lspci doesn't list the card as well (also tried -H1 and H2).

Another device, an old acx100-based WiFi card, is somehow detected by the PCI subsystem, but with incorrect PCI IDs: 104c:0000 instead of 104c:8400. Forcing the driver to work with it anyway leads to errors during firmware upload. But wait, that's not even interesting for you :P

Because both cards are OK on other laptops but wouldn't work on mine with Linux, including different Live CDs, and Windows 7, I decided to get a new CardBus slot. Maybe yours is fauly as well. I will test the new one either on Tuesday (if it arrives then) or much later, so don't count on me..

---

### Post by karlw1lk1ns on 2011-08-31
Thanks, your post was informative. 

I think my Card Bus must be okay, because when I first tried the network card intially before this problem, it worked seamlessly. I could surf the internet and ultilise all features I should be able to for networking. 

Although it did only work the once and then the card seems to have been "killed", tested and concluded to neither be working in XP. I got a replacement which is tested working on another Laptop with XP, it is physically noted in dmesg without the previously present issues. I have tried to install serveral drivers this Atheros based chipset (Doing a fresh install of Ubuntu after each failed attempt), but there seems to be no link between my hardware and the driver I'm installing. My card bus seems to be installed okay, I will look for another PCMCIA device I could test with to eliminate the possibility of the card slots being faulty. 

Keep in touch with your results, hope its works out!

---

### Post by Jones235 on 2012-01-31
My Linksys PCMCIA card is unrecognized on Ubuntu 11.1 but I know it works fine in Windoze XP...  Inspiron 8000 laptop.  No clue as to how to get it to work.
 
Ubuntu is still rough around the edges when it come to varied hardware.
 
Windoze sucks but it does work...

---

### Post by chili555 on 2012-02-01
> **Jones235 said:**
> My Linksys PCMCIA card is unrecognized on Ubuntu 11.1 but I know it works fine in Windoze XP...  Inspiron 8000 laptop.  No clue as to how to get it to work.
 
Ubuntu is still rough around the edges when it come to varied hardware.
 
Windoze sucks but it does work...Please provide the information requested in post #2.

---

### Post by ToxAtec on 2012-02-01
Sorry for interrupting you, but the email I got because of a new reply reminded me of posting here:

After replacing the CardBus slot any cards are working fine now, and I noticed a difference in the "eject" mechanism (with that stick you can push in).
May[COLOR=Black]be [karlw1lk1ns]("http://ubuntuforums.org/member.php?u=1401783")[/COLOR] you somehow broke the mechanics? Anyway I just wanted to let you know that it's working with the new slot, so it might be worth a try if you didn't fix it yet.

---

