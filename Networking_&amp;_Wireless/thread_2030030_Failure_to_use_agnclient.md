---
title: "Failure to use agnclient"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by susja on 2012-07-20
Hello,
I successfully used AT & T client on my Ubuntu 10.x but now I upgraded to 12.04 and reinstalled agnclient but have an issue to use it. Maybe someone could help me to understand what's going going wrong?
Here are my steps:
1. I used instructions from here -> [http://www.attnetclient.com/forum/viewtopic.php?t=715](http://www.attnetclient.com/forum/viewtopic.php?t=715)
2. I downloaded agnclient  [agnclient_1_0_2_0_1_3002_1_1_i386.zip]("http://www.attnetclient.com/forum/download/file.php?id=457")
3. I installed it like this: 
sudo dpkg -i agnclient_1.0~2.0.1.3002-1.1_i386.deb
# install all dependencies
sudo apt-get -f install
4. I am able to bring agnclient GUI, provide my credentials and login but then my client just hangs on 'Connecting ...'   ( see attachment )
5. When I look in detailed messages I see this:
07/20 11:12:46.121 [0E81] CSC fsmAction: connect
07/20 11:12:46.121 [0E63] GUI AGNC ACTIONREQUESTED: '100'
07/20 11:12:46.122 [0E63] GUI in action_requested_callback, parameter = 100
07/20 11:12:46.122 [0E81] CSC Adapter 'lo' has fam=17 addr=1.0.0.0.
07/20 11:12:46.122 [0E81] CSC Adapter 'eth0' has fam=17 addr=2.0.0.0.
07/20 11:12:46.122 [0E81] CSC Adapter 'wlan0' has fam=17 addr=3.0.0.0.
07/20 11:12:46.122 [0E81] CSC Adapter 'lo' has fam=2 addr=127.0.0.1.
07/20 11:12:46.122 [0E81] CSC IP adapter 'eth0' has address 192.168.1.7.
07/20 11:12:46.122 [0E81] CSC Adapter 'lo' has fam=10 addr=0.0.0.0.
07/20 11:12:46.123 [0E81] CSC Adapter 'eth0' has fam=10 addr=0.0.0.0.
07/20 11:12:46.123 [0E81] CSC starting auth command: /opt/agns/bin/smx_auth 204.146.172.230   
07/20 11:12:46.123 [0E5F] GUI AGNC ACTIONREQUESTED: '100'
07/20 11:12:46.124 [0E5F] GUI in action_requested_callback, parameter = 100
07/20 11:12:46.124 [0E81] CSC authProcessingThread() started.
07/20 11:12:46.185 [0E81] CSC FSM: VPN connection requested.
07/20 11:12:46.186 [0E5F] GUI agnState changed from 10 to 100.
07/20 11:12:46.186 [0E63] GUI agnState changed from 10 to 100.
07/20 11:12:46.187 [0E81] CSC STATE received.
07/20 11:12:46.187 [0E81] CSC STATE received.
07/20 11:12:46.187 [0E81] CSC FSM: agnclientd version is 2.0.1.3002.
07/20 11:12:46.188 [0E81] CSC SLR1000 - SLRStartNewVPNConnection() was called.
07/20 11:12:46.189 [0E5F] GUI agnState changed from 100 to 200.
07/20 11:12:46.189 [0E63] GUI agnState changed from 100 to 200.
07/20 11:12:46.212 [0E81] CSC CONNECTATTEMPTINFO received.
07/20 11:12:46.213 [0E81] CSC STATE received.
07/20 11:12:46.239 [0E63] GUI Window state changed to 'Not connected.'.
07/20 11:12:46.258 [0E5F] GUI Window state changed to 'Connecting...'.
07/20 11:12:46.260 [0E81] CSC STATE received.
07/20 11:12:46.288 [0E63] GUI Window state changed to 'Connecting...'.
07/20 11:12:46.652 [0E81] CSC authentication completed, auth_rc = 0
07/20 11:12:46.652 [0E81] CSC authProcessingThread() ended.
07/20 11:12:46.653 [0E81] CSC FSM: Authentication response received (SMX 0x00 - 00000000).
07/20 11:12:46.653 [0E81] CSC FSM: Authentication succeeded. (first VPN server 204.146.24.55)
07/20 11:12:46.653 [0E81] CSC starting vpn command: /opt/agns/bin/NetVPN   
07/20 11:12:46.654 [0E81] CSC vpnProcessingThread() started.
  
Any idea what/how could I fix it?
Thanks in advance

---

### Post by xinerd on 2013-01-07
I encountered the exactly same problem as yours, did you fix it ? I suspected that the root cause of this problem is because we want to install 32 bit at&t client on 64 bit linux, although I installed ia32-libs.


anybody solve this problem, please send me a message. thanks

---

### Post by susja on 2013-01-07
Hi,
I wasn't able to fix it.
not sure what you mean by 32/64 compatibility but my PC is 32 bit and I'm not aware about bits of at&t client
Regards

---

### Post by aschmeer on 2014-01-04
The solution for this issue can be found at [http://www.tummy.com/blogs/2012/04/17/att-global-network-client-under-ubuntu-1204-64-bit/](http://www.tummy.com/blogs/2012/04/17/att-global-network-client-under-ubuntu-1204-64-bit/)
I had the exact same problem and solved it by applying the steps documented there.

Basically, the issue is that the agnclientd cannot find the libraries for libssl.so.4 and libcrypto.so.4 
So you need to create symbolic links to use equivalent libraries:
ln -s libssl.so.0.9.8 libssl.so.4
ln -s libcrypto.so.0.9.8 libcrypto.so.4

The referenced url is for 64 bit but this is not a 64 bit specific issue. My system is 32 bit.

---

### Post by rob89 on 2014-08-11
I'm on 14.04 and the libraries are newer. If you don't link these libraries the client will still start but you may observe agnclientd hitting 100% CPU and get you'll an incorrect password message even though the password is correct.

 Best thing is:

cd /lib/i386-linux-gnu
ls libssl*
ls libcrypto*

in my case I got:

libssl.so.1.0.0 & libcrypto.so.1.0.0

so, as an example, and for others on Ubuntu 14.04, these were the commands I needed:

sudo ln -s libssl.so.1.0.0 libssl.so.4
ln -s libcrypto.so.1.0.0 libcrypto.so.4

If you haven't got this far because you can't find the bits you need to get to this point, then probably download links have gone or something. Follow these steps (99% of credit due to tummy as per link above):

Grab the rpm:
[ftp://ftp.prserv.net/pub/custom/ibm_linux/agnclient-1.0-2.0.1.3003.i386.rpm](ftp://ftp.prserv.net/pub/custom/ibm_linux/agnclient-1.0-2.0.1.3003.i386.rpm)

Get alien if you don't alrady have it:
sudo apt-get install alien

covert the rpm to a .deb (which will appear in your current directory)
sudo alien agnclient-1.0-2.0.1.3003.i386.rpm

install result of above step:
sudo dpkg -i agnclient_1.0-3_i386.deb

get those libraries to be found (an incorrect password message suggests this bit hasn't been done right, kill daemon & start again on this bit):
cd /lib/i386-linux-gnu
sudo ln -s libssl.so.1.0.0 libssl.so.4
sudo ln -s libcrypto.so.1.0.0 libcrypto.so.4

INSTALL BIT NOW COMPLETE. Let's run the VPN client:

run agent daemon:
sudo /opt/agns/bin/agnclientd&

run att network client
sudo /opt/agns/bin/agnclient&

---

### Post by vcesar on 2014-11-05
Thank you rob89 so much!!!! 
it worked for me 
I am using Ubuntu 14.04 32 bits

---

