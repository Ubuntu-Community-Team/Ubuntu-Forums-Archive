---
title: "Xorg doesn't start with more than 2Gb RAM"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by ravit on 2008-04-21
I have quite a strange problem with my Asus F3SR laptop. The main hardware info is the following:

Mobile Intel® 965PM + ICH8M/ Duo T7300 / 2 Gb RAM / ATI Mobility Radeon HD 2400

More details can be found here:
[http://www.asus.com/products.aspx?modelmenu=2&model=1825&l1=5&l2=26&l3=316&l4=0](http://www.asus.com/products.aspx?modelmenu=2&model=1825&l1=5&l2=26&l3=316&l4=0)

I was using 7.10 until recently and was quite happy with it except for that my sound didn't work as well as special laptop keys and suspending :) But that was something I could live with.

Recently I have faced a necessity to upgrade it to 4 Gb RAM. So I've bought the new RAM and installed. Quite surprisingly my system didn't load completely - there was an xorg error "invalid mem allocation" and xserver hasn't started. Then I thought that maybe new Ubuntu 8.04 will solve this problem, so I have downloaded several RCs. Then I tried Ubuntu 8.04, Kubuntu 8.04 and even Kubuntu 8.04 AMD64. I faced the same problem - on 2 Gb RAM everything seems to work fine from the live CD, but not with 4 Gb. Even the 64bit one didn't work with 4 Gb due to the same xorg error. Btw, neither of the systems worked with 3 Gb either.

I have did the memtest for the new RAM and it passed perfectly. I have also dig the Internet, tried to play around with xorg.conf, but without any success - but I'm too unexperienced probably to be successful in it.

I am not very experienced with Linux systems and would be very grateful for any help. I still keep my old RAM at hand because I need to continue working, so I am open to try anything, especially with a live CD :)

P.S. I will try to download Gnome-based Ubuntu 8.04 RC AMD64 tonight and will try it as well, but don't hope for any success.

Victor

---

### Post by prshah on 2008-04-21
> **ravit said:**
> 
Mobile Intel® 965PM + ICH8M/ Duo T7300 / 2 Gb RAM / ATI Mobility Radeon HD 2400

Recently I have faced a necessity to upgrade it to 4 Gb RAM. So I've bought the new RAM and installed. Quite surprisingly my system didn't load completely - there was an xorg error "invalid mem allocation" and xserver hasn't started. Then I thought that maybe new Ubuntu 8.04 will solve 

Please post your "/var/log/Xorg.0.log" file here for more information.

However, I don't believe it has anything to do with your RAM; the problem is with the display card, I think. In the BIOS, there is an option "AGP window aperture size".. can you set this to 128 or higher?

However, first... your log file, for a clue.

---

### Post by ravit on 2008-04-22
Hello PRShah!

Thank you for your help with my problem!

I have switched the RAM, loaded, then had to press ctrl+alt+del to reboot because I was not able to do anything with the computer. Then I have removed the 4Gb and installed 2Gb again and loaded fine as always. Please find an archive attached, which has two files inside - the old one is of the unsuccessful load with 4Gb, the other - the one after a successful load.

I am looking forward to your comments. Thank you very much!

---

### Post by ravit on 2008-04-23
I've updated my BIOS version recently - thought the problem was with it actually. I had 205 and now I have 209, but it hasn't solved the problem at least with the 7.10 I have installed. I will also try to play around with newer Ubuntu versions tomorrow and with driver settings. In any case I would be very grateful for any help with this strange issue.

---

