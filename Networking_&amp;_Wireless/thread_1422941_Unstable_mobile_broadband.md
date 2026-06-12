---
title: "Unstable mobile broadband"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by Tron87 on 2010-03-06
Hi,
I have just switched to Ubuntu from Win 7 RC. So far its been fun, learning to use terminal and all. But I have got a problem now I cannot find a solution to. 
I am using 3 Mobile Broadband. The thing just worked - I plugged it in, created a new connection, modified config a little and was happily browsing.
However, it started acting out yesterday. When I boot the system with the modem plugged in, the USB stick is recignised and NetworkManager starts connecting (I have auto connect on). It then shows the "connected" message, and generally appears working fine. On the other hand, I cannot open a single page in Firefox, it shows the default server not found page.
I used the approach Windows taught me: close, open, retry. I unmount the 3 Mobile Broadband drive, pull the modem out and reconnect it. NetworkManager then does it's job and this time everything works.
I nether had this problem in Win7 or Vista. It looks to me something goes wrong during the booting when the modem is plugged in.
So, any help would be appreciated.
PS I hope world-famous newbie-friendly community support is more than a myth =)

---

### Post by Pauligrinder on 2010-03-06
> **Tron87 said:**
> 
When I boot the system with the modem plugged in, the USB stick is recignised and NetworkManager starts connecting (I have auto connect on). It then shows the "connected" message, and generally appears working fine. On the other hand, I cannot open a single page in Firefox, it shows the default server not found page.

This is apparently a bug in NetworkManager, I get the same with my Elisa 3G here in Finland. The problem is that the modem isn't getting the DNS adresses automatically. I believe I solved this this way:
Right click networkmanager in the tray -> Connection Information -> Write the DNS-addresses for the 3G connection somewhere.
Then:
Right click networkmanager in the tray -> Edit Connections -> Mobile Broadband -> your mobile broadband -> Edit -> IPV4 Settings
Then choose "Automatic (PPP) adresses only" in the method dialog. Then you can manually type the DNS:s you wrote up, and that way it won't have to autodetect them :) Problem solved.

---

### Post by spiky001 on 2010-03-06
Hi I have the same prob have had a look at what you said, mine shows 2 DNS, primary & secondary they are different addresses should I just use the primary address

---

### Post by Pauligrinder on 2010-03-06
> **spiky001 said:**
> Hi I have the same prob have had a look at what you said, mine shows 2 DNS, primary & secondary they are different addresses should I just use the primary address

Use both, just put a space between them.

---

### Post by spiky001 on 2010-03-06
thanks for that

---

### Post by Tron87 on 2010-03-06
Thank you! You made my day =) I was afraid I would have to indulge in some kind of terminal kung-fu =)

---

### Post by alexfish on 2010-03-08
hi all

The on going saga of the Network Manager failing to return the NS1 and  NS2
IE the modem connects but the Browser and updates etc fail to  connect

Here I have change the IPCP configure-NAKs returned  before starting , remove the # and set the number to 30 ( or any thing  above the default value till there is a constant connection )

Code:

sudo  gedit /etc/ppp/options

# Set the maximum number of IPCP  configure-NAKs returned before starting
# to send configure-Rejects  instead to <n> (default 10).
ipcp-max-failure 30

save and exit

Hopefully leaving the NM IPv4 settings to Automatic (PPP) instead of  Setting the NM to IPv4 settings to Automatic (PPP) address only and  having to enter the numerical addresses in the DNS servers text box.

regards

alexfish

---

### Post by mahmoudmohammed80 on 2012-01-21
hi really i need help my mobile broadband doe not stable connection and internet speed is very slow  . have you any ideas  how can i solve this thanks a lot

---

