---
title: "how do i make this work?"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by hmmm on 2009-07-22
Hello everybody, 

I am pretty much new to the linux scene i have used ubuntu before for about a week and i got tired of things not being able to work such as my games, i figured out how to get my mp3 to play but i cant now. but anyway back on to subject.

i wasnt sure which one to download so i downloaded Kubuntu it looked more pleasing to the eyes then the Ubuntu Brown. would that matter if i cant get my wireless to work?

my computer is a:
compaq presario 
model # SR5113WM
Amd Athlon(tm) 64 x2 Dual Care Processor 3600+ 1.90GHz
894 MB Ram (suppose to come with 1gig)
32 Bit Os

I partitioned my hard drive to have a seperate space for Kubuntu I installed it and its not reading my wirless card :(  

I have tried following some of the guidlines to find the chipset info for you but i just cant seem to get any of the codes to work but here is the info i have off hand for the USB wireless Adaptor.

Belkin
Enhanced Wireless USB Network Adapter
N150
F6D4050
Ver.1000

the box says it only supports 2000,xp,vista

i will try again with the codes and let you know if i can find anything else out.

i found a code somewere it was
```
lspci -v | less
``` should i change it to ```
lsusb -v | less
```i hope this all makes sense to somebody. 

thanks

---

### Post by Bucky Ball on 2009-07-22
If you type:

```
lsusb
```... does your card show as being plugged in? Is there a blue light or some indication on the card that it is on?

The command you want is:

```
lspci
```

... to find the chipset on the card. It will be toward the bottom of the output somewhere.

---

### Post by bacil on 2009-07-22
probably lshw make more sense

---

### Post by JK3mp on 2009-07-22
yes since its a USB device give us the output of lsusb. That will allow us to determine if its reading the device as plugged in.

EDIT: Sorry when i looked the above two posts were'nt there. :p

---

### Post by hmmm on 2009-07-22
ok here is few things that i got screen shot and some code maybe you can find what your loking for


[IMG]http://i529.photobucket.com/albums/dd335/se7en-mm/snapshot2.jpg[/IMG]

and now the code
```
           Bus 001 Device 005: ID 050d:935a Belkin Components
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass            0 (Defined at Interface level)
   bDeviceSubClass         0
   bDeviceProtocol         0
   bMaxPacketSize0        64
   idVendor           0x050d Belkin Components
   idProduct          0x935a
   bcdDevice            1.01
   iManufacturer           1
   iProduct                2
   iSerial                 3
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength           67
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          0
     bmAttributes         0x80
       (Bus Powered)
     MaxPower              450mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           7
       bInterfaceClass       255 Vendor Specific Class
       bInterfaceSubClass    255 Vendor Specific Subclass
       bInterfaceProtocol    255 Vendor Specific Protocol
       iInterface              5
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x81  EP 1 IN
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x01  EP 1 OUT
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x02  EP 2 OUT
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x03  EP 3 OUT
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x04  EP 4 OUT
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x05  EP 5 OUT
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x06  EP 6 OUT
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes
          bInterval               0

 
```when i did the code that is when i typed lsusb -v | less and everything else was for my external hd and my mouse and the other must of been my printer

---

### Post by Bucky Ball on 2009-07-23
```
lspci
```... with the card plugged in, of course. :)

Are you online with this machine? Just wondering, and this might sound crazy, if you get online in ubuntu with an ethernet card and get your updates, then plug the USB device in and see if Ubuntu offers any restricted drivers for the chipset in the wireless USB device. Just a stab, this has definitely worked on a number of occasions with internal wireless cards. 

It is really a matter of finding out what chipset is on the wireless to see how to deal with it. No idea what Belkin uses.

* ps: Belkin offer no Linux support whatever and if you start to like Ubuntu, it will be a good idea to look for Linux-friendly hardware in the future. Makes life a lot easier. :)

---

### Post by hmmm on 2009-07-23
> **Bucky Ball said:**
> ```
lspci
```... with the card plugged in, of course. :)

Are you online with this machine? Just wondering, and this might sound crazy, if you get online in ubuntu with an ethernet card and get your updates, then plug the USB device in and see if Ubuntu offers any restricted drivers for the chipset in the wireless USB device. Just a stab, this has definitely worked on a number of occasions with internal wireless cards. 

It is really a matter of finding out what chipset is on the wireless to see how to deal with it. No idea what Belkin uses.

