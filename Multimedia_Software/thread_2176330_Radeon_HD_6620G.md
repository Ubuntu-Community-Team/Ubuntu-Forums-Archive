---
title: "Radeon HD 6620G"
date: 2013-09-23
forum: Multimedia Software
---

### Post by jl.matthews on 2013-09-23
Hello,

I am very new to Ubuntu and I am having a hell of a time with my video drivers. I get a watermark when I use the proprietary drivers but not using them overheats my laptop.

Here is the output from my Terminal:

 00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6620G]01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [Radeon HD 6600M/6700M/7600M Series]


Can anyone advise/link the driver I need to use and maybe how to install it.

Thanks

jl.matthews

---

### Post by Yellow Pasque on 2013-09-24
If you use the 13-8 beta driver, it should get rid of the watermark. Directions for Raring/13.04: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

---

### Post by Ephryn_Thompson on 2013-09-25
I've had problems also, and 13.8 didn't help much, but it did make a difference. The AMD Catalyst 13.9 drivers seem to be the best thing so far, but ATI really sucks when it comes to Linux, I wish I had a Nvidia gpu imo.

Try this: 

1. Download the [AMD Catalyst 13.9 Drivers]("http://www2.ati.com/drivers/linux/amd-catalyst-13.9-linux-x86.x86_64.zip")
2. Go to your Downloads folder, uncompress the file[COLOR=#333333][FONT=Arial]
[/FONT][/COLOR]3. Right-click on the amd-catalyst-13.9-linux-x86.x86_64.run file 
4. Click on Properties at the bottom of the menu
5. Click on the Permissions tab and check "Allow executing file as program" at the bottom
6. Open terminal by pressing Ctrl+Alt+T key combination
7. Finally run ./amd-catalyst-13.9-linux-x86.x86_64.run

If you have already installed 13.8, you may have to uninstall it before you can install 13.9 but not sure. 

One last thing, once you have 13.9 installed you might want to go to AMD Catalyst Control Center, there you will see "Switchable Graphics" select that and choose "Power-Saving" restart your PC and it wont run as hot.

If you come across anything better please let us know.

---

### Post by Yellow Pasque on 2013-09-25
^No, DO NOT execute the .run file directly (or instruct people to do so) unless installing from packaging fails for some reason. Always build packages when possible to make removal easier, follow Debian file system guidelines, etc.
(Also, Cat 13.9 is an "accidental release" and is actually older than 13.8 Beta: [http://wiki.cchtml.com/index.php/Catalyst_13.9](http://wiki.cchtml.com/index.php/Catalyst_13.9) )

---

### Post by Ephryn_Thompson on 2013-09-25
Good catch Temüjin, I didn't know 13.9 was an accidental release. I did read it was based on 13.6 because of stability issues. For me it seems to work better on my HP Pavilion dv7, but honestly the damn thing runs hot no matter what... I wish I had an Nvidia gpu instead

---

