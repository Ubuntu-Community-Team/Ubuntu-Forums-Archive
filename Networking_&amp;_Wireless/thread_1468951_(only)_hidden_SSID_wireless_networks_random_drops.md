---
title: "(only) hidden SSID wireless networks random drops"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by vrbik on 2010-05-01
I've installed Ubuntu 10 (LTS) onto my Thinkpad x100e.

I've followed these steps to enable my wireless networkings:

sudo apt-get install build-essential
wget [http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz](http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)
sudo tar -xvzf rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz
cd rtl8192se_linux_2.6.0010.1020.2009_64bit
sudo su
make
make install

It seems to be working but when I connect to networks with hidden SSID's (like my home network) --- the network disconnects periodically.

Any ideas?

+If you require things form me, like logs, kindly tell me how I can produce them for you!

Thank you

---

