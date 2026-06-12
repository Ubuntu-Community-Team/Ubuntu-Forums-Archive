---
title: "Tethering with the Blackberry Bold and ATT"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by st1ck3m_tux on 2009-04-26
**Tethering with the Blackberry Bold** 

Here is a quick tutorial on how to accomplish tethering in Ubuntu 9.04  via bluetooth and the blackberry bold.

The first thing you need to do is to head over  to [http://forums.crackberry.com/showthread.php?t=114019](http://forums.crackberry.com/showthread.php?t=114019) and follow that  article up to the point where you need the PPP scripts.  Thank you bthoward for the great tutorial!  

Now that your computer and your Blackberry are paired it is time to setup tethering.  This is actually very easy.  You need to add two files.  The first file that you need should look like the following and should be placed in the /etc/ppp/peers directory. Att does not require a user or password. The name of the file doesn't matter, just make sure that it makes sense, and you can remember it. I have named it BluetoothDialup.

[B]debug 
noauth 
connect "/usr/sbin/chat -v -f /etc/chatscripts/AttGPRS" 
usepeerdns 
/dev/rfcomm0 115200 
defaultroute 
crtscts 
lcp-echo-failure 0 
user "" 
password "" 
[/B]
The next file that you need should be placed in the /etc/chatscripts directory.  This file needs to be named AttGPRS as it is referenced in the first file that we created above, and it should contain the following content.

[B]TIMEOUT 35 
ECHO    ON 
ABORT   '\nBUSY\r' 
ABORT   '\nERROR\r' 
ABORT   '\nNO ANSWER\r' 
ABORT   '\nNO CARRIER\r' 
ABORT   '\nNO DIALTONE\r' 
ABORT   '\nRINGING\r\n\r\nRINGING\r' 
''      \rAT 
OK      'AT+CGDCONT=1,"IP","isp.cingular"' 
OK      ATD*99***1# 
CONNECT ""[/B]

Make sure that you have a tethering plan.  The isp.cingular APN is the APN you need.  The wap.cingular is not recommended, and isn't reliable for tethering.  I did also edit the file /etc/ppp/peers/provider. Under the comment that says &#8220; #Serial device to which the modem is connected.&#8221; it read  &#8220;/dev/modem&#8221; and I changed that to &#8220;/dev/rfcomm0&#8221;, but I don't think that it is necessary.  
.
After you have added all of the correct files in the correct places you should be able to open a terminal and type the command &#8220;sudo pon BluetoothDialup&#8221; replacing BluetoothDialup with the file that you placed in the /etc/ppp/peers directory.  Open another terminal window and type &#8220;tail -f /var/log/messages&#8221; and if everything is working you should see something similar to the following:

[B]Apr 22 16:51:43 <Your Computer Name> pppd[4343]: pppd 2.4.5 started by root, uid 0 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: timeout set to 35 seconds 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: abort on (\nBUSY\r) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: abort on (\nERROR\r) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: abort on (\nNO ANSWER\r) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: abort on (\nNO CARRIER\r) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: abort on (\nNO DIALTONE\r) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: abort on (\nRINGING\r\n\r\nRINGING\r) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: send (^MAT^M) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: expect (OK) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: AT^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: OK 
Apr 22 16:51:45 <Your Computer Name> chat[4346]:  -- got it 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: send (AT+CGDCONT=1,"IP","isp.cingular"^M) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: expect (OK) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: AT+CGDCONT=1,"IP","isp.cingular"^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: OK 
Apr 22 16:51:45 <Your Computer Name> chat[4346]:  -- got it 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: send (ATD*99***1#^M) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: expect (CONNECT) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ATD*99***1#^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: CONNECT 
Apr 22 16:51:45 <Your Computer Name> chat[4346]:  -- got it 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: send (^M) 
Apr 22 16:51:45 <Your Computer Name> pppd[4343]: Serial connection established. 
Apr 22 16:51:45 <Your Computer Name> pppd[4343]: Using interface ppp0 
Apr 22 16:51:45 <Your Computer Name> pppd[4343]: Connect: ppp0 <--> /dev/rfcomm0 
Apr 22 16:51:49 <Your Computer Name> pppd[4343]: PAP authentication succeeded 
Apr 22 16:51:49 <Your Computer Name> kernel: [  315.767094] PPP BSD Compression module registered 
Apr 22 16:51:49 <Your Computer Name> kernel: [  315.785411] PPP Deflate Compression module registered 
Apr 22 16:51:49 <Your Computer Name> pppd[4343]: local  IP address 166.129.189.246 
Apr 22 16:51:49 <Your Computer Name> pppd[4343]: remote IP address 169.254.1.1 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: AT+CGDCONT=1,"IP","isp.cingular"^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: OK 
Apr 22 16:51:45 <Your Computer Name> chat[4346]:  -- got it 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: send (ATD*99***1#^M) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: expect (CONNECT) 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ATD*99***1#^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: ^M 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: CONNECT 
Apr 22 16:51:45 <Your Computer Name> chat[4346]:  -- got it 
Apr 22 16:51:45 <Your Computer Name> chat[4346]: send (^M) 
Apr 22 16:51:45 <Your Computer Name> pppd[4343]: Serial connection established. 
Apr 22 16:51:45 <Your Computer Name> pppd[4343]: Using interface ppp0 
Apr 22 16:51:45 <Your Computer Name> pppd[4343]: Connect: ppp0 <--> /dev/rfcomm0 
Apr 22 16:51:49 <Your Computer Name> pppd[4343]: PAP authentication succeeded 
Apr 22 16:51:49 <Your Computer Name> kernel: [  315.767094] PPP BSD Compression module registered 
Apr 22 16:51:49 <Your Computer Name> kernel: [  315.785411] PPP Deflate Compression module registered 
Apr 22 16:51:49 <Your Computer Name> pppd[4343]: local  IP address 166.129.189.245
Apr 22 16:51:49 <Your Computer Name> pppd[4343]: remote IP address 169.254.1.1 
Apr 22 16:51:49 <Your Computer Name> pppd[4343]: primary   DNS address 209.183.54.151 
[/B]
I hope that this helps.  Have fun.

---

