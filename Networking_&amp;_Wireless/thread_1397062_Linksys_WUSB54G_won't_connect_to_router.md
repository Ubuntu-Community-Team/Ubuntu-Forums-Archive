---
title: "Linksys WUSB54G won't connect to router"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by rajasika on 2010-02-02
Hi all,

Just finished installing 9.10 on an old machine.  It looks like my wireless adapter is being recognized just fine (linksys WUSB54G ver. 4), and my wireless router shows up on the list of wireless networks.  However, when I enter my password to connect (WPA), it tries for 20-30 seconds to connect, and then just gives up.  I have several other machines that connect successfully to this router, and I've connected before with this adapter in windows, so I know I should be able to connect. And yes, I've triple and quadruple checked that I was using the correct password ;)

Any ideas?  I've skimmed through several other threads about trouble with wireless adapters, but I'm not sure any of that is applicable to me since the adapter is detected and displays my local network.  I just can't get the darn thing to connect.

---

### Post by parmruss on 2010-03-25
I'm using the same model and have had exactly the same symptoms. Works fine in Jaunty and kernels in the 6.28 series. Don't have the links but believe I've read that the new 6.30+ series of kernels have a problem with the encrypted authentication. I have yet to find ANY distro running the newer kernels that will work with this card.

You can downgrade your kernel, but this may lead to problems. Best just downgrade to Jaunty and hope Lucid will be better.

---

### Post by xem1x on 2010-05-13
I am also experiencing the same issue within Lucid. It was previously working in the Alpha release.

Any ideas?

---

### Post by tripower on 2010-06-22
I am having the same issues has anyone found a solution?

---

### Post by pyrokamileon on 2010-08-03
I have had this same problem for some time now, my solution was to use Debian Lenny because, as already stated above, it uses older packages and an older kernel however I am missing Ubuntu or at least the option to use a newer Debian (testing, unstable) :-( I am adding my name to this pile in hopes that we can get something moving...  how would we get this added in as a bug or how can we check to see if it's already a known bug?

---

### Post by Lost_in_Lynx on 2010-09-03
I have the same problem, using Lucid Lynx. The Linksys WUSB54G ver. 4 sees and connects to open access points, but will not associate with the WPA encrypted access point. 
 
dmesg's last entries are these:
 
.... wlan0: direct probe to AP [AP's mac address] (try 2)
.... wlan0: direct probe responded
.... wlan0: authenticate with AP [AP's mac address] (try 1)
.... wlan0: authenticated
.... wlan0: associate with AP [AP's mac address] (try 1)
.... wlan0: RX AssocResp from [AP's mac address] (capa=0x411 status=0 aid=3)
.... wlan0: associated
.... wlan0: deauthenticating from [AP's mac address] by local choice (reason=3)
 
Can someone point me towards a guide which shows me how to:
- find out what specific module is being loaded by the WUSB54G adapter
- find a working module
- and to help me configure it
 
(as a side note, the network-manager wireless icon on the top panel glows green for a while, and with my other wireless adapters, then glows blue for the Linksys. Can anyone point me to where this behavior is explained?)
 
Thank you VERY much!

---

### Post by parmruss on 2010-10-14
Update:
Re the WUSB54g problem in newer kernels; I've been successful with some distros using the rt2500usb.inf driver v4 under ndiswrapper; pclinux OS 2010.07 and Linux Mint 9 were successful most of the time.

---

### Post by SeijiSensei on 2010-10-15
I've had various problems with this device which I've resolved by upgrading to 10.10.  The driver for this device has been rather unstable in recent kernel releases, but 2.6.35-22, the current Maverick kernel, generally provides a solid connection.

---

### Post by pyrokamileon on 2010-10-17
I just tried 10.10 based on SeijiSensei's recommendation but it didn't work for me...

---

