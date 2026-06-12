---
title: "Ralink pci card"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by sophtpaw on 2006-07-10
Hello,

I would greatly appreciate your support with installing my wireless card. I thnk you in advance

Manufacturer: Edimax
its a pci card
and the chipset is Ralink

it says on the box: IEEE 802.11g 54Mbps

that is all the details i have on the hardware. I had my Linux guru install it for me on breezy, so i know it works. But its been a month in Dapper and i haven't got it installed yet, as i don't know how, and i don't want to bother my guru if i can help it :oops:  Please save me the blushes. That 10m network cable is becoming unseemly and dangerous too(tripped over it once already)

Again your help is appreciated :D 

--
sophtpaw

P.S i'm hoping that the drivers for this piece of hardware are in the new kernel(Dapper)

---

### Post by sophtpaw on 2006-07-10
i see that System/Administration/Networking detects a Ra0 which would be the Ralink pci sitting in my box. It acknowleges that it is not configured, which is what this post wants to achieve. 

Would it be possible to tick the configure box and then fill in the boxes? (not that i'd know how to right now) Does the gui configure the card? I wonder if anyone has any experience with it. 
I had a brief attempt when i had initially upgraded from Breezy to Dapper but my system completely crashed subsequent to me playing with the configuration tool and i had to do a clean installation.
 Since then i haven't touched it again. But the problem that got triggered might have been due to upgrading issues Dapper had from Breezy rather than the fault lying with the networking configuration gui. 
Could someone comment?

---

### Post by diepruis on 2006-07-10
Please post the output of ```
lspci -v
``` and also ```
iwconfig
``` and finally ```
ifconfig
```.

---

### Post by sophtpaw on 2006-07-10
> **diepruis said:**
> Please post the output of ```
lspci -v
```

[http://paste.ubuntu-nl.org/17680](http://paste.ubuntu-nl.org/17680)

 and also ```
iwconfig
```
[http://paste.ubuntu-nl.org/17681](http://paste.ubuntu-nl.org/17681)


 and finally ```
ifconfig
```.

[http://paste.ubuntu-nl.org/17682](http://paste.ubuntu-nl.org/17682)



thank you

--
sophtpaw

---

### Post by diepruis on 2006-07-10
Similiar symptoms to a problem I had. I believe that card uses the rt61 chip. Try [this howto]("http://www.ubuntuforums.org/showthread.php?t=132980") and let me know how it pans out. Good luck :)

---

### Post by sophtpaw on 2006-07-10
> **diepruis said:**
> Similiar symptoms to a problem I had. I believe that card uses the rt61 chip. Try [this howto]("http://www.ubuntuforums.org/showthread.php?t=132980") and let me know how it pans out. Good luck :)

ok, in the how to the tar.gz file links me to a chinese or japanese looking website which is don't understand at all.

i went to the ralink website and couldn't find a link for downloads either. 

I'll keep looking but maybe you have a proper link to the driver for the chipset in question

thank you

---

### Post by jesi on 2006-07-10
The driver is already installed thats why you are getting feedback after typing: iwconfig.

What you need to do is edit the config file to match your access point.  Im in the process of doing this now.

Use the readme file in the /modules folder in the driver folder when doing the editing.  This driver and firmware can be found here: [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)

c) d) and f) are the most important parts from: [http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

Execute those parts after getting the files above and it should work.  (REMEMBER: The driver is only being downloaded for the readme file, you aren't actually going to compile it because dapper comes with it preinstalled.  You do need to move the firmware to the correct folder though.)

---

### Post by diepruis on 2006-07-10
Normally the first part of that howto (the bit with the oddly chinese link) isn't needed for Dapper installs. I don't know if this is valid for an upgraded version but it should be. Try only the second part "rt61 in Dapper" and see if that works (this is the same as jesi's suggestion). If it doesn't then you should try the entire howto.

---

### Post by sophtpaw on 2006-07-10
> **diepruis said:**
> Similiar symptoms to a problem I had. I believe that card uses the rt61 chip. Try [this howto]("http://www.ubuntuforums.org/showthread.php?t=132980") and let me know how it pans out. Good luck :)

Ok, pls ignore my post about the link. I scrolled down to b) section relating to Dapper. I got as far as 2. downloaded the tar.gz and put it in /tmp as requested

but...

tar zxvf rt61sta.dat.tar.gz -C /etc/Wireless/RT61STA 

gives me: livingdaylight@baraka:/tmp$ sudo tar zxvf rt61sta.dat.tar.gz -C /etc/Wireless/RT61STA
tar: /etc/Wireless/RT61STA: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now

I don't know what the -C /etc/Wireless/Rt61STA does but as i say, that is the result i get.

So, i just untarred it but now i don't know how to do what the extra command was supposed to do. Can you pls, help me get past this so i can finish the section and hopefully get the wireless working

thank you

--
sophtpaw

---

### Post by diepruis on 2006-07-10
[QUOTE=sophtpaw]gives me: livingdaylight@baraka:/tmp$ sudo tar zxvf rt61sta.dat.tar.gz -C /etc/Wireless/RT61STA
tar: /etc/Wireless/RT61STA: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now[/QUOTE]

Check if the directory "/etc/Wireless/RT61STA" exists. If it does, try prepending the above command with sudo, as you might not have write access to this directory (in fact you shouldn't).

---

### Post by sophtpaw on 2006-07-10
> **diepruis said:**
> Check if the directory "/etc/Wireless/RT61STA" exists.

Ooops...

Yes, the directory /etc/Wireless doesn't exist. I went back and this is what i actually got: 

> livingdaylight@baraka:/tmp/RT61_Firmware_V1.2$ sudo mkdir /etc/Wireless/RT61STA
mkdir: cannot create directory `/etc/Wireless/RT61STA': No such file or directory


why wouldn't mkdir /etc/Wireless work then?

---

### Post by diepruis on 2006-07-10
It seems you have to take it a step at a time, like so:

```

sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT61STA

```

---

### Post by sophtpaw on 2006-07-10
> **diepruis said:**
> It seems you have to take it a step at a time, like so:

```

sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT61STA

```

Yes, that is what i also figured might be the case (just a guess) and so it was. it worked.

don't know what i'm supposed to do with:

> sudo vi -b rt61sta.dat

---

### Post by sophtpaw on 2006-07-10
> **diepruis said:**
> It seems you have to take it a step at a time, like so:

```

sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT61STA

```

livingdaylight@baraka:/etc/Wireless/RT61STA$ sudo cp *.bin /etc/W ireless/RT61STA/.
cp: cannot stat `*.bin': No such file or directory
livingdaylight@baraka:/etc/Wireless/RT61STA$



???

sudo cp rt61sta.dat /etc/Wireless/RT61STA/. seems to have worked anyways.

the rt61sta.dat file is in /etc/Wireless/RT61STA but as i said in my previous post i don't know what to do with it

after  sudo vi -b rt61sta.dat

it points to d)Enter the necessary information to access your network. Refer to the readme file for options.

**************************************************************
i'm stumped

---

### Post by diepruis on 2006-07-10
You have to edit that file (using vi with the -b switch). You have to enter the right info for your network (SSID, WEP Key, etc.) according to the readme that came with the driver. I posted it below for convenience.

If you're looking for help with vi, just type :h <enter> after starting it up.

---

### Post by diepruis on 2006-07-10
[QUOTE=sophtpaw]
livingdaylight@baraka:/etc/Wireless/RT61STA$ sudo cp *.bin /etc/W ireless/RT61STA/.
cp: cannot stat `*.bin': No such file or directory
livingdaylight@baraka:/etc/Wireless/RT61STA$
[/QUOTE]

You are in the wrong directory, after livingdaylight@baraka: you'll see the directory you are in. You are trying to copy all the bin files in that directory (thats the *.bin bit) to /etc/W ireless/RT61STA/. but they're the same directory (make sense? probably not...).

You need to go back to /tmp/RT61_Firmware_V1.2 and then do the copy from there.

---

### Post by sophtpaw on 2006-07-10
> **diepruis said:**
>  I posted it below for convenience.

?where?

---

### Post by diepruis on 2006-07-10
Gah! I must be getting tired :rolleyes:
Here it is. Don't get frustrated, you're almost there.

---

### Post by sophtpaw on 2006-07-10
> **diepruis said:**
> Gah! I must be getting tired :rolleyes:
Here it is. Don't get frustrated, you're almost there.

Hey, its cool. thanks for sticking with me. However, i can't figure out vi and what i have to do in there exactly. But, i'm gonna give it another go tomorrow now

thanks for the help

-
sophtpaw

---

### Post by diepruis on 2006-07-11
vi can be a bit confusing, but its not hard to learn. Just try the online help like I said and you'll have it in no time.

---

