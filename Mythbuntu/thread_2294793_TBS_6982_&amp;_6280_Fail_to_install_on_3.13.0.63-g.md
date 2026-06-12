---
title: "TBS 6982 &amp; 6280 Fail to install on 3.13.0.63-generic"
date: 2015-09-13
forum: Mythbuntu
---

### Post by drifting on 2015-09-13
Anyone else have this problem?

Normal routine is to just :-

sudo rm -R /lib/modules/3.13.0-63-generic/kernel/drivers/media/
cd /TBS/linux-tbs-drivers/
make distclean
./v4l/tbs-x86_64.sh
make -j5
sudo make install

dmesg | grep frontend

Tried the latest driver from TBS 150728.

Have not investigated further as I am going to be away for a week, so simply rolled back the kernel to 62. 

Anyone any ideas?

Regards P

---

### Post by vidtek on 2015-09-30
Drifting-

I had this and realized I forgotten to copy the firmware to /lib/firmware

Tony

---

### Post by drifting on 2015-09-30
Oh? What did you copy where? Have no idea, up till now the steps above worked fine with every kernel change.

Can you tell me exactly what you did? Would like to get to the bottom of this.

Regards Paul.

---

### Post by vidtek on 2015-09-30
> **drifting said:**
> Oh? What did you copy where? Have no idea, up till now the steps above worked fine with every kernel change.

Can you tell me exactly what you did? Would like to get to the bottom of this.

Regards Paul.

Firmware included in the TBS driver download, specifically, ¨dvb-fe-cx24116.fw¨ and ¨v4l-cx23885-avcore-01.fw¨

just copy them over to the /lib/firmware directory.

That´s all I did and it worked.

My system: Mythbuntu 64-bit Kernel 3.19-0-28-generic Kubuntu 14.04
mythtv:
Installed: 2:0.27.5+fixes.20150921.fbd5ef3-0ubuntu0mythbuntu3
Candidate: 2:0.27.5+fixes.20150930.2ad3158-0ubuntu0mythbuntu3
Version table:
2:0.27.5+fixes.20150930.2ad3158-0ubuntu0mythbuntu3 0

This card works like a charm, TBS support is very good, if you are still in trouble, go to their support page and they respond quickly.
They actually updated the driver for me to this latest one as I had problems with this card and my Hauppauge working together, their old linux driver reverted the system to an earlier dvb linux tree which broke the Hauppauge 2210 driver, they patched their driver and posted it within a couple of days.

Hope you get it sorted, Tony.

---

### Post by drifting on 2015-10-06
Thank you so much for the reply. Just updated to yet another kernel, and lo and behold the normal procedure worked? without copying the firmware manually.

Regards Paul

---