### Post by ravit on 2008-04-23
I have also installed the newest ATI proprietary driver and as far as ATI Control Center says it is actually used. But it didn't help. I have also tried the 8.04 amd64 live CD but with the same result - X doesn't start normally :(

---

### Post by ravit on 2008-04-25
I have no more ideas. Will try the newest Ubuntu releases within several hours, but if it will not work then probably would have to try Windows :( Unfortunately I need this much RAM very much for my work :(

I am more than a year on unix (FreeBSD and Ubuntu) already and it would be a pain for me to get back to MS :(

---

### Post by prshah on 2008-04-25
> **ravit said:**
> 
Then I have removed the 4Gb and installed 2Gb again and loaded fine as always. Please find an archive attached, which has two files inside - the old one is of the unsuccessful load with 4Gb, the other - the one after a successful load.


Did you try my earlier suggestion?> 
In the BIOS, there is an option "AGP window aperture size".. can you set this to 128 or higher?

Taking a look at your config files, I see:

Successful load:
> 
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 2400" (Chipset = 0x94c9)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x15b2)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[color=red](--) fglrx(0): Linear framebuffer (phys) at 0xc0000000[/color]


Unsuccessful load:
> 
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 2400" (Chipset = 0x94c9)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x15b2)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[color=red](EE) fglrx(0): No valid linear framebuffer address[/color]
(EE) fglrx(0): PreInitConfig failed


The linear framebuffer address in the successful load seems to be at the limit of 32bit accessibility. I'm guessing, (but without any qualifications to do so) that in the 4Gb case, the framebuffer address is out of the range of the driver.

Can you add the line ```
"Option" "UseFBDev" "false"
``` to your xorg.conf graphics "Device" section and see if it helps? The below is an example from my xorg.conf, only you set it to false.

> ```

Section "Device"
        Identifier      "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option  "UseFBDev" "true"
EndSection

```

---

### Post by ravit on 2008-04-25
Thank you very much for getting back to me. About the AGP size - while this option is it seems always available in BIOS for most PC, it is not presented in my laptop BIOS, so I was not able to try it.

About the xorg.conf - I will try your suggestion right now and will get back to you with results very soon. If it will not work out I will also attach my xorg.conf here - in case I made errors in there. Initially my xorg.conf is done using the aticonfig command.

Will be back with results very soon.

Thanks again.

---

### Post by ASULutzy on 2008-04-25
change your xorg.conf to use vesa as driver instead of fglrx (use recovery mode if necessary)

I think I may know your problem

type ```
cat /proc/mtrr
```

If you get output with stuff uncacheable, you'll probably have to edit your mtrr tables which can be a pain....

[http://ubuntuforums.org/showthread.php?p=4766662](http://ubuntuforums.org/showthread.php?p=4766662)

I made a post on what I had to do to get fglrx working with more than 3 GB of ram. Post there if you need more help

---

### Post by ravit on 2008-04-25
> **prshah said:**
> 
The linear framebuffer address in the successful load seems to be at the limit of 32bit accessibility. I'm guessing, (but without any qualifications to do so) that in the 4Gb case, the framebuffer address is out of the range of the driver.

Can you add the line ```
"Option" "UseFBDev" "false"
``` to your xorg.conf graphics "Device" section and see if it helps? The below is an example from my xorg.conf, only you set it to false.

I have tried it but X hasn't started even with 2 Gb of RAM. At least I saw black screen only and had to reboot. I have attached xorg.conf with the change done and both logs - maybe you will find some error in what I am doing.

I will also check the other thread now and will try to deal with vesa.

---

### Post by ravit on 2008-04-25
> **ASULutzy said:**
> change your xorg.conf to use vesa as driver instead of fglrx (use recovery mode if necessary)

I think I may know your problem

type ```
cat /proc/mtrr
```

If you get output with stuff uncacheable, you'll probably have to edit your mtrr tables which can be a pain....

[http://ubuntuforums.org/showthread.php?p=4766662](http://ubuntuforums.org/showthread.php?p=4766662)

I made a post on what I had to do to get fglrx working with more than 3 GB of ram. Post there if you need more help

Thank you! I will check that thread right now. I have also executed that code and got the following output:

```
# cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
```

---

### Post by lanks on 2008-05-08
Hello,

I'm having the exactly same problem. I have a Fujitsu-Siemens Amilo Si1520 (Core 2 Duo T7200, Intel® 945GM+ICH7-M, Intel® Graphic Media Accelerator 950 integrated) and I'm working with 3GB just fine. When I try to change to 4GB I have the exactly same problem. I'm using Ubuntu 8.04.

Here's my logs:

```
cat /proc/mtrr 
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xbf700000 (3063MB), size=   1MB: uncachable, count=1
reg03: base=0xbf800000 (3064MB), size=   8MB: uncachable, count=1
reg04: base=0xc0000000 (3072MB), size= 256MB: write-combining, count=1

```

Tanks

---

### Post by ravit on 2008-05-08
There is one more person contacted me via private message who has the same ASUS as I do and experienced the same problem. But at least for me X doesn't start even with 3Gb RAM - only with 2Gb :( 

Maybe you could try to fix mtrr (take a look at [http://ubuntuforums.org/showthread.php?p=4766662](http://ubuntuforums.org/showthread.php?p=4766662) for more details) - maybe it will work for you because your system works fine with 3 Gb. The mtrr fix didn't work for me.

I don't know what is the problem but have a feeling that something is wrong in the kernel. I was going to find some support section for it but hasn't yet tried to do it.

If you will have any news please tell all us about it.

Thank you.

---

### Post by siddtharth on 2008-05-08
Hi Guys,
I'm also having the same problem. I have a sony Vaio vgn fe 890 with Nvidia 7600Go 128MB memory. I was using ubuntu 7.10 with 2GB RAM and everything worked fine, but once I increased the RAM to 3GB I got the same problem that you guys have. I thought this might be fixed in ubuntu 8.04, but NO have the same problem. If I go back to 2GB ubuntu 8.04 works great but as soon as I increase the RAM to 3GB it gone. I have tried almost everything that has been suggested. I really want to use ubuntu but have to keep 3GB RAM.
There is a new Nvidia driver out 173.08 I think I have not tried that yet, will try it this weekend. Also my BIOS is up to date and there is no option to specify the AGP apature size

---

### Post by ravit on 2008-05-08
Hi siddtharth!

Your story is identical to my - my ASUS works with 2Gb only - doesn't work with 3Gb or 4Gb. I have also upgraded my BIOS and also I don't have AGP Aperture Size setting in my BIOS. I use the newest ATI drivers but X doesn't start on more than 2Gb regardless of all things I tried starting with xorg.conf changes and finishing with MTRR tweaks.

It seems that this problem is quite wide spread so I hope there will be more people coming to this forum thread and telling about it. I think we should tell about it also to some guys who could help. Maybe linux.org or some other quite general resource related to kernel development has some kind of issues reporting system?

Victor

---

### Post by ravit on 2008-05-26
Good news for everybody with Asus F3Sr laptop - many thanks to [[COLOR="Blue"]_black_sea_[/COLOR]]("http://ubuntuforums.org/member.php?u=570934") who has found that new BIOS for this laptop resolves all problems with 4 Gb RAM. So at least it is fixed for me also.

The only conclusion I can make is that probably it was not a problem of Ubuntu or xorg but rather the one of the laptop itself. For all other people having the same problem I would recommend to update their BIOS to the most recent version and if it doesn't work in this case then probably contact the manufacturer to ask them to provide a new BIOS version, which would fix the problem.

---

### Post by siddtharth on 2008-05-26
great new ravit for asus user! but I have a sony vaio and I dont think sony will release a new BIOS for a linux issue.

---

### Post by ravit on 2008-05-26
The thing is that the updated BIOS Asus provided has nothing to do with Linux - officially they say that they don't support Linux and there is nothing about Linux compatibility in the release notes. So maybe Sony will do the same... at least it costs one nothing to send them a correpondent inquiry.

---

### Post by ravit on 2008-05-26
The thing is that the updated BIOS Asus provided has nothing to do with Linux - officially they say that they don't support Linux and there is nothing about Linux compatibility in the release notes. So maybe Sony will do the same... at least it costs one nothing to send them a correspondent inquiry.

---

