---
title: "Trouble with static ip"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by cyberjar09 on 2010-07-08
Hi i am using a buffalo wireless converter WLI-TX4-G54HP with ubuntu and  am having a real hard time trying to access the web based menu because  im not able to setup the static ip to 1.1.1.2 for my system to access  the buffalo device which is at location 1.1.1.1.

my default router address is 192.168.2.1 and would like to change the buffalo address to something like 192.168.2.200 so that it can be accessed in DHCP (Default) mode from the web browser.

I need help with these values
address: 1.1.1.2 (is what i have set, but still not working)
netmask: 255.255.255.0 (is this right?)
gateway: ??

Thanks alot.

---

### Post by Iowan on 2010-07-08
Are you using Network Manager to set up the static address, or are you editing */etc/network/interfaces*?

---

### Post by cyberjar09 on 2010-07-09
im using system>Preferences>Network Connections

---

### Post by Iowan on 2010-07-09
See if it shows up in Network Manager - or at least affects the results of **ifconfig -a** (issued from a terminal)

---

### Post by gordintoronto on 2010-07-09
If you are connected, you should be able to type the address of the router (192.168.2.1) into the address bar of Firefox to access the router.

How did 1.1.1.1 and 1.1.1.2 come into the discussion? They are not useful addresses.

---

### Post by cyberjar09 on 2010-07-10
> **gordintoronto said:**
> If you are connected, you should be able to type the address of the router (192.168.2.1) into the address bar of Firefox to access the router.

How did 1.1.1.1 and 1.1.1.2 come into the discussion? They are not useful addresses.

I'm trying to connect to my buffalo ethernet device which is configured for 1.1.1.2 . In order to do that the manual says to set up a static up of 1.1.1.1. 
Please some1 give me values which I can directly enter into the appropriate fields so I can access the buffalo device and then change its up to something a lil less painful..

Thx..

---

### Post by Iowan on 2010-07-10
You *should* be able to set up a manual address with Network Manager. When setting up details, remember to hit [ENTER] - or the settings won't get saved...

---

### Post by capscrew on 2010-07-10
> **gordintoronto said:**
> If you are connected, you should be able to type the address of the router (192.168.2.1) into the address bar of Firefox to access the router.

How did 1.1.1.1 and 1.1.1.2 come into the discussion? They are not useful addresses.

This device is quirky.  It's factory default address is 1.1.1.1.  The user has to temporarily change his laptop or desktop to an IP that is compatable (i.e. 1.1.1.2) and then change the IP address of the device to the subnet the users LAN really is.  Pretty dumb, eh.

This doesn't help the OP, but after reading the manual I just had to answer your question.

---

### Post by capscrew on 2010-07-10
> **cyberjar09 said:**
> I'm trying to connect to my buffalo ethernet device which is configured for 1.1.1.2 . In order to do that the manual says to set up a static up of 1.1.1.1. 
Please some1 give me values which I can directly enter into the appropriate fields so I can access the buffalo device and then change its up to something a lil less painful..

Thx..

What does you manual say again?  I think you had it right in the first post.  The Buffalo is 1.1.1.1 and you lappy or desktop needs to be 1.1.1.2 or some such.

Either way, if you configure the IP address and subnet mask and you are connected directly (via Ethernet cable) that is all you need.  Since this is a known address on the same subnet (because you set it that way) you do not need a gateway address.

---

### Post by cyberjar09 on 2010-07-11
> **cyberjar09 said:**
> Hi i am using a buffalo wireless converter WLI-TX4-G54HP with ubuntu and  am having a real hard time trying to access the web based menu because  im not able to setup the static ip to 1.1.1.2 for my system to access  the buffalo device which is at location 1.1.1.1.

my default router address is 192.168.2.1 and would like to change the buffalo address to something like 192.168.2.200 so that it can be accessed in DHCP (Default) mode from the web browser.

[B]I need help with these values
address: 1.1.1.2 (is what i have set, but still not working)
netmask: 255.255.255.0 (is this right?)
gateway: ??[/B]

Thanks alot.

Please pay attention to the part in bold. 

I need someones help because i dont know what values to fill in when confiiguring my static ip.

please fill these out for me so that i may access my silly buffalo device.

Thank you.

---

