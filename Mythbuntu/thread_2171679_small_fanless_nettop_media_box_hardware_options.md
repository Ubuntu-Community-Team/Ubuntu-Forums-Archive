---
title: "small fanless nettop media box: hardware options?"
date: 2013-09-01
forum: Mythbuntu
---

### Post by feydrutha on 2013-09-01
Hi,

I am looking to buy a small, silent device to use as a media box plugged into my tv with either mythtv or xbmc, and have not had too much luck googling around so far (maybe I am using the wrong terminology..) so I would welcome some pointers

key requirements:

- fairly small
- silent: no fans or spinning disks
- HDMI output to my TV
- hardware well supported under linux

Other stuff:
- built-in IR receiver and remote would be nice!
- 128GB internal ssd storage would be my ideal, but micro-SD slot or USB port for storage would also be ok.

In addition to watching video, I plan to plug in my webcam and do video calling: skype would be great, though that requires an x86/x86_64 architecture it seems so it limits the options even more.

Any suggestions are appreciated (up to an included "post this on forum XYZ, not here")

thanks

---

### Post by Thee on 2013-09-01
You might wanna consider a Raspberry Pi: [http://www.raspberrypi.org/faqs](http://www.raspberrypi.org/faqs)

- It's a size of a credit-card.
- It has no active fans.
- Has HDMI with dedicated GPU that can play 1080p videos.
- You can install various distributions on it.
- It doesn't have built in HDD, but it has a SD slot on which the OS goes + It has 2 USB slots so you can connect an external HDD + It has a Ethernet port which you can hook up to a NAS device. So storage isn't really a problem.
- Costs around $35.

[FONT=Verdana]It doesn't have a IR receiver, but you can buy a cheap remote with a USB IR receiver and hook it up. That's what I did, and it makes a very nice Media Center solution.[/FONT]

Not sure about the Skype part tho.

---

### Post by Merrattic on 2013-09-01
It has got a fan, but you wouldn't know it is so quiet, just need to install an SSD if the HDD it too noisy, and the ion graphics take care of the rest

Asus EE 1015P (or a 1012 / 1012P for that matter) The 1015P usually comes with its own remote control and IR.

I have this setup at home as my HTPC running XBMC on top of Xubuntu, with an Eyetoy webcam and small remote keyboard, perfect.

---

### Post by feydrutha on 2013-09-01
Thanks for the suggestions.

I think I need an x86 architecture for skype, so that rules out the rasberry PI. This might also mean I have to compromise on the "no fan" requirement: I suppose I can live with a fan so long as it's not too loud!

>  Asus EE 1015P (or a 1012 / 1012P for that matter) The 1015P usually comes with its own remote control and IR.


Hmm are you sure? the 1015p seems to be a netbook... Maybe you mean 1501p? Anyhow one of the asus eee box options could be good, particularly the barebones ones so I can get an SSD without paying for a useless hard disk. The 1501p and 1012p seems to be out of stock though... There's a 1033 barebones still available here and there for about 200$, but I'm not sure how well it supports linux...

I'm also looking at the zotac zbox id80, which can be bought barebones for 200$ and also comes with IR receiver and remote according to the zotac site...

---

### Post by feydrutha on 2013-09-01
> **feydrutha said:**
> 
I'm also looking at the zotac zbox id80, which can be bought barebones for 200$ and also comes with IR receiver and remote according to the zotac site...

Looks like ([http://knurdtech.com/intel-atom-d2700-htpc-review/](http://knurdtech.com/intel-atom-d2700-htpc-review/)) this has an Nvidia Geforce GT520M, which should work out of the box, but the ethernet card is realtek which in my experience has terrible linux support.. and sure enough googling for Realtek RTL8111 linux finds lots of howtos to get it to work...

The asus EB1033 has a Geforce 610M which uses optimus which makes it a bit harder to make it to work on linux, and I cannot find out what ethernet/wireless chipset it has or how well it is supported. So I think I'll go for the zbox ID80 and see. I'll reporta back what I found.

---

### Post by Merrattic on 2013-09-01
Yes sorry I meant the Asus EB 1501. The Asus EB 1012 is just as good, but no DVD drive built in.

---

### Post by williammanda on 2013-09-05
This might work:

[http://www.linuxmint.com/store_mintbox.php](http://www.linuxmint.com/store_mintbox.php)

---

### Post by feydrutha on 2013-09-11
> **williammanda said:**
> This might work:

[http://www.linuxmint.com/store_mintbox.php](http://www.linuxmint.com/store_mintbox.php)

thanks, great idea! The mint model does not do exactly what I want (it comes with a spinning disk) but some of the fit-pc models look ideal! These are actually fanless!

I am ordering a fit-pc3 LP diskless, and fitting it with an SSD. We'll see how that goes

---

### Post by novellahub on 2013-09-12
Here is another option:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16856173034](http://www.newegg.com/Product/Product.aspx?Item=N82E16856173034)

---

### Post by feydrutha on 2013-09-19
> **feydrutha said:**
> thanks, great idea! The mint model does not do exactly what I want (it comes with a spinning disk) but some of the fit-pc models look ideal! These are actually fanless!

I am ordering a fit-pc3 LP diskless, and fitting it with an SSD. We'll see how that goes

This thing is amazing. Super-small, no moving parts or noise of any kind, solid metal to dissipate the heat.

Got it and popped in my SSD (that already had ubuntu installed on it from a previous box I had to send back). By the time I had it plugged into the TV, the desktop was already up and running. Have to love linux for doing this. Shortest setup ever :-). 

Initially it seemed laggy in response to input, but it turns out I just had to plug the wireless keyboard dongle on the front instead of the back: I think the metal body is heavy-duty enough to interfere with the signal from the wireless keyboard/touchpad. It seems more or less fast enough to run full ubuntu with unity, though I may want to switch it to some lighter-weight variant at some point.

I enabled the AMD proprietary driver to get audio over HDMI working and (possibly) smoother video playback. Normal resolution video plays well, 720p seemed to play OK though I'll have to test some more. Don't have any 1080p video to test.

---

### Post by topcat5 on 2013-09-19
If you are doing OTA then the real test will be 1080i with 2x interlacing.   If it can handle that, then you are fine.

---

