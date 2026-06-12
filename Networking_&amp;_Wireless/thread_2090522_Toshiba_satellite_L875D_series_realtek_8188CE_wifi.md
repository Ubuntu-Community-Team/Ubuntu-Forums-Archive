---
title: "Toshiba satellite L875D series realtek 8188CE wifi issue"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by Baji P. on 2012-12-02
Toshiba satellite L875D series includes model numbers L875D-S7210, L875D-S7230, L875D-S7232, L875D-S7332, L875D-S7342 & L875D-S7343.
I own a L875D-S7232 ( quad core AMD A8-4500M ).

This applies to Realtek 8188CE (& I believe 8192CE) wireless adapter.

I installed Ubuntu 12.04.1 x64 on the S7232 to triple boot with Windows 7 & Windows 8. The install went fine, my laptop was connected by ethernet during the install. Upon first ubuntu bootup in unity 3D, I noticed that the expected wifi networks were visible (I did not however attempt to connect to a wifi network at this point).

Then the update manager identified 200 odd packages that needed updating. Upon running the updates all my wifi options in the network-manager applet disappeared. The wired connection was still working fine but no wifi choices were available.

Using a combination of this [[COLOR="RoyalBlue"]**UbuntuForums thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604101") & this [[COLOR="Blue"]**Realtek driver site**[/COLOR]]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE") I was able to restore the wifi features. Thank you [**chili555**]("http://ubuntuforums.org/member.php?u=35909") & [**Zippy777**]("http://ubuntuforums.org/member.php?u=1173090")

Download the compressed tarball from Realtek's site, then do below:
```
tar zxvf <name-of-downloaded-pkg>
cd <to-folder-created-by-opening-pkg>
sudo su
make
make install

```

Reboot, and you should have your wifi options back. The README file in the package also lists "make uninstall", this will uninstall the wifi options.

If you are wondering whether Toshiba offers any Linux drivers/support, [[COLOR="RoyalBlue"]**see the attached screen shot**[/COLOR]]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletinDetail.jsp?pf=true&soid=108360") :(

--

---

