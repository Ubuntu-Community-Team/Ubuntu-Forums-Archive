---
title: "No wireless on new Toshiba Satellite L75"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by atomicspin on 2013-08-25
Did a new install of 13.04 and wireless isn't working.  

My output of lspci -nn | grep -i net

[INDENT]02:00.0 Network Controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)[/INDENT]

Anyone have any idea how to get this baby moving?

---

### Post by carl4926 on 2013-08-25
If you google on: [COLOR=#000000]Realtek Semiconductor Co., Ltd. Device [10ec:8179]
It looks not so good[/COLOR]

---

### Post by varunendra on 2013-08-25
It seems the proprietary rtl8188ee driver works for this device : [http://ubuntuforums.org/showthread.php?t=2162026](http://ubuntuforums.org/showthread.php?t=2162026)

However, the same driver gives compilation errors on 13.04 (due to critical changes in the kernel). A tested workaround was suggested by forum member ***Comasci*** [here]("http://ubuntuforums.org/showthread.php?t=2146803&p=12662928#post12662928"), which makes compilation a success and, to me, looks safe. But I can't say confidently if it may have any side effects.

Accordingly, *atomicspin*, please try the following -

[INDENT]1) Download the proprietary driver (RTL8188CE) from : [http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722) and copy it to your desktop (it's about 12 MB download).

2) Right-click the downloaded file (linux_mac80211_0012.0207.2013.tar.bz2) > "Extract here". This will extract a folder named "rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_001 2.0207.2013" on your desktop.

3) Now open the "**pci.h**" file from the extracted directory above, and add following lines below the ***line #31*** (that says - *"#define __RTL_PCI_H__"*)-
```
#ifndef __devinit
#define __devinit
#define __devinitdata
#endif
```
Proofread, save and close the file.

4) Open a terminal (Ctrl+Alt+T) and run following commands :
```
cd ~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
make
sudo make install
```
5) Reboot or manually load the driver with -
```
sudo modprobe -v rtl8188ee
```
 [/INDENT]
Watch out for errors during the whole process, post back if there are any.

If everything goes fine, please let us know how well it performs. Thank you.

---