* ps: Belkin offer no Linux support whatever and if you start to like Ubuntu, it will be a good idea to look for Linux-friendly hardware in the future. Makes life a lot easier. :)

its not a pci card it is a usb and yes its plugged in when i switch to kubuntu the light does  not turn on at all on it

is there a link or something to a list of wireless adapters that work with linux

---

### Post by Bucky Ball on 2009-07-23
Have you tried plugging in an ethernet cable to get updates and possibly restricted drivers offered when you plug the USB device in? Might save a lot of time if it works.

In your lsusb, device 005 named 'Belkin Components' could be it. You have a Belkin mouse; is the Belkin USB wireless dongle the only other Belkin USB device you have plugged in? If so, it is recognised, just not operational. Try the ethernet cable if that is the case.

If that fails, back to the drawing board. As I say, Belkin seem to provide no Linux support so you might need to rely on the community and your ingenuity or get a friendlier wireless dongle.

* As mentioned, it is a compatible wireless chipset on the adapter that is most important rather than compatible adapter; in this case I think Broadcom 4306 chipset (also mentioned) which should be fully supported.

* Please read this page and post #5:

[http://www.mikegerwitz.com/2008/05/15/ubuntu-804-hardy-heron-broadcom-wireless/](http://www.mikegerwitz.com/2008/05/15/ubuntu-804-hardy-heron-broadcom-wireless/)

---

### Post by hmmm on 2009-07-24
> **Bucky Ball said:**
> Have you tried plugging in an ethernet cable to get updates and possibly restricted drivers offered when you plug the USB device in? Might save a lot of time if it works.

In your lsusb, device 005 named 'Belkin Components' could be it. You have a Belkin mouse; is the Belkin USB wireless dongle the only other Belkin USB device you have plugged in? If so, it is recognised, just not operational. Try the ethernet cable if that is the case.

If that fails, back to the drawing board. As I say, Belkin seem to provide no Linux support so you might need to rely on the community and your ingenuity or get a friendlier wireless dongle.

* As mentioned, it is a compatible wireless chipset on the adapter that is most important rather than compatible adapter; in this case I think Broadcom 4306 chipset (also mentioned) which should be fully supported.

* Please read this page and post #5:

[http://www.mikegerwitz.com/2008/05/15/ubuntu-804-hardy-heron-broadcom-wireless/](http://www.mikegerwitz.com/2008/05/15/ubuntu-804-hardy-heron-broadcom-wireless/)


my mouse is a dynex, the belkin would be my wirless usb adaptor, i dont have a hard wire to plug in im picking up my neighbors wirless.  ill check out the link.

i guess if i cant get it working ill have to buy another one before i can use kubuntu.  but if anyone can help me figure this out that would be appreciated.

thanks

---

### Post by bkratz on 2009-07-24
A quick search for this adapter " Belkin 050d:935A " showed three pages of threads that you probably want to view. This is a typical one

[http://ubuntuforums.org/showthread.php?t=1175235&highlight=belkin+050d:935A](http://ubuntuforums.org/showthread.php?t=1175235&highlight=belkin+050d:935A)

---

### Post by hmmm on 2009-07-24
i tried doing what he said but for some reason i can not delete files or paste file in to the root folder? so i can not finish what i need to do.

is there a way so i can change it so i can delete and paste.

they say i need to delete existing rt2870sta driver but im not seeing it anywere in the /usr/src area they are talking about?

---

### Post by Bucky Ball on 2009-07-24
are you using 'sudo' before your commands to execute them as root?

You can try:

```
locate Driver_to_delete
```... replacing 'Driver_to_delete' with the one you're after.

---

### Post by hmmm on 2009-07-24
im just typing them in as people tell me what codes to type in.

---

### Post by hmmm on 2009-07-25
would anybody happen to know if these will work with kubuntu

[card1]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124314")  <--- thinking of getting this one

[card2]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833124347")

if neither one of those would work can anybody give some link for some that will work

i need something that can install without having to use a hard line cable to download drivers directly because i have no hard line to internet in my apt i am picking up strictly wireless from a neighbor, so i need something that just plug and play or something i can download save to my external hd and use it from there

thanks

---

### Post by Bucky Ball on 2009-07-26
As I mentioned before, Linksys provide no Linux support whatever on their site. Also mentioned; try to go for manufacturers who are Linux friendly when buying hardware. Have a look at the link in my signature and go to the part about the wireless card.

My reccomendation, based on a build I did at Christmas which required a wireless card for a long distance, is this[ tp-link]("http://www.tp-link.com/products/product_des.asp?id=17") model.

It worked beautifully from the start, I was offered the drivers and it was simple. Totally compatible and has been doing the job without a hitch for the last six months. :)


Check here for compatible cards:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Also, these seem to be the Linksys supported USB cards:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB)

---

### Post by hmmm on 2009-07-26
> **Bucky Ball said:**
> * ps: Belkin offer no Linux support whatever and if you start to like Ubuntu, it will be a good idea to look for Linux-friendly hardware in the future. Makes life a lot easier. :)

