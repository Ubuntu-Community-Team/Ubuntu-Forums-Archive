---
title: "VMWare with kernel 2.6.12-10-686 on wireless network"
date: 2006-02-12
forum: Networking &amp; Wireless
---

### Post by rjpa on 2006-02-12
Hi,

Does anyone have a workaround the "random lockup" thing that happens if you install VMWare Workstation 5.5 on Ubuntu kernel 2.6.12-10-686 when the laptop is running on wireless connections (ipw2100)??

- rjpa

---

### Post by souki on 2006-02-13
got this working today, I didin't test enough but ran several sessions with no problem.
here are my specs and quick steps:

breezy kernel 2.6.12-10-686
wireless card: ipw2200
VMware-workstation-5.5.1-19175 with nat configuration

get this fix :
[http://platan.vc.cvut.cz/ftp/pub/vmware/vmnet-wireless-fix-for-ws55.tar.gz](http://platan.vc.cvut.cz/ftp/pub/vmware/vmnet-wireless-fix-for-ws55.tar.gz)

now, you have to generate a new vmnet.tar archive with files from /usr/lib/vmware/modules/source/vmnet.tar and vmnet-wireless-fix-for-ws55.tar.gz

backup /usr/lib/vmware/modules/source/vmnet.tar and replace it with the new archive

run vmware-config.pl

---

### Post by rjpa on 2006-02-13
Great, thanks Souki! \\:D/ \\:D/ \\:D/

---

