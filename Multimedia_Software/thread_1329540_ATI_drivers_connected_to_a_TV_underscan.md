---
title: "ATI drivers connected to a TV underscan"
date: 2009-11-17
forum: Multimedia Software
---

### Post by Raimbow on 2009-11-17
[SIZE=2][FONT=&quot]Hello:[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]I am new to Linux. I am using a ATI Radeon R-4550 video card connected a LCD TV trough a HDMI cable.[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]I downloaded and installed the latest ATI drivers and Catalyst from here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.39&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.39&lang=English)[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]The video card underscan causes a black border around the desktop, no matter the resolution selected. The TV brand and resolution are correctly identified.[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]I have spent many hours searching in Internet. Many people are telling that with the latest ATI driver they have solved the underscan issues, but I have not being able to do it.[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]I have tried with no results the suggested command: [/FONT][/SIZE]
  [SIZE=2][FONT=&quot]-sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]Some people say that there is a slider bar in the ATI Catalyst Control center window. I just can’t find that bar.[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]It is really frustrating.[/FONT][/SIZE]
  [FONT=&quot][SIZE=2]Any help will be appreciated.[/SIZE][/FONT]

---

### Post by Raimbow on 2009-11-18
Hello:

Could any body give an idea?

---

### Post by leprotic on 2010-05-20
Hi. I had the same problem and yes,the slider bar in the ATI Catalyst Control center window seems to do the trick. Open the catalyst control center (System->Preferences->ATI Catalyst Control Center--Administrative--). Then choose "Digital Monitor" option from the menu on the left (just under display manager) and select "Adjustments" tab above. You will notice the "Scaling Options" bar. Bring it to 0% and that should do it.

---

