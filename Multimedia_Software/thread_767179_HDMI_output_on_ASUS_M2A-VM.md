---
title: "HDMI output on ASUS M2A-VM"
date: 2008-04-25
forum: Multimedia Software
---

### Post by aznel on 2008-04-25
I have been pulling my hair out trying to get HDMI output working with a ASUS M2A-VM HDMI using the ATI drivers.  HDMI works while linux is booting until the X login screen appears.  After that I cannot even get HDMI output on a text console. ](*,)

Running "aticonfig --query-monitor" shows that tmds2 is connected, but after I run "aticonfig --enable-monitor tmds2" I get nothing on the HDMI output.  Everything works perfectly when I use the VGA or DVI outputs.  I can't use DVI because I need audio over HDMI.  I am using latest ASUS BIOS (1705), and the latest proprietary ATI drivers (8.4).

Strangely, if I boot into Ubuntu using the install CD I get output on the HDMI port.  Is it just that the ATI drivers suck, or am I doing something wrong?  Please show me your working configuration!

---

### Post by GSMD on 2008-07-12
Any news on this?
I'm facing the same kind of issue, gonna spend the evening trying to fix it. I'll report here in case I could make the thing work.

---

### Post by wfeltmate on 2008-07-13
If it isn't too much of a chore to do so, I would probably suggest a fresh install of Ubuntu. I have never had any issues with HDMI video with any of the fglrx drivers I have tried, so maybe something went wrong during the initial install.

Presently, I am having an issue with the audio over HDMI. Ubuntu sees that the ability to send the sound is there, but in the volume control panel, there is no slider to set the volume. This only happened when I did my last fresh install and was working prior to it, so I think the continuing problem for me is just because I have been too lazy to do a fresh install.

But, have you tried uninstalling the fglrx drivers per ati's method and reinstalling?

---

### Post by GSMD on 2008-07-14
Well, I've performed a fresh install twice, no luck. Neither with the fglrx that comes with Hardy, nor 8.6. Are you on 8.04? I get video over hdmi with the default vesa drivers though. As for the sound, have you tried [this]("http://ubuntuforums.org/showpost.php?p=4855353&postcount=28")?

---

### Post by B-money on 2008-11-17
I am also having the same issue, HDMI port works fine until Unbuntu loads, in which then it goes completely black.  Have talked to ASUS technical support about issues and believe it to be an issue with Ubuntu.  Has any one came up with a fix for this issue.

---

