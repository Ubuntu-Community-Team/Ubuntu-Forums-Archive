---
title: "what is the best usb high speed wireless adapter  to work with ubuntu 11.10"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by SummerT on 2012-10-17
I have a crappy computer - low RAM (only 490mb RAM at the moment) - I can't get wired internet connection to work on it so I bought a belkin 150 usb wireless adapter which worked (sort of) with ubuntu but so slow I bought the better model Belkin N750db/n900db to see if that would work.  However, it did not work with Ubuntu, only came on in Windows.  But still incredibly too slow for me to download anything at all.  I then tried to load windows along side ubuntu to see if that would work.  It did not even show up in ubuntu.
 
We don't want to use Windows at all.   So do you know any USB wireless adapters that would work out of the box well with unbuntu 11.10?
 
Also, any suggestions on purchasing more RAM and/or new PCI card if I need to (I have a dell optiflex - older model that is a tower)
 
Thank you

---

### Post by kurt18947 on 2012-10-18
I've had pretty good luck with RealTek 8192SU USB adapters, they're plug 'n' play.  

Like this:  [http://www.amazon.com/gp/product/B002PHV6TK/ref=pd_lpo_k2_dp_sr_1/182-4365618-1829318?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=lpo-top-stripe-1&pf_rd_r=1VBGVDH733Z4RNGMBC2D&pf_rd_t=201&pf_rd_p=486539851&pf_rd_i=B007W7SCXG](http://www.amazon.com/gp/product/B002PHV6TK/ref=pd_lpo_k2_dp_sr_1/182-4365618-1829318?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=lpo-top-stripe-1&pf_rd_r=1VBGVDH733Z4RNGMBC2D&pf_rd_t=201&pf_rd_p=486539851&pf_rd_i=B007W7SCXG)

---

### Post by SummerT on 2012-10-20
does it work with linux out of the box? and would I have to download any drivers?

---

### Post by carl4926 on 2012-10-20
tenda-wireless-n150-usb-adapter-w311u

works out of the box

if you can't find it in stores, try ebay

---

### Post by kurt18947 on 2012-10-20
> **SummerT said:**
> does it work with linux out of the box? and would I have to download any drivers?

Mine has worked OOB since 11.04.  Prior to 11.04 I needed a pretty simple firmware installation.  I did run into one old issue with 12.10 but the fix is pretty simple.  I'd be using the RealTek 8192SU adapter, everything's peachy.  I suspend then later resume.  No wifi adapter found.  Huh?  The problem is that the network should be disconnected before the machine suspends.  It doesn't for whatever reason.  The fix is pretty simple.


[LIST=1]
[*]Log on as a SUDO user, you're editing a system file.
[*]Open a terminal or navigate via the GUI.  In terminal enter "sudo gedit /etc/pm/config.d/config.  A new blank text editor page will open.
[*]Enter this one line including caps, underscore  and quotes. :  SUSPEND_MODULES="r8712u".
[*]Save and exit.
[/LIST]
That's it. Now the wifi will resume properly after suspending.

---

