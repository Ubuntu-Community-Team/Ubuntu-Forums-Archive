---
title: "radeon x800 pro driver 9-3-x86 error installing"
date: 2012-05-06
forum: Multimedia Software
---

### Post by Odys1 on 2012-05-06
Hello everyone,
I've recently started using ubuntu 12.04 LTS 32bit on my computer, the graphics card of which is an old Ati Radeon x800 pro. I tried to install its video driver provided my amd which I downloaded from this link:                                                                       [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

That's exactly the error which appeared in console:
```
ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:3.2.0-24-generic-pae; make sure that the version is being
correctly set by --iscurrentdistro

```After googling the error I figured out that the version of ubuntu I have does not support this version of the driver, despite the fact that it is provided by AMD for linux x86! I am not sure about the above conclusion of mine, so I would like to hear your opinion before I go searching for open source drivers {If you have any suggestions please go on}.

In case you need to know the way I tried to install the driver using the .run file, I did the following:
1)Changed the file permissions to allow the file to be run as a program.
2)In console, while being in the directory where the file was {Downloads} I typed "sudo ./ati-driver-installer-9-3-x86.x86_64.run"

Ok, I hope I covered every question you could have. Its your turn now ;)

---

### Post by Odys1 on 2012-05-07
Well now, that's confusing. Wasn't the so called RadeonDriver one of the best open source drivers for 3D and 2D acceleration? According to this official documentation topic:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

for Natty 11.04 and the newer releases the default video driver is the RadeonDriver based on Gallium3D, which is supposed to offer a decent 3D and 2D acceleration. If that's true, then why can't I run 3D games, the sys requirements of which are well below my system's capabilities, without having around only 10 fps?

And how can ubuntu's default driver be the RadeonDriver by the time it only supports AMD graphics cards? I don't wanna go asking whether the appropriate driver is downloaded during ubuntu's setup cuz it's not what I should care about at the moment. And how could that KMS be relevant with my problem anyway? I would be grateful if anyone had some solution for me or would help me make things clear so I could find a solution myself.

---

### Post by pme 72 on 2012-05-10
Welcome Odys1,

Yes, your X800 Pro has been moved to the legacy software support structure by AMD. The good news is you should still experience the same good performance when using Windows.  

Did you see this disclaimer on that AMD page:

> AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

The important part for Ubuntu users is the part about Linux distributions. If I understand correctly, changes to the kernel adopted by Ubuntu that occurred around March of 2009 created a situation where the AMD provided Legacy Catalyst driver became incompatible as you found out when you attempted to install it in Ubuntu 12.04.  

Here is a link to the Ubuntu Precise Installation Guide which provides an overview of the available options for owners of AMD/ATI cards:

[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Take a look at the Radeon description:

> radeon - open source driver supporting all Radeon cards. This driver has excellent 2D acceleration and compatibility with the Linux graphics stack. 3D acceleration is sufficient for desktop effects and a nice set of native Linux games. Power management is now comparable to the Catalyst driver.

There are instructions for removing the incompatible AMD proprietary driver and reinstalling the default radeon driver further down the page should you need to do that. 

I have read that high performance cards take a big hit in performance with the radeon driver limiting the ability to play demanding Windows games in Linux which might explain your experience.

---

