---
title: "Asus N13 not connecting after installing 13.04"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by speedingvenuz on 2013-04-25
Hi

I used to use PeppermintOS 3, and the N13 was able to connect to my internet.  After upgrading to Raring, my computer can't connect to my router anymore.  But the weird thing is that it could connect to my Android hotspot.

My router is a Linksys E3200.  Please help me out.

Thank you very much

---

### Post by wildmanne39 on 2013-04-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by speedingvenuz on 2013-04-25
[T]("http://pastebin.ubuntu.com/5603257/")his is what I got

[http://pastebin.ubuntu.com/5603257/](http://pastebin.ubuntu.com/5603257/)

I am trying to connect to the network Quoc Giang.

Thank you so much for your quick response

---

### Post by wildmanne39 on 2013-04-26
Please post the output of:
```
modinfo rt2800usb
```
Thanks

---

### Post by speedingvenuz on 2013-04-26
```
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     E11543F7E315F8F145D43CA
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0323d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*in*
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.8.0-19-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)

```

---

### Post by wildmanne39 on 2013-04-26
The reason I am asking for the extra information is that 13.04 is new so I am having to look under the hood more.

Please post the output of:
```
grep -R [0-9a-zA-Z] /sys/module/rt2800usb/parameters/
```
Thanks

---

### Post by speedingvenuz on 2013-04-26
/sys/module/rt2800usb/parameters/nohwcrypt:N

---

### Post by wildmanne39 on 2013-04-26
Please do:
```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb 

```
if it does not connect change the channel to one in your router and the encryption to just wpa2 if you have that option and see if that helps.
Thanks

---

### Post by speedingvenuz on 2013-04-26
what channel do I put it into?

---

### Post by wildmanne39 on 2013-04-26
Channel 1

Also looks like you have another device connected to the net if so you have to turn it off for the wireless to work.
Thanks

---

### Post by speedingvenuz on 2013-04-26
I changed it into channel 1 and it still doesn't work, I was tethering from my phone, I turned that off too, and it still didn't work

---

### Post by speedingvenuz on 2013-04-26
thank you so much for being patience with me

---

### Post by Expe on 2013-04-26
Hi, I also have the same problem with the Asus N13 after upgrading to 13.04. Netinfo attached.

Thanks.

---

### Post by meldroc on 2013-04-26
I too am having problems. It sounds like my wi-fi USB device is the same as the OP's. And, of course, my desktop machine is on the opposite side of the house from my router, so my main desktop has no functional internet...

Please help!

Oh - I ran the network diag shell script on my machine - looks like my problems are definitely similar to the original poster's.

```

*************** info trace ****************



**** uname -a ****


Linux Sarah-Jane 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"


**** lspci ****


00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: ASUSTeK Computer Inc. M4N68T series motherboard [1043:83a4]
	Kernel driver in use: forcedeth


**** lsusb ****


Bus 001 Device 004: ID 03f0:8e07 Hewlett-Packard 
Bus 001 Device 005: ID 03f0:7711 Hewlett-Packard 
Bus 001 Device 007: ID 0951:1607 Kingston Technology DataTraveler 100
Bus 001 Device 006: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. A1) [Ralink RT3072]
Bus 002 Device 002: ID 0a34:0110 TG3 Electronics, Inc. Deck 82-key backlit keyboard
Bus 002 Device 003: ID 1532:0002 Razer USA, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
nls_iso8859_1          12713  1 
usb_storage            57204  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
dm_crypt               22820  1 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
binfmt_misc            17500  1 
snd_hda_codec_hdmi     36913  4 
snd_hda_codec_via      51018  1 
arc4                   12615  2 
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
ip6t_REJECT            12545  1 
xt_hl                  12521  6 
ip6t_rt                12529  3 
nf_conntrack_ipv6      18335  7 
nf_defrag_ipv6         13201  1 nf_conntrack_ipv6
snd_usb_audio         140685  1 
snd_usbmidi_lib        24938  1 snd_usb_audio
ipt_REJECT             12541  1 
xt_LOG                 17400  10 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_seq_midi           13324  0 
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
xt_limit               12711  13 
snd_seq_midi_event     14899  1 snd_seq_midi
rt2800usb              26854  0 
xt_tcpudp              12603  22 
rt2x00usb              20635  1 rt2800usb
rt2800lib              66507  1 rt2800usb
xt_addrtype            12635  4 
ppdev                  17073  0 
rt2x00lib              54869  3 rt2x00usb,rt2800lib,rt2800usb
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
mac80211              606457  3 rt2x00lib,rt2x00usb,rt2800lib
nf_conntrack_ipv4      14487  7 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_state               12578  14 
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
asus_atk0110           17646  0 
ip6table_filter        12815  1 
uvcvideo               80847  0 
parport_pc             28152  1 
ip6_tables             27025  1 ip6table_filter
videobuf2_vmalloc      13056  1 uvcvideo
cfg80211              510937  2 mac80211,rt2x00lib
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
nf_nat_ftp             12620  0 
nf_nat                 25866  1 nf_nat_ftp
nf_conntrack_ftp       13342  1 nf_nat_ftp
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
nf_conntrack           83275  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_state,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
edac_core              62003  0 
nvidia               9410995  38 
usblp                  18111  0 
mac_hid                13205  0 
videodev              129260  2 uvcvideo,videobuf2_core
psmouse                95870  0 
iptable_filter         12810  1 
edac_mce_amd           23114  0 
crc_ccitt              12707  1 rt2800lib
k10temp                13126  0 
snd_timer              29425  2 snd_pcm,snd_seq
i2c_nforce2            13020  0 
ip_tables              26995  1 iptable_filter
x_tables               29803  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_state,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
serio_raw              13215  0 
snd                    68876  20 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
soundcore              12680  1 snd
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
vesafb                 13828  1 
pata_acpi              13038  0 
pata_amd               14129  0 
forcedeth              66977  0 
sata_nv                31812  3 


**** nm-tool ****



NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    billdecker9:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    KATIE:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    CenturyLink7440: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    LUCKY:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA
    HOME-AE08:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    belkin.8d6:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    CenturyLink5216: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    HP-Print-A0-Officejet Pro 8600: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    ajpahls:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    CenturyLink7116: Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    ICE Task Force:  Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 29 WPA2
    maxx0110:        Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    HOME-8A68:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    roach4201986:    Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    PurplePine:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Ebenal:          Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 55 WEP
    HOME-3F18:       Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    SWEETIE-PC_Network: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    SENA:            Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 22 WPA2
    FBISurvelenceVan13: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    meldroc1:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA2
    jonesingbeaches: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2




**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"meldroc1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c5fb9983
                    Extra: Last beacon: 1372ms ago
                    IE: Unknown: 00086D656C64726F6331
                    IE: Unknown: 010882848B96A4B0C8EC
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C9298E0
                    IE: Unknown: DD090010180204F4000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"belkin.8d6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b5ab13176
                    Extra: Last beacon: 1396ms ago
                    IE: Unknown: 000A62656C6B696E2E386436
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"SWEETIE-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003f3847190
                    Extra: Last beacon: 960ms ago
                    IE: Unknown: 0012535745455449452D50435F4E6574776F726B
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD270050F204104A000110104400010210470010A63298F5EF8760F288828D4F353610DF103C000103
                    IE: Unknown: DD090010180204F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A400004243BC0062326600
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001700000000000000000000000000000000000000
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005768726671
                    Extra: Last beacon: 536ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D160B070000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000031127A
                    IE: Unknown: DD07000C4300000000
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"billdecker9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000055c933ad169
                    Extra: Last beacon: 528ms ago
                    IE: Unknown: 000B62696C6C6465636B657239
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880001DD347A740103C000101
                    IE: Unknown: 05040001000E
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000046127A
                    IE: Unknown: DD07000C4307000000
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"KATIE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000028d4dc3a252
                    Extra: Last beacon: 524ms ago
                    IE: Unknown: 00054B41544945
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050C020300000000000000000000
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink7116"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010707e83176
                    Extra: Last beacon: 1312ms ago
                    IE: Unknown: 000F43656E747572794C696E6B37313136
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD310050F204104A000110104400010210470010BC329E001DD811B28601FEF52844159C103C0001011049000600372A000120
                    IE: Unknown: 050400010008
                    IE: Unknown: DD310050F204104A000110104400010210470010BC329E001DD811B28601FEF52844159C103C0001011049000600372A000120
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602050600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05020057127A
                    IE: Unknown: DD07000C4300000000
          Cell 08 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008c818fe41f
                    Extra: Last beacon: 1148ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1604050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000022127A
                    IE: Unknown: DD07000C4300000000
          Cell 09 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008c818fed21
                    Extra: Last beacon: 1144ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEE1117FFFFFF0001000000000000000000000000030000000000
                    IE: Unknown: 3D1604050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000022127A
                    IE: Unknown: DD07000C4300000000
          Cell 10 - Address: <MAC address removed>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"roach4201986"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006d4d27d80
                    Extra: Last beacon: 668ms ago
                    IE: Unknown: 000C726F61636834323031393836
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030109
                    IE: Unknown: 050401020040
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3409071B00000000000000000000000000000000000000
                    IE: Unknown: 3D1609071B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD270050F204104A000110104400010210470010000000000000100000000026F28DB11D103C000103



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

#MELDROC Blacklisting stock RA2800 series drivers in attempt to make ******
# wifi work.
#blacklist rt2800usb
#blacklist rt2800lib
#blacklist rt2x00usb
#blacklist rt2x00lib


**** dmesg ****


[    1.386992] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d490763cc418e29de79f40a5aa7d97747ec8882c'
[   25.973003] usbcore: registered new interface driver rt2800usb
[   29.264706] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.265107] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   85.195356] wlan0: authenticate with <MAC address removed>
[   85.224111] wlan0: send auth to <MAC address removed> (try 1/3)
[   85.425527] wlan0: send auth to <MAC address removed> (try 2/3)
[   85.629010] wlan0: send auth to <MAC address removed> (try 3/3)
[   85.832476] wlan0: authentication with <MAC address removed> timed out
[   93.796941] wlan0: authenticate with <MAC address removed>
[   93.825743] wlan0: direct probe to <MAC address removed> (try 1/3)
[   94.026994] wlan0: direct probe to <MAC address removed> (try 2/3)
[   94.230460] wlan0: direct probe to <MAC address removed> (try 3/3)
[   94.433930] wlan0: authentication with <MAC address removed> timed out
[   95.972232] wlan0: authenticate with <MAC address removed>
[   96.002752] wlan0: direct probe to <MAC address removed> (try 1/3)
[   96.205290] wlan0: direct probe to <MAC address removed> (try 2/3)
[   96.408751] wlan0: direct probe to <MAC address removed> (try 3/3)
[   96.612208] wlan0: authentication with <MAC address removed> timed out
[   98.149903] wlan0: authenticate with <MAC address removed>
[   98.178267] wlan0: direct probe to <MAC address removed> (try 1/3)
[   98.379552] wlan0: direct probe to <MAC address removed> (try 2/3)
[   98.583035] wlan0: send auth to <MAC address removed> (try 3/3)
[   98.584627] wlan0: authenticated
[   98.587070] wlan0: associate with <MAC address removed> (try 1/3)
[   98.592514] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[   98.599320] wlan0: associated
[   98.599371] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  143.929465] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  148.278771] wlan0: authenticate with <MAC address removed>
[  148.306803] wlan0: send auth to <MAC address removed> (try 1/3)
[  148.508088] wlan0: send auth to <MAC address removed> (try 2/3)
[  148.509737] wlan0: authenticated
[  148.512109] wlan0: associate with <MAC address removed> (try 1/3)
[  148.715475] wlan0: associate with <MAC address removed> (try 2/3)
[  148.919020] wlan0: associate with <MAC address removed> (try 3/3)
[  149.122425] wlan0: association with <MAC address removed> timed out
[  150.661191] wlan0: authenticate with <MAC address removed>
[  150.696500] wlan0: direct probe to <MAC address removed> (try 1/3)
[  150.897748] wlan0: direct probe to <MAC address removed> (try 2/3)
[  151.101213] wlan0: direct probe to <MAC address removed> (try 3/3)
[  151.304701] wlan0: authentication with <MAC address removed> timed out
[  152.842776] wlan0: authenticate with <MAC address removed>
[  152.870761] wlan0: direct probe to <MAC address removed> (try 1/3)
[  153.072126] wlan0: direct probe to <MAC address removed> (try 2/3)
[  153.275521] wlan0: direct probe to <MAC address removed> (try 3/3)
[  153.478986] wlan0: authentication with <MAC address removed> timed out
[  155.016967] wlan0: authenticate with <MAC address removed>
[  155.049263] wlan0: direct probe to <MAC address removed> (try 1/3)
[  155.250348] wlan0: direct probe to <MAC address removed> (try 2/3)
[  155.453815] wlan0: direct probe to <MAC address removed> (try 3/3)
[  155.657273] wlan0: authentication with <MAC address removed> timed out
[  157.199068] wlan0: authenticate with <MAC address removed>
[  157.227397] wlan0: direct probe to <MAC address removed> (try 1/3)
[  157.428636] wlan0: direct probe to <MAC address removed> (try 2/3)
[  157.632106] wlan0: direct probe to <MAC address removed> (try 3/3)
[  157.835538] wlan0: authentication with <MAC address removed> timed out
[  165.804036] wlan0: authenticate with <MAC address removed>
[  165.832831] wlan0: direct probe to <MAC address removed> (try 1/3)
[  166.034035] wlan0: direct probe to <MAC address removed> (try 2/3)
[  166.237526] wlan0: direct probe to <MAC address removed> (try 3/3)
[  166.440961] wlan0: authentication with <MAC address removed> timed out
[  167.978664] wlan0: authenticate with <MAC address removed>
[  168.007111] wlan0: direct probe to <MAC address removed> (try 1/3)
[  168.208356] wlan0: direct probe to <MAC address removed> (try 2/3)
[  168.411815] wlan0: direct probe to <MAC address removed> (try 3/3)
[  168.615285] wlan0: authentication with <MAC address removed> timed out
[  170.153114] wlan0: authenticate with <MAC address removed>
[  170.181359] wlan0: direct probe to <MAC address removed> (try 1/3)
[  170.382646] wlan0: direct probe to <MAC address removed> (try 2/3)
[  170.586124] wlan0: direct probe to <MAC address removed> (try 3/3)
[  170.789574] wlan0: authentication with <MAC address removed> timed out
[  172.322746] wlan0: authenticate with <MAC address removed>
[  172.355692] wlan0: direct probe to <MAC address removed> (try 1/3)
[  172.556937] wlan0: direct probe to <MAC address removed> (try 2/3)
[  172.760418] wlan0: direct probe to <MAC address removed> (try 3/3)
[  172.963856] wlan0: authentication with <MAC address removed> timed out
[  174.497427] wlan0: authenticate with <MAC address removed>
[  174.529899] wlan0: direct probe to <MAC address removed> (try 1/3)
[  176.171331] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  179.125285] wlan0: authenticate with <MAC address removed>
[  179.157822] wlan0: direct probe to <MAC address removed> (try 1/3)
[  179.359080] wlan0: direct probe to <MAC address removed> (try 2/3)
[  179.562565] wlan0: direct probe to <MAC address removed> (try 3/3)
[  179.766041] wlan0: authentication with <MAC address removed> timed out
[  181.304218] wlan0: authenticate with <MAC address removed>
[  181.340883] wlan0: direct probe to <MAC address removed> (try 1/3)
[  181.541367] wlan0: direct probe to <MAC address removed> (try 2/3)
[  181.744846] wlan0: direct probe to <MAC address removed> (try 3/3)
[  181.948280] wlan0: authentication with <MAC address removed> timed out
[  183.489737] wlan0: authenticate with <MAC address removed>
[  183.518152] wlan0: direct probe to <MAC address removed> (try 1/3)
[  183.719649] wlan0: direct probe to <MAC address removed> (try 2/3)
[  183.923105] wlan0: direct probe to <MAC address removed> (try 3/3)
[  184.126584] wlan0: authentication with <MAC address removed> timed out
[  185.664103] wlan0: authenticate with <MAC address removed>
[  185.692697] wlan0: direct probe to <MAC address removed> (try 1/3)
[  185.893957] wlan0: direct probe to <MAC address removed> (try 2/3)
[  186.097417] wlan0: direct probe to <MAC address removed> (try 3/3)
[  186.300855] wlan0: authentication with <MAC address removed> timed out
[  187.838574] wlan0: authenticate with <MAC address removed>
[  187.866968] wlan0: direct probe to <MAC address removed> (try 1/3)
[  188.068256] wlan0: direct probe to <MAC address removed> (try 2/3)
[  188.271726] wlan0: direct probe to <MAC address removed> (try 3/3)
[  188.475160] wlan0: authentication with <MAC address removed> timed out
[  190.013190] wlan0: authenticate with <MAC address removed>
[  190.041235] wlan0: direct probe to <MAC address removed> (try 1/3)
[  190.242536] wlan0: direct probe to <MAC address removed> (try 2/3)
[  190.446007] wlan0: direct probe to <MAC address removed> (try 3/3)
[  190.649483] wlan0: authentication with <MAC address removed> timed out
[  192.187214] wlan0: authenticate with <MAC address removed>
[  192.215622] wlan0: direct probe to <MAC address removed> (try 1/3)
[  192.416813] wlan0: direct probe to <MAC address removed> (try 2/3)
[  192.620291] wlan0: direct probe to <MAC address removed> (try 3/3)
[  192.823754] wlan0: authentication with <MAC address removed> timed out
[  194.361498] wlan0: authenticate with <MAC address removed>
[  194.389770] wlan0: direct probe to <MAC address removed> (try 1/3)
[  194.591129] wlan0: direct probe to <MAC address removed> (try 2/3)
[  194.794616] wlan0: direct probe to <MAC address removed> (try 3/3)
[  194.998057] wlan0: authentication with <MAC address removed> timed out
[  196.535603] wlan0: authenticate with <MAC address removed>
[  196.564028] wlan0: direct probe to <MAC address removed> (try 1/3)
[  196.765421] wlan0: direct probe to <MAC address removed> (try 2/3)
[  196.968887] wlan0: direct probe to <MAC address removed> (try 3/3)
[  197.172344] wlan0: authentication with <MAC address removed> timed out
[  198.714452] wlan0: authenticate with <MAC address removed>
[  198.744672] wlan0: direct probe to <MAC address removed> (try 1/3)
[  198.947691] wlan0: direct probe to <MAC address removed> (try 2/3)
[  199.151136] wlan0: direct probe to <MAC address removed> (try 3/3)
[  199.354636] wlan0: authentication with <MAC address removed> timed out
[  200.896516] wlan0: authenticate with <MAC address removed>
[  200.925542] wlan0: direct probe to <MAC address removed> (try 1/3)
[  201.125957] wlan0: direct probe to <MAC address removed> (try 2/3)
[  201.329421] wlan0: direct probe to <MAC address removed> (try 3/3)
[  201.532906] wlan0: authentication with <MAC address removed> timed out
[  207.120683] wlan0: authenticate with <MAC address removed>
[  207.148366] wlan0: direct probe to <MAC address removed> (try 1/3)
[  207.349633] wlan0: direct probe to <MAC address removed> (try 2/3)
[  207.553116] wlan0: direct probe to <MAC address removed> (try 3/3)
[  207.756604] wlan0: authentication with <MAC address removed> timed out
[  209.294287] wlan0: authenticate with <MAC address removed>
[  209.322634] wlan0: direct probe to <MAC address removed> (try 1/3)
[  209.523928] wlan0: direct probe to <MAC address removed> (try 2/3)
[  209.727395] wlan0: direct probe to <MAC address removed> (try 3/3)
[  209.930852] wlan0: authentication with <MAC address removed> timed out
[  211.468721] wlan0: authenticate with <MAC address removed>
[  211.501014] wlan0: direct probe to <MAC address removed> (try 1/3)
[  211.702228] wlan0: direct probe to <MAC address removed> (try 2/3)
[  211.905694] wlan0: direct probe to <MAC address removed> (try 3/3)
[  212.109159] wlan0: authentication with <MAC address removed> timed out
[  213.646929] wlan0: authenticate with <MAC address removed>
[  213.675271] wlan0: direct probe to <MAC address removed> (try 1/3)
[  213.876491] wlan0: direct probe to <MAC address removed> (try 2/3)
[  214.079980] wlan0: direct probe to <MAC address removed> (try 3/3)
[  214.283434] wlan0: authentication with <MAC address removed> timed out
[  215.821283] wlan0: authenticate with <MAC address removed>
[  215.849542] wlan0: direct probe to <MAC address removed> (try 1/3)
[  216.050798] wlan0: direct probe to <MAC address removed> (try 2/3)
[  216.254281] wlan0: direct probe to <MAC address removed> (try 3/3)
[  216.457733] wlan0: authentication with <MAC address removed> timed out
[  217.995387] wlan0: authenticate with <MAC address removed>
[  218.023693] wlan0: direct probe to <MAC address removed> (try 1/3)
[  218.225119] wlan0: direct probe to <MAC address removed> (try 2/3)
[  218.428575] wlan0: direct probe to <MAC address removed> (try 3/3)
[  218.632052] wlan0: authentication with <MAC address removed> timed out
[  220.169720] wlan0: authenticate with <MAC address removed>
[  220.198079] wlan0: direct probe to <MAC address removed> (try 1/3)
[  220.399400] wlan0: direct probe to <MAC address removed> (try 2/3)
[  220.602861] wlan0: direct probe to <MAC address removed> (try 3/3)
[  220.806341] wlan0: authentication with <MAC address removed> timed out
[  222.343477] wlan0: authenticate with <MAC address removed>
[  222.372347] wlan0: direct probe to <MAC address removed> (try 1/3)
[  222.573711] wlan0: direct probe to <MAC address removed> (try 2/3)
[  222.777143] wlan0: direct probe to <MAC address removed> (try 3/3)
[  222.980613] wlan0: authentication with <MAC address removed> timed out
[  224.518195] wlan0: authenticate with <MAC address removed>
[  224.546726] wlan0: direct probe to <MAC address removed> (try 1/3)
[  224.747999] wlan0: direct probe to <MAC address removed> (try 2/3)
[  224.951447] wlan0: direct probe to <MAC address removed> (try 3/3)
[  225.154928] wlan0: authentication with <MAC address removed> timed out
[  226.692594] wlan0: authenticate with <MAC address removed>
[  226.720997] wlan0: direct probe to <MAC address removed> (try 1/3)
[  226.922260] wlan0: direct probe to <MAC address removed> (try 2/3)
[  227.125749] wlan0: direct probe to <MAC address removed> (try 3/3)
[  227.329202] wlan0: authentication with <MAC address removed> timed out
[  228.871023] wlan0: authenticate with <MAC address removed>
[  228.899371] wlan0: direct probe to <MAC address removed> (try 1/3)
[  229.100560] wlan0: direct probe to <MAC address removed> (try 2/3)
[  229.304345] wlan0: direct probe to <MAC address removed> (try 3/3)
[  229.507521] wlan0: authentication with <MAC address removed> timed out
[  235.034610] wlan0: authenticate with <MAC address removed>
[  235.063116] wlan0: direct probe to <MAC address removed> (try 1/3)
[  235.264384] wlan0: direct probe to <MAC address removed> (try 2/3)
[  235.467873] wlan0: direct probe to <MAC address removed> (try 3/3)
[  235.671328] wlan0: authentication with <MAC address removed> timed out
[  237.204989] wlan0: authenticate with <MAC address removed>
[  237.237505] wlan0: direct probe to <MAC address removed> (try 1/3)
[  237.438694] wlan0: direct probe to <MAC address removed> (try 2/3)
[  237.642141] wlan0: direct probe to <MAC address removed> (try 3/3)
[  237.845626] wlan0: authentication with <MAC address removed> timed out
[  239.383605] wlan0: authenticate with <MAC address removed>
[  239.411773] wlan0: direct probe to <MAC address removed> (try 1/3)
[  239.612996] wlan0: direct probe to <MAC address removed> (try 2/3)
[  239.816486] wlan0: direct probe to <MAC address removed> (try 3/3)
[  240.019926] wlan0: authentication with <MAC address removed> timed out
[  241.557691] wlan0: authenticate with <MAC address removed>
[  241.586050] wlan0: direct probe to <MAC address removed> (try 1/3)
[  241.787297] wlan0: direct probe to <MAC address removed> (try 2/3)
[  241.990754] wlan0: direct probe to <MAC address removed> (try 3/3)
[  242.194226] wlan0: authentication with <MAC address removed> timed out
[  243.739649] wlan0: authenticate with <MAC address removed>
[  243.768282] wlan0: direct probe to <MAC address removed> (try 1/3)
[  243.969562] wlan0: direct probe to <MAC address removed> (try 2/3)
[  244.173033] wlan0: direct probe to <MAC address removed> (try 3/3)
[  244.376502] wlan0: authentication with <MAC address removed> timed out
[  245.918136] wlan0: authenticate with <MAC address removed>
[  245.946546] wlan0: direct probe to <MAC address removed> (try 1/3)
[  246.147840] wlan0: direct probe to <MAC address removed> (try 2/3)
[  246.351301] wlan0: direct probe to <MAC address removed> (try 3/3)
[  246.554775] wlan0: authentication with <MAC address removed> timed out
[  248.092906] wlan0: authenticate with <MAC address removed>
[  248.120934] wlan0: direct probe to <MAC address removed> (try 1/3)
[  248.322166] wlan0: direct probe to <MAC address removed> (try 2/3)
[  248.525597] wlan0: direct probe to <MAC address removed> (try 3/3)
[  248.729075] wlan0: authentication with <MAC address removed> timed out
[  250.266147] wlan0: authenticate with <MAC address removed>
[  250.295202] wlan0: direct probe to <MAC address removed> (try 1/3)
[  250.496454] wlan0: direct probe to <MAC address removed> (try 2/3)
[  250.699903] wlan0: direct probe to <MAC address removed> (try 3/3)
[  250.903362] wlan0: authentication with <MAC address removed> timed out
[  252.441034] wlan0: authenticate with <MAC address removed>
[  252.469472] wlan0: direct probe to <MAC address removed> (try 1/3)
[  252.670738] wlan0: direct probe to <MAC address removed> (try 2/3)
[  252.874199] wlan0: direct probe to <MAC address removed> (try 3/3)
[  253.077657] wlan0: authentication with <MAC address removed> timed out
[  254.615474] wlan0: authenticate with <MAC address removed>
[  254.651598] wlan0: direct probe to <MAC address removed> (try 1/3)
[  254.852973] wlan0: direct probe to <MAC address removed> (try 2/3)
[  255.056465] wlan0: direct probe to <MAC address removed> (try 3/3)
[  255.259910] wlan0: authentication with <MAC address removed> timed out
[  256.801690] wlan0: authenticate with <MAC address removed>
[  256.830092] wlan0: direct probe to <MAC address removed> (try 1/3)
[  257.031273] wlan0: direct probe to <MAC address removed> (try 2/3)
[  257.234740] wlan0: direct probe to <MAC address removed> (try 3/3)
[  257.438199] wlan0: authentication with <MAC address removed> timed out


**************** done ********************



```

---

### Post by meldroc on 2013-04-27
Update: I'm able to work around the problem for now by booting with my previous 3.5 kernel rather than the 3.8 that comes with 13.04. I hope this bug gets fixed in a hurry!

---

### Post by speedingvenuz on 2013-04-27
Can you detail the steps to install the old kernel?

 Thank you

---

### Post by meldroc on 2013-04-27
> **speedingvenuz said:**
> Can you detail the steps to install the old kernel?

 Thank you

I didn't have to do anything, because I upgraded from 12.10 - the upgrader was kind enough to keep my old kernel as a backup. So I rebooted, then at the GRUB menu, I chose "Ubuntu advanced options", which presented me with the option to boot with the old kernel.

If you don't have that on your system, see if you can get on a wired connection, and try installing the packages "linux-image-3.5.0-27-generic" and "linux-image-extra-3.5.0-27-generic", and see if that gets you going.

---

### Post by meldroc on 2013-04-27
If you can't get some sort of Internet connectivity, then I'd have to research how to dig up the appropriate debs from the Ubuntu archives. Then the procedure would be to download them, transfer them to your machine via sneakernet, then install them with "dpkg -i". If it complains about dependencies, then you'll need to download the appropriate dependencies from the Ubuntu archives and install them too.

---

### Post by speedingvenuz on 2013-04-27
I do have internet access by tethering.  So I tried to use apt-get to to install the linux image you said, but it can't find it

---

### Post by meldroc on 2013-04-27
Hmmm. You might have to rig apt or whatever package manager you're using to grab this kernel from the Precise 12.10 repos. I'm trying to research how to do this cleanly.

---

### Post by meldroc on 2013-04-28
Have you been able to fetch the older kernel from the Precise repos?

---

### Post by speedingvenuz on 2013-04-28
I was able to get the the kernel from upubuntu, and I used the 3.5 like you said

---

### Post by Expe on 2013-04-29
Found this thread on the Arch forums, so it does seem to be something related in a newer kernel:
[https://bbs.archlinux.org/viewtopic.php?pid=1263941](https://bbs.archlinux.org/viewtopic.php?pid=1263941)

There is also a bug report on launchpad, but not sure if it is the same issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1154640](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1154640)

---

### Post by speedingvenuz on 2013-04-29
So the latest kernel that I was able to use is the 3.7.9

---

### Post by meldroc on 2013-05-01
Good. At least we have a workaround for the time-being.

---

### Post by meldroc on 2013-05-02
Any new news on this bug?

---

