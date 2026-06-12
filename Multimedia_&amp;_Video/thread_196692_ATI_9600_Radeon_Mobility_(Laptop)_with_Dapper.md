---
title: "ATI 9600 Radeon Mobility (Laptop) with Dapper"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by DonQuixote on 2006-06-14
I'm only posting this because I have tried just about eveything I have found to get my graphics working right.  So far I've had no luck (thus this post :D).

One of the solutions created the dreaded double drum sound when the login screen comes up.  I was able to resolve this with Breezy in [this]("http://ubuntuforums.org/showthread.php?t=133707&highlight=double+drum") thread.  However, that version of the driver will not work with xorg 700.  At least that is the message I am given when I try doing in Dapper what I did in Breezy.

If ***ANYONE*** has had success in getting this card to work on their laptop with Dapper, I would be most grateful if you would share how you did it.

Thanks

---

### Post by pksings on 2006-06-14
It is unfortunate but I too am in the same plight, nothing has worked, it still shows using the openmesa drivers in fglrxinfo.  Please notify me also if you have had success, I really would like to fix this....

Thanks

PK


[QUOTE=DonQuixote]I'm only posting this because I have tried just about eveything I have found to get my graphics working right.  So far I've had no luck (thus this post :D).

One of the solutions created the dreaded double drum sound when the login screen comes up.  I was able to resolve this with Breezy in [this]("http://ubuntuforums.org/showthread.php?t=133707&highlight=double+drum") thread.  However, that version of the driver will not work with xorg 700.  At least that is the message I am given when I try doing in Dapper what I did in Breezy.

If ***ANYONE*** has had success in getting this card to work on their laptop with Dapper, I would be most grateful if you would share how you did it.

Thanks[/QUOTE]

---

### Post by harishg on 2006-06-15
I'm not sure what is your exact problem.The card worked perfectly out of the box for me.

---

### Post by DonQuixote on 2006-06-15
Harishg,

Are you refering to the laptop card, or a desktop card?  I'm talking about the 9600 Radeon Mobility in a laptop.

If indeed you are talking about a laptop, then I'd like to know what you did.  Maybe I'm missing something.

---

### Post by norwichnick on 2006-06-16
Hi there, 

I'm new to this particular forum but I've been playing about with Ubuntu for some time on and off. Yesterday I downloaded and installed 6.06 on my laptop and I was extremely impressed by the hardware support 'out of the box'. 

My wireless card worked fine, as did the ACPI power management.

Likewise, my laptop has a ATi Radeon 9600 Mobility. While it seems ok for basics, the framerates for everything is extremely slow and provides very little 3D functionality.

My desktop has an nVIDIA GeForce 6600GT and it works fine on there after installing the nVIDIA drivers from their site.

If anyone has any answers as to getting a decent ATi driver to work, please post! I think I speak for all other 9600-M owners out there too, lol.

Regards, Nick

---

### Post by harishg on 2006-06-17
I'm talking of the laptop.In fact I'm not sure what exactly the problem is.What I did was just put my the breezy badger install CD and did the installation and it worked without any problem.Recently I updated to  dapper drake recently and it worked fine.I did not try to install the ati driver available through synaptic since I remember reading somewere it does not work for this card.The default ubuntu driver worked fine for me.

---

### Post by harishg on 2006-06-17
I did not try to get 3-d acceleration working since I was happy with the current performance.

---

### Post by DonQuixote on 2006-06-17
I would be happy with it as well, except the default drivers don't give me the 1600x1200 resolution I'm used to, and had working with Breezy.  As far as I know the default (vesa) drivers don't have that capability.

---

### Post by planetpounder on 2006-06-18
Hi there,

First of all, I am a complete n00b so forgive me if I bore you with my stupidity.
But err I happen to have a laptop with an ATI Radeon 9600 mobility.

In a clean Dapper install i just installed the driver through:

sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xorg (and made sure that the adapter is fglrx)

Reboot or stop/start explicit services and your 3d should work.

Good luck solving your problem

---

### Post by harishg on 2006-06-18
May be a signed petition should be send to ati for releasing a driver for this version of their graphic card. =)

---