### Post by DrMelon on 2010-07-11
> **cyberjar09 said:**
> Please pay attention to the part in bold. 

I need someones help because i dont know what values to fill in when confiiguring my static ip.

please fill these out for me so that i may access my silly buffalo device.

Thank you.

Your gateway will be your router's address.

---

### Post by cyberjar09 on 2010-07-11
> **DrMelon said:**
> Your gateway will be your router's address.

So would this work?

address: 1.1.1.2 
netmask: 255.255.255.0 
gateway: 192.168.2.1 (currently my routers ip)

---

### Post by Iowan on 2010-07-11
> **capscrew said:**
>  Since this is a known address on the same subnet (because you set it that way) you do not need a gateway address.Gateway address *shouldn't* matter. I saw one thread that suggested 0.0.0.0...

---

### Post by cyberjar09 on 2010-07-12
i

---

### Post by cyberjar09 on 2010-07-12
address: 1.1.1.1
netmask: 255.255.255.0 
gateway: 192.168.2.1

Now when i type 1.1.1.2 in the browser to access the buffalo device it **still** does not load the page.

Please help me.

---

### Post by Iowan on 2010-07-12
If the Buffalo is using 1.1.1.1, this would (should) work better:> **cyberjar09 said:**
> address: 1.1.1.2 
netmask: 255.255.255.0 
gateway: 192.168.2.1 (currently my routers ip)
Check (from a terminal) **ifconfig -a** to verify address - restart/reboot if necessary...

---

### Post by TWGTech on 2010-07-12
First, what is your buffalo ethernet device? is it a NIC, NAS, SAN...what? Is it physically separate from your client, but connected to your router?

Second, if your router is 192.168.2.1, and you're connecting to the buffalo through your router, you first have to connect to the router with your client. So, your IP needs to be on the 192.168.2.0/24 network. All that's needed for a network to function is IP and Netmask. The gateway is not need if you are not leaving the subnet. If you are leaving the Subnet, then the GW is the address of your router, and is required.

Now, if your Buffalo device IS connected to the router, then it, too needs a 192.168.2.0/24 address, not a 1.1.1.1. 

If you connect directly from the client to the Buffalo device (NOT through the router), then you will probably need a cross-over cable, and the 1.1.1.2/24 config. Direct connections do not require a gateway, since there is no gateway present.

---

### Post by cyberjar09 on 2010-07-12
> **Iowan said:**
> If the Buffalo is using 1.1.1.1, this would (should) work better:
Check (from a terminal) **ifconfig -a** to verify address - restart/reboot if necessary...

Thanks Iowan, 

i have attached a screenshot of what is happening for you to see. 

i restarted and ensured that ifconfig -a showed my new ip 

what do i do now?

---

### Post by cyberjar09 on 2010-07-12
> **TWGTech said:**
> First, what is your buffalo ethernet device? is it a NIC, NAS, SAN...what? Is it physically separate from your client, but connected to your router?

Second, if your router is 192.168.2.1, and you're connecting to the buffalo through your router, you first have to connect to the router with your client. So, your IP needs to be on the 192.168.2.0/24 network. All that's needed for a network to function is IP and Netmask. The gateway is not need if you are not leaving the subnet. If you are leaving the Subnet, then the GW is the address of your router, and is required.

Now, if your Buffalo device IS connected to the router, then it, too needs a 192.168.2.0/24 address, not a 1.1.1.1. 

If you connect directly from the client to the Buffalo device (NOT through the router), then you will probably need a cross-over cable, and the 1.1.1.2/24 config. Direct connections do not require a gateway, since there is no gateway present.

Thanks for the info TWGTech,

I am using a [buffalo wireless converter WLI-TX4-G54HP]("http://www.buffalo-technology.com/products/wireless/wireless-g-mimo-performance/wli-tx4-g54hp-wireless-g-mimo-performance-ethernet-converter/").

The manual says that i have to set my static ip to 1.1.1.1 so that i may access the devices web interface via its ip address of 1.1.1.2 

I have tried connecting the device directly to the desktop and shown a screenshot of the result in the prev post. 

I also tried connecting the device to my router and ran thru numbers 1-20 and then finally i punched in 255 and gave up when the browser dint show any page.

I have a rapsody player at home and want to be able to hook it up to my wifi but it only accepts ethernet rj45 so i need this buffalo device. 

