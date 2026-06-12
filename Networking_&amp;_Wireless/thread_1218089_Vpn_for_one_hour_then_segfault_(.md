---
title: "Vpn for one hour then segfault :("
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by thatsdaniel on 2009-07-20
UPDATE: Its not only the VPN, it also in effect when I dont use the VPN, for example the last days when Ive played nexuiz it has just disconnected :(

Hi! I have trouble with my VPN on ubuntu jaunty, it works fine for an hour then it "just", shuts down on me.. :(

I followed this guide: [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

I get this in my /var/log/messages

Jul 20 14:07:07 Jar pppd[11937]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jul 20 14:07:07 Jar pppd[11937]: pppd 2.4.5 started by root, uid 0
Jul 20 14:07:07 Jar pppd[11937]: Using interface ppp0
Jul 20 14:07:07 Jar pppd[11937]: Connect: ppp0 <--> /dev/pts/1
Jul 20 14:07:08 Jar pppd[11937]: CHAP authentication succeeded
Jul 20 14:07:08 Jar pppd[11937]: MPPE 128-bit stateless compression enabled
Jul 20 14:07:08 Jar pppd[11937]: local  IP address nevermindthis
Jul 20 14:07:08 Jar pppd[11937]: remote IP address nevermindthis
Jul 20 14:07:08 Jar pppd[11937]: primary   DNS address nevermindthis
Jul 20 14:07:08 Jar pppd[11937]: secondary DNS address nevermindthis
Jul 20 14:26:02 Jar -- MARK --
Jul 20 14:46:02 Jar -- MARK --
Jul 20 15:06:02 Jar -- MARK --
Jul 20 15:07:09 Jar pppd[11937]: Modem hangup
Jul 20 15:07:09 Jar kernel: [241683.554152] pptpcm[11949]: segfault at 7fffa58de128 ip 0000000000405cbd sp 00007fffa5557930 error 4 in pptp[400000+10000]
Jul 20 15:07:09 Jar pppd[11937]: Connect time 60.1 minutes.
Jul 20 15:07:09 Jar pppd[11937]: Sent 3822104088 bytes, received 1715168782 bytes.
Jul 20 15:07:09 Jar pppd[11937]: Connection terminated.
Jul 20 15:07:09 Jar pppd[11937]: Terminating on signal 15
Jul 20 15:07:09 Jar pppd[11937]: Exit.

Advice? Please halp! :D

---

### Post by jamest09 on 2009-07-20
Is it always for exactly an hour?

---

### Post by thatsdaniel on 2009-07-20
yes it seems like it. sure the vpn has died for a few hours sometime but, otherwise yes.
I thought it could be my router first but i can find any 3600 time out in the tcp/udp settings :( What else could it be?

---

### Post by thatsdaniel on 2009-07-24
Seems like this isnt just the VPN ! :(
When I have played nexuiz the last days, my net suddenly dies :(

yep, seems like its one hour, then dies.

Is there any other, setting I should look into, that could be the cause of this?
As I said before I have looked at my router...

---

