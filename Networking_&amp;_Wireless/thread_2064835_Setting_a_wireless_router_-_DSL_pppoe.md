---
title: "Setting a wireless router - DSL pppoe"
date: 2012-09-30
forum: Networking &amp; Wireless
---

### Post by ppv on 2012-09-30
Greetings,

I have an ad hoc setup on my laptop to share its Internet connection and now bought a wireless router (Trendnet TEW-432BRP). 
But don't know where in its configuration to enter the below details. Can someone please point out or let me know if it's even possible.

For internet access, there is a LAN cable coming in from ISP and has a static IP on it. Then there is a PPPoE connection which I have to dial to get connected to Internet. 

LAN IP - 169.254.xx.xx
subnet - 255.255.0.0 
gateway - 192.168.0.1

PPPoE uses a username and password. The connection is also restricted to a MAC address, my laptop's MAC in this case. I probably would also need MAC cloning. Is that true?

Thanks for any pointers.

---

### Post by Toz on 2012-09-30
Moved to Networking & Wireless.

---

### Post by ppv on 2012-09-30
I will try to upload screenshots of the router's configuration page, if that helps.

---

### Post by ppv on 2012-10-01
bump.

---

### Post by steeldriver on 2012-10-01
it seems like is should be straightforward to setup pppoe on the router (Router Setup --> Internet Connection Type)

[http://www.trendnet.com/asp/download_manager/inc_downloading.asp?iFile=5981](http://www.trendnet.com/asp/download_manager/inc_downloading.asp?iFile=5981)

what exactly is the problem?

---

### Post by ppv on 2012-10-01
thanks steeldriver for the reply.

pppoe setup probably looks to be simpler.

But where should I put the LAN configuration on the router setup page. Should I assign the LAN IP that the ISP has given to the router?

Please note the difference of subnets of the LAN IP and gateway.

I also likely need MAC cloning.

---

### Post by steeldriver on 2012-10-01
I assume you're talking about the WAN side? I'm pretty sure that 169.254.x.y is not a valid WAN side address - usually this would be an address range belonging to your ISP

169.254.x.y addresses are part of the automatic private address range (APIPA) and usually only pop up when the network is misconfigured, I think

According to the manual I linked before, the MAC address can be set as part of the WAN setup, same place you would enter the ISP-supplied WAN IP:

> This screen enables user to set up the router WAN connection, specify the IP
address for the WAN, add DNS numbers, and enter the MAC address.
Connection Type: Select the connection type, either DHCP client, Fixed IP or
PPPoE from the drop-down list.
WAN IP: Select whether user wants to specify an IP address manually, or want
DHCP to obtain an IP address automatically. When Specify IP is selected, type the
IP address, subnet mask, and default gateway in the text boxes. User’s ISP will
provide with this information.
DNS 1/2/3: Type up to three DNS numbers in the text boxes. User’s ISP will
provide with this information.
MAC Address: If required by user’s ISP, type the MAC address of the router WAN
interface in this field.
DNS 1/2/3: Type up to three DNS numbers in the text boxes. User’s ISP will
provide with this information.

---

### Post by ppv on 2012-10-01
ok...let me try it out... get back in a few minutes.

---

### Post by ppv on 2012-10-01
ok..so I tried doing it but on WAN configuration page there is a drop down. I see all the settings fields that are required but they are not all available in a single selection within the drop down. Some settings are available in the "DHCP client or FIXED IP" page while others are available on the "PPPoE" page.


Please see attachment screenshots.

---

### Post by steeldriver on 2012-10-01
well I'm not sure I can offer much advice since I'm not familiar with your setup - in my experience it is username and password for DSL / PPPoE connections and MAC based authentication for cable modems - I've never seen both required

in any case it's not really a Ubuntu question - maybe you would get better advice on your ISP support pages or a router / networking forum?

---

### Post by ppv on 2012-10-01
Thanks steeldriver.

Would you have a suggestion for a router/networking forum.

And probably, would you know if the below is correct or not.

In the standalone laptop scenario, I see the LAN connection configured with the 169.254.x.y details and another WAN miniport pppoe connection, which I dial to connect to internet.

So, the 169 ip belongs to DHCP client page? Or does it belong to the PPPoE page in the screenshots.

---

### Post by steeldriver on 2012-10-01
I'm not very knowledgeable about these things, but I believe you should  ignore the 169.254.xxx.xxx address altogether - it is my understanding  that it's just a guaranteed private (APIPA) IP that (particularly Windows) clients fall  back to when they are expecting a DHCP supplied IP and don't get one

If I were you I would try configuring the WAN as

Connection type: PPPoE
Obtain IP address automatically

with your username and password credentials and see if that 'just works' - if it doesn't and you believe you should have a fixed IP then you will probably need to contact your ISP to get it

---

### Post by ppv on 2012-10-02
ok...thanks.

any recommendation for the router / networking forums?

---

### Post by ppv on 2012-10-04
I have tried searching elsewhere and the issue still remains. It would be great if someone can give some pointers.

Thanks.

---

### Post by ppv on 2012-10-06
Trying one more time on ubuntuforums.

Anyone please. Thanks.

---

### Post by steeldriver on 2012-10-07
Sorry I don't understand what your issue is - what exactly is going wrong?

If you previously connected your PC to a modem directly (using a PPPoE client on the computer) and you have now introduced a router to the mix, then usually you would set up the router to do the PPPoE side of things and then connect the computer to the router with a regular DHCP LAN connection. The computer would just see it as any other wired or wireless ethernet infrastructure connection.

It should be as simple as selecting PPPoE on the WAN side of the router and plugging in your old credentials (username and password)

---

### Post by ppv on 2012-10-11
Thank you steeldriver.

Just seeing your post now as I wasn't expecting any replies on this thread ;)

I will try to simplify it more and list out my setup and issue.


CURRENT SETUP
- A lan cable from ISP connects to my laptop.
- I have to dial-in a "WAN miniport PPPoE" connection on my laptop to get connected to internet. This connection requires a user name and password.
- As per ISP, the internet connection is linked to the MAC address of this particular laptop, so I cannot use another laptop to connect to the internet.
- I have setup ad-hoc networking to share this PPPoE connection over WiFi and that is how my other devices receive internet connection.


DESIRED SETUP
- Use a wireless router in the above conditions to replace the laptop so that the laptop doesn't get tied down to this assumed role of "router".


ISSUE
(Please refer to screenshots in one of my previous posts to help understand the below points.)


Screenshot 1 - wan_menu_dropdown
This lists the type of WAN connections I can use on the router.

Question 1 : should I use "DHCP client or fixed IP" or "PPPoE" in the dropdown.


Screenshot 2 - dhcp_client_fixed_ip_page
This shows the settings available if I select "DHCP client or fixed IP" from the dropdown in screenshot 1.

Question 2 : This has most of the settings that I need to do on the laptop like assigning a LAN IP which the ISP has provided to my laptop, cloning of the MAC address, and so on. But this does not have the option to put in username and password for the PPPoE connection that I have to dial to connect to internet.


Screenshot 3 - pppoe_page 
This shows the settings available if I select "PPPoE" from the dropdown in screenshot 1.

Question 3 : If I use this dropdown, then I can specify the username/password and other things but can't clone the MAC address. 

Question 4 : Is it correct to specify the IP that the ISP has given for LAN connection in here in the "WAN IP" field.

Thank you once again and hope this helps clarify things a bit.

---