Thanks again.

---

### Post by Iowan on 2010-07-12
> **cyberjar09 said:**
> 
The manual says that i have to set my static ip to 1.1.1.1 so that i may access the devices web interface via its ip address of 1.1.1.2 

One of us has it backwards - my understanding was that the Buffalo had the 1.1.1.1 IP address, and the configuring machine is 1.1.1.2 (-up to 1.1.1.254). 

Again, if the Buffalo is using 1.1.1.1, enter that into your browser. If the Buffalo is at 1.1.1.2, then post #11 would be right... but you say it doesn't work.

The next trick may be the cable. A gigabit interface might auto-configure, but the stuff I work with (100MBit) requires a crossover cable directly between devices ( or a hub/switch with straight cables).

---

### Post by cyberjar09 on 2010-07-12
> **Iowan said:**
> One of us has it backwards - my understanding was that the Buffalo had the 1.1.1.1 IP address, and the configuring machine is 1.1.1.2 (-up to 1.1.1.254). 

Again, if the Buffalo is using 1.1.1.1, enter that into your browser. If the Buffalo is at 1.1.1.2, then post #11 would be right... but you say it doesn't work.

The next trick may be the cable. A gigabit interface might auto-configure, but the stuff I work with (100MBit) requires a crossover cable directly between devices ( or a hub/switch with straight cables).

Thanks alot IOWAN. It turns out there was a problem with the cable. I used some other cable I had lying around and viola! it was up and running. 

Thanks again one and all!
The community is really what has helped me transition from windows to ubuntu! 
cheers.

---

### Post by bab1 on 2010-07-12
> **cyberjar09 said:**
> ...

The manual says that i have to set my static ip to 1.1.1.1 so that i may access the devices web interface via its ip address of 1.1.1.2 

Folks have been trying to tell you that you have it wrong.  The manual does not state that.  It says the Buffalo is 1.1.1.1 and you should set your computer to 1.1.1.2.  From the manual [I]"**[COLOR="Red"]The Ethernet Converter has an IP address of 1.1.1.1 by default.[/COLOR]** You'll need to configure
the computer to be on the same subnet;[B][COLOR="Green"] an IP address of 1.1.1.2 is recommended for the
computer."[/COLOR][/B][/I]> 

I have tried connecting the device directly to the desktop and shown a screenshot of the result in the prev post. 

And everyone has been telling you you have it backwards.

...Further on in the manual it states: *"To configure the Ethernet Converter in the future, [COLOR="RoyalBlue"]**a user must both know its [ Buffalo] IP address, and, be on the same subnet.**[/COLOR] Be careful when changing the Ethernet Converter&#8217;s IP address!*

So, do you know what the converters address is?  I don't think you really do.

---

### Post by cyberjar09 on 2010-07-12
> **bab1 said:**
> I tried to tell you the other day that this was wrong.  The manual does not state that.  It says the Buffalo is 1.1.1.1 and you should set your computer to 1.1.1.2.  From the manual [I]"**[COLOR="Red"]The Ethernet Converter has an IP address of 1.1.1.1 by default.[/COLOR]** You'll need to configure
the computer to be on the same subnet;[B][COLOR="Green"] an IP address of 1.1.1.2 is recommended for the
computer."[/COLOR][/B][/I]And everyone has been telling you you have it backwards.

...Further on in the manual it states: *"To configure the Ethernet Converter in the future, [COLOR="RoyalBlue"]**a user must both know its [ Buffalo] IP address, and, be on the same subnet.**[/COLOR] Be careful when changing the Ethernet Converter’s IP address!*



So, do you know what the converters address is?  I don't think you really do.

Hi Bab,

yes you are right I had it the other way round. 

I apologize for not checking clearly and making every1 run in circles. 

thanks.

---

### Post by bab1 on 2010-07-12
> **cyberjar09 said:**
> Hi Bab,

yes you are right I had it the other way round. 

I apologize for not checking clearly and making every1 run in circles. 

thanks.

So does it work now????

If so then mark the thread solved (see THREAD TOOLS).

---

### Post by Iowan on 2010-07-12
\\:D/ This one is gonna look GOOD preceeded by  [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")  =D>

---

### Post by cyberjar09 on 2010-07-12
done...

---