> If that fails, back to the drawing board. As I say, Belkin seem to provide no Linux support so you might need to rely on the community and your ingenuity or get a friendlier wireless dongle.

you said belkin not linksys, just thought i would point that out and i will probably go with the one you used newegg had it for 15$

thanks

---

### Post by Bucky Ball on 2009-07-27
> **hmmm said:**
>  i will probably go with the one you used newegg had it for 15$

thanks

You're welcome, but that is for a desktop, not laptop. Not sure which yours is. Yea, got my threads mixed up! oops, must have been getting late again.

Just one thing; are you running the AMD64 version of Ubuntu? I just re-read your first post and you should be if your not. Will still run 32bit apps and has its advantages. Will utilise your hardware better. :)

---

### Post by hmmm on 2009-07-27
i do have a desktop, i downloaded the first option standard personal computer, i didnt download the 64-bit cuz my computer says its only a athlon63 but its a 32-bit os  here is screen shot

but if ur sure the 64-bit will install and run fine i will download and install that.

[IMG]http://i529.photobucket.com/albums/dd335/se7en-mm/Untitled.jpg[/IMG]

---

### Post by Bucky Ball on 2009-07-28
Yep, 64bit for you. Note the 'Processor' line under 'System': AMD Athlon 64 x2. A 64bit dual core AMD processor ready to roll. 

You might be currently running a 32bit version of Windoze, but you have a 64bit processor in there so I would advise you take advantage of that. :)

---

### Post by hmmm on 2009-07-30
i installed the 64 bit and it still wont read the usb device,

 im working on building me a new computer and buying that card that you bought. here is a link to my computer build if it works.

 [http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=12160786](http://secure.newegg.com/WishList/PublicWishDetail.aspx?WishListNumber=12160786)

---

### Post by Bucky Ball on 2009-07-30
I would go back to my link in my signature and check the part about power supplies. There is no way you need this beast and it is probably rated at 70% and below efficiency. A good power supply will give what it's rated and you probably don't need anything over 480W for this rig (and that might be pushing it). As it says in the HOWTO in my signature, it is worth spending a little extra at the beginning.

Read the section about [_ENERGY-EFFICIENT, 85+ PSUs_]("http://ubuntuforums.org/showthread.php?t=1179877") carefully and be aware of the pitfalls of 'cheap' and 'powerful'. Punch the details in to the Antec PSU calculator linked to there and see what you come up with. I'd be interested to know. (NB: this calculator is calibrated for Antec supplies NOT other like the one you're looking at). This one might fit the bill, although twice the price:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=antec+earthwatts&x=0&y=0](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=antec+earthwatts&x=0&y=0)

... by no means not the only 85+ PSU on the market. Hopefully there is a wider selection of 85+ PSUs where you are than there is in Australia.

And for a few extra bucks I would probably go for [THIS]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136358") hard drive. It is 40% more energy-efficient, virtually silent and runs pretty much cold ... and it's double the size of the one you've selected. :)

ps: AMD man myself when I build 'em nowadays but that's neither here nor there. I used an AMD 4850e for the machine in the link, again, 45W; less energy and virtually the same specs and runs ***very*** cool. 2.5 as opposed to 2.8 though I think. I have just spent a week on holiday at the in-laws tweaking that machine and it certainly is sweet.

... having said all that, I am typing from the first serious machine I built with Intel CPU (single core P4 A/V machine).

---

### Post by hmmm on 2009-07-30
ill look into the info and specs. i usualy do build amd but im gona try out intel this time around. i never had an intel so it will be the first for me. just wanting to try something different.

thanks again on the info.

---

